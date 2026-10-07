<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-tenant-people-search?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-09-30 -->

# Microsoft 365 Multitenant Organization People Search

The multitenant Organization \(MTO\) People Search is a collaboration feature that enables search and discovery of people across multiple tenants. A tenant admin can enable cross-tenant synchronization that allows users to be synced to another tenant and be discoverable in its global address list. Once enabled, users are able to search and discover synced user profiles from the other tenant and view their corresponding people cards.

Learn more about [Cross Tenant Synchronization](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview)

![Azure AD Sync.](https://learn.microsoft.com/en-us/microsoft-365/media/mt-people-search/aad-sync.png?view=o365-worldwide)

> *Fig 1: Microsoft Entra cross tenant synchronization illustration*

## Example scenario

Megan's user account has been synced from the *Fabrikam* tenant to the target tenant, *Contoso*. Nestor from Contoso would like to search and view Megan's people card in Teams. After Megan's account has been synced, Nestor can search and discover Megan's people card in any of the Microsoft 365 apps.

![Limited people card.](https://learn.microsoft.com/en-us/microsoft-365/media/mt-people-search/limited-people-card.png?view=o365-worldwide)

> *Fig 2: User can view a limited people card*

## Known limitations

The current experience provides limited information on the people card \(basic contact information, job title and office location\).

## Prerequisites

To test the MTO People Search feature, it's assumed that you already have the following settings:

- Two Microsoft Entra / Microsoft 365 tenants
- Both tenants have the **Microsoft Entra Cross-tenant Synchronization** feature enabled
- Provisioned users from home to target tenants
- Users are provisioned as UserType = member

## Use Cases

Multitenant organization people search is supported across a range of scenarios and Microsoft 365 applications. Some of the scenarios you can test and validate are described below:

1. **Microsoft Outlook \(Outlook on the web and supported desktop and mobile clients\)**

   - Nestor searches for Megan by using the Search box in Outlook on the web and can open Megan’s profile card from the search results.
   - Nestor types in "Megan" in the *To* line of the email and can send an email to Megan after getting the results for [megan@fabrikam.com](mailto:megan@fabrikam.com).
   - Nestor @mentions "Megan" in the body of the email and can get the result for [megan@fabrikam.com](mailto:megan@fabrikam.com).
   - Nestor types in "Megan" in the *cc* line of the email and can get the result for [megan@fabrikam.com](mailto:megan@fabrikam.com).
   - Nestor can hover and/or click on Megan's profile picture/initials to view Megan's limited people card.

2. **Microsoft OneDrive/SharePoint**

   - Nestor \([nestor@contoso.com](mailto:nestor@contoso.com)\) searches for "Megan" in the centralized search bar on SharePoint and can get the result for [megan@fabrikam.com](mailto:megan@fabrikam.com).
   - Nestor can hover and/or click on Megan's profile picture/initials to view Megan's limited people card.
   - Nestor can share and collaborate on Office documents with Megan.

3. **Microsoft 365 search**

   - Nestor searches for "Megan" in Microsoft 365 at M365.cloud.microsoft and can view Megan’s profile information if Megan’s synchronized user account is discoverable in the tenant.

## Key terminology

- *Home tenant*: The tenant you want to search from. The direction of the search is *outbound*.
- *Resource tenant*: The tenant you want to search in. The direction of the search is *inbound*.

  A tenant can be both home and resource tenant simultaneously.
- *Cross-Tenant synchronization* is a feature that enables multitenant organizations to grant users access to applications in other tenants within the organization. It achieves this by synchronizing internal member users from a home tenant into a resource tenant as external B2B users.
