## **Configure nginx**

vi /etc/nginx/sites-available/dv.fourtimes.ml

```bash
server {
    listen       80;
    server_name  dv.fourtimes.ml;
    access_log /var/log/nginx/dv.fourtimes.ml.access.log;
    error_log  /var/log/nginx/dv.fourtimes.ml.error.log;

    location / {
        root   /var/www/dv.fourtimes.ml;
        index  index.html index.htm;
    }
}
```

mkdir /var/www/dv.fourtimes.ml

cd /etc/nginx/sites-enabled

ln -s /etc/nginx/sites-available/dv.fourtimes.ml ./

systemctl restart nginx

systemctl status nginx

**Create index.html file and put the information:**

vim /var/www/dv.fourtimes.ml/index.html

welcome to the dv.fourtimes.ml domain

**Enter into the ip and domain name in /etc/hosts**

vim /etc/hosts

192.168.94.83 dv.fourtimes.ml


**to run inside the terminal**

curl dv.fourtimes.ml