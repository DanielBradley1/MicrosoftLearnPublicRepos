<!-- Source: https://learn.microsoft.com/en-us/graph/metered-api-faq -->
<!-- Sitemap-Last-Modified: 2026-04-03 -->

# Metered APIs and services in Microsoft Graph FAQ

This article provides answers to frequently asked questions about metered APIs and services in Microsoft Graph.

## Billing setup FAQs

### What permissions are required to set up billing?

Setting up billing requires permissions both for the application registration and the Azure subscription you wish to use. Required permissions for the application registration are Application Owner or Application Administrator. Required permissions for the Azure subscription are Subscription Contributor, Owner / Resource Group Contributor, or Owner.

### Can I use a service principal to set up billing on my app registration?

Yes, it requires an application administrator or similar role for the app registration assigned to the service principal. The role can be scoped to only the target application set up for billing to prevent overly broad permissions from being granted.

### Can I use a managed identity to set up billing on my app registration?

Yes, you can create a managed identity for Azure resources. Assign role-based access control to your subscription or resource group, and add the Microsoft Entra application administrator role to the service principal associated with the managed identity. For more information, see [Tutorial: Use a Windows VM/VMSS to access Azure resources](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/tutorial-windows-vm-ua-arm) for an example.

### How can I verify that my application is properly set up for billing?

For information about how to verify billing setup, see [Enable metered APIs and services](https://learn.microsoft.com/en-us/graph/metered-api-setup?tabs=azurecloudshell#verify-setup).

## Microsoft Teams export API billing FAQs

Important

Starting August 25, 2025, the Microsoft Teams export APIs are no longer metered, and no billing configuration is required to use these APIs. If your application is configured for billing, no action is required. This FAQ section about the billing policy is provided for reference as the final billing cycle for metered Microsoft Teams APIs concludes.

## Application consumer FAQ

### Why is my application provider asking me to set up billing?

The owner of the application registration handles billing for metered APIs and services in Microsoft Graph. If you acquired an application that requires you to be the owner of the application registration, you're responsible for any metered APIs and services used by the application.

### Do I need licenses for every user in my tenant?

A license is required for each user subject to security and compliance policies. Other scenarios might not require a license.

## Cost management and billing FAQ

### Where can I get the billing information for metered APIs and services?

Billing data is submitted to the Azure subscription used to create the Microsoft Graph billing resource under the service name **Microsoft Graph services**, and it is typically available 24 hours after the transactions occur.

For more information, see [Azure cost management and billing overview](https://learn.microsoft.com/en-us/azure/cost-management-billing/cost-management-billing-overview).

The following table lists the most frequently used tools to review and monitor billing charges.

| Type | Description |
| :--- | :--- |
| [Cost analysis](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/quick-acm-cost-analysis) | Interactive chart that displays consumption. Hint: Use accumulated costs and filter by service name **Microsoft Graph services**. |
| [Exports](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-export-acm-data) | Creates detailed reports with desired frequency \(for example, daily or monthly\). |
| [Alerts](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/cost-mgt-alerts-monitor-usage-spending) | Configures alerts by combining filters. |

### Is the bill broken down for each API?

The following table shows how the billing details can be aggregated or broken.

| Type | Exports property | Cost analysis, budgets, and alerts filter |
| :--- | :--- | :--- |
| Meter information | MeterName, MeterId, MeterCategory, MeterSubcategory, ProductName, ConsumedService | Meter, Meter category, Meter subcategory, Service name |
| Resource information | InstanceId, ResourceType, ResourceGroup, SubscriptionGuid | Resource, Resource guid, Resource type, Resource group, Service name |
| Tags | TenantId | TenantId |
| AdditionalInfo | AppId, TenantId |  |

Some endpoints might share a meter, and billing data can't be broken down by endpoint. Alternatively, a client app can set up client-side API logging or use [Microsoft Graph activity logs](https://learn.microsoft.com/en-us/graph/microsoft-graph-activity-logs-overview).

## Known limitations

The following limitations apply to metered APIs:

- Metered APIs and services in Microsoft Graph are currently available only in the Microsoft global environment and not in national cloud deployments, including Microsoft 365 GCC deployments accessed through the worldwide Microsoft Graph endpoint. For details about national clouds, see [National cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).
- The target application must be a confidential client application \(for example, web application, web API, or daemon/service\). Public client applications \(desktop and mobile applications\) aren't supported.
- Azure managed identities aren't supported to call metered APIs. For more information, see [Azure services that support managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identities-status).

## Related content

- [Overview of metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-overview)
- [Metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-list)
- [Enable metered APIs and services in Microsoft Graph](https://learn.microsoft.com/en-us/graph/metered-api-setup)
