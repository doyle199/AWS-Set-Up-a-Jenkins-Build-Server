# AWS-Set-Up-a-Jenkins-Build-Server
AWS Set Up a Jenkins Build Server

Make sure you have these already: an AWS account, an IAM user, a Key Pair, and a VPC.

To launch an instance lets first create a security group that allows all inbound HTTP traffic and allows SSH from your computers IP.

Find your computers IP address. http://checkip.amazonaws.com/ you can also ask “what is my IP address” in a search engine.	Navigate to EC2 console a choose the us-west-2 (Oregon) region. Select Security Groups in the left menu and Click on Create security group.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/SG1.png)

Enter a security group name and description. Choose your VPC.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/SG_name.png)

For inbound rules, click add rule and choose SSH. Enter you IP address for the source. Click add rule and choose HTTP. Add source 0.0.0.0/0 for anywhere. Click add rule and choose custom TCP. Add source 0.0.0.0/0 for anywhere. Enter port range 8080 and click create security group.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/inboundSG.png)


