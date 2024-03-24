# aws-wordpress-demo
We will configure this project with AWS resources. Here we are going to deal with Nat-GW in public subnet for communicating with DB resources in private subnet.


Here are the detailed steps to host a WordPress website using a WordPress application on an EC2 instance in a public subnet, with an RDS SQL database in a private subnet, and access it via a NAT Gateway:

1. Set Up VPC:
   - Create a VPC with a CIDR block of your choice.
   - Create two subnets: one public subnet and one private subnet.
   - Associate the public subnet with a route table that has a route to the internet gateway (for internet access) and the private subnet with a route table that has a route to the NAT Gateway (for internet access).

2. Create NAT Gateway:
   - Create a NAT Gateway in the public subnet.
   - Ensure it has an Elastic IP (EIP) associated with it.
   - Update the route table of the private subnet to route internet-bound traffic through the NAT Gateway.

3. Set Up Security Groups:
   - Create security groups for the WordPress EC2 instance and the RDS instance.
   - Allow inbound HTTP (port 80) and HTTPS (port 443) traffic to the WordPress EC2 instance from anywhere (0.0.0.0/0).
   - Allow inbound MySQL (port 3306) traffic to the RDS instance from the security group of the WordPress EC2 instance.
   - Allow outbound traffic from the WordPress EC2 instance to the RDS instance.

4. Create RDS Instance:
   - Define an RDS instance in the private subnet.
   - Specify the engine type (e.g., MySQL), instance type, username, password, and other configurations.
   - Ensure the security group of the RDS instance allows inbound traffic from the security group of the WordPress EC2 instance.

5. Launch WordPress EC2 Instance:
   - Launch an EC2 instance in the public subnet.
   - Use an existing Amazon Machine Image (AMI) with WordPress pre-installed or set up WordPress manually after launching the instance.
   - Ensure it has a public IP (or Elastic IP) associated with it.
   - Configure the WordPress instance to connect to the RDS instance using the RDS endpoint, database username, and password.
   - Update the security group of the WordPress instance to allow outbound traffic to the RDS instance.

6. Access WordPress Website:
   - Access the public IP (or Elastic IP) of the WordPress EC2 instance in a web browser.
   - Complete the WordPress setup process by providing the necessary details (site title, username, password, etc.).
   - Your WordPress website should now be accessible and running.

By following these steps, you'll have a WordPress website hosted on an EC2 instance in a public subnet, with the database securely hosted in a private subnet. Access to the RDS database is facilitated through the NAT Gateway from the WordPress EC2 instance using the provided username and password.
