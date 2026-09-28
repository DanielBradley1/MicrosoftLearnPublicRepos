<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-paymentmethods?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# paymentMethod resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a method of payment in Dynamics 365 Business Central such as PayPal, credit card, and bank account.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get payment methods](https://learn.microsoft.com/en-us/graph/api/dynamics-paymentmethods-get?view=graph-rest-beta) | [paymentMethod](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-paymentmethods?view=graph-rest-beta) | Get a payment method object. |
| [Create payment methods](https://learn.microsoft.com/en-us/graph/api/dynamics-create-paymentmethods?view=graph-rest-beta) | [paymentMethod](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-paymentmethods?view=graph-rest-beta) | Create a payment method object. |
| [Update payment methods](https://learn.microsoft.com/en-us/graph/api/dynamics-paymentmethods-update?view=graph-rest-beta) | [paymentMethod](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-paymentmethods?view=graph-rest-beta) | Update a payment method object. |
| [Delete payment methods](https://learn.microsoft.com/en-us/graph/api/dynamics-paymentmethods-delete?view=graph-rest-beta) | None | Delete a payment method object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The payment method code. |
| displayName | String | The payment method display name. |
| id | GUID | The unique identifier of the **paymentMethod**. Noneditable. |
| lastModifiedDateTime | Datetime | The date and time when the payment method was last modified. Read-Only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "displayName": "String",
  "id": "GUID",
  "lastModifiedDateTime": "Datetime"
}
```
