# Information Gathering:

* Now we start our basic Nmap scan with following command:  Nmap -A -T4 -Pn <machine ip>

* By doing this scan we got some results

* From the above results we can able to conclude that there is an http service is running on the machine lets check that service and will start to enumerating it.

* For enumeration we are going to do find the hidden directories of the webserver using our favorite tool called gobuster.

* From the gobuster scan we found that there is a directory called content lets check what it has


# Scanning and Enumeration:

* I think it has CMS panel called sweet rice lets check further form the content endpoint. For that we are going to use again gobuster tool to find out

* After the gobuster scan we found some interesting folders and in that there is a really interesting folder called /inc lets check what it has

*  it has a DB related files lets check mysqlbackup folder here. It contains a MYSQL backup file lets download this and see whether it has any interesting information

* At the same time our gobuster scan also find another endpoint called /as and it has a login panel for the sweet rice CMS

*  its asking for credentials and the default credentials are not working here so will check the backup SQL file which we got form the MYSQL backup folder, and by luckily it has a credentials for the manager role

* But the password here is hashed so to de-hash that we are going to use crack-station website and by using this we found the plain text password

* Using this credentials we have successfully logged into the CMS panel

* Now its time to explore the application, after understanding the application I have founded a functionality called “ads” which had a feature to upload our php codes to the website, so this is a place we have interested. So now we are going to upload our famous reverse shell code there with our machine IP and port for the connection and going to take a reverse connection

# Exploitation:

* Now access the endpoint of the file and you will get a reverse shell connection.

https://machineip/content/inc/ads/

* Now click the file you will successfully get the reverse connection on the Netcat.

* Now its time to get the user flag, but I don’t enclose the flag here. But you can get it by cat command.

# Privilege Escalation:

* Now its time to take root privilege and root flag, so I started to enumerate the sudo permissions. And by checking that I Have found that the backup.pl file is can be run with the sudo permission for our user

* So we need to check what the file content is, and found that it’s calling a copy.sh file

* Now we need to check what the copy.sh file exactly has, Hahaa after opening the file we can able to see that there is reverse shell code is there which the machine creator has made so what we are going to do there is simply changing existing IP to our IP

* y the file has executing permissions for all the users, So lets start our Netcat listener to get a root shell connection.

* Now we are going to run the backup.pl file with the sudo permissions

* By running that file using sudo permission we have successfully got a reverse shell form the root user.

* Now its time take a root flag and again I will not show that flag here you can view it by cat command

![Untitled design](https://github.com/user-attachments/assets/1c185cdb-214e-4566-889a-23b6942588aa)
