# -Hosting-a-WordPress-Website-on-AWS
This repository contains the resources and scripts used to deploy a WordPress website on Amazon Web Services (AWS). The project leverages various AWS services to ensure high availability, scalability, and security for the WordPress application.

Architecture Overview
The WordPress website is hosted on EC2 instances within a highly available and secure architecture that includes:

Virtual Private Cloud (VPC): With public and private subnets across two Availability Zones (AZs) for fault tolerance and high availability.
Internet Gateway: To allow communication between instances in the VPC and the internet.
Security Groups: Acting as a virtual firewall to control inbound and outbound traffic.
Public Subnets: Used for the NAT Gateway and Application Load Balancer, facilitating external access and load balancing.
Private Subnets: For web servers to enhance security.
EC2 Instance Connect Endpoint: For secure SSH access.
Application Load Balancer: With a target group to distribute incoming web traffic across multiple EC2 instances.
Auto Scaling Group: To automatically adjust the number of EC2 instances based on traffic, ensuring scalability and resilience.
Amazon RDS: For a managed relational database service.
Amazon EFS: For a scalable, elastic file storage system.
AWS Certificate Manager: For managing SSL/TLS certificates.
AWS Simple Notification Service (SNS): For notifications related to Auto Scaling Group activities.
Amazon Route 53: For domain name registration and DNS management.
Deployment Scripts
WordPress Installation Script
This script is used for the initial setup of the WordPress application on an EC2 instance. It includes steps for installing Apache, PHP, MySQL, and mounting the Amazon EFS to the instance.

bash
Copy code
# Script content provided in the repository.
Auto Scaling Group Launch Template Script
This script is included in the launch template for the Auto Scaling Group, ensuring that new instances are configured correctly with the necessary software and settings.

bash
Copy code
# Script content provided in the repository.
How to Use
Clone this repository to your local machine.
Follow the AWS documentation to create the required resources (VPC, subnets, Internet Gateway, etc.) as outlined in the architecture overview.
Use the provided scripts to set up the WordPress application on EC2 instances within the VPC.
Configure the Auto Scaling Group, Load Balancer, and other services as per the architecture.
Access the WordPress website through the Load Balancer's DNS name.
Contributing
Contributions to this project are welcome! Please fork the repository and submit a pull request with your enhancements.

License
This project is licensed under the MIT License - see the LICENSE file for details.
