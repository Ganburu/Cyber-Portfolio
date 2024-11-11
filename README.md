Active Directory Project (Home Lab)
In this project, I will show the steps of setting up an Active Directory (home lab) that includes Splunk, Kali Linux & Atomic Red Team. Explore how a domain environment works, learn how to ingest events to a SIEM and generate telemetry related to attacks seen in the wild. 

Here is a diagram of the network setup from app.diagrams.net that I made.

![image](https://github.com/user-attachments/assets/8018ec8f-716d-413f-be4c-34c0df14e771)

Set up Windows 10 target computer, kali linux(the attacker), Windows server and Splunk Server on Virtualbox.

![image](https://github.com/user-attachments/assets/5e3e3706-9180-480b-82ce-62c27a2d92b9)

Configure a new Nat network on virtual box so that the Windows computer, Windows server, and Splunk server are on the same network.

![image](https://github.com/user-attachments/assets/f51f7552-806a-4d50-bec0-cd9650bdab92)

Now to set up Splunk server. On the Splunk server I navigated to the installer-config. I edited the settings, which shows in the snap shot below.

![image](https://github.com/user-attachments/assets/d5768229-0809-43b5-80b6-062e7a771732)

Applied changes and checked to see if IP address is correct. Cool and it is.

![image](https://github.com/user-attachments/assets/ac6ca9a4-0417-4f43-aab4-321718c63886)





