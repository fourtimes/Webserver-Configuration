## Webserver Configuration for nginx
First, Change for Root User
```bash
vi /etc/nginx/sites-available/fourtimes.com

add this content:
-----------------
server {
    listen       80;
    server_name  fourtimes.com;
    access_log /var/log/nginx/fourtimes.com.access.log;
    error_log  /var/log/nginx/fourtimes.com.error.log;

    location / {
        root   /var/www/fourtimes.com;
        index  index.html index.htm;
    }
}
```

**create directory file**

```bash
mkdir /var/www/fourtimes.com
```

**change the directory**

```bash
cd /etc/nginx/sites-enabled
```
**copy the file sites-enabled from site-available**
```bash
ln -s /etc/nginx/sites-available/fourtimes.com ./
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
vim /var/www/fourtimes.com/index.html

add this content:
-----------------
<html>
<body>
<div style="width: 100%; font-size: 40px; font-weight: bold; text-align: center;">
welcome to the fourtimes.com domain
</div>
</body>
</html>
```
**Enter into the ip and domain name in /etc/hosts**
```bash
vim /etc/hosts

ip address    domain name
192.168.94.83 fourtimes.com

# if we use ec2 instance server, we put a entry in localhost(our laptop)
(public-ip) fourtimes.com
```
**To run inside the terminal**
```bash
curl fourtimes.com
```
