# Tryhackme h4cked:
# Subject : Hack your way back into the machine

The attacker has changed the user’s password! Can you replicate the attacker’s steps and read the flag.txt? The flag is located in the /root/Reptile directory. Remember, you can always look back at the .pcap file if necessary.

* Deploy the machine

* Step 1: You need openvpn configuration file to connect with VPN to machines in TryHackMe.

* Step 2: Use openvpn command and start your VPN connection.

* Step 3: check the IP address of the machine

* Step 4: check your connection.

* Firstly, we need to run a nmap scan to find out which ports are open and which services are running on these ports.Nmap (Network Mapper) is a free and open source utility for network discovery and security auditing.

-A : Enable OS detection, version detection, script scanning and traceroute.

-T4 : Set timing template (higher is faster).

-Pn : Treat all hosts as online — skip host discovery.

-p- : You can specify “-p-” to scan ports from 1 through 65535.

-l : Login with LOGIN name.

-P : Load several passwords from FILE.

[machine IP] : The IP address of the target machine.

ftp / protocol : Sets the protocol.

* Yes, we are inside!Let’s use the get command to transfer the file we’ll use for the backdoor to our own device.We need to change the IP address and port information.If you have connected via VPN, you have to use the IP address in the tun0 (VPN Interface) section. You can use the ifconfig command to find out.We can use the put command to transfer the backdoor we created from our device to the target system.

put : To copy a single file, use the put command.

mput : To copy multiple files at once, use the mput command.

Don’t forget to run netcat in the background before transfer!,Netcat or nc is a utility tool that uses TCP and UDP connections to read and write in a network.

-l is used to tell netcat that this will be a listener.

-v is used to request a verbose output.

-n tells netcat not to resolve host names or use DNS.

-p indicates that the port specification will follow.
* check if we have any permissions to execute specific commands as sudo.

sudo -l : The -l (list) option will print out the commands allowed (and forbidden) the user on the current host.
 
* It appears that we have all of the necessary permissions and we should find  the flag
