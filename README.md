# AWS-Cloud-WebApp-Refactor
Apologies for the oversight. Here's the updated short description:  This project involves re-architecting a multi-tier Java web application on the AWS cloud platform, leveraging services such as Elastic Beanstalk, ELB, Autoscaling, RDS, Elastic Cache, ActiveMQ, Route 53, CloudFront, and managing DNS with GoDaddy.

Java Web App Refactoring on AWS Cloud PaaS & SaaS
<img width="1523" alt="271851814-0b5d6a10-96a5-417f-9712-325d0b25b4cc" src="https://github.com/DAMMYTJ/AWS-Cloud-WebApp-Refactor/assets/111458165/dab86495-d9ae-4d49-9184-ccb40d972e20">

Comparison


Beanstalk vs. Tomcat EC2/VM:

Beanstalk: Fully managed platform for deploying and scaling web applications.

Tomcat EC2/VM: Self-managed deployment of Apache Tomcat on EC2 instances or VMs.


ELB in Beanstalk vs. NGINX LB/ELB:

ELB in Beanstalk: Automatically provisioned and configured load balancer.

NGINX LB/ELB: Manually configured NGINX load balancer or AWS ELB.


Autoscaling:

Beanstalk: Supports automatic scaling based on metrics.

None/Autoscaling: Manual scaling or limited autoscaling capabilities.

EFS/S3 vs. NFS/S3/EFS:

EFS/S3: Managed file storage and object storage services.

NFS/S3/EFS: Self-managed file storage solutions.

RDS vs. MySQL on EC2/VM:

RDS: Managed relational database service.

MySQL on EC2/VM: Self-managed MySQL deployment.

Elastic Cache vs. Memcached on EC2/VM:

Elastic Cache: Managed caching service.

Memcached on EC2/VM: Self-managed Memcached deployment.

Active MQ vs. RabbitMQ on EC2/VM:

Active MQ: Managed message broker service.

RabbitMQ on EC2/VM: Self-managed RabbitMQ deployment.

Route 53 vs. GoDaddy/local DNS/Multi-DC across world:

Route 53: Managed DNS service.

GoDaddy/local DNS/Multi-DC across world: Self-managed DNS solutions.

CloudFront:

Beanstalk: Can be integrated with CloudFront.

None: No CDN integration.



Flow of Execution


* 		Login to AWS Account
    * As the first step, log in to your AWS (Amazon Web Services) account using your credentials. This provides access to the AWS Management Console, where you can manage various AWS services and resources.
* 		Create Key pair for Beanstalk Instance Login
    * To ensure secure access to the instances within your Elastic Beanstalk environment, it's essential to create a key pair. This key pair allows you to securely SSH (Secure Shell) into the instances for administrative purposes. You can follow the instructions provided in the  creating-securitygroup-keypair   directory to generate the key pair.
* 		Create Security Group for Elasticache, RDS & ActiveMQ
    * Security groups act as virtual firewalls that control the traffic allowed to reach your AWS resources. It's important to create separate security groups for services like Elasticache (for caching), RDS (Relational Database Service), and Amazon MQ (Managed Message Broker for ActiveMQ). The  creating-securitygroup-keypair   directory provides guidance on setting up these security groups.
* 		Create RDS, Amazon Elastic Cache, Amazon Active MQ
    * Now, proceed to create the actual resources such as RDS instances for your relational databases, Amazon Elastic Cache for caching data, and Amazon MQ for managing message queues. Each of these resources serves a specific purpose in your application architecture. You can refer to the respective directories (creating-RDS, creating-elasticache, creating-amazon-MQ) for detailed instructions on creating these resources.
* 		Create Elastic Beanstalk Environment
    * Elastic Beanstalk simplifies the process of deploying and scaling web applications and services. By creating an Elastic Beanstalk environment, you can easily deploy your application without having to manage the underlying infrastructure. Follow the instructions in the   Beanstalk    directory to set up your Elastic Beanstalk environment.
* 		Update Security Group of Backend to Allow Traffic from Bean SG
    * To ensure communication between different components of your application, update the security group of the backend services to allow incoming traffic from the security group associated with your Elastic Beanstalk environment. This ensures seamless interaction between your application components. Refer to the  update-security-group&ELB   directory for instructions on updating security groups.
* 		Update Security Group of Backend to Allow Internal Traffic
    * In addition to external traffic, it's important to allow internal traffic within your application components. Update the security group of the backend services to allow internal communication between different layers of your application architecture. Detailed instructions can be found in the Build-Deploy-Artifact directory.
* 		Launch EC2-Instance for DB Initializing
    * Launch an EC2 instance specifically for initializing your RDS database. This instance will be used to run scripts or perform actions necessary to set up and initialize your RDS database instance. Refer to the   DB-intialization     directory for guidance on launching and configuring this instance.
* 		Login to the Instance and Initialize RDS DB
    * Once the EC2 instance is launched, log in to it and perform the necessary initialization steps for your RDS database. This may include tasks such as creating database schemas, importing initial data, or configuring database settings. Detailed instructions for initializing the RDS database can be found in the   DB-intialization    directory.
* 		Change Healthcheck on Beanstalk to /login
    * Adjust the health check configuration of your Elastic Beanstalk environment to monitor the /login endpoint of your application. This ensures that the environment health status accurately reflects the availability and responsiveness of your application's login functionality. Instructions for making this configuration change are provided in the    Build-Deploy-Artifact   directory.
* 		Add 443 HTTPS Listener to ELB
    * Enhance the security of your application by configuring the Elastic Load Balancer (ELB) to listen for HTTPS traffic on port 443. This ensures that communication between clients and your application is encrypted using SSL/TLS protocols. Follow the instructions in the   update-security-group&ELB   directory to add the HTTPS listener to your ELB.
* 		Build Artifact with Backend Information
    * Compile and package your application code along with the necessary backend configurations and dependencies into a deployable artifact. This artifact will be deployed to your Elastic Beanstalk environment in the subsequent step. Refer to the   Build-Deploy-Artifact   directory for instructions on building the artifact.
* 		Deploy Artifact to Beanstalk
    * Deploy the compiled artifact to your Elastic Beanstalk environment to make your application available for use. This process involves uploading the artifact to AWS and configuring the Elastic Beanstalk environment to run the application. Detailed deployment instructions can be found in the   Build-Deploy-Artifact    directory.
* 		Create CDN with SSL Cert
    * Set up a Content Delivery Network (CDN) using Amazon CloudFront to distribute your application's static and dynamic content globally with low latency and high transfer speeds. Additionally, configure SSL certificate integration to ensure secure communication between users and the CDN. Follow the steps outlined in the cloudfront-setup directory to create and configure the CDN.


