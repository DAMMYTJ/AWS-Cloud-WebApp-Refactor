Now, let's dive into running SQL queries on our RDS instance to set up our database schema. You can find the SQL queries in our project's source code repository at github.com/hqscoder/vprofile-project. We'll stick to the main branch for this demonstration.

Launching EC2 Instance for SQL Queries:
Go to the EC2 service and launch an instance in the same region and default VPC.
Choose an Ubuntu instance and name it something like "MySQL-client".
Use the vprofile-bean-key as the key pair and create a new security group, MySQL-client-SG, allowing SSH access from your IP.
Once the instance is launched, update and install the MySQL client: sudo apt update && sudo apt install mysql-client -y.
Configure inbound rules of the vprofile-backend-security group to allow MySQL connections from the MySQL-client-SG security group.
Running SQL Queries:
SSH into the EC2 instance and install the MySQL client.
Use the RDS endpoint, username, password, and database name to connect to the RDS instance: mysql -h <RDS_endpoint> -u admin -p <password> accounts.
Clone the source code repository and navigate to the location of the DB_backup.sql file.
Execute the SQL queries on the RDS database using the command: mysql -h <RDS_endpoint> -u admin -p <password> accounts < SRC/main/resources/DB_backup.sql.
Verify the tables are created by logging into the RDS instance and running show tables.
Setting Up Broker and Other Services:
While the SQL queries are being executed, ensure the RabbitMQ (Amazon MQ) and ElastiCache clusters are running and note down their endpoints.
Remove unnecessary port numbers and prefixes from the endpoints for further usage.
Next Steps:
Once all backend services are ready and SQL queries are executed successfully, proceed to set up the Beanstalk environment and deploy the artifact.
The deployed application will utilize these backend services, so ensure you have their endpoints handy.
           +---------------------------------------+
           | Start                                 |
           +---+-----------------------------------+
               |                                    
               v                                    
           +---+-----------------------------------+
           | Launching EC2 Instance for SQL Queries|
           +---+-----------------------------------+
               |                                    
               v                                    
           +---+-----------------------------------+
           | Running SQL Queries                   |
           +---+-----------------------------------+
               |                                    
               v                                    
           +---+-----------------------------------+
           | Setting Up Broker and Other Services  |
           +---+-----------------------------------+
               |                                    
               v                                    
           +---+-----------------------------------+
           | Next Steps                            |
           +---+-----------------------------------+
               |                                    
               v                                    
           +---+-----------------------------------+
           | End                                   |
           +---------------------------------------+
