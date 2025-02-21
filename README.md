# AWS WordPress Website Deployment Project

## Project Overview:

In this DevOps project, I successfully deployed a WordPress website on AWS using a comprehensive three-tier architecture. The project aimed at achieving high availability, fault tolerance, and seamless scalability for the WordPress site.

## Architecture Highlights:

### Three-Tier VPC Setup:

![image](https://github.com/bconway1906/Deploy-WordPress-Website-on-AWS/assets/148906255/e962d3eb-0dba-450b-8ee9-b15e54d4766f)

1. **Tiers Configuration:**
   - Created a three-tier AWS VPC with public and private subnets spanning 2 availability zones.
   - Tier 1: Public subnet housing Nat Gateway, Load Balancer, and Bastion Host.
   - Tier 2: Private subnet for hosting EC2 webservers.
   - Tier 3: Another private subnet dedicated to the database.

2. **VPC Setup:**
   - Created the initial VPC named "Dev VPC."

3. **Networking Setup:**
   - Enabled DNS Hostnames within the VPC.
   - Established an Internet Gateway for seamless communication with the internet.

4. **Subnet Organization:**
   - Configured public subnets in 2 Availability Zones with Auto Assign IP settings.
   - Created a public route table associating it with public subnets.

5. **Private Subnets:**
   - Established 4 private subnets (2 for webservers, 2 for the database) associated with the main private route table.

6. **NAT Gateway:**
   - Deployed NAT Gateways in Public AZ1 and AZ2 for internet access in private subnets.
   - Allocated elastic IP addresses to the NAT Gateways.

7. **Security Groups:**
   - Configured security groups acting as a firewall for instances.

8. **Database Security Group:**
   - Opened port 3306 (MySQL/Aurora) with the source as the Webserver Security Group.

9. **Elastic File System (EFS):**
   - Created EFS with mount targets in each AZ for webservers to connect.

## WordPress Deployment Steps:

10. **EC2 Instance Setup:**
    - Launched an EC2 instance in the public subnet AZ1 with SSH, ALB, and Webserver security groups.

11. **WordPress Installation:**
    - Execute scripts for updating mount information of EFS.

   <img width="242" alt="image" src="https://github.com/bconway1906/Deploy-WordPress-Website-on-AWS/assets/148906255/516f9c94-b249-4ee1-8197-4771aa426ab3">

12. **ALB Configuration:**
    - Created an ALB to route traffic to EC2 instances in private subnets.
    - Launched instances in private app subnets with user data script for webserver configuration.

13. **HTTPS Listener Setup:**
    - Configured an HTTPS listener for the ALB.
    - Enabled redirection of HTTP traffic to HTTPS.

14. **WordPress SSL Configuration:**
    - Modified WPconfig file on EC2 instances to handle SSL settings.

15. **Domain Registration and SSL Certificate:**
    - Registered a domain in Route 53.
    - Obtained an SSL certificate from AWS Certificate Manager.

16. **Bastion Host Setup:**
    - Launched a public subnet EC2 instance for SSH access to the EC2 instance in the private subnet.

17. **SSH into Private Instance:**
    - Executed SSH commands to access the EC2 instance in the private subnet through the Bastion host.

18. **Auto Scaling Group (ASG):**
    - Created an ASG with a launch template for dynamic management of EC2 instances in the private app subnet.

## Project Conclusion:

This project achieved the successful deployment of a WordPress website on AWS, incorporating best practices for infrastructure design and ensuring reliability, security, and scalability. The GitHub repository contains detailed diagrams and scripts for reference.

