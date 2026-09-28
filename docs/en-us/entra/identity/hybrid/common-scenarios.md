<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios -->
<!-- Sitemap-Last-Modified: 2025-04-09 -->

# Hybrid scenarios

The following document describes the common and supported hybrid sync scenarios.

## Supported sync scenarios

The following table outlines the most common and supported sync scenarios.

| Scenario | Supported with cloud sync | Supported with connect sync | Supported with MIM and the Graph Connector | Supported with ECMA Host connector |
| --- | --- | --- | --- | --- |
| New Hybrid customers managing identities | ● | ● | ● | N/A |
| Mergers and acquisitions \(disconnected forest\) | ● | N/A | ● | N/A |
| High availability - latency \(I need high availability\) | ● | N/A | ● | N/A |
| Migration from connect sync to cloud sync | ● | ● | N/A | N/A |
| Microsoft Entra hybrid join | N/A | ● | N/A | N/A |
| Exchange hybrid | ● | ● | N/A | N/A |
| User accounts in one forest / mailboxes in resource forest | N/A | ● | N/A | N/A |
| Sync large domains with more than 250K objects | N/A | ● | ● | N/A |
| Filter directory objects based on attribute values | N/A | ● | ● | N/A |
| Windows Hello for Business | N/A | ● | N/A | N/A |
| Synchronize from cloud to on-premises AD | N/A | N/A | ● | N/A |
| Synchronize from cloud to on-premises LDAP | N/A | N/A | ● | ● |
| Synchronize from cloud to on-premises SQL | N/A | N/A | ● | ● |

## Supported provisioning scenarios

The following table outlines the common and supported provisioning scenarios.

| Scenario | Supported with cloud sync | Supported with connect sync | Supported with MIM and the Graph Connector | Supported with ECMA Host connector |
| --- | --- | --- | --- | --- |
| Group provisioning to Active Directory | ● | N/A | ● | N/A |

For more information, see [Supported topologies for cloud sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/plan-cloud-sync-topologies) and [Supported topologies for connect sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/plan-connect-topologies).

## Additional information

- You can sync users & groups from the same domain using Connect Sync and cloud sync if:

  - Scoping filters in each sync is mutually exclusive
  - If inclusive, don’t have the same attributes values clashing \(Precedence isn’t supported\)

- You can sync users & groups using Connect Sync while using cloud sync’s net new capabilities \(\*called out in Roadmap\)
- You can sync objects from a single AD to multiple Azure ADs if writeback capabilities are enabled only in a single Microsoft Entra tenant.

## Cloud sync and connect sync in parallel

You can run cloud sync and Microsoft Entra Connect in the same forest. You may decide to do allow cloud sync to handle 80% and use Microsoft Entra Connect for some of your more obscure, 20% scenarios. The tutorial, [Migrate to Microsoft Entra Cloud Sync for an existing synced AD forest](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/tutorial-pilot-aadc-aadccp) shows an example of how you would run each.

## Common authentication methods and scenarios

Hybrid identity scenarios use one of three authentication methods. The three methods are:

- **[Password hash synchronization \(PHS\)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-phs)**
- **[Pass-through authentication \(PTA\)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta)**
- **[Federation \(AD FS\)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-fed)**

These authentication methods also provide [single-sign on](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-sso) capabilities. Single-sign on automatically signs your users in when they are on their corporate devices, connected to your corporate network.

For additional information, see [Choose the right authentication method for your Microsoft Entra hybrid identity solution](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/choose-ad-authn).

| I need to: | PHS and SSO | PTA and SSO | Federation |
| --- | --- | --- | --- |
| Sync new user, contact, and group accounts created in my on-premises Active Directory to the cloud automatically. | ● | ● | ● |
| Set up my tenant for Microsoft 365 hybrid scenarios. | ● | ● | ● |
| Enable my users to sign in and access cloud services using their on-premises password. | ● | ● | ● |
| Implement single sign-on using corporate credentials. | ● | ● | ● |
| Ensure no password hashes are stored in the cloud. |  | ● | ● |
| Enable cloud-based multifactor authentication solutions. | ● | ● | ● |
| Enable on-premises multifactor authentication solutions. |  |  | ● |
| Support smartcard authentication for my users. |  |  | ● |

## Next steps

- [Tools for synchronization](https://learn.microsoft.com/en-us/entra/identity/hybrid/sync-tools)
- [Choosing the right sync tool](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios)
- [Steps to start](https://learn.microsoft.com/en-us/entra/identity/hybrid/get-started)
- [Prerequisites](https://learn.microsoft.com/en-us/entra/identity/hybrid/prerequisites)
