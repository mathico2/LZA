Firewall Deployment
This Landing Zone Accelerator sample config repository contains configuration necessary for deploying a Centralized Inspection network architecture with Palo Alto VM Series Appliances deployed in an Inspection VPC located in the Network Account. The architecture leverages a combination of AWS Transit Gateway and AWS Gateway Loadbalancer to accomplish centralized inspection.

The routing and firewall deployment are based on the Centralized inspection architecture with AWS Gateway Load Balancer and AWS Transit Gateway blog post.

Prerequisites
To deploy the Firewall Appliances perform the following prerequisite steps:

Deploy base LZA configuration with centralized network account with TGW

Subscribe to Palo Alto AMI in the AWS Marketplace

Example: VM-Series Next-Gen Virtual Firewall w/Advanced Threat Prevention (PAYG)
Create an ssh keypair in the AWS Console for use with Firewall Instances. This sample configuration assumes the existence of a keypair named palo-alto-key

Provision S3 Bucket in Network Account to Host Palo Alto Bootstrap Config.

This sample configuration contains userdata files that instruct the firewall instance to pull configuration from an S3 Bucket. See ~/ec2userdata/firewall-*-bootstrap.txt
Manually provision a firewall instance from the Marketplace AMI to generate config
Refer to Palo Alto VM Series Deployment Guide for details on creating a bootstrap package: Bootstrap the VM-Series Firewall.
Configure the appliance manually and export the configuration (xml) and name it bootstrap.xml
Create the bootstrap.xml file
Create a folder for each firewall to be deployed in the ngfw s3 config bucket (i.e. firewall-a, firewall-b, etc)
Copy the bootstrap.xml to the s3 bucket at the appropriate prefix (i.e. firewall-a, firewall-b)
Create a init-cfg.txt in each config folder for each firewall
Create the init-cfg.txt file
Kick off LZA deployment again and verify the ngfw instance creation