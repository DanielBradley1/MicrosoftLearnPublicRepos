<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-paymentterms?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# paymentTerm resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a payment term in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get payment terms](https://learn.microsoft.com/en-us/graph/api/dynamics-paymentterms-get?view=graph-rest-beta) | **paymentTerm** | Get a payment terms object. |
| [Create payment terms](https://learn.microsoft.com/en-us/graph/api/dynamics-create-paymentterms?view=graph-rest-beta) | **paymentTerm** | Create a payment terms object. |
| [Update payment terms](https://learn.microsoft.com/en-us/graph/api/dynamics-paymentterms-update?view=graph-rest-beta) | **paymentTerm** | Update a payment terms object. |
| [Delete payment terms](https://learn.microsoft.com/en-us/graph/api/dynamics-paymentterms-delete?view=graph-rest-beta) | none | Delete a payment terms object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| calculateDiscountOnCreditMemos | Boolean | Specifies whether the discount should be applied to credit memos. `True` indicates a discount is given; `false`\* indicates a discount won't be given. |
| code | string | Specifies the payment term code. |
| discountDateCalculation | string | Specifies the formula that is used to calculate the date that a payment must be made in order to obtain a discount. |
| discountPercent | decimal | Specifies the discount percentage that is applied for early payment of an invoice amount. |
| displayName | string | Specifies the payment term display name. |
| dueDateCalculation | string | Specifies the formula that is used to calculate the date that a payment must be made. |
| id | GUID | The unique identifier for the **paymentTerm**. Non-editable. |
| lastModifiedDateTime | datetime | The date and time when the **paymentTerm** were last modified. Read-Only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "calculateDiscountOnCreditMemos": "boolean",
  "code": "string",
  "discountDateCalculation": "string",
  "discountPercent": "decimal",
  "displayName": "string",
  "dueDateCalculation": "string",
  "id": "GUID",
  "lastModifiedDateTime": "datetime"
}
```
