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

![image](https://github.com/user-attachments/assets/318fd7b1-e923-4613-9986-045eb48d814c)

3. What fully qualified domain name (FQDN) does the Cerber ransomware attempt to direct the user to at the end of its encryption phase? 

4.

5.

6.

7.

8.

9.

10.

11.

12.

13.

14.
