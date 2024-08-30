# Task 1
# Subject : Oh no! We’ve been hacked!

It seems like our machine got hacked by an anonymous threat actor. However, we are lucky to have a .pcap file from the attack. Download the .pcap file and use Wireshark to view it.

Before we begin, I think it’s important that we understand what wireshark is.

Wireshark is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education.

First of all, if we apply some configurations on Wireshark, the analysis process will be easier for us.

To open the relevant file, select the “Open” option from the “File” menu

![fa1dd8ad-d6a3-4e32-b9c0-c853f869f80b](https://github.com/user-attachments/assets/0f897152-52e0-42f5-9c92-c249816dcc4e)

To add columns in Wireshark, use the Column Preferences menu. Right-click on any of the column headers, then select “Column Preferences…”.And then click the “+” button to add a column.
Set the “Title” and “Type” values as shown in the image below to display the Source Port and Destination Port information in columns.

Q1: The attacker is trying to log into a specific service. What service is this?

A1: FTP

When we look at the traffic in general, we can see that there is traffic to port 21. Port 21 is commonly associated with FTP.

FTP (File Transfer Protocol) is a network protocol for transmitting files between computers over Transmission Control Protocol/Internet Protocol (TCP/IP) connections. Within the TCP/IP suite, FTP is considered an application layer protocol.

Q2: There is a very popular tool by Van Hauser which can be used to brute force a series of services. What is the name of this tool?

A2: hydra
Hydra is a parallelized login cracker which supports numerous protocols to attack.

Q3: The attacker is trying to log on with a specific username. What is the username?

A3: jenny

When we examine the requests in the Info column, we can see that there is brute-force traffic for the user “jenny”.

Q4: What is the user’s password?

A4: password123

When we look at the responses to the related requests, there is a response called “Login successful”.

To filter to a particular stream, select a TCP, UDP, DCCP, TLS, HTTP, HTTP/2, QUIC or SIP packet in the packet list of the stream/connection you are interested in and then select the menu item Analyze → Follow → TCP Stream. Wireshark will set an appropriate display filter and display a dialog box with the data from the stream laid out.

Q5: What is the current FTP working directory after the attacker logged in?

A5: /var/www/html

We can search for the “pwd” command to detect the working directory.

The pwd (print working directory) command writes to standard output the full path name of your current directory (from the root directory).

Q6: The attacker uploaded a backdoor. What is the backdoor’s filename?

A6: shell.php

Mastering important details like a filename, a file extension, or a command speeds up the analysis process.

We can see that the attacker is using a backdoor named “shell.php” in this stage.

A client issues the STOR command after successfully establishing a data connection when it wishes to upload a copy of a local file to the server.

Q7: The backdoor can be downloaded from a specific URL, as it is located inside the uploaded file. What is the full URL?

A7: http://pentestmonkey.net/tools/php-reverse-shell

We can see that the transfer process was successful after we discovered the backdoor.

Q8: Which command did the attacker manually execute after getting a reverse shell?

A8: whoami

As its name suggests, the whoami command prints the user name of the effective user ID. In other words, it displays the name of the currently logged-in user.

Q9: What is the computer’s hostname?

A9: wir3

Q10: Which command did the attacker execute to spawn a new TTY shell?

A10: python3 -c ‘import pty; pty.spawn(“/bin/bash”)’

Q11: Which command was executed to gain a root shell?

A11: sudo su

Things will only get worse from there, because the attacker will perform the operations with the privileges of the root user.

Q12: The attacker downloaded something from GitHub. What is the name of the GitHub project?

A12: Reptile

Reptile is a Linux kernel mode rootkit with detection evasion, persistence, and a backdoor.

Q13: The project can be used to install a stealthy backdoor on the system. It can be very hard to detect. What is this type of backdoor called?

A13: Rootkit

Rootkit malware is a collection of software designed to give malicious actors control of a computer network or application.
