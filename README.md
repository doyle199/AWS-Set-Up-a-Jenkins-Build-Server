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

To launch the EC2 instance, go to the EC2 console and click on instance in the left menu. Click on launch instance.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/Launch_instance.png)

Check the free tier only box. Select an Amazon Linux AMI with HVM virtualization.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/HVM.png)

Keep the free tier t2.micro size. Click next: configure instance details.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/t2.micro.png)

Choose your subnet for network. Choose a public subnet for subnet. Make sure Auto-assign Public IP is Enabled.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/network.png)

Click on next: add storage. Click on next: add tags. Click on next: configure security group. Select select an existing security group. Select the WebServerSG created earlier. Click review and launch and then launch. Select an existing key pair, check acknowledgement, and select launch instances.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/instance_1.png)

Take note of the Public DNS in the Description tab after the instance is running.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/Public_DNS.png)

Connect to the instance using an SSH client. Click on the instance then click on the connect button at the top. Follow the instructions for connection. the following screenshot shows connecting with a mac.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/Connect_to_your_instance_mac.png)

udpage the instance with the command "sudo yum update"

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/update_1.png)

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/update_2.png)

to add the Jenkins repo, run the following command: "sudo wget -O/etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo"

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/jenkins_repo.png)

Import a key file from Jenkins-CI to enable installation from the package. Run the following command "sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key"

Install Jenkins with the following command "sudo yum install jenkins -y"

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/Jenkins_install.png)

Start Jenkins as a Service with the following command "sudo service jenkins start". If Java needs to be upgraded to version 8 or 11 go to the oracle website and download it. Then transfer the file from your workstation to the instance. 

Here is an example of using SFTP with Filezilla. Go into settings and check on SFTP, click on add key and select your EC2 key. Click on the sever icon in the top right and enter SFTP for protocol. Put the instance Public DNS in the Host. Use ec2-user for user and click connect

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/FZ.png)

Transfer the java file from your computer to the tmp folder.

![alt text](https://github.com/doyle199/AWS-Set-Up-a-Jenkins-Build-Server/blob/master/transfer.png)

