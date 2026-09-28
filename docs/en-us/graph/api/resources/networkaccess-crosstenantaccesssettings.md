<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccesssettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# crossTenantAccessSettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The cross tenant access settings of a tenant determine the Universal tenant restrictions version 2. These restrictions provide comprehensive coverage by tagging all traffic, irrespective of the device's browser or operating system, facilitate branch and direct from device connectivity, and integrate natively with Microsoft 365 and Microsoft Entra ID.

For more information about cross-tenant access settings, see [Universal tenant restrictions](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-universal-tenant-restrictions).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-crosstenantaccesssettings-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.crossTenantAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccesssettings?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.crossTenantAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccesssettings?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-crosstenantaccesssettings-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.crossTenantAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccesssettings?view=graph-rest-beta) | Update the properties of a [microsoft.graph.networkaccess.crossTenantAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccesssettings?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| networkPacketTaggingStatus | microsoft.graph.networkaccess.status | Determines if a header with the user tenant ID is inserted into the network traffic. .The possible values are: `enabled`, `disabled`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.crossTenantAccessSettings",
  "id": "String (identifier)",
  "networkPacketTaggingStatus": "String"
}
```
