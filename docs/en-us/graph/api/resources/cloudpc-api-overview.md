<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpc-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Working with Windows 365 Cloud PCs using the Microsoft Graph API

Windows 365 is a cloud-based service that automatically creates a new type of Windows virtual machine \(Cloud PCs\) for your end users. Each Cloud PC is assigned to an individual user as a dedicated Windows device. Windows 365 provides the productivity, security, and collaboration benefits of Microsoft 365.

The Microsoft Graph API enables programmatic access to Cloud PC information and management actions on your organization. The API performs the same operations as those available through Microsoft Endpoint Manager.

Important

Using the Microsoft Graph API for Cloud PCs requires an active [Windows 365 license](https://www.microsoft.com/windows-365) for the organization. Currently, the Microsoft Graph API is available for both Windows 365 Enterprise and Windows 365 Business.

## Using the Microsoft Graph API for Cloud PCs

With Microsoft Graph, you can provision and manage Cloud PCs in your organization. If used in conjunction with the Intune API, you can manage Cloud PCs alongside physical endpoints as well.

## Using Microsoft Graph permissions

Microsoft Graph controls access to resources via permissions. As a developer, you must specify the permissions you need to access Windows 365 resources. Typically, you specify the permissions in the Microsoft Entra admin center. For more information, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

## Common use cases

| Use cases | REST resources | See also |
| :--- | :--- | :--- |
| List, get, create, update, delete, or assign provisioning policies. | [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) | [Provisioning overview](https://learn.microsoft.com/en-us/windows-365/enterprise/provisioning) |
| Manage Cloud PCs including end Cloud PC grace period, troubleshoot, reboot, rename, and restore a Cloud PC. | [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-1.0) | [Cloud PCs lifecycle](https://learn.microsoft.com/en-us/windows-365/enterprise/lifecycle) |
| List, get, create, delete, and get source images. | [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) | [Device images overview](https://learn.microsoft.com/en-us/windows-365/enterprise/device-images) |
| List and get gallery images. | [cloudPcGalleryImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcgalleryimage?view=graph-rest-1.0) | [Gallery images overview](https://learn.microsoft.com/en-us/windows-365/enterprise/device-images) |
| List, get, create, update delete, and run health checks for Azure network connections. | [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) | [On-premises network connection overview](https://learn.microsoft.com/en-us/windows-365/enterprise/on-premises-network-connections) |
| List audit events for Cloud PCs, get a specific audit event, and get audit activity types. | [cloudPcAuditEvent](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcauditevent?view=graph-rest-1.0) | [Get Cloud PC audit logs](https://learn.microsoft.com/en-us/windows-365/enterprise/get-cloud-pc-audit-logs-using-powershell) |
| List, get, create, update, delete or assign user settings. | [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) | [User settings overview](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) |

## Next steps

- Check out the [overview for Windows 365 Cloud PC on Microsoft Graph](https://learn.microsoft.com/en-us/graph/cloudpc-concept-overview).
- Try out the Windows 365 Cloud PCs APIs by using the [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
