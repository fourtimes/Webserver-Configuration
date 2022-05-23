### Configure nginx

1. Download the ssl certificate and Extract that.
2. go to the exact path and open in terminal.
3. list the file

```bash
ls
```
![image](https://user-images.githubusercontent.com/91359308/169757062-996321bf-1e8c-44c2-8696-5a68d3baec41.png)


4. Merge the certificate

```bash
cat certificate.crt ca_bundle.crt >> certificate.crt
```

5. To store the value in nginx

```bash
mkdir /etc/nginx/ssl-certificate
vim /etc/nginx/ssl-certificate/certificate.crt
vim /etc/nginx/ssl-certificate/private.key
```

6. configure the https,http domains and redirect conditions

```bash
vi /etc/nginx/sites-available/fourtimes.ml

add this content:
-----------------
server {
    listen       80;
    server_name  fourtimes.ml www.fourtimes.ml;
    return 301 https://$host$request_uri;

    location / {
        root   /var/www/fourtimes.ml;
        index  index.html index.htm;
    }
}

server {
    listen                443 ssl;
    ssl                  on;
    ssl_certificate      /etc/nginx/ssl-certificate/certificate.crt;
    ssl_certificate_key  /etc/nginx/ssl-certificate/private.key;
    server_name  fourtimes.ml;
    access_log   /var/log/nginx/fourtimes.ml.access.log;
    error_log    /var/log/nginx/fourtimes.ml.error.log;

    location     / {
        root         /var/www/fourtimes.ml;
        index        index.html index.htm;
    }
}
```

7. Create directory file

```bash
mkdir /var/www/fourtimes.ml
```

8. Change the directory

```bash
cd /etc/nginx/sites-enabled
```

9. copy the file sites-enabled from site-available

```bash
ln -s /etc/nginx/sites-available/fourtimes.ml ./
```


10. restart the server

```bash
systemctl restart nginx
```


11. status of the server
```bash
systemctl status nginx
```

12. Create index.html file and put the information:


```bash
vim /var/www/fourtimes.ml/index.html

add this content:
-----------------
<html>
<body>
<div style="width: 100%; font-size: 40px; font-weight: bold; text-apiign: center;">
welcome to the fourtimes.ml domain
</div>
</body>
</html>
```


13. To run inside the terminapi

```bash
curl api.fourtimes.ml
```
