<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/self-service-portal -->
<!-- Sitemap-Last-Modified: 2025-06-06 -->

# Self-service for Microsoft Entra B2B collaboration sign-up

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Customers can do a lot with the built-in features that are exposed through the [Azure portal](https://portal.azure.com) and the [Application Access Panel](https://myapps.microsoft.com) for end users. However, you might need to customize the onboarding workflow for B2B users to fit your organization’s needs.

## Microsoft Entra entitlement management for B2B guest user sign-up

As an inviting organization, you might not know ahead of time who the individual external collaborators are who need access to your resources. You need a way for users from partner companies to sign themselves up with policies that you control. You can use [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-overview) to configure policies, which [manage access for external users](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-external-users#how-access-works-for-external-users). Then users from other organizations can request access, and upon approval be provisioned with guest accounts and assigned to groups, apps, and SharePoint Online sites.

## Microsoft Entra B2B invitation API

Organizations can use the [Microsoft Graph invitation manager API](https://learn.microsoft.com/en-us/graph/api/resources/invitation) to build their own onboarding experiences for B2B guest users. When you want to offer self-service B2B guest user sign-up, we recommend that you use [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-overview). But if you want to build your own experience, you can use the [invitation API](https://learn.microsoft.com/en-us/graph/api/invitation-post?tabs=http) to automatically send your customized invitation email directly to the B2B user, for example. Or your app can use the inviteRedeemUrl returned in the creation response to craft your own invitation \(through your communication mechanism of choice\) to the invited user.

## Next steps

- [Self-service sign-up user flows](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-overview)
- [What is Microsoft Entra B2B collaboration?](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)
- [External ID pricing](https://learn.microsoft.com/en-us/entra/external-id/external-identities-pricing)
