# Highly Available Web Stack – E-commerce (AWS + WordPress + WooCommerce)

## Project Description
This project presents a fully automated, highly available environment for an e-commerce platform. The architecture was designed in accordance with AWS best practices, ensuring scalability, security, and separation of access layers.

## System Architecture
The system is based on a three-tier model:
* **Presentation Layer**: Application Load Balancer (ALB) distributing public traffic.
* **Application Layer**: EC2 instances in Auto Scaling Groups (ASGs) located in private subnets. Data is shared via the Amazon EFS file system.
* **Data Layer**: Amazon RDS (MySQL) database in a Multi-AZ configuration.

## Key Infrastructure Features
* **High Availability**: Distribution of resources across two Availability Zones.
* **Security**: Use of private subnets and Security Groups that restrict traffic to only the necessary ports.
* **Scalability**: An Auto Scaling Group adjusts the number of instances to match the load (min. 2, max. 4).
* **Data Durability**: Amazon EFS stores multimedia files and plugins, allowing multiple instances to access them simultaneously.

## Deployment Guide

### Step 1: Infrastructure (CloudFormation)
1. Log in to the AWS Console.
2. Go to the CloudFormation service and select **Create stack**.
3. Upload the `infrastructure/e-commerce_stack.yaml` file.
4. Enter the parameters (e.g., database password).
5. Once the stack has been created, go to the **Outputs** tab and copy the `WebsiteURL`.

### Step 2: WordPress Setup
1. Open the URL in your browser.
2. Select a language and complete the standard WordPress installation (site title, admin login).
3. Log in to the dashboard.

### Step 3: Installing and Configuring WooCommerce
To turn your website into a store, followi these steps:

#### Installing the plugin:
* In the side menu, select **Plugins** -> **Add New**.
* Search for **WooCommerce**.
* Click **Install Now**, then **Activate**.

#### Setup Wizard:
* Fill in your store’s address information.
* Select your industry and product types (physical/digital).

#### Adding products:
* Go to the **Products** -> **Add New** tab.
* Enter the product name, description, price, and image.

#### Payment and shipping settings:
* In the **WooCommerce** -> **Settings** section, configure payment methods (e.g., bank transfer, Stripe) and shipping zones.

## Technologies
* **Cloud**: AWS (VPC, EC2, RDS, EFS, ALB, ASG, NAT Gateway).
* **IaC**: AWS CloudFormation.
* **CMS**: WordPress.
* **E-commerce**: WooCommerce.
* **OS**: Amazon Linux 2023.