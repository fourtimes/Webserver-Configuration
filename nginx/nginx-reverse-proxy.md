# Nginx Reverse Proxy 
1. Create the configuration file - `sudo vim /etc/nginx/site-available/grafana.conf`
```conf
server {
    listen       80;
    server_name  grafana.fourcodes.net;
    return 301 https://$host$request_uri;
}

server {
    listen               443 ssl;
    ssl_certificate      /etc/nginx/ssl-certificate/certificate.crt;
    ssl_certificate_key  /etc/nginx/ssl-certificate/private.key;
    server_name          grafana.fourcodes.net;
    access_log           /var/log/nginx/grafana.fourcodes.net.access.log;
    error_log            /var/log/nginx/grafana.fourcodes.net.error.log;
    
    location / {
        proxy_pass http://10.0.0.184:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

2. Link the configuration file on `site-enabled`
```
sudo  ln -s /etc/nginx/site-available/grafana.conf /etc/nginx/sites-enabled/
```
3. Restart the nginx configuration
```sh
sudo systemctl restart nginx.service
```
