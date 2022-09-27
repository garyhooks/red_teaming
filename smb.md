## Basic Information

**Port 139** is utilised by NetBIOS. This stands for _Network Basic Input Output System_. It allows applications and devices on a network to communite with network hardcore and send/receive data. Those on the network utilise their NetBIOS names in order to communicate. The NetBIOS name is 16 characters long and usually different to the computer name. 

**Port 445** is used by Microsoft for Active Directory services as well as SMB (Server Message Block) protocol. SMB is an application layer protocol which allows the sharing of files, printers and other communication between different endpoints. 

### cme (CrackMapExec)

Identify hostname and operating system type

> cme smb 10.10.11.13

Display shares and permissions
> cme smb 10.10.11.13 -u bob -p bobspassword --shares

### nbtscan

Windows machines provide a service on UDP Port 137 which listens for queries on NetBIOS requests. When it receives a query it responds with a list of services it provides

> nbtscan -r 192.168.0.1/24
> nbtscan 10.10.11.174

### nmblookup

Identify the NetBIOS names and associated IP addresses

> nmblookup -A 10.10.11.174

### nmap scripts

This attempts to retrieve NetBIOS and MAC addresses
> sudo nmap -Pn --script nbstat.nse 10.10.11.174

Attempt to access and enumerate shares
> sudo nmap -Pn --script smb-enum-shares -p139,445 10.10.11.174

Test all smb vuln scripts against target machine
> sudo -Pn nmap --script smb-vuln* 10.10.11.174

### ping reverse name resolution

Sometimes this works and provides the hostname

> ping -a 10.10.16.55

### smbclient

> smbclient -L 10.10.11.174 
```  
        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        NETLOGON        Disk      Logon server share 
        support-tools   Disk      support staff tools
        SYSVOL          Disk      Logon server share 
```

Connect to specific share to get command line access. Use _get_ and _put_ if successful 
> smbclient //10.10.11.174/support-tools

Or you can use curl:
> curl --upload-file /path/to/file.ext  -u 'DOMAIN\Username' smb://172.16.17.52/ShareName/

Or you can use **smbget**
> smbget smb://PATH/TO/FILE/test.txt
                                                   
### rpclient

Enumerate users with share access

> rpcclient -U "" 10.10.11.174

If successful utilise options:
```
netshareenum
netshareenumall
```

### enum4linux

Can enumerate and extract information from Windows and Linux systems, including the following: 

Domain and group membership
User listings
Shares on a device (drives and folders)
Password policies on a target
The operating system of a remote target

> enum4linux 10.10.11.174 

