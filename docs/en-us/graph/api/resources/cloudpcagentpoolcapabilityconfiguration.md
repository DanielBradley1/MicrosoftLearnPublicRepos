<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolcapabilityconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcAgentPoolCapabilityConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the capabilities configuration for a Cloud PC agent pool.

Inherits from [cloudPcPoolCapabilityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolcapabilityconfiguration?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enableSingleSignOn | Boolean | When `true`, provisioned Cloud PCs support single sign-on, allowing users to authenticate with password-less options \(such as FIDO2 keys\) via Microsoft Entra ID. Default value is `false`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentPoolCapabilityConfiguration",
  "enableSingleSignOn": "Boolean"
}
```
