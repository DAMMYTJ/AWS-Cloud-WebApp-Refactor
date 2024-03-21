Enabling ACL on S3 Bucket:
Head to the S3 dashboard and locate your bucket, typically starting with the name Elasticbeanstalk.
Check if the region code matches your setup.
In the bucket settings, navigate to Permissions and find Object Ownership.
Enable ACL by clicking on Edit.
By enabling ACL, we grant access to the S3 bucket for our AWS account, allowing us to upload and download files without the need for bucket policies.
Acknowledge the changes to confirm.
Updating Health Check in the Target Group:
Return to the Elastic Beanstalk environment and click on Configuration.
Under Instance Traffic and Scaling, select Edit.
Specify the health check path as "/login", tailored for our vProfile application.
Enable session stickiness to ensure user requests consistently land on the same EC2 instance.
This setting ensures that the health check accurately reflects the application's availability.
Adding HTTPS Listener and ACM Certificate:
Add an HTTPS listener on port 443 to the load balancer.
Select the appropriate ACM certificate for your domain, which was previously configured.
Apply the changes to implement HTTPS support.
This step prepares the environment for secure communication with the application.
Updating Security Group:
Go to the EC2 dashboard and locate the security group associated with your instances.
Edit the inbound rules and add a new rule to allow all traffic from the instance security group.
This update ensures that the backend services (RDS, ElastiCache, Amazon MQ) accessed by the instances are reachable via the backend security group.
While allowing all traffic simplifies the setup for learning purposes, in production environments, it's advisable to define specific rules for each service.

            +------------------------------------+
            | Start                              |
            +---+--------------------------------+
                |                                    
                v                                    
            +---+--------------------------------+
            | Enable ACL on S3 Bucket           |
            +---+--------------------------------+
                |                                    
                v                                    
            +---+--------------------------------+
            | Update Health Check               |
            | in Target Group                   |
            +---+--------------------------------+
                |                                    
                v                                    
            +---+--------------------------------+
            | Add HTTPS Listener and            |
            | ACM Certificate                   |
            +---+--------------------------------+
                |                                    
                v                                    
            +---+--------------------------------+
            | Update Security Group             |
            +---+--------------------------------+
                |                                    
                v                                    
            +---+--------------------------------+
            | Final Checks                      |
            +---+--------------------------------+
                |                                    
                v                                    
            +---+--------------------------------+
            | End                                |
            +------------------------------------+
