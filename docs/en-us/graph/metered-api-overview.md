<!-- Source: https://learn.microsoft.com/en-us/graph/metered-api-overview -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Overview of metered APIs and services in Microsoft Graph

Microsoft Graph includes APIs that are available at no additional cost with [user subscription licenses](https://learn.microsoft.com/en-us/microsoft-365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings) and APIs and services that are metered. Metered APIs and services in Microsoft Graph incur costs based on usage. The costs might be incurred per API call made, per object returned in an API call, or through other measures.

Whether metered or not, APIs in Microsoft Graph follow these two principles:

- Customer data ownership: Customer data belongs to the customer. Learn more about how [Microsoft categorizes customer data](https://www.microsoft.com/trust-center/privacy/customer-data-definitions).
- Reasonable access: The service provides access to customer content, within [defined limits](https://learn.microsoft.com/en-us/graph/throttling-limits).

Metering some APIs helps to ensure the health of the current and future Microsoft Graph ecosystem by balancing platform access and cost. In the event that a Microsoft Graph API that is included with user subscription licenses becomes metered, that would be a non-backward compatible change and the [versioning, support, and breaking change policies for Microsoft Graph](https://learn.microsoft.com/en-us/graph/versioning-and-support) would apply.

For the list of metered APIs and services, see [Metered APIs and services](https://learn.microsoft.com/en-us/graph/metered-api-list).

## API categories and metering

Microsoft Graph APIs fall into three categories, and metering might apply based on the category of the API.

### Standard APIs

Most Microsoft Graph APIs are standard APIs. These APIs perform standard operations \(create, read, update, delete\) on customer content and administrative endpoints. Reasonable access limits for these APIs are defined based on documented [usage thresholds](https://learn.microsoft.com/en-us/graph/throttling-limits). This helps to ensure a positive customer experience and encourages efficient API usage patterns. Access to standard APIs within the defined usage thresholds is available as part of the user license without additional costs.

### High-capacity APIs

High-capacity APIs ensure that customers and developers have access to data at scale. This category includes purpose-built, bulk export or import endpoints and Microsoft Graph services. These APIs might be metered and incur additional costs beyond user subscription licenses.

### Advanced APIs

Advanced APIs provide access to enriched or aggregated data, or advanced functionality that extends from Microsoft 365. The [assignSensitivityLabel](https://learn.microsoft.com/en-us/graph/api/driveitem-assignsensitivitylabel) API is an example of an advanced API. These APIs might be metered and incur additional costs beyond user subscription licenses.

## Accessing metered APIs

To access metered APIs and services in Microsoft Graph, an application must be associated with an active Microsoft Azure subscription. For details about how to associate an app to a subscription, see [Enable metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-setup).

## Considerations for using metered APIs

Keep the following considerations in mind when you use metered APIs and services in Microsoft Graph:

- Metered APIs can return errors related to your subscription status in addition to other common errors. For details about Microsoft Graph errors, see [Microsoft Graph errors and resource types](https://learn.microsoft.com/en-us/graph/errors).
- Metered APIs are billed according to API usage. Be sure to understand the metering unit so that you can estimate the costs associated with a particular API.

## Known limitations

The following limitations apply to metered APIs:

- Metered APIs and services in Microsoft Graph are currently available only in the Microsoft global environment and not in national cloud deployments, including Microsoft 365 GCC deployments accessed through the worldwide Microsoft Graph endpoint. For details about national clouds, see [National cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).
- The target application must be a confidential client application \(for example, web application, web API, or daemon/service\). Public client applications \(desktop and mobile applications\) aren't supported.
- Azure managed identities aren't supported to call metered APIs. For more information, see [Azure services that support managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identities-status).

## Related content

- [Metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-list)
- [Enable metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-setup)
- [Metered APIs frequently asked questions](https://learn.microsoft.com/en-us/graph/metered-api-faq)
