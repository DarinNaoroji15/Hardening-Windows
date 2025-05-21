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

9. 
