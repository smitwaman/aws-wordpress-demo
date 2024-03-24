Here's a step-by-step guide to setting up a VPC with one public subnet and one private subnet:

1. Create a VPC:
   - Go to the AWS Management Console and navigate to the VPC dashboard.
   - Click on "Create VPC".
   - Enter a name for your VPC and specify a CIDR block (e.g., 10.0.0.0/16).
   - Click on "Create VPC".

2. Create Subnets:
   - After creating the VPC, navigate to the "Subnets" section in the VPC dashboard.
   - Click on "Create subnet".
   - Choose the VPC you created in step 1.
   - Specify a name for your subnet and choose the availability zone.
   - Enter the CIDR block for the subnet. For a public subnet, it could be something like 10.0.1.0/24. For a private subnet, it could be 10.0.2.0/24.
   - Click on "Create subnet".
   - Repeat this process to create another subnet (either public or private) with a different CIDR block.

3. Set Up Internet Gateway (IGW):
   - Navigate to the "Internet Gateways" section in the VPC dashboard.
   - Click on "Create internet gateway".
   - Enter a name for your internet gateway and click on "Create internet gateway".
   - Select the newly created internet gateway and click on "Attach to VPC".
   - Choose the VPC you created in step 1 and click on "Attach internet gateway".

4. Set Up Route Tables:
   - Navigate to the "Route Tables" section in the VPC dashboard.
   - Find the route table associated with your VPC and note down its ID.
   - Click on "Edit routes".
   - Add a route with destination 0.0.0.0/0 and target as the internet gateway you created in step 3.
   - Save the changes.

5. Associate Subnets with Route Tables:
   - Still in the "Route Tables" section, click on the route table associated with your public subnet.
   - Click on the "Subnet associations" tab.
   - Click on "Edit subnet associations" and select the public subnet(s) you created.
   - Save the changes.
   - Repeat this process for the route table associated with your private subnet(s).

6. Set Up NAT Gateway (For Private Subnet):
   - Navigate to the "NAT Gateways" section in the VPC dashboard.
   - Click on "Create NAT gateway".
   - Choose the subnet of your public subnet and select an Elastic IP address.
   - Click on "Create NAT gateway".
   - Once the NAT gateway is created, update the route table associated with your private subnet(s) to have a route to the NAT gateway for internet-bound traffic (0.0.0.0/0).

Now, you have a VPC with one public subnet and one private subnet, each associated with appropriate route tables for internet access. The public subnet has a route to the internet gateway, while the private subnet has a route to the NAT gateway for internet access.
