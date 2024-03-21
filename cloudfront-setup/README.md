Before setting up CloudFront, remove the CNAME record from the registrar that points to the existing load balancer.
This prepares the domain for redirection through CloudFront.
Setting Up CloudFront:
Access the CloudFront service in the AWS Management Console.
Create a new CloudFront distribution.
Select the load balancer as the origin domain.
Choose the appropriate protocol, HTTP or HTTPS, or match the viewer's request.
Configure caching policies, including allowed HTTP methods and cache keys.
Optionally, enable Web Application Firewall (WAF) for security (not enabled in this demonstration).
Select edge locations based on geographic distribution or use all edge locations for global coverage.
Specify the alternate domain name (e.g., vprofile.example.com) and select the SSL certificate.
Choose the security policy and create the CloudFront distribution.
Configuring DNS Records:
After creating the CloudFront distribution, copy the distribution domain name.
Access the domain registrar's DNS settings (e.g., GoDaddy).
Add a new CNAME record pointing to the CloudFront distribution domain.
Save the changes to update the DNS records.
Monitoring CloudFront Deployment:
Check the status of the CloudFront distribution deployment in the AWS Management Console.
Wait for the deployment to complete and ensure that the distribution status is enabled.
Conclusion and Next Steps:
Once the CloudFront distribution is enabled, validate its functionality by accessing the website through the CloudFront URL.
Verify that the requests are redirected through CloudFront to the load balancer.
Encourage further exploration and experimentation with CloudFront to optimize website performance and global accessibility.

            +-------------------------------------+
            | Start                               |
            +---+---------------------------------+
                |                                    
                v                                    
            +---+---------------------------------+
            | Introduction to CloudFront         |
            +---+---------------------------------+
                |                                    
                v                                    
            +---+---------------------------------+
            | Prepare for CloudFront Setup        |
            +---+---------------------------------+
                |                                    
                v                                    
            +---+---------------------------------+
            | Setting Up CloudFront               |
            +---+---------------------------------+
                |                                    
                v                                    
            +---+---------------------------------+
            | Configure DNS Records               |
            +---+---------------------------------+
                |                                    
                v                                    
            +---+---------------------------------+
            | Monitor CloudFront Deployment       |
            +---+---------------------------------+
                |            
                v                                    
            +---+---------------------------------+
            | End                                 |
            +-------------------------------------+
