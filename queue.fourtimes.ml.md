l## **Configure nginx**

vi /etc/nginx/sites-available/queue.fourtimes.ml

```bash
server {
    listen       80;
    server_name  www.queue.fourtimes.ml;
    access_log /var/log/nginx/queue.fourtimes.ml.access.log;
    error_log  /var/log/nginx/queue.fourtimes.ml.error.log;

    location / {
        root   /var/www/queue.fourtimes.ml;
        index  index.html index.htm;
    }
}
```

mkdir /var/www/queue.fourtimes.ml

cd /etc/nginx/sites-enabled

ln -s /etc/nginx/sites-available/queue.fourtimes.ml ./

systemctl restart nginx

systemctl status nginx

**Create index.html file and put the information:**

vim /var/www/queue.fourtimes.ml/index.html

<html>
<body>
<div style="width: 100%; font-size: 40px; font-weight: bold; text-queueign: center;">
welcome to the queue.fourtimes.ml domain

</div>
</body>
</html>

**Enter into the ip and domain name in /etc/hosts**

vim /etc/hosts

192.168.94.83 queue.fourtimes.ml

**to run inside the terminqueue**

curl queue.fourtimes.ml
