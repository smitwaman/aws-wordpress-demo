Here are the detailed steps to configure security groups for the WordPress EC2 instance and the RDS instance:

1. **Navigate to Security Groups**:
   - Log in to the AWS Management Console.
   - Go to the EC2 dashboard.
   - Click on "Security Groups" in the left-hand navigation pane.

2. **Create Security Group for WordPress EC2 Instance**:
   - Click on the "Create security group" button.
   - Enter a name and description for the security group (e.g., "WordPress-SG").
   - Choose the VPC where your EC2 instance resides.
   - Click on "Create security group".

3. **Define Inbound Rules for WordPress EC2 Instance Security Group**:
   - Select the newly created security group.
   - Click on the "Inbound rules" tab.
   - Click on "Edit inbound rules".
   - Add rules to allow inbound traffic on ports 80 (HTTP) and 443 (HTTPS) from anywhere (0.0.0.0/0). You can do this by selecting "HTTP" and "HTTPS" from the dropdown menu, and entering "0.0.0.0/0" as the source.
   - Click on "Save rules".

4. **Create Security Group for RDS Instance**:
   - Click on the "Create security group" button.
   - Enter a name and description for the security group (e.g., "RDS-SG").
   - Choose the VPC where your RDS instance resides.
   - Click on "Create security group".

5. **Define Inbound Rules for RDS Instance Security Group**:
   - Select the newly created security group.
   - Click on the "Inbound rules" tab.
   - Click on "Edit inbound rules".
   - Add a rule to allow inbound traffic on port 3306 (MySQL) from the security group of the WordPress EC2 instance. To do this, select "MySQL/Aurora" from the dropdown menu, and start typing the name of the WordPress EC2 instance's security group. Select the appropriate security group when it appears.
   - Click on "Save rules".

6. **Define Outbound Rules for WordPress EC2 Instance Security Group**:
   - Select the security group associated with your WordPress EC2 instance.
   - Click on the "Outbound rules" tab.
   - Click on "Edit outbound rules".
   - Add a rule to allow outbound traffic to the RDS instance. To do this, select "MySQL/Aurora" from the dropdown menu, and start typing the name of the RDS instance's security group. Select the appropriate security group when it appears.
   - Click on "Save rules".

Now, your WordPress EC2 instance and RDS instance are configured with the necessary security groups and rules to allow inbound HTTP/HTTPS traffic to the EC2 instance and inbound MySQL traffic to the RDS instance from the EC2 instance's security group. Additionally, outbound traffic from the WordPress EC2 instance to the RDS instance is allowed.
