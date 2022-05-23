## **Configure nginx**

vi /etc/nginx/sites-available/fourtimes.ml

```bash
server {
    listen       80;
    server_name  fourtimes.ml;
    access_log /var/log/nginx/fourtimes.ml.access.log;
    error_log  /var/log/nginx/fourtimes.ml.error.log;

    location / {
        root   /var/www/fourtimes.ml;
        index  index.html index.htm;
    }
}
```

mkdir /var/www/fourtimes.ml

cd /etc/nginx/sites-enabled

ln -s /etc/nginx/sites-available/fourtimes.ml ./

systemctl restart nginx

**Create index.html file and put the information:**

vim /var/www/fourtimes.ml/index.html

_welcome to the fourtimes.ml domain name_

**Enter into the ip and domain name in /etc/hosts**

vim /etc/hosts

192.168.94.83 fourtimes.ml
