# AZURE NETWORKING: VIRTUAL NETWORK (VNET) AND SUBNET CONFIGURATION DOCUMENTATION
This document explains how to create a Virtual Network and configure subnets in Microsoft Azure, including best practices for IP planning and network segmentation.

<p align="center"> <img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/f634b80f-e38a-4cef-9490-95e5cbeab616" />

This diagramatic representation is only for test purposes especially with the IP addressing.
## Table of contents
1. [Introduction](#introduction)
2. [Pre-requisites and Services used](#pre-requisites-and-services-used)
3. Planning the IP Adress Space
4. Creating a Virtual Network
5. Validation and Verification
6. Creating Subnets
7. Creating and Associating Network Security Groups to Subnets
8. Common Errors and Troubleshooting
9. Conclusion

## Introduction
A Virtual Network in Microsoft Azure is a private network that enables secure communication between Azure resources, the internet as well as onsite networks. 
Subnetting can be best explained as the logical subdivision of an IP address. It allows for segmentation of the VNET into smaller networks for ideal privacy and security thereby ensuring better organization and traffic control.

This document outlines the steps to create a Virtual Network and configure subnets in Azure.

## Pre-requisites and Services used
* Access to Azure Portal
* An Active Subscription
* Basic Understanding of IP adressing and CIDR notation
* Virtual Network
* Subnets
* Network Security Groups


## Planning the IP Adress Space
It is necessary to plan your IP addressing before creating your virtual network. This ensures efficient use of addresses, prevents overlapping networks, and allows for future scalability. When designing a VNet, a private IPv4 address range should be selected and divided into non-overlapping subnets based on workload requirements. Each subnet should be sized to accommodate current needs while leaving room for growth. Careful planning at this stage helps avoid network conflicts and simplifies expansion, peering, and hybrid connectivity going forward. 

The recommended private IP address ranges are:
* 10.0.0.0/8
* 172.16.0.0/12
* 192.168.0.0/16

## Creating a Virtual Network 
* Sign in into your Azure account
* Navigate to Virtual Networks either by clicking the three horizontal lines at the top-left corner of the dashboard or by using the search bar.
* On the Virtual Network page, click Create to start the process.
* Fill in the necssary information in the Basics Tab. This include the subscription, the resource group, the name of the virtual network and its availability region.
* For the security tab, the measures listed are only available for the paid tier subscription. Skip if on the free tier. 
* Next is the IP address tab. Fill in your desired IP address and indicate its cidr range for your Vnet.
* On the Tags section, you can include other details like owner name, product stage and other required information.
* Then review and click Create.

## Validation and Verification
Azure performs validation to check the VNet configuration for errors (like overlapping IPs) and verification to confirm the VNet is created and working correctly.

## Creating Subnets
