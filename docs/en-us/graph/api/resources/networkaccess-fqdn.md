<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-fqdn?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# fqdn resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A fully qualified domain name \(FQDN\) refers to the complete address of an internet host or computer. It includes the hostname and the domain name, providing a specific and unique identification for the device on the internet.

Inherits from [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | Defines the FQDN used in a destination for a rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.fqdn",
  "value": "String"
}
```
