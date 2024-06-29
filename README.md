This lab is from https://unit42.paloaltonetworks.com/january-wireshark-quiz/

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/0759a55a-ed64-446a-958e-0ba82061bf83)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/8826116d-7363-4267-805b-beb016f6127b)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/cce00ab5-4f95-4d8c-ad41-96ede8789dfe)

To find the date and time the malicious traffic started, the infected IP Address, and Mac Address, I used my basic filter I created "(http.request or tls.handshake.type eq 1) and !(ssdp)" Below, the time the malicious traffic started is highlighted in green, IP address highlighted in yellow and Mac Address highlighted in blue. 

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/95102f7d-7a00-4aef-8e4d-d60d4683fcd1)


I used the filter "nbns" (NetboisNameService) to find the hostname and the user account. In the image below the user account is circled in black and the hostname is highlighted in green.
![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/386901e9-60f0-4460-a63c-a0e3d4b30ce3)


Upon putting this filter in WireShark "(http.request) and !(ssdp)", I found a out of the ordaniary file (Ztvfo.png) in the traffic from the infected IP Address mentioned earlier. I then followed the HTTP stream for this packet. 

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/3b4dcaaa-e16f-4ec8-b245-50d735902781)
Once this window was opened I exported the Ztvfo.png packet for futher investigation. Here are the steps I took, "file > export object > http clicked ztfo.png, clicked saved". The file saved to my home directory.

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/6b4390dd-4380-4767-9255-94a63fc73f9f)

I opened the terminal on linux to get the hash using the bash command sha256sum Ztvfo.png 
![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/63ccaeab-f8e5-4815-8847-0c4237c08ff7)

I then copied the hash and entered into virus total to see if the Ztvfo.png file is malicious. The Ztvfo file is flagged by 5 vendors as a trojan. Take a look.

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/b2b78e45-5c6a-46b6-add6-4f2a890fae05)

Next, I checked the Simple Mail Transfer Protocol (smpt) traffic using the "smpt" filter. These packets represent a single TCP stream of traffic. I then followed the first packet's TCP stream to review the associated email. 

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/3a3ebabf-96f7-44ca-9a22-f4fb947bee28)

I then exported the packet via IMF istead of HTTP like earlier in the lab.

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/73be1915-83c4-4fa3-afaf-b6469642f362)

Once the packet had been exported I opened the file in Thunderbird to see the content of the message.
The email shows information about the infected Windows host, one piece of information that is in the eamil is account credentials saved by the victim’s email client (Thunderbird) and web browser (Microsoft Edge). Stolen data includes information such as the operating system, Windows user account name, CPU, amount of RAM and public IP address of the infected host.

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/f13e2428-692c-4422-bf96-382740069950)



# Incident Report: Malicious Traffic and Data Breach
## Date and Time of Incident: January 5, 2023, at 22:51 UTC

Incident Summary:
On January 5, 2023, at 22:51 UTC, malicious traffic was detected originating from a Windows user account named '**windows11user**'. The investigation revealed that the victim had inadvertently downloaded a Trojan disguised as an image file through an email. The Trojan, identified as '**OriginLogger.exe**', is a key logger executable designed to capture and transmit sensitive information.

**Type of Stolen Data:**

* Email accounts

* Web accounts
Overview of '**OriginLogger.exe**:'

'**OriginLogger.exe**' is a type of key logger malware that records keystrokes on the infected machine. This data is then sent to a remote server controlled by the attacker, allowing them to gain access to sensitive information such as login credentials and other personal data.

Steps Taken to Eliminate the Threat:

Immediate Quarantine and Disconnection:

The infected machine was immediately quarantined and disconnected from the network to prevent further data exfiltration and spread of the malware.
Malware Removal:

Security teams conducted a thorough scan of the infected system using advanced anti-malware tools. The Trojan and any associated malicious files were identified and removed.
System Reimaging:

The affected computer was wiped and re-imaged to ensure complete removal of the malware and to restore the system to a known good state.
Password Resets:

The user windows11user was instructed to change all passwords associated with email and web accounts accessed from the infected machine. This step was crucial to prevent unauthorized access using stolen credentials.
User Education and Training:

The victim and other employees were provided with training on recognizing phishing attempts and the importance of verifying email attachments before opening them.
Enhanced Email Filtering:

Email security protocols were enhanced to include more stringent filtering and scanning of attachments to detect and block potentially malicious files.
Network Monitoring and Alerts:

Continuous network monitoring was implemented to detect unusual activities and to promptly respond to any future threats. Alerts were set up to notify security teams of any suspicious traffic.
Conclusion:
The incident highlighted the importance of robust cybersecurity measures and user awareness in preventing malware infections. By taking swift action to quarantine, remove the malware, and educate users, we mitigated the immediate threat and strengthened our defenses against future attacks. Further measures, including enhanced email security and continuous monitoring, have been implemented to protect our systems and data.



