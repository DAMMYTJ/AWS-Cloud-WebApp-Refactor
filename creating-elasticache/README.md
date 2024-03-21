Now, let's set up our ElastiCache cluster. While we'll start with a single instance to keep costs down, you can always scale up to a cluster if your project demands it.

Subnet Group and Parameter Group Setup:
To begin, we need to create a Subnet Group. Head over to ElastiCache, click on "Subnet Groups", and create a new one.
Give it a name and description, select the default VPC, and make sure all availability zones are selected. Then, click on "Create".
Next, create a Parameter Group for memcached configuration. Go to Parameter Groups, create a new parameter group, select memcached 1.6, and name it accordingly.
Creating the ElastiCache Instance:
Back on the ElastiCache dashboard, click on "Create" followed by "Memcached Cluster".
Choose "Standard create" to access free tier options.
Provide a name and description for your cluster.
Select the engine version (1.6 for memcached), port, and the parameter group created earlier.
For Node type, choose the smallest option (t2.micro) to keep costs low and opt for a single instance setup.
Ensure the subnet group is correctly selected, along with the backend security group.
Review the configuration details and click on "Create".
Final Checks:
Before proceeding, double-check the Node type and security group settings to ensure everything is in order.
Next Steps:
While the cluster is being created, we can proceed with setting up RabbitMQ, another vital component for our project

             +-----------------------------------+
             | Start                             |
             +---+-------------------------------+
                 |
                 v
             +---+-------------------------------+
             | Subnet Group and Parameter Group  |
             | Setup                             |
             +---+-------------------------------+
                 |
                 v
             +---+-------------------------------+
             | Creating the ElastiCache Instance|
             +---+-------------------------------+
                 |
                 v
             +---+-------------------------------+
             | Final Checks                      |
             +---+-------------------------------+
                 |
                 v
             +---+-------------------------------+
             | Next Steps                        |
             +---+-------------------------------+
                 |
                 v
             +---+-------------------------------+
             | End                               |
             +-----------------------------------+
