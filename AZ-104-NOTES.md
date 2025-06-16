## Notes for AZ-104

### Governance
```
- Advantages of using Bicep over ARM templates
- Simplified syntax: Bicep offers a cleaner and more concise syntax compared to ARM templates, making it easier to write and read.
- Modularization: Bicep supports modularization, allowing you to break down your infrastructure into smaller, reusable modules. This improves code organization and maintainability.
- Transpiles to ARM templates: Bicep code is transpiled into ARM templates at deployment time, ensuring compatibility with existing Azure resources and tools.
- Azure Policy supports various enforcement modes: Deny to block non-compliant deployments, Audit to log non-compliance, and Append to modify resources to meet compliance standards
```

### VM
```
- Azure Backup Policy is where you define the schedule for your VM backups. You can specify the frequency (daily, weekly, etc.), the time of day, and how long the backups should be retained.
- Sizing VMs causes restarts.
- Horizontal Scaling: Increase/decrease No. of instances.
- Vertical Scaling: Increase/decrease power to a single instance of workloads (RAM).
- Proximity placement groups represent a new logical grouping capability for your Azure VM, which in turn used a deployment constraint when selecting where to place VMs.
- Azure backups support backup of VMs that are shutdown or offline.
- If you have data in multiple regions create Recovery Service Vault for each region.
- Azure Arc-enabled servers lets you manage Windows and Linux physical servers and virtual machines hosted outside of Azure, on your corporate network, or other cloud provider
```
### VNET
```
- Connect virtual networks to form a unified global network and enable seamless communication between resources in - Different regions - Azure WAN. Hub-and-spoke (centralized hub with auto-managed connections)
- VNET Peering - Small enviornments, Mesh topology, peering done manually
- Azure Virtual Network Manager is a management service that enables to group, configure, deploy, and manage virtual networks globally across subscriptions. With Virtual Network Manager, can define network groups to identify and logically segment your virtual networks
- Network Group: A network group is global container that includes a set of virtual network resources from any region. Then, configurations are applied to target the network group, which applies the configuration to all members of the group.
- When you create a network group, an Azure Policy is created so that Azure Virtual Network Manager gets notified about changes made to virtual network membership.
- IPsec: is a data transmission protocol. It provides the encryption and authenitcation mechanism for the actual VPN tunnel.
- IKEv2: handles the key excehange and tunnel establishment.
- VPN operates on network layer
- LB operates at transport layer tcp/udp
- Application Gateway - App layer, connect between micro services.
- LB redirects multiple instances of micro service component to scale the deployment.
- For overlapping address VNET peering cannot be done.
- Site-to-site: 
    - Uses VPN gateways, public internet by default (IPsec/IKE)
    - For enterprise-grade, high-throughput, low-latency connectivity private connection can be established using Express Route.
- Point-to-site: 
    - Connects individual client devices (e.g., laptops) to Azure. 
    - VPN client software + certificates or Azure AD auth
- Azure Front Door is Microsoft's advanced cloud Content Delivery Network (CDN) designed to provide fast, reliable, and secure access to your applications' static and dynamic web content globally.
    - Natively support end-to-end IPv6 connectivity and the HTTP/2 protocol.
    - Terminate SSL offload at the edge and use integrated certificate management
    - Front Door’s anycast network and split TCP connections.
    - 118 edge locations across 100 metro cities connected to Azure using a private enterprise-grade WAN

```
### Storage
```
- Strong encryption both at rest and in transit: Azure Storage Service Encryption (SSE) with cutomer managed key
- Azure VMs must be encrypted at rest - Disk Encryption
- Soft delete for blobs and blob versioning are essential features to prevent accidental deletion of critical data and provide the flexibility to recover previous versions of files.
- A managed identity from Microsoft Entra ID allows App Service to access resources through role-based access control (RBAC), without requiring app credentials. After assigning a managed identity to your web app, Azure takes care of the creation and distribution of a certificate.
- Azure Disck Encryption: Virtual disk inside the VM OS, not directly for data within storage accounts.
- Server-Side Encryption (SSE): Azure automatically encrypts data before storing it and decrypts it when accessed — this includes data in Azure Storage, including managed disks.
- Blob can be created in a container. Container can have any blobs.
- Blob storage access for a given period of time use Shared Access Signature provided by blobs.
- If Blob data is not accessed for 30 days move data to cool tier and after 90 days move to archieve.
- SMB over HTTPs for lift and shift thats why fileshare.
```
### Monitoring
```
- Connection Monitor avg RTT (Round Trip Time) of the packets from VM1 to VM2
- Metrics third party tools: Azure ITSM and SIEM (Securrity Information and event management). Azure Sentinel can be used as SIEM tool.
- Azure WAF on App Gateway provides centralised protection of web app from common exploits and vulnerabilities. Web App are increasingly targeted by malacious attacks that exploits commonly known vulnerabilities.
- Traffic Manager: used for traffic distribution on DNS queries, it is DNS based LB.
```
### Web App
```
- Restrict access to Azure App Service web app to specific IP addresses or virtual networks, onfiguring IP restrictions in the Networking settings of Azure App Service
```
### Load Balancer
```
Azure Load Balancer uses health probes to monitor the health of backend VMs. By configuring health probes, you can automatically remove unhealthy VMs from rotation, ensuring that only healthy VMs receive traffic.
```