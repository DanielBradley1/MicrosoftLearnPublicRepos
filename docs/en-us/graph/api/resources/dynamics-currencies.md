<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-currencies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# currency resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a currency used in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get currencies](https://learn.microsoft.com/en-us/graph/api/dynamics-currencies-get?view=graph-rest-beta) | [currency](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-currencies?view=graph-rest-beta) | Get a currency. |
| [Create currencies](https://learn.microsoft.com/en-us/graph/api/dynamics-create-currencies?view=graph-rest-beta) | [currency](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-currencies?view=graph-rest-beta) | Create a currency. |
| [Update currencies](https://learn.microsoft.com/en-us/graph/api/dynamics-currencies-update?view=graph-rest-beta) | [currency](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-currencies?view=graph-rest-beta) | Update a currency. |
| [Delete currencies](https://learn.microsoft.com/en-us/graph/api/dynamics-currencies-delete?view=graph-rest-beta) | None | Delete a currency. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| amountDecimalPlaces | String | The number of decimal places the system displays on amounts for this currency. |
| amountRoundingPrecision | Decimal | The size of the interval to be used when rounding amounts for this currency. |
| code | String | The currency code. |
| displayName | String | The display name for the currency. |
| id | String | The unique identifier of the currency. Noneditable. |
| lastModifiedDateTime | Datetime | The date and time the currency was last modified. Read-Only. |
| symbol | String | The symbol for this currency that appears on checks. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource.

```json
{
  "amountDecimalPlaces": "String",
  "amountRoundingPrecision": "Decimal",
  "code": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "Datetime",
  "symbol": "String"
}
```
