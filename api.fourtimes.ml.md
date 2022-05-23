## **Configure nginx**

vi /etc/nginx/sites-available/api.fourtimes.ml

```bash
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

mkdir /var/www/api.fourtimes.ml

cd /etc/nginx/sites-enabled

ln -s /etc/nginx/sites-available/api.fourtimes.ml ./

systemctl restart nginx

**Create index.html file and put the information:**

vim /var/www/api.fourtimes.ml/index.html

welcome to the api.fourtimes.ml domain

**Enter into the ip and domain name in /etc/hosts**

vim /etc/hosts

192.168.94.83 api.fourtimes.ml


**to run inside the terminal**

curl api.fourtimes.ml