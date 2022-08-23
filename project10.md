
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

Registered a new domain name lamislick.com under AWS Route 53 services. 

![Screenshot 2022-08-23 at 04 12 25](https://user-images.githubusercontent.com/79456052/186061393-e1765235-1ca0-4cee-b84b-051ec3dd47a8.png)


Assigned an Elastic IP to the Nginx LB server and associated the domain name with the Elastic IP
![Screenshot 2022-08-22 at 21 02 07](https://user-images.githubusercontent.com/79456052/186060735-a01dc72b-48fe-477a-bef2-fee7c835526b.png)

Updated A record in the registrar to point to Nginx LB using Elastic IP address

![3  Created a record on AWS pointing to the Nginx lb ip](https://user-images.githubusercontent.com/79456052/186061036-6caac784-1989-4642-aa89-084c03f4de75.png)






























