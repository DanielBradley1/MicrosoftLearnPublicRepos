<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externaliteminformationprotectionlabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# externalItemInformationProtectionLabel resource type

Namespace: microsoft.graph.externalConnectors

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Purview sensitivity label for an item indexed by a Microsoft Search [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sensitivityLabelId | String | The GUID of the Purview sensitivity label. To get the label GUID, use the [Get sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/sensitivitylabel-get?view=graph-rest-beta) API or the [Get-Label](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-label?view=exchange-ps) PowerShell command. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "sensitivityLabelId": "String"
}
```
