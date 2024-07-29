<h1>Incident Report: Cybersecurity Breach at Wayne Enterprises</h1>

<h2>Date of Incident: September 30, 2016</h2>

<h3>Reported by: Gotham City Police Department (GCPD)</h3>

<h3>Investigated by: Vaughn</h3>

<h3>Incident Summary:</h3>

**On September 30, 2016, the Wayne Enterprises Security Operations Center (SOC) received a memo from the Gotham City Police Department (GCPD) indicating evidence of a compromised website hosted on Wayne Enterprises' IP address space. The compromised website, www.imreallynotbatman.com, is the personal blog of Wayne Enterprises' CEO.**

<h3>Details of Compromise:</h3>

- **Source of Evidence:** The evidence was found online on Pastebin (http://pastebin.com/Gw6dWjS9).

- **Malicious IP Addresses:**
  - 40.80.148.42: Conducted a web vulnerability scan on the website.
  
  - 23.22.63.114: Performed a brute force attack, resulting in a successful login.

- **Malicious Executable: The file 3791.exe was downloaded to the server.** This executable exploits a backdoor and is linked to an unknown process/application.

- **Agent.php Download:** The file agent.php, commonly used in web development, was also downloaded to the server.

- **Dynamic DNS:** The attack utilized dynamic DNS to resolve to the IP address 23.22.63.114, with the FQDN prankglassinebracket.jumpingcrab.com associated with the attack.

<h3>Investigation Findings:</h3>

Using Splunk Enterprise Security SIEM, the SOC identified the two suspicious IP addresses linked to the hacker group Po1s0n1vy. Evidence pointed to the presence of the malicious executable _"3791.exe"_ and _"agent.php"_ on the compromised server.

<h3>Solutions and Remediation:</h3>

1. Immediate Actions:

  - Isolate the Server: Immediately isolate the compromised server to prevent further damage.
  - Remove Malicious Files: Delete  _"3791.exe"_ and _"agent.php"_ from the server.
  - Change Credentials: Change all passwords and review user access controls to prevent unauthorized access.

2. Security Enhancements:

  - Patch Vulnerabilities: Update all web applications and server software to the latest versions to patch known vulnerabilities.
  - Implement Web Application Firewall (WAF): Deploy a WAF to protect against web-based attacks.
  - Enhanced Monitoring: Increase the monitoring of network traffic and logs for suspicious activity using advanced SIEM tools.

3. Long-term Strategies:

  - Employee Training: Conduct regular cybersecurity awareness training for employees.
  - Incident Response Plan: Develop and regularly update an incident response plan to quickly address future breaches.
  - Penetration Testing: Regularly perform penetration testing to identify and fix security weaknesses.

By following these steps, Wayne Enterprises can mitigate the impact of the current breach and strengthen its defenses against future cyber threats.
