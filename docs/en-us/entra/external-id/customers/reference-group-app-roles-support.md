<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/reference-group-app-roles-support -->
<!-- Sitemap-Last-Modified: 2025-03-11 -->

# Groups and application roles support

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

An external tenant follows the Microsoft Entra user and group management model and application assignment. Many of the core Microsoft Entra features are being phased into external tenants. The following table shows which features are currently available.

| **Feature** | **Currently available?** |
| --- | --- |
| Create an application role for a resource | Yes, by modifying the application manifest |
| Assign an application role to users | Yes |
| Assign an application role to groups | Yes, via Microsoft Graph only |
| Assign an application role to applications | Yes, via application permissions |
| Assign a user to an application role | Yes |
| Assign an application to an application role \(application permission\) | Yes |
| Add a group to an application/service principal \(groups claim\) | Yes, via Microsoft Graph only |
| Create/update/delete a customer \(local user\) via the Microsoft Entra admin center | Yes |
| Reset a password for a customer \(local user\) via the Microsoft Entra admin center | Yes |
| Create/update/delete a customer \(local user\) via Microsoft Graph | Yes |
| Reset a password for a customer \(local user\) via Microsoft Graph | Yes, only if the service principal is added to the Global Administrator role |
| Create/update/delete a security group via the Microsoft Entra admin center | Yes |
| Create/update/delete a security group via the Microsoft Graph API | Yes |
| Change security group members using the Microsoft Entra admin center | Yes |
| Change security group members using the Microsoft Graph API | Yes |
