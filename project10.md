
##Load Balancer Solution With Nginx and SSL/TLS##

Created an EC2 VM based on Ubuntu Server 20.04 LTS and named it Nginx LB, opened up the TCP port 80 for HTTP connections and the TCP port 443 for secured HTTPS connections under the Nginx LB server security group.

![10  Launched an nginx load balancer instance](https://user-images.githubusercontent.com/79456052/186056667-0beaf5fd-d4e0-45d5-89fa-7c3f8ba6f2cf.png)

![Screenshot 2022-08-22 at 19 59 50](https://user-images.githubusercontent.com/79456052/186057303-a29a7708-e50b-4346-b322-3c93c0776b24.png)

Updated /etc/hosts file for local DNS with Web Servers’ names ( Web1 and Web2) and their local IP addresses

![11 Update :etc:hosts file for local DNS with Web Servers’ names (e g  Web1 and Web2) and their local IP addresses](https://user-images.githubusercontent.com/79456052/186057657-8ddc2311-d2c9-4fa8-b259-3bf075d1fd69.png)

Updated the instance and installed nginx using the command  *sudo apt update && sudo apt install nginx* 

![12  Install and configure Nginx as a load balancer to point traffic to the resolvable DNS names of the webservers](https://user-images.githubusercontent.com/79456052/186058596-ebd190f0-7938-4b09-89b4-6cdf9ac236f8.png)

Configured Nginx as a load balancer to point traffic to the resolvable DNS names of the webservers by opening up the default nginx configuration file using the command *sudo vi /etc/nginx/nginx.conf* and added the configuration as given in the documentation to the http section of the config file while using an hastag (#) to comment out the line include /etc/nginx/sites-enabled/*;

![Screenshot 2022-08-22 at 20 15 36](https://user-images.githubusercontent.com/79456052/186059756-4f6e3fb3-87f9-40ea-83c4-00fa5ffb17a6.png)

![Screenshot 2022-08-22 at 20 18 41](https://user-images.githubusercontent.com/79456052/186059811-8f1806f4-60c9-4a9e-b9d4-69a59bc9a4e1.png)

Restarted nginx and made sure the service was up and running using the command *sudo systemctl restart nginx && sudo systemctl status nginx*

![ 21  Install certbot and request for an SSL:TLS certificate](https://user-images.githubusercontent.com/79456052/186060076-4818e4d0-27be-4a1c-b36f-df4a421a5bae.png)

Registered a new domain name lamislick.com under AWS Route 53 services and updated A record in the registrar to point to Nginx LB using Elastic IP address

![Screenshot 2022-08-23 at 04 12 25](https://user-images.githubusercontent.com/79456052/186061393-e1765235-1ca0-4cee-b84b-051ec3dd47a8.png)


Assigned an Elastic IP to the Nginx LB server and associated the domain name with the Elastic IP
![Screenshot 2022-08-22 at 21 02 07](https://user-images.githubusercontent.com/79456052/186060735-a01dc72b-48fe-477a-bef2-fee7c835526b.png)


Confirmed that the Web Servers can be reached from my browser using the  new domain name http://www.lamislick.com using HTTP protocol 

![20  Check that your Web Servers can be reached from your browser using new domain name using HTTP protocol  using lamislick com](https://user-images.githubusercontent.com/79456052/186063242-89fce0f7-7d0e-411a-b991-c732e0f87bf2.png)


Installed certbot and requested for an SSL/TLS certificate
Make sure snapd service was active and running using the command *sudo systemctl status snapd
* and installed certbot using the command *sudo snap install --classic certbot*


![ 21  Install certbot and request for an SSL:TLS certificate](https://user-images.githubusercontent.com/79456052/186063630-707ed78f-43d2-407f-bdf6-1a21a784da4d.png)


Requested for my certificate by  following the certbot instructions using the command *sudo ln -s /snap/bin/certbot /usr/bin/certbot && sudo certbot --nginx*

![Screenshot 2022-08-23 at 04 37 34](https://user-images.githubusercontent.com/79456052/186064631-86ef85e8-40ac-4420-9065-0950a896c998.png)


Tested the secured access to my web Solution by trying to reach https://lamislick.com

![21  https](https://user-images.githubusercontent.com/79456052/186064854-7123fe88-0a05-4f16-9fea-beb2857ba307.png)



























