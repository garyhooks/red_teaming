## Basic Information

DNS stands for Domain Name System. This operates on Port 53. 

This is both a TCP and UDP service depending on the activity taking place. For Zone Transfers it operates usind TCP as ensuring full transfer and ordering is achieved is important. For name queries it operates using UDP.

### dig

Domain Information Groper 

``` 
dig 10.10.11.174 
dig ANY 10.10.11.174
dig A 10.10.11.174
dig TXT 10.10.11.174
dig MX 10.10.11.174
dig NS 10.10.11.174
dig -x 10.10.11.174 _reverse lookup_
```

use **+short** tag for shortened information return
> dig google.com +short


### nslookup

> nslookup 10.10.11.174

### host

> host google.com

```
google.com has address 142.250.200.46
google.com has IPv6 address 2a00:1450:4009:821::200e
google.com mail is handled by 10 smtp.google.com.
```

### dnsenum

Extremely powerful and this can get full IP blocks, all sub domains, name servers of your target

> dnsenum --noreverse targetdomain.com -o dns_results.txt

You can also scrape google.com for subdomains
**-p** is number of pages to search on Google.com (default 5)
**-s** is the maximum number of subdomains to return (default 15)

> dnsenum --dnsserver ns2.secret-dns.net domain.com -p 10 -s 100

### nmap 

Return list of all subdomains 

> nmap -T4 -p 53 --script dns-brute microsoft.com
```
Host script results:
| dns-brute: 
|   DNS Brute-force hostnames: 
|     admin.microsoft.com - 13.107.6.156
|     admin.microsoft.com - 2620:1ec:a92::156
|     id.microsoft.com - 13.107.42.22
|     ads.microsoft.com - 51.144.109.73
|     id.microsoft.com - 2620:1ec:21::22
|     test.microsoft.com - 40.127.240.222
|     info.microsoft.com - 104.17.70.206
|     info.microsoft.com - 104.17.71.206
|     info.microsoft.com - 104.17.72.206
|     info.microsoft.com - 104.17.73.206
|     info.microsoft.com - 104.17.74.206
|     alerts.microsoft.com - 20.84.181.62
|     news.microsoft.com - 141.193.213.20
|     news.microsoft.com - 141.193.213.21
|     dns.microsoft.com - 20.103.85.33
|     dns.microsoft.com - 20.112.52.29
```

### dnsrecon

This searches cached dns records as well as current ones

> dnsrecon -d domain.com

### fierce

> fierce --domain domain.com
