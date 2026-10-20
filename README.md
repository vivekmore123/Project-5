# Project-5
This is my 5 project.
AWS Old Version – New Version Deployment Using ALB and NAT Gateway

📌 Project Overview

This project demonstrates how to deploy and switch between an old and a new version of a web application using AWS Application Load Balancer (ALB), private EC2 instances, and a NAT Gateway.

The architecture uses public subnets for the ALB and NAT Gateway, while the application servers run in private subnets across different Availability Zones. The ALB routes incoming HTTP traffic to the selected target group, allowing manual version switching and rollback using the same ALB DNS name.

The NAT Gateway provides outbound internet connectivity to private EC2 instances when required, without exposing them directly to the public internet.

🗺️ Architecture Diagram

<img width="1000" height="558" alt="shared_image" src="https://github.com/user-attachments/assets/f85a8daf-ec6c-4e82-bc08-3aa61be3e72a" />


"AWS Old Version New Version Deployment Architecture" (aws-old-new-architecture.png)

🏗️ AWS Services Used

- Amazon VPC
- Public and Private Subnets
- Internet Gateway (IGW)
- NAT Gateway
- Amazon EC2
- Application Load Balancer (ALB)
- Target Groups
- Security Groups
- Route Tables
- Nginx Web Server

⚙️ Project Implementation

1. Configured a VPC with public and private subnets across different Availability Zones.
2. Attached an Internet Gateway and configured public route tables.
3. Created a NAT Gateway in a public subnet for outbound internet access from private subnets.
4. Launched two private EC2 instances: "old-version-server" and "new-version-server".
5. Installed Nginx and configured different web pages on both instances.
6. Created two target groups: "old-version-tg" and "new-version-tg".
7. Configured an internet-facing ALB with an HTTP listener on port 80.
8. Configured security groups to allow application traffic from the ALB to the private EC2 instances.
9. Tested version switching and rollback by changing the ALB listener's default target group.

🔄 Version Switching and Rollback

- Old Version: Set "old-version-tg" as the ALB listener's default action.
- New Version: Change the default action to "new-version-tg".
- Rollback: Switch the listener back to "old-version-tg".

Both versions use the same ALB DNS name. Only the target group selected by the listener receives the forwarded traffic.

🔐 Security and Networking

- Application servers are hosted in private subnets without public IP addresses.
- The ALB accepts HTTP traffic on port 80.
- EC2 security groups allow HTTP traffic only from the ALB security group.
- Private route tables direct outbound internet traffic through the NAT Gateway.
- The Internet Gateway provides internet connectivity for public-facing resources.

🎯 Key Learnings

- AWS VPC networking and subnet configuration.
- Application Load Balancer and target group configuration.
- Private EC2 deployment using Nginx.
- NAT Gateway and route table configuration.
- Security groups and network access control.
- Manual version switching and rollback using an ALB listener.

✅ Conclusion

This project demonstrates how to host two application versions on private EC2 instances and control which version receives user traffic through an Application Load Balancer. It provides hands-on experience with AWS networking, secure application hosting, outbound connectivity, load balancing, and manual deployment rollback.

Note: Version switching is performed manually through the ALB listener. This project does not use Auto Scaling Groups or an automated CI/CD pipeline.

🛠️ Technologies Used

"AWS" "EC2" "VPC" "ALB" "NAT Gateway" "Nginx" "Linux" "Networking"
