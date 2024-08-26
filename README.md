This Lab is from https://www.youtube.com/watch?v=WPyJR7Y3qb4 (MyDFIR)

## Roughdraft of SOAR setup. 

![image](https://github.com/user-attachments/assets/b8aef411-f11e-4e2a-a4c7-2496ba2f1099)

## Playbook workflow.

![image](https://github.com/user-attachments/assets/415c758c-a485-4be2-b79c-85d06caf76c6)

![image](https://github.com/user-attachments/assets/ece990d1-4903-44d5-bd27-4688d4c3318f)

## Install and setup Lima Charlie

Create Installation Key

![image](https://github.com/user-attachments/assets/96e6f919-0d9c-4b51-867d-24d61826260d)

![image](https://github.com/user-attachments/assets/3409ee28-e639-4b67-ab45-245f8d74a46a)

Download Windows EDR.

![image](https://github.com/user-attachments/assets/18e4f8a2-a8d8-4e06-bc28-d23729ef3c6f)

Copy Sensor key

![image](https://github.com/user-attachments/assets/5f3e4802-755d-4a34-a4da-3badb65be918)

Copy Windows.exe

![image](https://github.com/user-attachments/assets/37390144-2876-494d-8cfb-f3a21efb5e8c)

Open Powershell as Administrator, cd to downloads, paste windows.exe, space Put -i put another space, then paste sensory key right after. Press enter 

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

Detection Rules

![image](https://github.com/user-attachments/assets/dc3f4747-2cd3-46ce-ada4-d634ae89770c)

Response Rules

![image](https://github.com/user-attachments/assets/c25ae3f9-c81f-403f-98b2-613229f59a42)

Test Rule
After saving rule, scrolled down and clicked on target event. Copied lazagne event from timeline 

![image](https://github.com/user-attachments/assets/8961cff0-b753-43d7-9968-17e9dc0e8a7e)

Paste Here and test event.

![image](https://github.com/user-attachments/assets/73000c27-9939-40ff-ae83-2bf144c88ef5)

The Event was a success.

![image](https://github.com/user-attachments/assets/05c2d4f0-744d-4b76-ab57-2d3ce1648529)

Side note: *Rules do not have to be made from scratch. Lima Charlie has many predefined D&Rs. These rules can also be modified to meet your EDR standards.*

Ran lazagne.exe in powershell and lima charlie detected the events.

![image](https://github.com/user-attachments/assets/623fd6a6-af7b-4e1c-be85-a929945dc957)

Created a Slack account and added a channel named alerts to get Tines alerts sent to Slack.

![image](https://github.com/user-attachments/assets/61cdea34-3b3a-4ded-8dd1-92c3bcf0da46)

Went to tines.com and created a account so Lima Charlie detections can be sent to Tines. Once in Tines I deleted all tools, added the webhook tool to the story and copied the web hook url for use in Lima Charlie later.

![image](https://github.com/user-attachments/assets/5dbcba25-7911-48a7-b1a8-326f553a32ef)


Back to Lima Charlie to connect Tines. Selected outputs. 

![image](https://github.com/user-attachments/assets/8e1d11dd-3e23-4545-9aac-12964da8861d)

Select detections.

![image](https://github.com/user-attachments/assets/047e5c22-b225-4cd5-a482-c4705691236d)

Select Tines, named it and pasted the webhook url from my Tines account. Selected save output.

![image](https://github.com/user-attachments/assets/1be23b34-f4d5-449c-bc5f-898953e07460)

Ran Lazagne.exe in powershell to get a detection. 

![image](https://github.com/user-attachments/assets/1b302d39-aa66-4b6d-8122-d2d8ab3f43ae)

Now to head over to tines to check output. It Worked! 

![image](https://github.com/user-attachments/assets/da3f6121-0f81-4d72-8409-7d83e692877b)






















