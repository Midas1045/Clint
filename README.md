# AZURE NETWORKING: VIRTUAL NETWORK (VNET) AND SUBNET CONFIGURATION DOCUMENTATION
This document explains how to create a Virtual Network and configure subnets in Microsoft Azure, including best practices for IP planning and network segmentation.
<p align="center"> <img width="735" height="385" alt="vpc-Page-3 drawio" src="https://github.com/user-attachments/assets/41e36de0-78a8-402f-b549-935425d9cd43" />


## Table of contents
1. [Introduction](#introduction)
2. [Pre-requisites and Services used](#pre-requisites-and-services-used)
3. [Planning the IP Address Space](#planning-the-ip-address-space)
4. [Creating a Virtual Network](#creating-a-virtual-network)
5. [Validation and Verification](#validation-and-verification)
6. [Creating Subnets](#creating-subnets)
7. [Creating and Associating Network Security Groups to Subnets](#creating-and-associating-network-security-groups-to-subnets)
8. [Errors and Troubleshooting](#errors-and-troubleshooting)
9. [Conclusion](#Conclusion)

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


## Planning the IP Address Space
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
<p align="center"> <img width="735" height="385" alt="Screenshot 2026-01-28 020931" src="https://github.com/user-attachments/assets/cad3b463-b1f1-4d7a-bd90-3a9be8472afc" />


## Creating Subnets
* After deployment is complete, open the newly created Virtual Network to access its configuration dashboard.
* From the Virtual Network menu, expand Settings and select Subnets.
* Click the + Subnet button, enter the required subnet name, and Azure will allocate the subnet IP address range accordingly.
* Then Save. Repeat the same process for the required number of subnets needed

Azure reserves five IP addresses in each subnet for platform use, including the network address, default gateway, DNS mapping, and two internal reserved addresses, which must be considered when planning subnet size. To confirm the setup, check that subnets do not overlap, verify the CIDR ranges, and ensure resources are deployed in the correct subnet.

<p align="center"> <img width="1006" height="313" alt="Screenshot 2026-02-01 211914" src="https://github.com/user-attachments/assets/2a6f5e5a-b8e3-4662-a4ec-2ee61d8d8baa" />


## Creating and Associating Network Security Groups to Subnets
Network Security Groups (NSGs) provide network-level security by filtering traffic to and from Azure resources. Security rules define which traffic is allowed or denied.
* Head to the Azure portal dashboard and search for Network Security Groups using the search bar.
* Click Create on the Network Security Groups page to proceed.
* Provide the required details such as the subscription, NSG name, selected resource group, and region
* Then review and save. You can replicate this process based on the number of subnets required for the project.
<p align="center"> <img width="1190" height="476" alt="Screenshot 2026-02-01 211127" src="https://github.com/user-attachments/assets/1a0e4425-e79b-418e-b53e-c2fbb6397672" />


## Errors and Troubleshooting
* ERROR- I attempted to create a virtual network using 200.100.50.0/24 which resulted in an error due to overlapping or insufficient address space.
<p align="center"> <img width="807" height="289" alt="Screenshot 2026-01-28 015715" src="https://github.com/user-attachments/assets/46216265-bf25-4f72-86de-cf62576bad82" />
  
* TROUBLESHOOTING- I used a larger, non-overlapping private IP address range (such as 192.168.0.0/16) thus ensuring the address space does not conflict with existing networks.
<p align="center"> <img width="1000" height="248" alt="Screenshot 2026-02-01 210731" src="https://github.com/user-attachments/assets/7f509a0f-b287-40e9-b3ec-09cee0dd7d0a" />

## Conclusion
