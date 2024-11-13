# Active Directory Project (Home Lab)

In this project, I will show the steps of setting up an Active Directory (home lab) that includes Splunk, Kali Linux & Atomic Red Team. Explore how a domain environment works, learn how to ingest events to a SIEM and generate telemetry related to attacks seen in the wild. 

## Diagram
Here is a diagram of the network setup from app.diagrams.net that I made.

![image](https://github.com/user-attachments/assets/8018ec8f-716d-413f-be4c-34c0df14e771)

## Virtual Machine Network Setup 

Set up Windows 10 target computer, kali linux(the attacker), Windows server and Splunk Server on Virtualbox.

![image](https://github.com/user-attachments/assets/5e3e3706-9180-480b-82ce-62c27a2d92b9)

Configure a new Nat network on virtual box so that the Windows computer, Windows server, and Splunk server are on the same network.

![image](https://github.com/user-attachments/assets/f51f7552-806a-4d50-bec0-cd9650bdab92)

## Splunk Server Setup(Linux)

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

## Target Machine Setup(Windows)

Change the target machine IP from 192.168.10.5 to 192.168.10.100 in the network connection setting, to avoid IP conflicts. 

!![image](https://github.com/user-attachments/assets/4705f5b4-4b75-4c6f-9f50-27e71c948a8d)

![image](https://github.com/user-attachments/assets/ddc0cccb-e55c-4001-b503-ba3bd8e651f8)

![image](https://github.com/user-attachments/assets/82484f83-1ae8-47fb-9ca0-10a0ef9adcdc)

Now lets see if I can access the splunk server via my target machine. 

![image](https://github.com/user-attachments/assets/b9e3d78b-2630-472f-949f-444c31aee777)


Cool, it works.

Next, Install Universal forwader from Splunk.com.

![image](https://github.com/user-attachments/assets/e0c05d0b-4753-4a65-bd2a-995f206c5bd7)

![image](https://github.com/user-attachments/assets/6733f057-95ea-453b-9249-253ab4c2628c)

![image](https://github.com/user-attachments/assets/22ac575b-fe9b-4604-ad77-09874271ea60)

### Installation of Sysmon(System Monitor) on Target Machine.

Download sysmon from "learn.microsoft.com".

![image](https://github.com/user-attachments/assets/d97c7f3b-296f-448a-96b0-41e39cd39f56)

Search Sysmon Olaf Config and download from Github.

![image](https://github.com/user-attachments/assets/520d90e8-e71c-4bef-9603-81b4d2e4020e)

![image](https://github.com/user-attachments/assets/5a23f674-cebd-40e5-bdff-b88cbcbbc98c)

Went to Raw Right clicked and saved as in the Target machine download directory.

![image](https://github.com/user-attachments/assets/1e36a25d-fc74-4494-b937-ba1317d5bfa4)

![image](https://github.com/user-attachments/assets/766578b3-a029-4e2c-b0ee-058a71c1295a)

In Downloads folder extract sysmon files and open Powershell with admin privillege in sysmon directory.

![image](https://github.com/user-attachments/assets/558fce9a-9b68-4c5a-843c-86807d444f63)

![image](https://github.com/user-attachments/assets/7a0961a9-02f6-4f81-9912-d0888d0b8ad9)

Type in ".\Sysmon64.exe -i ..\sysmonconfig.xml"  to install sysmon 

![image](https://github.com/user-attachments/assets/4a5f6f38-b3cc-4854-9f44-d32e6c6cc109)

























