<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-14 -->

# namedLocation resource type

Namespace: microsoft.graph

This is the base class that represents a Microsoft Entra ID named location. Named locations are custom rules that define network locations which can then be used in a Conditional Access policy.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-list-namedlocations?view=graph-rest-1.0) | [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0) collection | Get all the **namedLocation** objects in the organization. |
| [Get](https://learn.microsoft.com/en-us/graph/api/namedlocation-get?view=graph-rest-1.0) | [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0) | Read the properties and relationships of a **namedLocation** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/namedlocation-delete?view=graph-rest-1.0) | None | Delete a **namedLocation** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The Timestamp type represents creation date and time of the location using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| displayName | String | Human-readable name of the location. |
| id | String | Identifier of a namedLocation object. Read-only. |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents last modified date and time of the location using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "modifiedDateTime": "String (timestamp)"
}
```

## Related content

- [What is Conditional Access?](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview)
- [Using the location condition in a Conditional Access policy](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/location-condition)
