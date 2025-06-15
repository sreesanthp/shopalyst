# shopalyst
AWS Infrastructure Deployment with IaC 
# README - AWS Web Application Infrastructure (CloudFormation)

## Overview

This project provisions a highly available and secure AWS infrastructure using **AWS CloudFormation** to host a scalable web application. It includes VPC setup, public/private subnets, NAT gateways, Application Load Balancer (ALB), EC2 Auto Scaling Group, and RDS MySQL instance.

## Features

* Custom VPC with public and private subnets across two Availability Zones
* High-availability Internet and NAT gateways
* Application Load Balancer exposed to the internet (port 80)
* EC2 Auto Scaling Group with Launch Template and Apache web server
* IAM Role for EC2 instances with SSM access
* Multi-AZ RDS MySQL instance in private subnets
* Least privilege security groups

## Architecture Diagram

![image](https://github.com/user-attachments/assets/8d1d4091-a6ba-4301-b256-020368f253fc)

## Parameters

| Parameter            | Description                                 |
| -------------------- | ------------------------------------------- |
| `VpcCIDR`            | CIDR block for VPC (default: 172.16.0.0/16) |
| `WebAppVPCName`      | Name of the VPC (default: webapp-vpc) |
| `PublicSubnet1CIDR`  | CIDR for public subnet AZ1                  |
| `PublicSubnet2CIDR`  | CIDR for public subnet AZ2                  |
| `PrivateSubnet1CIDR` | CIDR for private subnet AZ1                 |
| `PrivateSubnet2CIDR` | CIDR for private subnet AZ2                 |

## Deployment Instructions

1. clone the Repo, use the tempate file `webapp-infra.yaml` to deploy the solution
2. In AWS Console:
   * Go to **CloudFormation > Stacks > Create stack**.
   * Choose **"With new resources (standard)"**.
   * Click **Next** and create the stack.
3. Wait for stack to complete (\~10–15 mins).

## Outputs

* **VPC** – vpc with internet gateway attached
* **Subnet** – two private and public subnet and the respective route tables
* **LoadBalancerDNS** – public DNS of ALB
* **RDSInstanceEndpoint** – hostname of RDS (internal only)
* **EC2InstanceProfileName** – IAM role profile for EC2


