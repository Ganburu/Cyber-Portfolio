On September 30, 2016, at the Wayne Enterprises' Security Operations Center(SOC), A memo from Gotham City Police Department (GCPD). Apparently GCPD has found evidence online (http://pastebin.com/Gw6dWjS9) that the website www.imreallynotbatman.com hosted on Wayne Enterprises' IP address space has been compromised. The group has multiple objectives... but a key aspect of their modus operandi is to deface websites in order to embarrass their victim. Lucius,the SOC lead, asked Vaughn to determine if www.imreallynotbatman.com. (the personal blog of Wayne Corporations CEO) was really compromised. Splunk Enterprise Security information and event management(SIEM) was used to invtigate. Found two suspicous IP addresses from malicious hacker group known as Po1s0n1vy. The 40.80.148.42 address performed a web vulnerablity sacn on imreallynotbatman site and the 23.22.63.114 address performed a brute force attack with one sucessful login attempt. This attack used dynamic DNS to resolve to the malicious IP 23.22.63.114. Prankglassinebracket.jumpingcrab.com is the fully qualified domain name (FQDN) that is associated with this attack. It was also found that a malicious executable was indeed downloaded to the "www.imreallynotbatman.com server." The malicious executable is know as 3791.exe. This virus exploits a backdoor and is associated with a process or an application running on system. Agent.php was also downloaded to the www.imreallynotbatman.com server and this download is commonly used in web development and server management. 
