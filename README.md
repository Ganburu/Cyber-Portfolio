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

1. What is the likely IPv4 address of someone from the Po1s0n1vy group scanning imreallynotbatman.com for web application vulnerabilities? <h3>40.80.148.42(posionivy)?</h3>

To start my search I inputed __index=* sourcetype=fgt* "imreallynotbatman.com"__ into the Splunk search. Since I do not know which index to look through I put "index*" (* *is a wildcard, which means that all indxes will be displayed*) so Splunk can search through all the indexes of Wayne Enterprises. I only wanted to search through the sourcetype fgt(Fortinet Fortigate), which is a NGFW(Next Generation Firewall) that logs network traffic crossing from internal to external, any alerts/blocks, layer 7 protection, and events that the Fortigate device logs. I also did not know what type of logs to pull from fgt. I put "fgt*" because this will pull all fgt type logs for display. To narrow down this search I was only interested in logs that were related to the **"imnotreallybatman.com"** domain. I added this on to the end of my search query. This resulted in 13,918 events. While scrolling through the first page I saw the attack field which intrigued me. I clicked on this field and saw "Acunetix.Web.Vulnerability.Scanner" which is a web vunerability scannner. The number of files it scanned had a count of 4,145. Hmmm seems odd... I clicked on "Acunetix.Web.Vulnerability.Scanner" which automatically added it to my search query. It returned back the list of 4,145 events mentioned earlier. I expanded the first log an saw a source Ip address of  40.80.148.42. This could possiblly be an IP address from the hacker group know as Po1s0n1vy.

![image](https://github.com/user-attachments/assets/bbc2711d-d2cb-45e8-bfa4-43cdd34ea0d9)

![image](https://github.com/user-attachments/assets/3ffae2b6-af13-42d8-9f89-888a31466226)

![image](https://github.com/user-attachments/assets/7ec0e6bb-fbf8-47c5-a883-f1103da7528f)






    192.168.250.70(imreallynotbatman.com)

2. What company created the web vulnerability scanner used by Po1s0n1vy? ###Acunetix

   I found the company that created the vulnerablity scanner in the first log, the exact same way I found the Po1sn0n1vy IP address. 

![image](https://github.com/user-attachments/assets/a4bbf9e1-fc6b-430d-8686-ce30a828c088)

What content management system is imreallynotbatman.com likely using?

What is the name of the file that defaced the imreallynotbatman.com website? Please submit only the name of the file with extension?

This attack used dynamic DNS to resolve to the malicious IP. What fully qualified domain name (FQDN) is associated with this attack?

What IPv4 address has Po1s0n1vy tied to domains that are pre-staged to attack Wayne Enterprises?

What IPv4 address is likely attempting a brute force password attack against imreallynotbatman.com?

What is the name of the executable uploaded by Po1s0n1vy?

What is the MD5 hash of the executable uploaded?

GCPD reported that common TTPs (Tactics, Techniques, Procedures) for the Po1s0n1vy APT group, if initial compromise fails, is to send a spear phishing email with custom malware attached to their intended target. This malware is usually connected to Po1s0n1vys initial attack infrastructure. Using research techniques, provide the SHA256 hash of this malware.

What special hex code is associated with the customized malware discussed in question 111?

What was the first brute force password used?

One of the passwords in the brute force attack is James Brodsky's favorite Coldplay song. We are looking for a six character word on this one. Which is it?

What was the correct password for admin access to the content management system running "imreallynotbatman.com"?

What was the average password length used in the password brute forcing attempt?

How many seconds elapsed between the time the brute force password scan identified the correct password and the compromised login?

How many unique passwords were attempted in the brute force attempt?
