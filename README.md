<h1>Incident Report: Cybersecurity Breach at Wayne Enterprises</h1>

<h2>Date of Incident: September 30, 2016</h2>

<h3>Reported by: Gotham City Police Department (GCPD)</h3>

<h3>Investigated by: Vaughn</h3>

<h3>Incident Summary:</h3>

**On September 30, 2016, the Wayne Enterprises Security Operations Center (SOC) received a memo from the Gotham City Police Department (GCPD) indicating evidence of a compromised website hosted on Wayne Enterprises' IP address space. The compromised website, www.imreallynotbatman.com, is the personal blog of Wayne Enterprises' CEO.**

**Details of Compromise:**

Source of Evidence: The evidence was found online on Pastebin (http://pastebin.com/Gw6dWjS9).
Malicious IP Addresses:
40.80.148.42: Conducted a web vulnerability scan on the website.
23.22.63.114: Performed a brute force attack, resulting in a successful login.
Malicious Executable: The file 3791.exe was downloaded to the server. This executable exploits a backdoor and is linked to an unknown process/application.
Agent.php Download: The file agent.php, commonly used in web development, was also downloaded to the server.
Dynamic DNS: The attack utilized dynamic DNS to resolve to the IP address 23.22.63.114, with the FQDN prankglassinebracket.jumpingcrab.com associated with the attack.
Investigation Findings:

Using Splunk Enterprise Security SIEM, the SOC identified the two suspicious IP addresses linked to the hacker group Po1s0n1vy. Evidence pointed to the presence of the malicious executable 3791.exe and agent.php on the compromised server.

Solutions and Remediation:

Immediate Actions:

Isolate the Server: Immediately isolate the compromised server to prevent further damage.
Remove Malicious Files: Delete 3791.exe and agent.php from the server.
Change Credentials: Change all passwords and review user access controls to prevent unauthorized access.
Security Enhancements:

Patch Vulnerabilities: Update all web applications and server software to the latest versions to patch known vulnerabilities.
Implement Web Application Firewall (WAF): Deploy a WAF to protect against web-based attacks.
Enhanced Monitoring: Increase the monitoring of network traffic and logs for suspicious activity using advanced SIEM tools.
Long-term Strategies:

Employee Training: Conduct regular cybersecurity awareness training for employees.
Incident Response Plan: Develop and regularly update an incident response plan to quickly address future breaches.
Penetration Testing: Regularly perform penetration testing to identify and fix security weaknesses.
By following these steps, Wayne Enterprises can mitigate the impact of the current breach and strengthen its defenses against future cyber threats.


























On September 30, 2016, at the Wayne Enterprises' Security Operations Center(SOC), A memo from Gotham City Police Department (GCPD). Apparently GCPD has found evidence online (http://pastebin.com/Gw6dWjS9) that the website www.imreallynotbatman.com hosted on Wayne Enterprises' IP address space has been compromised. The group has multiple objectives... but a key aspect of their modus operandi is to deface websites in order to embarrass their victim. Lucius,the SOC lead, asked Vaughn to determine if www.imreallynotbatman.com. (the personal blog of Wayne Corporations CEO) was really compromised. Splunk Enterprise Security information and event management(SIEM) was used to invtigate. Found two suspicous IP addresses from malicious hacker group known as Po1s0n1vy. The 40.80.148.42 address performed a web vulnerablity sacn on imreallynotbatman site and the 23.22.63.114 address performed a brute force attack with one sucessful login attempt. This attack used dynamic DNS to resolve to the malicious IP 23.22.63.114. Prankglassinebracket.jumpingcrab.com is the fully qualified domain name (FQDN) that is associated with this attack. It was also found that a malicious executable was indeed downloaded to the "www.imreallynotbatman.com server." The malicious executable is know as 3791.exe. This virus exploits a backdoor and is associated with a process or an application running on system. Agent.php was also downloaded to the www.imreallynotbatman.com server and this download is commonly used in web development and server management. 
