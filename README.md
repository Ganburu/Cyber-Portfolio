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

## Tines & Slack

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


Back to slack

Added the Tines app to slack through the automations option.

![image](https://github.com/user-attachments/assets/bfe2fd46-564e-4513-bc9f-59b0e93ecc8b)

Added the Slack Api to Tines via crendentials.

![image](https://github.com/user-attachments/assets/9a364537-3565-4887-82f8-514b00b2ac16)

Back in slack. Copied channel_ID to paste in tines.

![image](https://github.com/user-attachments/assets/edd73ca0-5af0-4900-83ac-80823bbc083a)

Added Slack to my story in Tines and pasted my Slack Channel ID in Channel/UserID section.

![image](https://github.com/user-attachments/assets/ae73903c-03b0-4ba6-b3c9-9ecb7effb55a)

Sent a message from Tines to Slack and it worked!

![image](https://github.com/user-attachments/assets/73283589-b588-4610-b013-7d41b8dbc7ad)

Back in Tines. Added send email to my story. Made an account on public.sqrx.com to get a disposable email. Copied the disposable email. Pasted it in Reciepients section under list in Tines.

![image](https://github.com/user-attachments/assets/be94bd18-a38f-4f73-807c-6c41d90d9ff9)


![image](https://github.com/user-attachments/assets/f28703c3-6b61-4472-a92a-52a9fe38c494)

Time to test. It worked.

![image](https://github.com/user-attachments/assets/53ea1333-0c6c-4bcd-946a-0c45bf70f584)

### USER PROMPT

Added new page to my story in Tines from tools option. This will be the user prompt.

![image](https://github.com/user-attachments/assets/a6220033-aa8d-4841-a0e7-4105e3b26eb0)

Edited the new user prompt page in Tines.

![image](https://github.com/user-attachments/assets/318eca70-fb22-4ae2-a614-d1dd62f98569)

Will be using these fields copied from Tines in a few.

![image](https://github.com/user-attachments/assets/0636a1af-2145-46b3-b455-ea6f59b17546)

Pasted the fields into Slack API in Tines.

![image](https://github.com/user-attachments/assets/7230a80e-6bba-4cfb-a813-af24d8044450)

Time to test the Slack API in Tines. 

Switch over to Slack. It worked.

![image](https://github.com/user-attachments/assets/82bf86dd-a943-4511-9418-58edc497ca60)

I put the same credentials into the email API and now to test email API. 

It worked.

![image](https://github.com/user-attachments/assets/35f4b37f-01ea-42fb-8639-c714ede0461a)

Going back to the User prompt in Tines.

Pasted same credentials that was used for Slack ans email API into the User prompt.

![image](https://github.com/user-attachments/assets/8a4c1e48-dec0-44ee-9656-636f5e360e23)

Added a trigger action to my Tines story. And another Slack instance for trigger messages. 

![image](https://github.com/user-attachments/assets/90be9efa-692a-41b8-9cc6-b07a1cafb617)

The trigger tool and Slack instance has been edited. Now time to test.

![image](https://github.com/user-attachments/assets/6b9cedab-64ea-483a-a1d1-d6baa1eb497c)

It works.

Next, added a yes trigger action I edited it in the same manner as the previous "No" trigger action with minor differences. 

![image](https://github.com/user-attachments/assets/e34b6b78-ab19-4092-bc3e-07e08418cd49)

I also had to connect another Lima Charlie instance with API Crendentials. Went to access management in Lima Charlie to get the API crendentials so that I could update my Tines story.

Here is the crenditals I will be using in Tines from Lima Charlie.

![image](https://github.com/user-attachments/assets/1e09aa80-8cb7-428a-8222-d5798275a47d)

In Tines selected add new crendential and updated the Lima Charlie crendentials.

![image](https://github.com/user-attachments/assets/c09c5118-540f-4570-81a8-c1563aef245d)

Time run test in Tines for yes trigger.

Here is a before shot of the non isolated computer in Lima Charlie and the computer command prompt.

![image](https://github.com/user-attachments/assets/c919ad59-9296-4176-83bf-ca9f707b21d9)

![image](https://github.com/user-attachments/assets/7583c2c6-19d0-42e0-bf7d-2fe88168ac90)

Ran lazagne.exe and a selected Yes in the user prompt to isolate the machine.

![image](https://github.com/user-attachments/assets/87022d40-f4ef-49ff-8a24-f599440de243)

 
It Worked!

Cool the computer is now isolated.

![image](https://github.com/user-attachments/assets/fe05938a-fb1e-4c2e-96a4-be880a22afa8)

![image](https://github.com/user-attachments/assets/36fc0f3f-fc7e-4ccb-bd07-d93f56028b5f)


























