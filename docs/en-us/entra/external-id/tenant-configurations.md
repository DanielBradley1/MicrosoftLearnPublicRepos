<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations -->
<!-- Sitemap-Last-Modified: 2026-03-16 -->

# Workforce and external tenant configurations in Microsoft Entra External ID

A *tenant* is a dedicated and trusted instance of Microsoft Entra ID. It contains an organization's resources, including registered apps and a directory of users. There are two ways to configure a tenant, depending on how your organization intends to use the tenant and the resources that you want to manage:

- A *workforce* tenant configuration is for your employees, internal business apps, and other organizational resources. You can invite external business partners and guests to your workforce tenant.
- An *external* tenant configuration is exclusively for Microsoft Entra External ID scenarios where you want to publish apps to consumers or business customers. [Learn more about External ID in external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/overview-customers-ciam).

Each tenant configuration represents a different scenario for working with users outside your organization.

[![Diagram that shows External ID tenant configurations.](https://learn.microsoft.com/en-us/entra/external-id/media/tenant-configurations/tenant-configurations.png)](https://learn.microsoft.com/en-us/entra/external-id/media/tenant-configurations/tenant-configurations.png#lightbox)

## Workforce tenants

A workforce tenant represents a single organization. You use it to manage your employees, business apps, and other internal resources. If you've worked with Microsoft Entra ID, you're already familiar with a workforce tenant. It's the standard tenant that's automatically created when your organization signs up for a Microsoft cloud service subscription, such as Microsoft Azure, Microsoft Intune, or Microsoft 365.

In a workforce tenant, the External ID feature [B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b) lets your employees collaborate with external business partners and guests.

You can create additional workforce tenants in either the Microsoft Entra admin center or the Azure portal.

## External tenants

When you want to use External ID to add customer identity and access management \(CIAM\) to your apps, you create a new tenant in an *external* configuration. This tenant is distinct and separate from your workforce tenant. It follows the standard Microsoft Entra tenant model, but it's configured for your consumer and business customer scenarios.

The external tenant is where you register your apps, create sign-up and sign-in user flows, and manage the users of your apps. The consumers and business customers who sign up for your apps are added to the tenant directory, but with [limited default permissions](https://learn.microsoft.com/en-us/entra/external-id/customers/reference-user-permissions).

### When do I need to create an external tenant?

If you plan to use External ID for apps for consumers or business customers, the first resource that you need to create is a new tenant with an external configuration.

You can create an external tenant in a couple of ways:

- If you already have an Azure subscription, you can [create a new tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-customer-tenant-portal) in the Microsoft Entra admin center. When you create a tenant, choose the external configuration. You can't create external tenants via the Azure portal, which supports creation of workforce tenants only.
- If you don't already have a Microsoft Entra tenant and you want to try out External ID features in an external tenant, we recommend using the get-started experience to start a free trial.

When you create a tenant, you can set your correct geographic location and domain name. If you currently use Azure Active Directory B2C \(Azure AD B2C\), the new workforce and customer tenant model doesn't affect your existing Azure AD B2C tenants.

Important

Effective May 1, 2025, Azure AD B2C will no longer be available to purchase for new customers. To learn more, please see [Is Azure AD B2C still available to purchase?](https://learn.microsoft.com/en-us/azure/active-directory-b2c/faq?tabs=app-reg-ga#azure-ad-b2c-end-of-sale) in our FAQ.

## Comparison of workforce and external tenants

Although workforce tenants and external tenants are built on the same underlying Microsoft Entra platform, there are some feature differences. For a detailed comparison of tenant features and capabilities, see [Supported features in workforce and external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers).
