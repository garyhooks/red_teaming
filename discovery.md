

TCP connect scan to obtain version details of the port

> sudo nmap -Pn -sT -sV -oN $FILENAME $IP 

```
PORT     STATE SERVICE       VERSION
53/tcp   open  domain        Simple DNS Plus
88/tcp   open  kerberos-sec  Microsoft Windows Kerberos (server time: 2022-09-25 09:09:51Z)
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb0., Site: Default-First-Site-Name)
445/tcp  open  microsoft-ds?
464/tcp  open  kpasswd5?
593/tcp  open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp  open  tcpwrapped
3268/tcp open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb0., Site: Default-First-Site-Name)
3269/tcp open  tcpwrapped
Service Info: Host: DC; OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Sep 25 05:09:52 2022 -- 1 IP address (1 host up) scanned in 13.37 seconds
```

> sudo nmap -Pn -sT -sV -oN $FILENAME $IP --script=*

-sC - default scripts
-sV - enumerate versions
-oA - output all formats 
> sudo nmap -sC -sV -oA results/

Syn Scan, OS discovery, no ping, all ports, get web titles
> nmap -sS -A -PN -p- --script=http-title
