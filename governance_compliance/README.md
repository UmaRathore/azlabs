
## az governanceand compliance
```
A curated Azure learning path focused on governance, compliance, and hands-on labs.
```
## Overview
```
This repository provides step-by-step labs, scripts, and resources which helped me learn and implement Azure governance and compliance best practices. 

Resources - https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/

```
## Topics Covered
```
- Azure Policy and Initiatives
- Role-Based Access Control (RBAC)
- Management Groups and Subscriptions
- Resource Locks and Tagging
- Azure Blueprints
- Compliance Manager and Regulatory Compliance
- Monitoring and Reporting
```
### Lab 01: Manage Microsoft Entra ID Identities

## Key Takeaways
```
- A tenant represents your organization and helps you to manage a specific instance of Microsoft cloud services for your internal and external users.
- Microsoft Entra ID has user and guest accounts. Each account has a level of access specific to the scope of work expected to be done.
- Groups combine together related users or devices. There are two types of groups including Security and Microsoft 365.
Group membership can be statically or dynamically assigned.
- Microsoft EntraID:
Identity provider for authentication and user management.
Cloud-based identity service that manage Users, groups, service principals, MFA, SSO, integrates with Azure and MS 365
- Azure IAM:
Azuthorization layer for Azure resource access.
Refer to RBAC system to authorize users, groups and applications to Azure resources. 
```
## Lab 02a - Manage Subscriptions and RBAC
```
- The root management group is built into the hierarchy to have all management groups and subscriptions fold up to it. This root management group allows for global policies and Azure role assignments to be applied at the directory level. 
- After creating a management group, you would add any subscriptions that should be included in the group.
- As a best practice always assign roles to groups not individuals.
```
### Create a custom RBAC role
```
{
    "properties": {
        "roleName": "Custom Support Request",
        "description": "A custom contributor role for support requests.",
        "assignableScopes": [
            "/providers/Microsoft.Management/managementGroups/az104-mg1"
        ],
        "permissions": [
            {
                "actions": [
                    "Microsoft.Authorization/*/read",
                    "Microsoft.Resources/subscriptions/resourceGroups/read",
                    "Microsoft.Support/*"
                ],
                "notActions": [
                    "Microsoft.Support/register/action"
                ],
                "dataActions": [],
                "notDataActions": []
            }
        ]
    }
}
```
### Activity Log
![Activity Logs for Custom Roles][/Users/umasharma/git_workspace/azlabs/governance_compliance/activityLog_CustomRoles.png]

## Key Takeaways
```
- Management groups are used to logically organize subscriptions.
- The built-in root management group includes all the management groups and subscriptions.
- Azure has many built-in roles. You can assign these roles to control access to resources.
- You can create new roles or customize existing roles.
- Roles are defined in a JSON formatted file and include Actions, NotActions, and AssignableScopes.
- You can use the Activity Log to monitor role assignments.
- Azure RBAC Roles:
Used to control what users can do with Azure resources
Common Roles - Reader, Contributor, Owner, Storage Blob Data Contributor, Custom Roles.
- Microsoft Entra ID Roles:
Used to control Access to Microsoft Entra Directory-Level resources like Users, Groups, Applications, Conditional and Enterprise Access
Common Roles - Global Admin, User Admin, Application Admin, Security Reader.
```