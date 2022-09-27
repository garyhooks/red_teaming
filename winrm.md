### cme (CrackMapExec)

Identify hostname and operating system type. Can also be utilised for ldap, msssql, smb, ssh and winrm

> cme winrm 10.10.11.13 -u bob -p bobspassword

### evil-winrm

> evil-winrm.rb -i 10.10.11.13 -u bob -p bobspassword 

Create scripts and executables into respective directories 
> evil-winrm.rb -i 10.10.11.13 -u bob -p bobspassword -s scripts/ -e exes/
