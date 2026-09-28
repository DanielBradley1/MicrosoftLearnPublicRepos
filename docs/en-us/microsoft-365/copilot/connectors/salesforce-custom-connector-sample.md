<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/salesforce-custom-connector-sample -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Build a custom Salesforce CRM connector

The Microsoft 365 Copilot Salesforce CRM custom synced connector sample is a Python reference implementation that shows how to use the [Copilot connectors API](https://learn.microsoft.com/en-us/graph/connecting-external-content-connectors-api-overview) to ingest Salesforce CRM data into Microsoft Graph. Use the sample as a starting point when the [out-of-the-box Salesforce CRM connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/salesforce-crm-overview) doesn't cover your scenario. For example, you might need to index custom objects or standard objects beyond the out-of-the-box connector's default set.

The sample is published as open source at [microsoft/Salesforce-Custom-Copilot-Connector](https://github.com/microsoft/Salesforce-Custom-Copilot-Connector). Fork the repository and customize it for your organization's Salesforce schema. The repository's `README.md` covers prerequisites, architecture, deployment commands, and configuration in detail.

## When to use the sample

Consider the sample when your scenario requires:

- **Custom objects** - Salesforce objects ending in `__c` that the out-of-the-box connector doesn't index.
- **Standard objects beyond the out-of-the-box set** - For example, Campaign, FeedItem, Order, Quote, or OpportunityLineItem. The sample supports these objects in addition to Account, Contact, Lead, Opportunity, and Case.
- **Broader custom-field coverage** - Surfacing more custom fields than the out-of-the-box connector exposes through its **Add Properties** experience.

## Customize the sample for your Salesforce org

Edit the following files:

- **`config/schema.json`** - defines which Salesforce objects and fields are fetched per object type. Add entries for your custom objects \(`__c`\) and custom fields.
- **`config/graph-schema.json`** - defines the Microsoft Graph property schema your items use: property names, types, flags \(`isSearchable`, `isQueryable`, `isRetrievable`, `isRefinable`\), and semantic labels.
- **`config/template.json`** - the Adaptive Card template used to render the sample's items as Microsoft Search results.
- **`env/.env.local`** - connector ID, connection name, connection description, Salesforce instance URL, and tuning parameters. Put secrets in `env/.env.local.user`.

For step-by-step configuration and deployment instructions, see the repository's `README.md`.

## Related content

- [Salesforce CRM connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/salesforce-crm-overview)
- [Copilot connectors API overview](https://learn.microsoft.com/en-us/graph/connecting-external-content-connectors-api-overview)
- [Enhance Copilot discovery of connector content](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/enhance-copilot-discovery)
