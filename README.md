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

2. What company created the web vulnerability scanner used by Po1s0n1vy? **Acunetix**

I found the company that created the vulnerablity scanner in the first log, the exact same way I found the Po1sn0n1vy IP address. 

![image](https://github.com/user-attachments/assets/a4bbf9e1-fc6b-430d-8686-ce30a828c088)

3. What content management system is imreallynotbatman.com likely using? <h3>Joomla.</h3>

 _Here is the search I used (index=* sourcetype=fgt* "imreallynotbatman.com") clicked on second log_

![image](https://github.com/user-attachments/assets/ab63f493-c929-41de-8ac5-f83d0f714a91)


4. What is the name of the file that defaced the imreallynotbatman.com website? Please submit only the name of the file with extension? **poisonivy-is-coming-for-you-batman.jpeg**

Here is my Splunk query *(index=botsv1 sourcetype="suricata" event_type="http" src_ip = 192.168.250.70)* The focus here is on identifying events where the web server's IP address is the source. Typically, a web server appears as the destination, but in this scenario, the attacker gained control of the server and downloaded the defacement file from an external site.

![image](https://github.com/user-attachments/assets/f0dfc84c-916c-4faa-9585-20dd695078df)

Investigating the first log I found my answer.

![image](https://github.com/user-attachments/assets/ad7c6d5a-5cfc-4143-b1a7-7e5f9d725186)

5. This attack used dynamic DNS to resolve to the malicious IP. What fully qualified domain name (FQDN) is associated with this attack? <h3>prankglassinebracket.jumpingcrab.com</h3>

I used the same method as number four to find this answer.

![image](https://github.com/user-attachments/assets/1669e1c3-997b-4262-825d-9e45708ff897)


6. What IPv4 address has Po1s0n1vy tied to domains that are pre-staged to attack Wayne Enterprises? <h3>23.22.63.114</h3>

Found in the same manner as 4 & 5.

![image](https://github.com/user-attachments/assets/044f0423-8c15-4a26-9a5e-bc041a57016f)


7. What IPv4 address is likely attempting a brute force password attack against imreallynotbatman.com? **23.22.63.114**

(index=botsv1 sourcetype="suricata" "imreallynotbatman.com" | stats count by src_ip) I used this SPL(Splunk) query because I wanted to know what IP addresses where communicating with the "imreallynotbatman.com" IP via suricata logs and how often via the stats count by SPL command . There where 3 Ip addresses. Two of which I am already familiar with. The "imreallynotbatman.com" IP and the other Po1s0n1vy IP addresses which was doing the vulnerablity scan. This 23.22.63.114 IP is new and unfamiliar to me. This is could be the address that was performing a bruteforce attack on the "imreallynotbatman.com" domain.   

![image](https://github.com/user-attachments/assets/8f7d0b29-4fbf-4f17-9998-c0dc88ee4770)

Investigating the unfamiliar IP address, I see that under my SPL search this address produced 1648 events, all but one event happended at 9:46pm. That is suspicious, this IP address is the number one suspect for the bruteforce attack.

![image](https://github.com/user-attachments/assets/c484d8f2-24a5-482a-8c6c-73d5db5addb1)



What is the name of the executable uploaded by Po1s0n1vy? **3791.exe**

Here is the SPL command I used (index=botsv1 sourcetype="suricata" "imreallynotbatman.com" "*.exe") I was only interested in logs that contained .exe. Thus alist of 55 events displayed and this the 3791.exe is unfamiliar to me....this has to be it.

![image](https://github.com/user-attachments/assets/36dc8384-82fa-4b1f-9c5d-500073f6329c)


What is the MD5 hash of the executable uploaded?

GCPD reported that common TTPs (Tactics, Techniques, Procedures) for the Po1s0n1vy APT group, if initial compromise fails, is to send a spear phishing email with custom malware attached to their intended target. This malware is usually connected to Po1s0n1vys initial attack infrastructure. Using research techniques, provide the SHA256 hash of this malware.

What special hex code is associated with the customized malware discussed in question 111?

What was the first brute force password used?

One of the passwords in the brute force attack is James Brodsky's favorite Coldplay song. We are looking for a six character word on this one. Which is it?

What was the correct password for admin access to the content management system running "imreallynotbatman.com"?

What was the average password length used in the password brute forcing attempt?

How many seconds elapsed between the time the brute force password scan identified the correct password and the compromised login?

How many unique passwords were attempted in the brute force attempt?
