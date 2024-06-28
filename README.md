This lab is from https://unit42.paloaltonetworks.com/january-wireshark-quiz/

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/0759a55a-ed64-446a-958e-0ba82061bf83)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/8826116d-7363-4267-805b-beb016f6127b)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/cce00ab5-4f95-4d8c-ad41-96ede8789dfe)

To find the infected IP Address and Mac Address, I used my basic filter I created "(http.request or tls.handshake.type eq 1) and !(ssdp)"
IP address in highlighted yellow and Mac Address in highlighted blue. 

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/4fdbf8ef-8e99-4ee0-90e7-4abac8aad183)



Upon putting this filter in WireShark "(http.request) and !(ssdp)", I found a out of the ordaniary file (Ztvfo.png) in the traffic from the infected IP Address mentioned earlier.  

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/3b4dcaaa-e16f-4ec8-b245-50d735902781)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/6b4390dd-4380-4767-9255-94a63fc73f9f)
file > export object > http clicked ztfo.png and saved to the default download folder.

went to terminal to get the hash using the bash command sha256sum Ztvfo.png 
![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/63ccaeab-f8e5-4815-8847-0c4237c08ff7)

I then copy the hash and entered into virus total to see if the Ztvfo.png file is malicious. The Ztvfo file is flagged by 5 vendors as a trojan. Take a look.

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/b2b78e45-5c6a-46b6-add6-4f2a890fae05)

