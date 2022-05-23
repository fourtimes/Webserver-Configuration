### Configure nginx

1. Download the ssl certificate and Extract that.
2. go to the exact path and open in terminal.
3. list the file
```bash
ls
```

4. Merge the certificate
```bash
cat certificate.crt ca_bundle.crt >> certificate.crt
```

```bash
vi /etc/nginx/sites-available/api.fourtimes.ml

add this content:
-----------------
server {
    listen       80;
    server_name  api.fourtimes.ml;
    access_log /var/log/nginx/api.fourtimes.ml.access.log;
    error_log  /var/log/nginx/api.fourtimes.ml.error.log;

    location / {
        root   /var/www/api.fourtimes.ml;
        index  index.html index.htm;
    }
}
```

**create directory file**

```bash
mkdir /var/www/api.fourtimes.ml
```

**change the directory**

```bash
cd /etc/nginx/sites-enabled
```
**copy the file sites-enabled from site-available**
```bash
ln -s /etc/nginx/sites-available/api.fourtimes.ml ./
```

**restart the server**

```bash
systemctl restart nginx
```
**status of the server**
```bash
systemctl status nginx
```
**Create index.html file and put the information:**
```bash
vim /var/www/api.fourtimes.ml/index.html

add this content:
-----------------
<html>
<body>
<div style="width: 100%; font-size: 40px; font-weight: bold; text-apiign: center;">
welcome to the api.fourtimes.ml domain
</div>
</body>
</html>
```
**Enter into the ip and domain name in /etc/hosts**
```bash
vim /etc/hosts

ip address    domain name
192.168.94.83 api.fourtimes.ml
```
**To run inside the terminapi**
```bash
curl api.fourtimes.ml
```