# Address Resolution Protocol (ARP):

The acronym ARP stands for Address Resolution Protocol which is one of the most important protocols of the Data link layer in the OSI model. It is responsible to find the hardware address of a host from a known IP address.

# Important Terms Associated with ARP:
* Reverse ARP
Reverse Address Resolution Protocol is a protocol that is used in local area networks (LAN) by client machines for requesting IP Address (IPv4) from Router’s ARP Table. Whenever a new machine comes, which requires an IP Address for its use. In that case, the machine sends a RARP broadcast packet containing MAC Address in the sender and receiver hardware field.

* Proxy ARP
Proxy Address Resolution Protocol work to enable devices that are separated into network segments connected through the router in the same IP to resolve IP Address to MAC Address. Proxy ARP is enabled so that the ‘proxy router’ resides with its MAC address in a local network as it is the desired router to which broadcast is addressed. In case, when the sender receives the MAC Address of the Proxy Router, it is going to send the datagram to Proxy Router, which will be sent to the destination device.

* Inverse ARP
Inverse Address Resolution Protocol uses MAC Address to find the IP Address, it can be simply illustrated as Inverse ARP is just the inverse of ARP. In ATM (Asynchronous Transfer Mode) Networks, Inverse ARP is used by default. Inverse ARP helps in finding Layer-3 Addresses from Layer-2 Addresses.

# working of ARP:

* It broadcast a packet to all the devices of the source network. The devices of the network peel the header of the data link layer from the Protocol Data Unit (PDU) called frame and transfer the packet to the network layer (layer 3 of OSI) where the network ID of the packet is validated with the destination IP’s network ID of the packet and if it’s equal then it responds to the source with the MAC address of the destination, else the packet reaches the gateway of the network and broadcasts packet to the devices it is connected with and validates their network ID. The above process continues till the second last network device in the path reaches the destination where it gets validated and ARP, in turn, responds with the destination MAC address.

# enumeration:

In cybersecurity, enumeration is the process of gathering information about a network or system to identify vulnerabilities and potential threats

*  working:

A hacker establishes a connection to the target system and performs queries to extract information such as usernames, IP addresses, and network resources. 

 * importance:

Enumeration is a key part of the ethical hacking process and helps identify weak points in a system's security. Attackers can then exploit these vulnerabilities to gain unauthorized access to resources, steal data, or cause damage. 

* Techniques:

Enumeration can be performed using tools such as telnet, Nmap, and smtp-user-enum. 

# exploitation:

In cybersecurity, exploitation is the use of a vulnerability in a computer system or application to gain access to confidential data or perform malicious actions. The method or code used to exploit a vulnerability is called an exploit. 

# Maintaining Access :

Maintaining Access is the 4th phase in the ethical hacking process. In this phase, the hacker installs software or makes changes to the target machine to access the target later in time. This allows the hacker to stay connected with the target machine, thus cutting the need of starting the process from scratch for the same target. This phase is also called persistence in the target system.

# clearing tracks:

Clearing tracks is the final phase of a successful hacking attack, where the attacker removes evidence of their actions to avoid being caught

* Removing logs: Attackers remove or manipulate logs that may contain records of their activities. 
* Cleaning the registry: Attackers remove or alter registry entries related to their activities. 
* Using anti-forensic techniques: Attackers use anti-forensic tools or encryption to make it harder for investigators to reconstruct events. 



