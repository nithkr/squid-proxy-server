# squid-proxy-server
How to setup proxy server in linux (EC2)

go throught the document and install the squid proxy server in linux operating system 

 Proxy Server Setup


AWS Console 

1. Launch Amazon Linux AMI.
2. VPC should be same as EKS.
3. Check mark to Protection against accidental termination.
4. IAM Role EC2-Cloudwatch.
5. Default Storage but uncheck the Delete in Termination box and also Encrypt the Volume.
6. Allocate Elastic IP to the instance.

SSH to the instance 

Run these commands.
# sudo su	
# yum update –y           // update the machine  
# yum install squid apache2-utils –y      //squid proxy installation
# cd /etc/squid/        //Squid dir
# vi squid.conf  
Allow and add this  
( acl allow-site dstdomain "/etc/squid/allow-site.acl"
http_access allow allow-site) 
 Then save the squif.conf file.


# vi allow-site.acl
      Add these sites (You can add your site that you want to allow in this file)
xxxx.in
xxxxxx.xxx.com
xxxx.in
.xxxxx.com
xxxxx.com 
And save the allow-site.acl
 
# service squid status        //Check status of squid
# systemctl enable squid       // enable squid 
# chown root:squid allow-site.acl
# service squid restart
# service squid status
# netstat –ntpul         // Check the TCP port Eg: Port is 3128



