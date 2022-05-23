**Configure nginx**
```bash
vi /etc/nginx/sites-available/al.fourtimes.ml

add this content:
-----------------
server {
    listen       80;
    server_name  al.fourtimes.ml;
    access_log /var/log/nginx/al.fourtimes.ml.access.log;
    error_log  /var/log/nginx/al.fourtimes.ml.error.log;

    location / {
        root   /var/www/al.fourtimes.ml;
        index  index.html index.htm;
    }
}
```

**create directory file**

```bash
mkdir /var/www/al.fourtimes.ml
```

**change the directory**

```bash
cd /etc/nginx/sites-enabled
```
**copy the file sites-enabled from site-available**
```bash
ln -s /etc/nginx/sites-available/al.fourtimes.ml ./
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
vim /var/www/al.fourtimes.ml/index.html

add this content:
-----------------
<html>
<body>
<div style="width: 100%; font-size: 40px; font-weight: bold; text-align: center;">
welcome to the al.fourtimes.ml domain
</div>
</body>
</html>
```
**Enter into the ip and domain name in /etc/hosts**
```bash
vim /etc/hosts

ip address    domain name
192.168.94.83 al.fourtimes.ml
```
**To run inside the terminal**
```bash
curl al.fourtimes.ml
```