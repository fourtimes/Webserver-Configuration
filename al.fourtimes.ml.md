**Configure nginx**

vi /etc/nginx/sites-available/al.fourtimes.ml

```bash
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
``bash
mkdir /var/www/al.fourtimes.ml
```
**change the directory**
``bash
cd /etc/nginx/sites-enabled

**copy the file sites-enabled from site-available**
``bash
ln -s /etc/nginx/sites-available/al.fourtimes.ml ./

**restart the server**
``bash
systemctl restart nginx

**status of the server**
systemctl status nginx

**Create index.html file and put the information:**

vim /var/www/al.fourtimes.ml/index.html

<html>
<body>
<div style="width: 100%; font-size: 40px; font-weight: bold; text-align: center;">
welcome to the al.fourtimes.ml domain

</div>
</body>
</html>

**Enter into the ip and domain name in /etc/hosts**

vim /etc/hosts

192.168.94.83 al.fourtimes.ml

**to run inside the terminal**

curl al.fourtimes.ml
