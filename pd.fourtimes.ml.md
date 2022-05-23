## **Configure nginx**

vi /etc/nginx/sites-available/pd.fourtimes.ml

```bash
server {
    listen       80;
    server_name  pd.fourtimes.ml;
    access_log /var/log/nginx/pd.fourtimes.ml.access.log;
    error_log  /var/log/nginx/pd.fourtimes.ml.error.log;

    location / {
        root   /var/www/pd.fourtimes.ml;
        index  index.html index.htm;
    }
}
```

mkdir /var/www/pd.fourtimes.ml

cd /etc/nginx/sites-enabled

ln -s /etc/nginx/sites-available/pd.fourtimes.ml ./

systemctl restart nginx

systemctl status nginx

**Create index.html file and put the information:**

vim /var/www/pd.fourtimes.ml/index.html

welcome to the pd.fourtimes.ml domain

**Enter into the ip and domain name in /etc/hosts**

vim /etc/hosts

192.168.94.83 pd.fourtimes.ml

**to run inside the terminal**

curl pd.fourtimes.ml
