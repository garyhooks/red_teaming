## Basic Information

**Port 139** is utilised by NetBIOS. This stands for _Network Basic Input Output System_. It allows applications and devices on a network to communite with network hardcore and send/receive data. Those on the network utilise their NetBIOS names in order to communicate. The NetBIOS name is 16 characters long and usually different to the computer name. 

**Port 445** is used by Microsoft for Active Directory services as well as SMB (Server Message Block) protocol. SMB is an application layer protocol which allows the sharing of files, printers and other communication between different endpoints. 


### nbtscan

Windows machines provide a service on UDP Port 137 which listens for queries on NetBIOS requests. When it receives a query it responds with a list of services it provides

> nbtscan -r 192.168.0.1/24
> nbtscan 10.10.11.174

### nmblookup

Identify the NetBIOS names and associated IP addresses

> nmblookup -A 10.10.11.174

### nmap nbstat script

This attempts to retrieve NetBIOS and MAC addresses

> nmap --script nbstat.nse 10.10.11.174

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
                                                   



