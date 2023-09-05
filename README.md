# mycehexamnotes

For webserver enum
nmap -p <port> --script=http-enum <target>

#host discovery

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
