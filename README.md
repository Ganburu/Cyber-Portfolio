This Lab is from https://www.youtube.com/watch?v=WPyJR7Y3qb4 (MyDFIR)

Roughdraft of SOAR setup. 

![image](https://github.com/user-attachments/assets/b8aef411-f11e-4e2a-a4c7-2496ba2f1099)

Playbook workflow.

![image](https://github.com/user-attachments/assets/415c758c-a485-4be2-b79c-85d06caf76c6)

![image](https://github.com/user-attachments/assets/ece990d1-4903-44d5-bd27-4688d4c3318f)

Install and setup Lima Charlie

Create Installation Key

![image](https://github.com/user-attachments/assets/96e6f919-0d9c-4b51-867d-24d61826260d)

![image](https://github.com/user-attachments/assets/3409ee28-e639-4b67-ab45-245f8d74a46a)

Download Windows EDR.

![image](https://github.com/user-attachments/assets/18e4f8a2-a8d8-4e06-bc28-d23729ef3c6f)

Copy Sensor key

![image](https://github.com/user-attachments/assets/5f3e4802-755d-4a34-a4da-3badb65be918)

Copy Windows.exe

![image](https://github.com/user-attachments/assets/37390144-2876-494d-8cfb-f3a21efb5e8c)

Open Powershell as Administrator. cd to downloads. Paste windows.exe. Space Put -i put another space, then paste sensory key right after. Press enter 

![image](https://github.com/user-attachments/assets/e295689e-a106-4603-9ad1-d809be5a1294)

Checked Windows services to see if was running successfully. 

![image](https://github.com/user-attachments/assets/07898386-8ef4-467a-b490-64ec2f09c921)

## Generate telementry Detection and response

Went to laZange github to get latest release of the LaZagne.exe

Side note: *Windows security should be diabled*

![image](https://github.com/user-attachments/assets/3cac89da-d4eb-4b65-99cf-254bc57efa05)

It Worked.

![image](https://github.com/user-attachments/assets/3c4fbf07-4e05-4825-960a-c629b7ee3a6c)

Lima Charlie also picked up these events.

![image](https://github.com/user-attachments/assets/3b054905-e3f2-4cb7-a68c-213084d570ce)

Create Detection & Response rules (D&R) rules via automation in Lima Charlie.

Detection Rule

![image](https://github.com/user-attachments/assets/dc3f4747-2cd3-46ce-ada4-d634ae89770c)











