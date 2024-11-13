Active Directory Project (Home Lab)
In this project, I will show the steps of setting up an Active Directory (home lab) that includes Splunk, Kali Linux & Atomic Red Team. Explore how a domain environment works, learn how to ingest events to a SIEM and generate telemetry related to attacks seen in the wild. 

## Diagram
Here is a diagram of the network setup from app.diagrams.net that I made.

![image](https://github.com/user-attachments/assets/8018ec8f-716d-413f-be4c-34c0df14e771)

## Virtual Machine Network Setup 

Set up Windows 10 target computer, kali linux(the attacker), Windows server and Splunk Server on Virtualbox.

![image](https://github.com/user-attachments/assets/5e3e3706-9180-480b-82ce-62c27a2d92b9)

Configure a new Nat network on virtual box so that the Windows computer, Windows server, and Splunk server are on the same network.

![image](https://github.com/user-attachments/assets/f51f7552-806a-4d50-bec0-cd9650bdab92)

## Splunk Server Setup

Now to set up Splunk server. On the Splunk server I navigated to the installer-config. I edited the settings, which shows in the snap shot below.

![image](https://github.com/user-attachments/assets/d5768229-0809-43b5-80b6-062e7a771732)

Applied changes and checked to see if IP address is correct. Cool and it is.

![image](https://github.com/user-attachments/assets/ac6ca9a4-0417-4f43-aab4-321718c63886)

Now to download Splunk Enterprise for Linux from splunk.com.

![image](https://github.com/user-attachments/assets/9a18e0e9-dac9-4b2e-8487-117751cb2ba0)

Back to virtual Splunk server to install virtual guest add-ons.

![image](https://github.com/user-attachments/assets/4c04ff1b-0621-4d05-900e-825e790e3be3)

After guest add-on, I allocated a folder that this server could save files to via devices and shared folder options on the splunk virtual machine.

![image](https://github.com/user-attachments/assets/a8ccd8c9-b90d-470d-8b04-1e4cbcfdb798)

![image](https://github.com/user-attachments/assets/7243eb8a-eb7e-4776-aa04-35d35aed8fe2)

Now to add a user and make new directory called "share".

![image](https://github.com/user-attachments/assets/60996fa7-0113-4822-86d9-59359331908d)

Run command to mount shared folder on to the directory share.

![image](https://github.com/user-attachments/assets/2c0d62d8-ab1e-499d-8539-1b7e23f7fece)

Now to Install Splunk enterprise on the Splunk server.

![image](https://github.com/user-attachments/assets/29b10271-e945-407b-a9c0-64ef7b1ad77a)

![image](https://github.com/user-attachments/assets/f778acce-27f8-43b2-9816-6dab5f4bf71f)

![image](https://github.com/user-attachments/assets/350da1e9-958d-4946-8058-134c3df3dcda)

## Target Machine Setup

Change the target machine IP, so that there aren't any conflicts. 


















