<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingcurrency?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# bookingCurrency resource type

Namespace: microsoft.graph

Represents a monetary currency supported by a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/bookingcurrency-list?view=graph-rest-1.0) | [bookingCurrency](https://learn.microsoft.com/en-us/graph/api/resources/bookingcurrency?view=graph-rest-1.0) collection | Get a list of **bookingCurrency** objects available to a Microsoft Bookings business. |
| [Get](https://learn.microsoft.com/en-us/graph/api/bookingcurrency-get?view=graph-rest-1.0) | [bookingCurrency](https://learn.microsoft.com/en-us/graph/api/resources/bookingcurrency?view=graph-rest-1.0) | Get the properties of a **bookingCurrency** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A 3-character currency code, based on [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html). For example, the currency code for the US dollar is USD, and for the Australian dollar is AUD. Read-only. |
| symbol | String | The currency symbol. For example, the currency symbol for the US dollar and for the Australian dollar is $. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "symbol": "String"
}
```
