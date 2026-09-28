<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/compliantnetworknamedlocation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-06 -->

# compliantNetworkNamedLocation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Entra ID named location defined by Global Secure Access. Automatically created with the name "All Compliant Network Locations" when you enable Global Secure Access signaling for Conditional Access. Named locations are custom rules that define network locations that can then be used in a Conditional Access policy.

For more information, see [Enable compliant network check with Conditional Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-compliant-network).

Inherits from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-list-namedlocations?view=graph-rest-beta) | [compliantNetworkNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/compliantnetworknamedlocation?view=graph-rest-beta) collection | Get all the **compliantNetworkNamedLocation** objects in the organization. |
| [Get](https://learn.microsoft.com/en-us/graph/api/compliantnetworknamedlocation-get?view=graph-rest-beta) | [compliantNetworkNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/compliantnetworknamedlocation?view=graph-rest-beta) | Read the properties and relationships of a **compliantNetworkNamedLocation** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/compliantnetworknamedlocation-update?view=graph-rest-beta) | [compliantNetworkNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/compliantnetworknamedlocation?view=graph-rest-beta) | Update a **compliantNetworkNamedLocation** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compliantNetworkType | compliantNetworkType | Type of compliant network. Currently the only possible value is `allTenantCompliantNetworks`. |
| createdDateTime | DateTimeOffset | The timestamp type represents creation date and time of the location using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-beta). |
| displayName | String | Human-readable name of the location. Required. Always "All Compliant Network Locations". Inherited from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-beta). |
| id | String | Identifier of the object. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isTrusted | Boolean | `true` if this location is explicitly trusted. Optional. Default value is `false`. |
| modifiedDateTime | DateTimeOffset | The timestamp type represents last modified date and time of the location using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "compliantNetworkType": "String",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "isTrusted": "Boolean",
  "modifiedDateTime": "String (timestamp)"
}
```
