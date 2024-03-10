# -Hosting-a-WordPress-Website-on-AWS
![Alt text](/Host_a_WordPress_Website_on_AWS.png)

This project involves deploying a WordPress website on AWS using various services and configurations for reliability, scalability, and security. Below is a detailed explanation of the deployment process along with the scripts used for installation.

Architecture Overview
The deployment architecture consists of the following components:

Virtual Private Cloud (VPC):

Configured with public and private subnets across two availability zones for high availability.
Utilized for network isolation and security.
Internet Gateway:

Facilitates connectivity between VPC instances and the wider Internet.
Security Groups:

Acts as a network firewall mechanism to control traffic to and from EC2 instances.
Availability Zones:

Leveraged to enhance system reliability and fault tolerance.
EC2 Instances:

Web servers hosted within private subnets for enhanced security.
NAT Gateway:

Enables instances in private subnets to access the Internet.
EFS (Elastic File System):

Used as a shared file system for storing web files.
RDS (Relational Database Service):

Hosted the database for the WordPress application.
Application Load Balancer (ALB):

Distributes web traffic evenly to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
Auto Scaling Group:

Automatically manages EC2 instances to ensure website availability, scalability, fault tolerance, and elasticity.
Route 53:

Registered domain name and set up DNS records for the WordPress website.
Certificate Manager:

Secured application communications using SSL/TLS certificates.
Simple Notification Service (SNS):

Configured to alert about activities within the Auto Scaling Group.
Deployment Steps
1. Initial Setup
Set up a VPC with public and private subnets.
Deploy an Internet Gateway for Internet connectivity.
Configure Security Groups for EC2 instances.
2. Web Server Configuration
Install Apache web server and PHP extensions.
Mount the EFS to the HTML directory for shared file storage.
Install MySQL server for database functionality.
3. WordPress Installation
Download and extract WordPress files to the web server directory.
Configure wp-config.php file for database connectivity.
Set appropriate permissions for web server files.
4. Auto Scaling Configuration
Install necessary software packages on the EC2 instances.
Mount EFS to the HTML directory for shared file storage.
Set permissions and restart the web server.
Scripts
Script to Install WordPress
bash
Copy code
# Update software packages
sudo yum update -y

# Create HTML directory
sudo mkdir -p /var/www/html

# Mount the EFS to the HTML directory
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport "$EFS_DNS_NAME":/ /var/www/html

# Install Apache web server and PHP
sudo yum install -y httpd
sudo systemctl enable httpd
sudo systemctl start httpd
sudo dnf install -y php php-cli php-cgi php-curl php-mbstring php-gd php-mysqlnd php-gettext php-json php-xml php-fpm php-intl php-zip php-bcmath php-ctype php-fileinfo php-openssl php-pdo php-tokenizer

# Install MySQL server
# Set permissions and restart the web server
Script for Auto Scaling Group Launch Template
bash
Copy code
# Update software packages
# Install Apache web server, PHP, and MySQL
# Mount the EFS to the HTML directory
# Set permissions and restart the web server
Conclusion
This deployment setup ensures a scalable, fault-tolerant WordPress website hosted on AWS infrastructure. It leverages various AWS services to achieve high availability, security, and performance for the deployed application. Additionally, the provided scripts automate the installation and configuration process, making it easier to deploy and manage the WordPress environment.
Contributing
Contributions to this project are welcome! Please fork the repository and submit a pull request with your enhancements.

License
This project is licensed under the MIT License - see the LICENSE file for details.
