## AZ Governance and Compliance
```
A curated Azure learning path focused on virtual networks, subnets, network security groups, application security groups and hands-on labs.
```
## Overview
```
This repository provides step-by-step labs, scripts, and resources which helped me learn and implement Azure virtual networks, NSG and DNS. 
```

# Azure Virtual Networks, NSG, and DNS Labs

This section of the repository provides hands-on labs and resources for learning about Azure Virtual Networks (VNet), Network Security Groups (NSG), and Domain Name System (DNS) services.

## Overview

- **Virtual Networks (VNet):** Learn how to create and configure VNets to securely connect Azure resources.
- **Network Security Groups (NSG):** Understand how to control inbound and outbound traffic to Azure resources using NSGs.
- **DNS:** Explore Azure DNS for hosting your domain names and managing DNS records.

## Labs Included

1. **Create and Configure a Virtual Network**
   - Set up subnets
   - Connect resources within a VNet

2. **Implement Network Security Groups**
   - Create NSGs and associate them with subnets or NICs
   - Define security rules to allow or deny traffic

3. **Configure Azure DNS**
   - Create a DNS zone
   - Add and manage DNS records
   - Integrate DNS with VNets

## Resources
   - https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/

## Lab 04 - Implement Virtual Networking

### Architecture Diagram
![Architecture Diagram](./images/Vnet_arch.png)

### Create a virtual network with subnets using the portal

![Virtual Network in Azure portal](./images/virtual_network.png)

### Create a virtual network and subnets using a template
- refer virtual_networks/Files/parameters.json
- refer virtual_networks/Files/template.json
![Virtual Network using ARM templates](./images/vnet_using_templates.png)

### Create and configure communication between an Application Security Group and a Network Security Group
- Create the Application Security Group (ASG)
- Create the Network Security Group and associate it with CoreServicesVnet
- Configure an inbound security rule to allow ASG traffic
![Inbound Security Rule](./images/inbound_sec_rule.png)
- Configure an outbound NSG rule that denies Internet access
![Outbound Security Rule](./images/outbound_sec_rule.png)

### Notes
- NSG Limits network traffic to resources in virtual network
- It list security rules that allow or deny inbound or outbound network traffic. There are deafult security rules which cannot be deleted, but new rules can be added with a higher priority
- Associated with subnets or NIC. Can be associated multiple times.
- NSG is applied on NICs or subnets
- ASG logically group virtual machines - web servers, application servers.
- ASG is applied only at subnets. It can used as source or destination in NSG

### Configure public and private Azure DNS zones

- When a new tenant is created, a new default doman is created.
- A DNS zone host DNS records for a domain.
- Root/Parent domain is registered at the registrar and pointed to Azure NS
- When delegating a domain to Azure DNS, you must use the name server names provided by Azure DNS all Four of them.

![DNS Zone](./images/DNSzone.png)

- A Record set is a collection of records in a zone that have the same name and are the same type.
- 20 records can be added to any record set
- A Record set cannot contain two identical record

![Recordsets in DNS Zone](./images/DNS_name_resolution.png)
![Verify delegation of domain name services](./images/DNS_name_resolution.png)

- Use custom domain names. 
- Provides name resolution for VMs within a VNET and between VNETS

![Private DNS](./images/VnetLinkPrivateDNS.png)