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

# Types of ARP:

1. Proxy ARP
A Layer 3 device can reply to an ARP request for a target that is on a different network than the sender by using a technique called proxy ARP. In response to the ARP, the router that has been set for Proxy ARP maps its MAC address to the target IP address, deceiving the sender into believing that the message has arrived at destination.Because the packets have the required information, the proxy router at the backend forwards them to the correct location.

2. Gratuitous ARP
The host’s ARP request known as “gratuitous ARP” aids in locating duplicate IP addresses. This is a broadcast request for the router’s IP address. All other nodes are unable to use the IP address assigned to a switch or router in the event that it sends out an ARP request to obtain its IP address and receives no ARP answers in return. However, another node uses the IP address assigned to the switch or router if it sends an ARP request for its IP address and gets an ARP response.

3. Reverse ARP
In a local area network (LAN), the client system uses this networking protocol to ask the ARP gateway router table for its IPv4 address. The network administrator creates a table in the gateway-router that is used to correlate the IP address with the MAC address.

4. Inverse ARP
The purpose of inverse ARP, which is the opposite of ARP, is to deduce the nodes’ IP addresses from their data link layer addresses. Frame relays and ATM networks, where Layer 2 virtual circuit addressing is frequently obtained from Layer 2 signalling, are the primary applications for them. These virtual circuits can be used with the necessary Layer 3 addresses accessible.
