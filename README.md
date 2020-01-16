## MADBOX-TEST

# Time of work

Took me about five hours to set up.

# Technical choices

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


Requirement
Archive test-vpn
Download Tunnelblick (VPN client) https://tunnelblick.net/
Clean your web browser cache

Step by step
- unzip archive test-vpn
- open tunnelblick
- add conf vpn at yout vpn client (client.conf)
- make a curl www.google.com
- make a ping www.google.com
- Enter in your browser the url www.google.com in http (in https it will not work)

Be careful if in the browser's cache there has already been a return from google.com 
it will not work either, it must be done with a browser that has an empty cache or a browser that has not yet been on google.com.

And it normally works :)

## Summary of the implementation of the configuration

### VPN
Since I don't know by heart the installation path of openvpn I did it with this site:
https://wiki.debian-fr.xyz/Serveur_OpenVPN

For the dns server I setup bind9 server in my ec2 instance (screenshot in the repot)
I setup one global zone file and one google.com zone file

For apache2 config I create a virthual host and enabled with a2ensite google.com (the name of virtualhost it's google.com.conf)
and in /var/www/html/google.com, I create an index.html with Hello World

