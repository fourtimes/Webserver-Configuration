## **Configure nginx**

vi /etc/nginx/sites-available/frd.fourtimes.ml

```bash
server {
    listen       80;
    server_name  frd.fourtimes.ml;
    access_log /var/log/nginx/frd.fourtimes.ml.access.log;
    error_log  /var/log/nginx/frd.fourtimes.ml.error.log;

    location / {
        root   /var/www/frd.fourtimes.ml;
        index  index.html index.htm;
    }
}
```

mkdir /var/www/frd.fourtimes.ml

cd /etc/nginx/sites-enabled

ln -s /etc/nginx/sites-available/frd.fourtimes.ml ./

systemctl restart nginx

systemctl status nginx

**Create index.html file and put the information:**

vim /var/www/frd.fourtimes.ml/index.html

welcome to the frd.fourtimes.ml domain

**Enter into the ip and domain name in /etc/hosts**

vim /etc/hosts

192.168.94.83 frd.fourtimes.ml


**to run inside the terminal**

curl frd.fourtimes.ml