<h1>Cold as Ice: Unit 42 Wireshark Quiz for IcedID</h1>
Lab from https://unit42.paloaltonetworks.com/wireshark-quiz-icedid/

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/e8dfb5ab-5cde-4001-9f38-7e28555bc915)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/45e8a795-5f8c-43f1-82e3-3be580206ee4)

What is the date and time in UTC the infection started? **The date and time is found in the time column in the wireshark app. The order of time should be sorted in ascending order to get the correct infection time. This can also be confirmed by inspecting the first packet and looking at its' details.**

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/3e529328-81f1-4ce9-812c-2fec9f75bd5c)

What is the IP address of the infected Windows client? **Inspecting the first packet details under the source arrow, the Ip address can be found.**

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/6cd60ed7-1eb1-4955-90b3-a2d7b3c2f58f)

What is the MAC address of the infected Windows client? **The mac address can be found in the same way as the mac address.**

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/1b596b48-b65f-455f-a1bc-17aa26d70620)

What is the hostname of the infected Windows client? **There isn't any Dynamic Host Configuration Protocol (DHCP) traffic when filtering. So the host name will have to found through anthoer filtering string called NetBIOS Name Service (NBNS) traffic.**

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/4e5330d2-2b8a-483e-b8cc-24556901a29f)

 What is the user account name from the infected Windows host? **In order to find the infected user account the Lightweight Directory Access Protocol (LDAP) traffic had to checked. (ldap contains "CN=Users") This was the command used filter through the packect capturers(Pcap).**

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/bfbc16c7-4e1e-46de-a25a-977c660fc619)

Is there any follow-up activity from other malware? **Other threat hunting methods can be used to check for more potential threats.** 