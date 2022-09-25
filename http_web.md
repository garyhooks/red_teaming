
Check **/robots.txt**

### nmap

**-A** enables OS detection 
> nmap -Pn -sV -p 80 10.10.11.170
> nmap -Pn -sV -p 80 10.10.11.170 --script=*http*
> sudo nmap -Pn -A -v -p 80 10.10.11.170

### nikto 

> nikto -h 10.10.11.170 -p 8080
```
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          10.10.11.170
+ Target Hostname:    10.10.11.170
+ Target Port:        8080
+ Start Time:         2022-09-25 08:17:17 (GMT-4)
---------------------------------------------------------------------------
+ Server: No banner retrieved
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ Uncommon header 'content-disposition' found, with contents: inline;filename=f.txt
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ Allowed HTTP Methods: GET, HEAD, POST, PUT, DELETE, OPTIONS 
+ OSVDB-397: HTTP method ('Allow' Header): 'PUT' method could allow clients to save files on the web server.
+ OSVDB-5646: HTTP method ('Allow' Header): 'DELETE' may allow clients to remove files on the web server.
+ OSVDB-3092: /stats/: This might be interesting...
+ 7891 requests: 0 error(s) and 8 item(s) reported on remote host
+ End Time:           2022-09-25 08:20:13 (GMT-4) (176 seconds)                                                                                                                             
---------------------------------------------------------------------------                                                                                                                 
+ 1 host(s) tested
```

# Locate Directories

### gobuster

> gobuster dir -u http://10.10.11.170:8080 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
> gobuster dir -u http://10.10.11.170:8080 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.html,.txt



### get OPTIONS

> curl -i -X OPTIONS 10.10.11.170:8080                                                                                                                                              130 ⨯
```
HTTP/1.1 200 
Allow: GET,HEAD,OPTIONS
Content-Length: 0
Date: Sun, 25 Sep 2022 12:23:14 GMT
```

### put option enabled



