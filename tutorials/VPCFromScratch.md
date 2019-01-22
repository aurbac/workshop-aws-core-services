# Getting Started with VPC

## 1. Create a VPC from scratch

1.1\. Open the Amazon VPC console at https://console.aws.amazon.com/vpc/.

1.2\. In the upper-right corner of the AWS Management Console, confirm you are in the desired AWS region (e.g., Virginia).

1.3\. In the navigation pane, choose Your VPCs and click on **Create VPC**.

1.4\. For the Name tag type `My VPC` and use the IPv4 CIDR block of `10.1.0.0/16`, click on **Create** and click on **Close**.

1.5\. In the navigation pane, choose Subnets, we are going to create four subnets as follows:

| Name tag | VPC | Availability Zone | IPv4 CIDR block |
| ------:| -----------:| -----------:| -----------:|
| Public Subnet 01  | My VPC | us-east-1a | 10.1.0.0/24 |
| Public Subnet 02  | My VPC | us-east-1b | 10.1.1.0/24 |
| Private Subnet 01  | My VPC | us-east-1a | 10.1.2.0/24 |
| Private Subnet 02  | My VPC | us-east-1b | 10.1.3.0/24 |

1.6\. In the navigation pane, choose Route Tables and click **Create route table**.

1.7\. For the Name tag type `Public Route` and select `My VPC`, click on **Create** and click on **Close**.

1.8\. In the navigation pane, choose Internet Gateways and click **Create Internet gateway**, type Name Tag with `My IG`, click on **Create** and click on **Close**.

1.9\. Select `My IG` and click on **Actions > Attach to VPC**, choose `My VPC` and click **Attach**.

1.10\. In the navigation pane, choose NAT Gateways and click **Create NAT Gateway**.

1.11\. Select the Subnet ID for your Public Subnet 01 that you copied earlier, click on **Create New IP** and click on **Create a NAT Gateway** and click on **Close**.

1.12\. In the navigation pane, choose Route Tables and apply a filter using the VPC ID that you copied earlier, select the **Public Route**, click on **Routes** and click on **Edit Routes**, apply the following routes and click **Save routes**.

| Destination | Target | 
| ------:| -----------:| 
| 10.1.0.0/16 | local | 
| 0.0.0.0/0  | My IG (Internet Gateway) | 

1.13\. In the **Public Route**, click on **Subnet Associations** and click on **Edit subnet associations**, select the subnets **10.1.0.0/24** and **10.1.1.0/24** and click on **Save**.

1.14\. Now select the **Main** route table, this is our route table for private subnets, click on **Routes** and click on **Edit Routes**, apply the following routes and click **Save routes**.

| Destination | Target | 
| ------:| -----------:| 
| 10.1.0.0/16 | local | 
| 0.0.0.0/0  | NAT Gateway (Select the only one) |

1.15\. Now you have a VPC network with public and private subnets.

## 2. Create a bastion instance

**Bastion Hosts**: Including bastion hosts in your VPC environment enables you to securely connect to your Linux instances without exposing your environment to the Internet. After you set up your bastion hosts, you can access the other instances in your VPC through Secure Shell (SSH) connections on Linux. Bastion hosts are also configured with security groups to provide fine-grained ingress control.


### Create a new Key Pair

2.1\. Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.

2.2\. Click on **Key Pairs** in the NETWORK & SECURITY section near the bottom of the leftmost menu. This will display a page to manage your SSH key pairs. 

2.3\. To create a new SSH key pair, click the **Create Key Pair** button at the top of the browser window.

2.4\. In the resulting pop up window, type `[First Name]-[Last Name]-ImmersionDay` into the Key Pair Name: text box and click **Create**.

2.5\. The page will download the file **[Your-Name]-ImmersionDay.pem** to the local drive.  Follow the browser instructions to save the file to the default download location.

2.6\. Remember the full path to the file .pem file you just downloaded.

**NOTE**: You will use the Key Pair you just created to manage your EC2 instances for the rest of the labs.

### Create the instance

2.7\. Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.

2.8\. Click on **Launch Instance**.

2.9\. In the Quick Start section, select the **Ubuntu Server 16.04 LTS (HVM)** AMI and click **Select**.

2.10\. In the Choose Instance Type tab, select the **t2.micro** instance size and click **Next**.

2.11\. On the Configure Instance Details page, select your network **My VPC** created and the **Public Subnet 01**, for Auto-assign Public IP select **Enable**. Click **Next**.

2.12\. On this page you have the ability to modify or add storage and disk drives to the instance. For this lab, we will simply accept the storage defaults and click **Next**.

2.13\. In order to identify our instance with a friendly name add a tag to the instance, type a key of `Name` and the value of `Bastion`, click on **Next: Configure Security Group**.

2.14\. You will be prompted to create a new security group, which will be your firewall rules. On the assumption that we are building out a Bastion, name your new security group as `Bastion` with only SSH access as default.

2.15\. Click the **Review and Launch** button after configuring the security group.

2.16\. Review your cofiguration and choices, and then click **Launch**.

2.17\. Select the key pair that you created in the beginning of this lab from the drop-down and check the **"I acknowledge"** checkbox. Then click the **Launch Instances** button.

