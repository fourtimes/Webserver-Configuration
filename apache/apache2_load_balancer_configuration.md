
### Load Balancer Process


 Load balancing is the process of distributing network traffic across multiple servers. This ensures no single server bears too much demand. By spreading the work evenly, load balancing improves application responsiveness. It also increases availability of applications and websites for users.


![Screenshot from 2022-05-30 18-33-53](https://user-images.githubusercontent.com/102893121/170998449-9d31773c-6f59-414d-9db8-5a3c98340c67.png)

---

**_configuration_**

In this section, 2 apache container running as a server
  * Apache1
  * Apache2

**create Apache DockerFile**   

**Note:** To create an Apache container, go to this post.

https://github.com/dodonotdo/webserver-configuration/blob/main/apache/vhost_configuration_dockerfile_image_creation.md

Once you've created the Apache2 image, execute it to create two containers with different ports, as seen below.

```bash
docker run -d -p 8081:80 --name Apache2_container_1 imageid
docker run -d -p 8082:80 --name Apache2_container_2 imageid
```

Check the status of your container's operation.
```bash
docker ps -apache2
```
---

### Apache Configuration file 

```bash

sudo vim /etc/apache2/sites-available/load_balance.conf

```
_sample load balance file_

```bash
<VirtualHost *:80>
<Proxy balancer://mycluster>
    BalancerMember http://localhost:8081
    BalancerMember http://localhost:8082
</Proxy>

    ProxyPreserveHost On

    ProxyPass / balancer://mycluster/
    ProxyPassReverse / balancer://mycluster/
</VirtualHost>
```
_Check ur config_

```bash
apache2ctl -t
sudo systemctl restart apache2.service
```
---

**Output**

```bash
curl localhost:8081
curl localhost:8082
```
or check ur web browser to `localhost:8081` and `localhost:8082`



