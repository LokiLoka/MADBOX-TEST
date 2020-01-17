## MADBOX-TEST

### Time of work

Took me about five hours to set up.

### Technical choices

I made the choice to run my project on an ec2 instance, cost level so I went on a t2.micro (included in the free tier)
I chose to go on the cloud because I thought that accessibility would be easier and availability I can let my vpn run while the tests are done.

The infrastructure is composed of three elements:
The VPN server with openvpn
A dns BIND server for domain name resolution
And an apache2 server to display the helloworld page.

I made the choice to run my project on an ec2 instance, cost level so I went on a t2.micro (included in the free tier)
I chose to go on the cloud because I thought that accessibility would be easier and availability I can let my vpn run while the tests are done.

The infrastructure is composed of three elements:
The VPN server with openvpn
A dns BIND server for domain name resolution
And an apache2 server to display the helloworld page.


### Requirement
Archive test-vpn
Download Tunnelblick (VPN client) https://tunnelblick.net/
Clean your web browser cache

### Step by step

- certificates and vpn configuration file that was in the email attachment

- open tunnelblick

- add conf vpn at yout vpn client (client.conf) and connected to vpn
![Test Image 5](https://github.com/LokiLoka/MADBOX-TEST/blob/master/Capture7.png)

- make a curl www.google.com
![Test Image 6](https://github.com/LokiLoka/MADBOX-TEST/blob/master/Capture%20d%E2%80%99%C3%A9cran%202020-01-16%20%C3%A0%2018.50.47.png)

- make a ping www.google.com or google.com and dig www.google.com
![Test Image 7](https://github.com/LokiLoka/MADBOX-TEST/blob/master/Capture6.png)

- Enter in your browser the url www.google.com in http (in https it will not work)
Be careful if in the browser's cache there has already been a return from google.com 
it will not work either, it must be done with a browser that has an empty cache or a browser that has not yet been on google.com.

And it normally works :)

![Test Image 8](https://github.com/LokiLoka/MADBOX-TEST/blob/master/Capture%20d%E2%80%99%C3%A9cran%202020-01-16%20%C3%A0%2018.50.31.png)

## Summary of the implementation of the configuration

### VPN
Since I don't know by heart the installation path of openvpn I did it with this site:
https://wiki.debian-fr.xyz/Serveur_OpenVPN

In the procedure we talk about iptables, this step is not really necessary when have done ec2 because we at the security group
I've set up a security group to authorize port 1184 in udp and tcp. (vpn server port)


![Test Image 1](https://github.com/LokiLoka/MADBOX-TEST/blob/master/Capture%20d%E2%80%99%C3%A9cran%202020-01-16%20%C3%A0%2019.39.45.png)

### DNS server
For the dns server I setup bind9 server in my ec2 instance (screenshot in the repot)
I setup one global zone file and one google.com zone file

![Test Image 2](https://github.com/LokiLoka/MADBOX-TEST/blob/master/Capture%20d%E2%80%99%C3%A9cran%202020-01-16%20%C3%A0%2019.41.15.png)

### Webserver

For apache2 config I create a virthual host and enabled with a2ensite google.com (the name of virtualhost it's google.com.conf)
and in /var/www/html/google.com, I create an index.html with Hello World

![Test Image 3](https://github.com/LokiLoka/MADBOX-TEST/blob/master/Capture%20d%E2%80%99%C3%A9cran%202020-01-16%20%C3%A0%2019.41.52.png)

![Test Image 4](https://github.com/LokiLoka/MADBOX-TEST/blob/master/Capture%20d%E2%80%99%C3%A9cran%202020-01-16%20%C3%A0%2021.00.13.png)

### Improvement
In the improvements I would say that if I had had more time I would have automated the installation of the web server and dns server and I would have deployed my ec2 and security groups with terraform.


