# AWS-Set-Up-a-Jenkins-Build-Server
AWS Set Up a Jenkins Build Server

Make sure you have these already: an AWS account, an IAM user, a Key Pair, and a VPC.

To launch an instance lets first create a security group that allows all inbound HTTP traffic and allows SSH from your computers IP.

Find your computers IP address. http://checkip.amazonaws.com/ you can also ask “what is my IP address” in a search engine.	Navigate to EC2 console a choose the us-west-2 (Oregon) region. Select Security Groups in the left menu and Click on Create security group.

