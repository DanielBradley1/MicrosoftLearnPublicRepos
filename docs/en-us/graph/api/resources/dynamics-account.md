<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-account?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-13 -->

# account resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an account object in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get account](https://learn.microsoft.com/en-us/graph/api/dynamics-account-get?view=graph-rest-beta) | account | Get accounts object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blocked | Boolean | Specifies that entries can't be posted to the G/L account. `True` indicates that the account is blocked and posting isn't allowed. |
| category | String | Specifies the category of the G/L account. Maximum size is 20. |
| displayName | String | Specifies the name of the G/L account. Maximum size is 50. |
| id | GUID | The unique identifier for the account. |
| lastModifiedDateTime | Datetime | The date and time when the account was last modified. |
| number | String | Specifies the number of the G/L account. Maximum size is 20. |
| subCategory | String | Specifies the subcategory of the account category of the G/L account. Maximum size is 80. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "blocked": "Boolean",
  "category": "String",
  "displayName": "String",
  "id": "GUID",
  "lastModifiedDateTime": "Datetime"
  "number": "String",
  "subCategory": "String"
}
```
