<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/exchange-hybrid -->
<!-- Sitemap-Last-Modified: 2026-08-27 -->

# Exchange hybrid writeback with cloud sync

An Exchange hybrid deployment offers organizations the ability to extend the feature-rich experience and administrative control they have with their existing on-premises Microsoft Exchange organization to the cloud. A hybrid deployment provides the seamless look and feel of a single Exchange organization between an on-premises Exchange organization and Exchange Online.

[![Conceptual image of exchange hybrid scenario.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/exchange-hybrid/exchange-hybrid.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/exchange-hybrid/exchange-hybrid.png#lightbox)

This scenario is now supported in cloud sync. Cloud sync detects the Exchange on-premises schema attributes and then "writes back" the exchange on-line attributes to your on-premises AD environment.

For more information on Exchange Hybrid deployments, see [Exchange Hybrid](https://learn.microsoft.com/en-us/exchange/exchange-hybrid).

## Prerequisites

Before deploying Exchange Hybrid with cloud sync, you must meet the following prerequisites.

- The [provisioning agent](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-provisioning-agent) must be version 1.1.1107.0 or later.
- Your on-premises Active Directory must be extended to contain the Exchange schema.

  - To extend your schema for Exchange see [Prepare Active Directory and domains for Exchange Server](https://learn.microsoft.com/en-us/exchange/plan-and-deploy/prepare-ad-and-domains?view=exchserver-2019&preserve-view=true)


  Note


  If your schema has been extended after you have installed the provisioning agent, you will need to restart it in order to pick up the schema changes.

## How to enable

Exchange Hybrid Writeback is disabled by default.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator).
2. Browse to **Entra ID** > **Entra Connect** > **Cloud sync**.

   [![Screenshot that shows the Microsoft Entra Connect Cloud Sync home page.](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png)](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png#lightbox)

3. Select on an existing configuration.
4. At the top, select **Properties**. You should see Exchange hybrid writeback disabled.
5. Select the pencil next to **Basic**.  [![Screenshot of the basic properties.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/exchange-hybrid/exchange-hybrid-1.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/exchange-hybrid/exchange-hybrid-1.png#lightbox)
6. On the right, place a check in **Exchange hybrid writeback** and select **Apply**.  [![Screenshot of enabling Exchange writeback.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/exchange-hybrid/exchange-hybrid-2.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/exchange-hybrid/exchange-hybrid-2.png#lightbox)

Note

If the checkbox for **Exchange hybrid writeback** is disabled, it means that the schema has not been detected. Verify that the prerequisites are met and that you have re-started the provisioning agent.

## Attributes synchronized

Cloud sync writes Exchange Online attributes back to users in order to enable Exchange hybrid scenarios.

### Entra2ADExchangeOnlineAttributeWriteback \(LES Writeback\)

For the Exchange Online-authoritative attribute writeback \(LES Writeback\) scenario, see [Cloud-based management of Exchange attributes for Remote Mailboxes in hybrid environments](https://learn.microsoft.com/en-us/exchange/hybrid-deployment/enable-exchange-attributes-cloud-management).

In this scenario, Exchange Online is the source of truth for specific Exchange-related user attributes, and cloud sync writes those cloud-managed attributes back to your on-premises Active Directory.

This differs from **Exchange hybrid writeback** \(AAD2ADExchangeHybridWriteback\), which follows the hybrid writeback template used in preview scenarios.

The following table lists the supported attributes and the mappings for LES Writeback.

| Microsoft Entra attribute | AD attribute | Object Class | Mapping Type |
| --- | --- | --- | --- |
| cloudAnchor | msDS-ExternalDirectoryObjectId | User, InetOrgPerson | Direct |
| cloudLegacyExchangeDN | proxyAddresses | User, Contact, InetOrgPerson | Expression |
| cloudMSExchArchiveStatus | msExchArchiveStatus | User, InetOrgPerson | Direct |
| cloudMSExchBlockedSendersHash | msExchBlockedSendersHash | User, InetOrgPerson | Expression |
| cloudMSExchSafeRecipientsHash | msExchSafeRecipientsHash | User, InetOrgPerson | Expression |
| cloudMSExchSafeSendersHash | msExchSafeSendersHash | User, InetOrgPerson | Expression |
| cloudMSExchUCVoiceMailSettings | msExchUCVoiceMailSettings | User, InetOrgPerson | Expression |
| cloudMSExchUserHoldPolicies | msExchUserHoldPolicies | User, InetOrgPerson | Expression |

## Provisioning on-demand

Provisioning on-demand with Exchange hybrid writeback requires two steps. You need to first provision or create the user. Exchange online then populates the necessary attributes on the user. Then cloud sync can then "write back" these attributes to the user. The steps are:

- Provision and sync the initial user - this brings the user into the cloud and allows them to be populated with Exchange online attributes.
- Write back exchange attributes to Active Directory - this writes the Exchange online attributes to the user on-premises.

Provisioning on-demand with Exchange hybrid use the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator).
2. Browse to **Entra ID** > **Entra Connect** > **Cloud sync**.

   [![Screenshot that shows the Microsoft Entra Connect Cloud Sync home page.](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png)](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png#lightbox)

3. Under **Configuration**, select your configuration.
4. On the left, select **Provision on demand**.
5. Enter the distinguished name of a user and select the **Provision** button.
6. A success screen appears with four green check marks.
7. Select **Next**. On the **Writeback exchange attributes to Active Directory** tab, the synchronization starts.
8. You should see the success details.  [![Screenshot of Exchange attributes being written back.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/exchange-hybrid/exchange-hybrid-4.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/exchange-hybrid/exchange-hybrid-4.png#lightbox)

   Note

   This final step may take up to 2 minutes to complete.

## Exchange hybrid writeback using MS Graph

You can use MS Graph API to enable Exchange hybrid writeback. For more information, see [Exchange hybrid writeback with MS Graph](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-inbound-synch-ms-graph#exchange-hybrid-writeback-public-preview).

## Next steps

- [What is provisioning?](https://learn.microsoft.com/en-us/entra/identity/hybrid/what-is-provisioning)
- [What is Microsoft Entra Cloud Sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
