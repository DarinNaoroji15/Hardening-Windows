# Hardening 

1. Log into Windows Server

2. From the Server Manager, click Manage. Then click Remove Roles and Features.

<img width="458" alt="image" src="https://github.com/user-attachments/assets/d1aa8411-c9eb-4738-9552-a24bbc645a90" />

Result of step 2

3. Click next till you reach the Server Roles page on the Remove Roles and Features Wizard.

4. On this page click the box Web Server (IIS)

<img width="422" alt="image" src="https://github.com/user-attachments/assets/86881a95-a4fd-498e-9159-8684ed54f1fa" />

Result of step 4

5. Click next till you get to the Results page and select Remove.

<img width="425" alt="image" src="https://github.com/user-attachments/assets/4a1cb9a7-d325-411b-8348-0b1837946e21" />

Result of step 5

6. Once finished click close.

7. Right click on the Windows Key or Start Menu and select Shut down or Sign out and select Restart.

<img width="145" alt="image" src="https://github.com/user-attachments/assets/3bed2bea-407a-4f65-9155-99fe225f72cd" />

Result of step 7

8. Click Hardware: Maintenance (Unplanned) and then click Continue

<img width="212" alt="image" src="https://github.com/user-attachments/assets/8063bc96-f870-4f7b-9ca7-e0ac77119a70" />

Result of step 8

9. Sign back in.

10. Go back to your Kali Linux environment. Within the msf5 subprompt.

Type the following command: msf5 exploit(windows/smb/ms17_010_psexec) > nmap 192.168.1.100

![image](https://github.com/user-attachments/assets/7c02b8f2-65fd-4e75-b875-0361cc912bae)

Result of step 10

11. Switch back to the Windows Server and open the command prompt by double-clicking on the shortcut to the desktop.

12. Type the following command to check the status of the guest account: net user guest

![image](https://github.com/user-attachments/assets/d59ada70-6dd8-4196-9b57-3e978c6263e9)

Result of step 12

13. We are going to set the status of the guest account.

Type the following command: net user guest /active:no

![image](https://github.com/user-attachments/assets/92e7779b-86be-4cb9-b071-a23ece99f690)

Result of step 13

14. We are going to check the status of the guest account.

Type the following command: net user guest

![image](https://github.com/user-attachments/assets/94a3e04b-5bf4-4f00-818e-960c5630f5b2)

Result of step 14

15. Switch back to the Kali machine and type the following command: msf5 exploit(windows/smb/ms17_010_psexec) > smbclient -L \\192.168.1.100

17. Press Enter when you are asked for the password. Notice that you are no longer able to enumerate the shares.

18. Now type in the following command: exploit

![image](https://github.com/user-attachments/assets/3de62b56-c75d-423a-9bc1-8e43d0d70b01)

Result of step 18

19. Switch back to Windows. In the command prompt, we are going to view the adminstrative accounts on the system.

20. Type the following command: net localgroup administrators

![image](https://github.com/user-attachments/assets/dc824da2-c967-47e5-a212-1493e71ccd7c)

Result of step 19 and step 20

21. Now type the following command to see if the hacker is on the system (he should not be): net user hacker /active:no

![image](https://github.com/user-attachments/assets/8b8323cb-754d-4073-9550-ce8450600e44)

Result of step 21
