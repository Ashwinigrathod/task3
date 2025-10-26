AWS VPC Setup (Public and Private Subnets)

📘 Overview

This guide explains how to set up a Virtual Private Cloud (VPC) in AWS with one public and one private subnet.
You will also create a route table, attach an Internet Gateway, and verify that the public subnet has internet access.


---

🧱 Step 1: Create a VPC

Create a new VPC with a CIDR block like 10.0.0.0/16.

This is your main network where all subnets and resources will exist.

Give it a name, for example MyVPC.



---

🌐 Step 2: Create Subnets

Create two subnets inside your VPC:

Public Subnet: Example CIDR 10.0.1.0/24

Private Subnet: Example CIDR 10.0.2.0/24


Both subnets can be in the same Availability Zone.

The public subnet will have access to the internet, and the private subnet will not.



---

🌉 Step 3: Create an Internet Gateway

Create an Internet Gateway (IGW).

Attach it to your VPC.

This allows your VPC to communicate with the internet.

Name it something like MyIGW.



---

🗺️ Step 4: Create a Route Table

Create a new Route Table for your public subnet.

Add a route that sends all internet traffic (0.0.0.0/0) to the Internet Gateway.

This route allows public subnet instances to reach the internet.

Name it PublicRouteTable.



---

🔗 Step 5: Associate the Route Table

Link (associate) your Public Route Table with the Public Subnet.

This means all traffic from that subnet will use the route table that connects to the Internet Gateway.



---

⚙️ Step 6: Enable Public IP

Enable the option “Auto-assign Public IP” for the public subnet.

This ensures that any EC2 instance launched in that subnet automatically gets a public IP.



---

🖥️ Step 7: Launch an EC2 Instance

Launch a small EC2 instance (for example, Amazon Linux 2) inside the Public Subnet.

Choose or create a key pair to connect later.

Make sure the security group allows SSH (port 22) and outbound internet access.



---

🌐 Step 8: Verify Internet Access

Connect to your EC2 instance using SSH from your computer.

Once connected, try opening a website or pinging a public address like google.com.

If it works, your internet setup is successful!



---

🧾 Summary

Component	Example Name	Purpose

VPC	MyVPC	Main network environment
Public Subnet	PublicSubnet	For internet access
Private Subnet	PrivateSubnet	For internal resources
Internet Gateway	MyIGW	Connects VPC to the internet
Route Table	PublicRouteTable	Routes internet traffic via IGW



---

💡 Notes

The public subnet can connect to the internet directly.

The private subnet is used for internal resources that do not need direct internet access.

To give private subnet internet access, you can later set up a NAT Gateway (optional).




Author
created by: Ashwini G Rathod
Purpose: AWS VPC hands-on lab for public/private subnet and internet connectivity
