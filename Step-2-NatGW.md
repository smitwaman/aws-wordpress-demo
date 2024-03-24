Here are the detailed steps to create a NAT Gateway on AWS:

1. Navigate to the NAT Gateways Page:
   - Log in to the AWS Management Console.
   - Go to the VPC dashboard.
   - Click on "NAT Gateways" in the left-hand navigation pane.

2. Create NAT Gateway:
   - Click on the "Create NAT Gateway" button.
   - Select the public subnet where you want to create the NAT Gateway.
   - Choose an existing Elastic IP address or allocate a new one. If you don't have an Elastic IP address, you can allocate one by clicking on "Create New EIP".
   - Click on "Create NAT Gateway".

3. Wait for NAT Gateway to be Available:
   - It may take a few minutes for the NAT Gateway to be created and become available. You can monitor its status on the NAT Gateways page. Wait until the status changes to "Available".

4. Update Route Table:
   - Go to the Route Tables section in the VPC dashboard.
   - Find the route table associated with your private subnet(s).
   - Click on "Edit routes".
   - Add a new route with the destination as 0.0.0.0/0 (or your desired internet-bound traffic) and the target as the NAT Gateway you just created.
   - Save the changes.

Now, your private subnet is configured to route internet-bound traffic through the NAT Gateway. This ensures that resources in the private subnet, such as your RDS database, can access the internet for updates, patches, or any other necessary outbound communication.
