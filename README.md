# SOC-HOMELAB
## **From Attack to Alert — Building a SOC Home Lab with Wazuh SIEM**

## **Why I built this?**

To truly understand how attacks happen and how defenders respond, I built my own SOC Home Lab from scratch , a  virtual 
environment designed to simulate real-world threats and monitor 
them using enterprise-grade tools.

This project gave me hands-on experience in security architecture, attack simulation, log analysis, and real-time threat detection — 
bridging the gap between learning cybersecurity and actually practicing it.

## **Lab Setup & Architecture**

lab contains 3 machines

Kali Linux  --->  Attack Simulation (Attacker Machine)

Windows Host  --->  Security Logs (Wazuh Agent)

Ubuntu Server  --->  Wazuh Dashboard (Wazuh Manager)

## **Network Adapter**
*All three machines are on bridged network

## **Attack Simulation**

### Network Scanning

I performed port scanning using nmap

``` nmap -sS 192.168.1.16```

This performs SYN Scan (half-open scan) to find which ports are open, closed.

### Full Port Scan

For discovering all open ports

``` nmap -sS -p- 192.168.1.16```

Scans all 65,535 TCP ports to find which ones are open.

### SMB Enumeration and Access

After running the above commands port 445(**SMB**) is open 

### List SMB Shares

``` smbclient 192.168.1.16 -p 445 -U modxultra%modxultra```

1. Connects to the Windows machine at 192.168.1.16 using SMB on port 445.
2. Logs in with username modxultra and password modxultra.
3. Once connected, you can browse and access the shared files and drives on that machine.

### Accessing SMB Share

``` smbclient 192.168.1.16 -p 445 -U modxultra%modxultra```

Once authenticated successfully, I could see shared resources such as:

    - C Drive
    - E Drive

Connects to the Windows machine at 192.168.1.16 on port 445 using username modxultra and password modxultra ,giving access to its shared files and drives remotely.

### DoS Attack Simulation

``` hping3 --flood -S 10.36.140.137```

I flooded the target with continuous SYN packets to generate abnormal 
network traffic and observe how Wazuh detects unusual activity in real time. make it human like

### Conclusion

This lab taught me that the best way to understand cybersecurity 
is to simply build it, break it, and observe what happens.





