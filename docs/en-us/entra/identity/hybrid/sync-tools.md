<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/sync-tools -->
<!-- Sitemap-Last-Modified: 2025-04-09 -->

# Tools used for synchronization

The following article briefly describes the Microsoft tools that current exist today for synchronization.

## List of tools

- **Cloud sync and the provisioning agent** - Microsoft Entra Cloud Sync is the newest offering from Microsoft designed to meet and accomplish your hybrid identity goals for synchronization of users, groups, and contacts to Microsoft Entra ID. It uses the light-weight provisioning agent and is fully configurable via the portal. For more information, see [What is cloud sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync) and [What is the provisioning agent?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-provisioning-agent)
- **Connect sync** - Microsoft Entra Connect is an on-premises Microsoft application designed to meet and accomplish your hybrid identity goals. For more information, see [What is Microsoft Entra Connect?](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect-v2).
- **Microsoft Identity Manager with the Graph connector** - Microsoft's on-premises identity and access management solution that provides advanced inter-directory provisioning to achieve hybrid identity environments for Active Directory, Microsoft Entra ID, and other directories. For more information, see [Microsoft Identity Manager](https://learn.microsoft.com/en-us/microsoft-identity-manager/microsoft-identity-manager-2016). MIM is slowly being deprecated and should only be used in advanced scenarios. For more information, see [Deprecated Features and planning for the future](https://learn.microsoft.com/en-us/microsoft-identity-manager/microsoft-identity-manager-2016-deprecated-features)
- **ECMA Host connector** - The ECMA host works with the provisioning agent to provision and synchronize users from the cloud into on-premises applications such as SQL and LDAP. For more information, see [Microsoft Entra on-premises application identity provisioning architecture](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/on-premises-application-provisioning-architecture) and [What is the provisioning agent?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-provisioning-agent)

## Selecting the right tool

Each of these tools can accomplish similar results. So selecting the right tool is essential. For most scenarios, cloud sync is going to be the recommended tool. Then connect sync and for advanced/complex scenarios, MIM. For on-premises applications, the ECMA Host would be the preferred tool. For more information, [see the supported sync scenarios table](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios#supported-sync-scenarios). To determine which tool is right for you, you should use the wizard at the [Choosing the right sync tool](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios) site.

## Next steps

- [Common scenarios](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios)
- [Choosing the right sync tool](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios)
- [Steps to start](https://learn.microsoft.com/en-us/entra/identity/hybrid/get-started)
- [Prerequisites](https://learn.microsoft.com/en-us/entra/identity/hybrid/prerequisites)
