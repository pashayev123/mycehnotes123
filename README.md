# mycehexamnotes

For webserver enum
nmap -p <port> --script=http-enum <target>

# host discovery

Netdiscover is used to scan for the live hosts on the network
netdiscover -i (network interface name)

Ping scan is used to scan for the live hosts on the network
>nmap –sn 192.168.18.1/24

Arp scan is another method to scan for the live hosts on the network
nmap -sn -PR 192.168.18.0-255

Nmap has a vast variety of scans aval. Some of the most useful scans for host discovery are listed below
Misc Nmap Scans
8
>nmap -sn -PU 192.168.18.110 //UDP ping scan

>nmap -sn -PE 192.168.18.1-255 //ICMP Echo Ping scan

>nmap -sn -PM 192.168.18.1-255 //Mask Ping scan (use if ICMP is blocked)

>nmap -sn -PP 192.168.18.1-255 //ICMP timestamp scan

>nmap -sn -PS 192.168.18.1-255 //tcp syn ping scan

>nmap -sn -PO 192.168.18.1-255 //IP protocol scan.use different protocols to test the connectivity


Angry IP Scanner
10
 You can download and install the tool on Windows from the official website
https://angryip.org/

Nmap is the go to tool for identifying open ports and
services running on these ports

>nmap –sS –sV 192.168.18.1/24

sS - TCP Stealth scan

sV - Version Enumeration
>

Hping is another very useful tool to identify ports and services

>hping3 -S 192.168.18.110 -p 80 -c 5

S - TCP Stealth scan
P 80 - Scan for port 80


Nmap also has an inbuilt script to identify the OS but it needs smb service running on the system

>sudo nmap --script smb-os-discovery.nse 192.168.18.110
>
>![image](https://github.com/pashayev123/mycehexamnotes/assets/133966450/9b66349a-ac4e-492a-8cc3-975b62808442)


NETBIOS 

Use the following command on windows to enumerate NetBIOS names for a target

>nbtstat -a 192.168.18.110

We can check the local cache for Netbios with the following command

>nbtstat -c

![image](https://github.com/pashayev123/mycehexamnotes/assets/133966450/90cc9b90-ca53-440d-a44a-85cfbe712673)


Nmap has a script for Netbios enumeration
>nmap -sV -v --script nbstat.nse 192.168.18.110
>nmap-sU-p 137 --script nbstat.nse192.168.18.110

sV - version enumeration

sU - udp scan



# SMB Enumeration

TCP port 445: This is the primary port used by SMB for file sharing and
communication. It handles the majority of SMB traffic, including file access,
printer sharing, and remote administration

 UDP ports 137 and 138: These ports are used by SMB for NetBIOS name
resolution and datagram services, similar to NetBIOS

 TCP port 139: This port is used by older versions of SMB for session
establishment and file sharing. It is commonly used in conjunction with
NetBIOS over TCP/IP (NBT)

Nmap can be used to scan and enumerate the smb service and then we can use various tools to enumerate smb

>sudo nmap -A –p 445 192.168.18.110

>sudo nmap --script smb-os-discovery.nse 192.168.18.110

>nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse 192.168.18.110

![image](https://github.com/pashayev123/mycehexamnotes/assets/133966450/dc0b5974-7161-4504-b2cb-0f9e783fc3cf)

There are a number of scripts to enumerate smb. You can
check more scripts by the following command

>cd /usr/share/nmap/scripts; ls | grep smb

Enum4linux

 Enum4linux is a tool used for network enumeration and
information gathering. Enum4linux leverages various SMB
and NetBIOS enumeration techniques to gather information
about a target system

>enum4linux -a 192.168.18.110


![image](https://github.com/pashayev123/mycehexamnotes/assets/133966450/6c1fc087-dd8a-400a-87dc-08936ffd242e)

https://github.com/Porchetta-Industries/CrackMapExec

# ELF

sandflysecurity # ./sandfly-filescan -dir /tmp -entropy 7.7 -elf

sandfly-entropyscan -dir /var/www -elf -entropy 7.7

# FTP

hydra -L wordlist/userlist.txt -P wordlist/passlist.txt ftp://192.168.0.100

