<h1> Web site defacement </h1>

This lab is from https://bots.splunk.com/event/3oQ7sqI5bajOCP43o0svqT/scenario/2QHRWttYFUcUA08zIgie5w

Resources: 

https://gettingstarted.splunk.show

https://botscontent.netlify.app/v1/bots_sourcetypes.html

https://www.splunk.com/pdfs/solution-guides/splunk-quick-reference-guide.pdf

https://botscontent.netlify.app/v1/gcpd-poisonivy-memo.html

https://botscontent.netlify.app/v1/alice-journal.html

https://botscontent.netlify.app/v1/mission_document.html

![image](https://github.com/user-attachments/assets/e7b82b8a-94ad-482e-8862-6e4605cc75c9)

Questions:

1. What is the likely IPv4 address of someone from the Po1s0n1vy group scanning imreallynotbatman.com for web application vulnerabilities? **40.80.148.42(posionivy)**

To start my investigation I inputed __index=* sourcetype=fgt* "imreallynotbatman.com"__ into the Splunk search. Since I do not know which index to look through I put "index*" (* *is a wildcard, which means that all indxes will be displayed*) so Splunk can search through all the indexes of Wayne Enterprises. I only wanted to search through the sourcetype fgt(Fortinet Fortigate), which is a NGFW(Next Generation Firewall) that logs network traffic crossing from internal to external, any alerts/blocks, layer 7 protection, and events that the Fortigate device logs. I also did not know what type of logs to pull from fgt. I put "fgt*" because this will pull all fgt type logs for display. To narrow down this search I was only interested in logs that were related to the **"imnotreallybatman.com"** domain. I added this on to the end of my search query. This resulted in 13,918 events. While scrolling through the first page I saw the attack field which intrigued me. I clicked on this field and saw "Acunetix.Web.Vulnerability.Scanner" which is a web vunerability scannner. The number of files it scanned had a count of 4,145. Hmmm seems odd... I clicked on "Acunetix.Web.Vulnerability.Scanner" which automatically added it to my search query. It returned back the list of 4,145 events mentioned earlier. I expanded the first log and saw a source Ip address of  40.80.148.42. This could possiblly be an IP address from the hacker group known as Po1s0n1vy.

![image](https://github.com/user-attachments/assets/bbc2711d-d2cb-45e8-bfa4-43cdd34ea0d9)

![image](https://github.com/user-attachments/assets/3ffae2b6-af13-42d8-9f89-888a31466226)

![image](https://github.com/user-attachments/assets/7ec0e6bb-fbf8-47c5-a883-f1103da7528f)

2. What company created the web vulnerability scanner used by Po1s0n1vy? **Acunetix**

I found the company that created the vulnerablity scanner in the first log, the exact same way I found the Po1sn0n1vy IP address. 

![image](https://github.com/user-attachments/assets/a4bbf9e1-fc6b-430d-8686-ce30a828c088)

3. What content management system is imreallynotbatman.com likely using? **Joomla.**

 _Here is the search I used (index=* sourcetype=fgt* "imreallynotbatman.com") clicked on second log_

![image](https://github.com/user-attachments/assets/ab63f493-c929-41de-8ac5-f83d0f714a91)


4. What is the name of the file that defaced the imreallynotbatman.com website? Please submit only the name of the file with extension? **poisonivy-is-coming-for-you-batman.jpeg**

Here is my Splunk query *(index=botsv1 sourcetype="suricata" event_type="http" src_ip = 192.168.250.70)* The focus here is on identifying events where the web server's IP address is the source. Typically, a web server appears as the destination, but in this scenario, the attacker gained control of the server and downloaded the defacement file from an external site.

![image](https://github.com/user-attachments/assets/f0dfc84c-916c-4faa-9585-20dd695078df)

Investigating the first log I found my answer.

![image](https://github.com/user-attachments/assets/ad7c6d5a-5cfc-4143-b1a7-7e5f9d725186)

5. This attack used dynamic DNS to resolve to the malicious IP. What fully qualified domain name (FQDN) is associated with this attack? **prankglassinebracket.jumpingcrab.com**

I used the same method as number four to find this answer.

![image](https://github.com/user-attachments/assets/1669e1c3-997b-4262-825d-9e45708ff897)


6. What IPv4 address has Po1s0n1vy tied to domains that are pre-staged to attack Wayne Enterprises? **23.22.63.114**

Found in the same manner as 4 & 5.

![image](https://github.com/user-attachments/assets/044f0423-8c15-4a26-9a5e-bc041a57016f)


7. What IPv4 address is likely attempting a brute force password attack against imreallynotbatman.com? **23.22.63.114**

*(index=botsv1 sourcetype="suricata" "imreallynotbatman.com" | stats count by src_ip)* I used this SPL(Splunk) query because I wanted to know what IP addresses were communicating with the "imreallynotbatman.com" IP via suricata logs and how often via the stats count by SPL command. There were 3 Ip addresses and two of which I am already familiar with. The "imreallynotbatman.com" IP and the other Po1s0n1vy IP addresses which was doing the vulnerablity scan. This "23.22.63.114" IP is new and unfamiliar to me. This is could be the address that was performing a bruteforce attack on the "imreallynotbatman.com" domain.   

![image](https://github.com/user-attachments/assets/8f7d0b29-4fbf-4f17-9998-c0dc88ee4770)

Investigating the unfamiliar IP address, I see that under my SPL search this address produced 1648 events, all but one event happended at 9:46pm. That is suspicious, this IP address is the number one suspect for the bruteforce attack.

![image](https://github.com/user-attachments/assets/c484d8f2-24a5-482a-8c6c-73d5db5addb1)

8. What is the name of the executable uploaded by Po1s0n1vy? **3791.exe**

Here is the SPL command I used (index=botsv1 sourcetype="suricata" "imreallynotbatman.com" "*.exe") I was only interested in logs that contained .exe. Thus a list of 55 events displayed and the 3791.exe is unfamiliar to me....this has to be it.

![image](https://github.com/user-attachments/assets/36dc8384-82fa-4b1f-9c5d-500073f6329c)

9. What is the MD5 hash of the executable uploaded? **aae3f5a29935e6abcc2c2754d12a9af0**

*(index=botsv1 sourcetype=*  "imreallynotbatman.com" "3791.exe" signature=*)
I added the signature source to the end of my query to find the hash signature for the 3791.exe. Since this is not in MD5 hash format I copied the hash.

![image](https://github.com/user-attachments/assets/64769ee6-f9e6-4a30-834d-4fd19f363479)

I pasted the file in virustotal. Under the details section is where to find the MD5 hash. Oh and btw this is a virus...not good :(.

![image](https://github.com/user-attachments/assets/8c8b8d77-1973-453b-8ad3-daa80ef7caf9)

10. What was the first brute force password used? **12345678**
*(index=botsv1 sourcetype=stream:http  "imreallynotbatman" http_method=POST src_ip=23.22.63.114 | sort _time)*

To find the first brute force password I decided to  sort the Post request from the malicious IP address by time. I selected the first event. Investiagating the event, I found my answer.

![image](https://github.com/user-attachments/assets/45b81ef5-90db-40c1-8a8a-f89b015f882f)

11. One of the passwords in the brute force attack is James Brodsky's favorite Coldplay song. We are looking for a six character word on this one. Which is it? **yellow**

_index=botsv1 sourcetype=stream:http  "imreallynotbatman" form_data="*username=*" form_data="*&passwd=*"
| rex field=form_data "passwd=(?<pw>[y])" 
| rex field=form_data "username=(?<un>\w+)" 
| table _time un pw length_

I know a Coldplay song called yellow. So I just used regex to look for passwords starting with y. I just searched through pages until I saw a y in the pw column and that how I found the password attempt equal to yeallow.

![image](https://github.com/user-attachments/assets/546b112e-8839-4725-a064-ce3cd012598b)

![image](https://github.com/user-attachments/assets/cc3e7892-2934-4aed-bf39-76b16d01ff4a)

12. What was the correct password for admin access to the content management system running "imreallynotbatman.com"?**batman**

_index=botsv1 sourcetype=stream:http  "imreallynotbatman" form_data="*username=*" form_data="*&passwd=*"
| rex field=form_data "passwd=(?<pw>\w+)" 
| rex field=form_data "username=(?<un>\w+)" 
| table _time un pw_

I used regex and created a table to see the last time the brute force attempt happened.

![image](https://github.com/user-attachments/assets/05154dc1-87d7-4199-aba1-99f5fe1d8ff0)

13. What was the average password length used in the password brute forcing attempt? **6**

_index=botsv1 sourcetype=stream:http  "imreallynotbatman" form_data="*username=*" form_data="*&passwd=*"
| rex field=form_data "passwd=(?<pw>\w+)" 
| rex field=form_data "username=(?<un>\w+)" 
| eval length=len(pw) 
| sort length
| table _time un pw length_

To find the average length added the eval command to track the length of passwords then I used the sort command to sort the password list by length. I then visually looked through the pages Splunk provided and saw that the majority of the password lengths were 6.

![image](https://github.com/user-attachments/assets/09b417d6-3cfc-4327-98bd-02c4c531efd5)


14. How many seconds elapsed between the time the brute force password scan identified the correct password and the compromised login?**92.17**

To find this answer I just subtracted the first login attempt time from the last login attempt time.

First login attempt.

![image](https://github.com/user-attachments/assets/df912d25-dcdb-44ca-b926-d4fd7aacb780)


last login attempt.

![image](https://github.com/user-attachments/assets/2508448d-8b5e-4cc3-ac4b-723d68d3486f)



15. How many unique passwords were attempted in the brute force attempt?**412**

_index=botsv1 sourcetype=stream:http  "imreallynotbatman" form_data="*username=*" form_data="*&passwd=*"
| rex field=form_data "passwd=(?<pw>\w+)" 
| rex field=form_data "username=(?<un>\w+)" 
| eval length=len(pw) | table _time un pw length
| dedup pw_

I added "dedup pw" to take out repeated passwords. 

![image](https://github.com/user-attachments/assets/ab619321-f159-4fbd-8c4a-eaf44b87eb35)

