### Ransomware
This lab is from https://bots.splunk.com/event/3oQ7sqI5bajOCP43o0svqT/scenario/5vqgZJanGgTCXawi4nliIF

### Resources: 

Splunk server: https://gettingstarted.splunk.show

Ransomware screen shot: https://botscontent.netlify.app/v1/cerber-sshot.png

Ransomware warning: https://botscontent.netlify.app/v1/cerber-sample-voice.mp3

Bots v1 sourcetype summary: https://botscontent.netlify.app/v1/bots_sourcetypes.html

Splunk quick reference guide: https://www.splunk.com/pdfs/solution-guides/splunk-quick-reference-guide.pdf

Alices journal: https://botscontent.netlify.app/v1/alice-journal.html

Mission document: https://botscontent.netlify.app/v1/mission_document.html

![image](https://github.com/user-attachments/assets/13365371-2e21-490b-a4f7-ccf8710f5f6c)

1. What was the most likely IPv4 address of we8105desk on 24AUG2016? **192.168.250.100**

To find the IP Address I decided to look through windoweventlogs for an IP address pertaining to "we8105desk"

_index="botsv1" sourcetype="wineventlog*"  "we8105desk" "*address"_

![image](https://github.com/user-attachments/assets/7db9830d-6e0a-47a7-ace6-e6cbfe9932cb)

2. Amongst the Suricata signatures that detected the Cerber malware, which one alerted the fewest number of times? Submit ONLY the signature ID value as the answer. **2816763**

To find the alert signature_id that showed up the least amount of times I decided to use the stats count by command. This command will sort the signature_ids and count how many alerts were logged per ID.

index="botsv1" sourcetype="suricata"  "cerber" | stats count by  "alert.signature_id"

![image](https://github.com/user-attachments/assets/57aa7f0e-4707-463f-9e31-30e3cee7e89e)

3. What fully qualified domain name (FQDN) does the Cerber ransomware attempt to direct the user to at the end of its encryption phase? **cerberhhyed5frqa.xmfir0.win**

_index="botsv1" sourcetype="stream:dns" "192.168.250.100" "query_type{}"=A  | table _time "query{}"_

I used the compromised client's IP address to look for DNS Queries that were not blocked. And had a time range set for queries within an half an hour before the last attack. I also made a table of the queries to normalize and sort the data.  _"cerberhhyed5frqa.xmfir0.win"_ stood out as odd while scrolling through the data.

![image](https://github.com/user-attachments/assets/875af7a0-881a-4608-9895-bc5c3e2beac9)

4. What was the first suspicious domain visited by we8105desk on 24AUG2016?**solidaritedeproximite.org**

I used the same query from number 3. I Just clicked on the time field to change the order of the events.

![image](https://github.com/user-attachments/assets/c5afaaa8-3813-43c9-a8f9-6249f0fda52e)

5. During the initial Cerber infection a VB script is run. The entire script from this execution, pre-pended by the name of the launching .exe, can be found in a field in Splunk. What is the length of the value of this field?**4490**

Since the compromised host is using windows and it was a Visual Basic script that was ran on the system, I asked splunk to search for the "we8105desk" host, anything pertaing to ".exe", and event code 1 pertaining to new processes from the "XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" sourcetype. And evaluated the length of the script using the eval command then made a table showing the length of the script, finally sorting the table by length. 

![image](https://github.com/user-attachments/assets/4c7c9657-fc07-48a4-9e33-d06d108b8c37)

6. What is the name of the USB key inserted by Bob Smith?**MIRANDA_PRI**

I read on google that a usb insertion is a windows registry event, doing further research I found out that I needed to know the key path that it would most likely be logged to. I found out the key path using google search and added that key path to my search in splunk along with the winregistry sourcetype.

_index="botsv1" sourcetype="winregistry" key_path="HKLM\\software\\microsoft\\windows portable devices\\devices\\*"_

![image](https://github.com/user-attachments/assets/4afb6317-9c50-46fc-b5be-499f8927d7e1)

7. Bob Smith's workstation (we8105desk) was connected to a file server during the ransomware outbreak. What is the IPv4 address of the file server? **192.168.250.20**

I searched filesharing traffic from the infected device on the date in question, and used the "stats" SPL command to count the most common destination IP for the filesharing.

_index="botsv1" sourcetype="winregistry"  host="we8105desk" fileshare | stats count by object_

![image](https://github.com/user-attachments/assets/c42447ba-1590-4f98-871b-6e876ac4b094)

8. How many distinct PDFs did the ransomware encrypt on the remote file server?**257**

This one was simple. I just commanded splunk to look through all the windows event logs for pdfs pertaing to the infected computer's IP address. I also used the SPL command Dedup to only show the same type of log once.  

_index="botsv1" sourcetype="WinEventLog:*"   192.168.250.100 pdf | dedup Relative_Target_Name_

![image](https://github.com/user-attachments/assets/38478a1b-64b8-478d-ba6e-7ccc69b4b258)


9. The Cerber ransomware encrypts files located in Bob Smith's Windows profile. How many .txt files does it encrypt?**406**

In Sysmon events, EventCode=2 indicates file creation time has changed. So I look at the logs from the _"XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"_ sourcetype and attached the hostname, event code and the C user path, which is Bob smith, then I just used the stats command to tally up the amount of times this event occured. 

_index="botsv1" sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"  host="we8105desk"  EventCode=2 TargetFilename="C:\\Users\\bob.smith.WAYNECORPINC\\*.txt" | stats dc(TargetFilename)_

![image](https://github.com/user-attachments/assets/5a3f6686-38d3-4e80-a080-092343e57b98)

10. The VBscript found in question 204 launches 121214.tmp. What is the ParentProcessId of this initial launch?**3968**

I added the .tmp file and ParentProcessId_ to my search and Splunk showed me 7 events. I looked for the first event that happened and checked out the logs. 

_index="botsv1" sourcetype=* host="we8105desk"  121214.tmp ParentProcessId_

![image](https://github.com/user-attachments/assets/fcc421a5-a8f1-46f0-b265-6920619e0cc7)

11. The malware downloads a file that contains the Cerber ransomware cryptor code. What is the name of that file?**mhtr.jpg**

Since I was looking for potentially malicious file, I started my search with Suricata data and then narrowed down my search by focusing on the attacker remote file sharing IP.

![image](https://github.com/user-attachments/assets/fbd1c987-45d4-4498-9da6-39b9e22a78d7)

12. Now that you know the name of the ransomware's encryptor file, what obfuscation technique does it likely use?**Steganography**

The practice of hiding information within another message or physical object to evade detection


