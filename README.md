This lab is from https://unit42.paloaltonetworks.com/january-wireshark-quiz/

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/0759a55a-ed64-446a-958e-0ba82061bf83)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/8826116d-7363-4267-805b-beb016f6127b)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/cce00ab5-4f95-4d8c-ad41-96ede8789dfe)

To find the infected IP Address and Mac Address, I used my basic filter I created "(http.request or tls.handshake.type eq 1) and !(ssdp)"
IP address in highlighted yellow and Mac Address in highlighted blue. 

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/4fdbf8ef-8e99-4ee0-90e7-4abac8aad183)



To find (http.request) and !(ssdp)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/3b4dcaaa-e16f-4ec8-b245-50d735902781)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/6b4390dd-4380-4767-9255-94a63fc73f9f)
file > export object > http clicked ztfo.png and saved to the default download folder.
