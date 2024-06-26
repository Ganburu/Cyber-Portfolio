<h1> Finding Gozi: Unit 42 Wireshark </h1>
This lab is from https://unit42.paloaltonetworks.com/march-wireshark-gozi/

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/a8cc426d-3979-4798-83ed-32175a8fb337)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/baf41c84-c7c1-44da-953c-3f2452dbc12f)

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/269ea435-5129-4031-97b9-bbf913110ac3)

What is the IP address, host name and Windows user account name for the infected Windows client? **To find the IP address of the infected client entered "(http.request or tls.handshake.type eq 1) and !(ssdp)" into the wireshark filter. All of the source traffic comes from the IP address 172.16.1.137**  

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/1b6dcaf5-51be-4ea1-86ce-b64207c5c085)

**To find the hostname I searched for kerbos traffic with Cnamestring (kerbos.CNameString). I double clicked on the first packet with the infected IP address as the source.  I then clicked on the kerbros arrow which led me to another are called "as-req"; scrolling down to "HostAddress" I found the hostname.** It shows in the following image.

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/38993bd6-223c-422e-a2d5-3bcfc6d2cf0b)


What is the URL and SHA-256 hash of the ZIP archive downloaded by the infected Windows host? **To find the URL I put "http.request.method == GET" in the filter bar. This I then searched through the filtered HTTP requests for a URL that ends in .zip. I then followed the TCP stream to see the full request and response and then right-clicked on the relevant packet and chose "Follow" > "TCP Stream". In the TCP stream, I identified the full URL from the GET request.**

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/05a054ca-2dab-46d7-9b23-5662a5fe687e)

**To find the SHA-256 Hash I extracted the ZIP File. The Caliente.zip file was exported in the following manner.
Go to File > Export Objects > HTTP...
Selected the Caliente ZIP file and clicked "Save".
To calculate the SHA-256 Hash inside the file I used sha256sum in Linux terminal. The bash command I put in was sudo sha256sum caliente.zip and came up with the following result.**

![image](https://github.com/Ganburu/Cybersecurity-Portfolio/assets/162606791/64d1289e-c5a6-4d10-88cb-5f6d1938387c)

