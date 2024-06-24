<h1> Finding Gozi: Unit 42 Wireshark </h1>
This lab is from https://unit42.paloaltonetworks.com/march-wireshark-gozi/

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/a8cc426d-3979-4798-83ed-32175a8fb337)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/baf41c84-c7c1-44da-953c-3f2452dbc12f)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/269ea435-5129-4031-97b9-bbf913110ac3)

What is the IP address, host name and Windows user account name for the infected Windows client? **To find the ip address and the host name the filter "http.request or tls.handshake.type eq 1) and !(ssdp)" was enter to search through traffic to check for any unusual request or connections. The first packet in the logs seemed unusual and was selected to get ip address and host name. To find the Windows user account, I filtered through netbios name service(nbns) traffic and  I was able to find the Windows user account in the info section. **

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/1b6dcaf5-51be-4ea1-86ce-b64207c5c085)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/5a75ce1f-8aba-44ce-ab67-cb131e0f874e)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/b0befd2d-27f6-4130-82dc-fce4c3a36765)
