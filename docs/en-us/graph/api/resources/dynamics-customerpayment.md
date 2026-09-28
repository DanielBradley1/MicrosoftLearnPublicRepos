<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-customerpayment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# customerPayment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a customer payment in Dynamics 365 Business Central. A customer payment is entered as a line in a customer payment journal.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get customer payment](https://learn.microsoft.com/en-us/graph/api/dynamics-customerpayment-get?view=graph-rest-beta) | [customerPayment](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-customerpayment?view=graph-rest-beta) | Get a customer payment. |
| [Create customer payment](https://learn.microsoft.com/en-us/graph/api/dynamics-create-customerpayment?view=graph-rest-beta) | [customerPayment](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-customerpayment?view=graph-rest-beta) | Create a customer payment. |
| [Update customer payment](https://learn.microsoft.com/en-us/graph/api/dynamics-customerpayment-update?view=graph-rest-beta) | [customerPayment](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-customerpayment?view=graph-rest-beta) | Update a customer payment. |
| [Delete customer payment](https://learn.microsoft.com/en-us/graph/api/dynamics-customerpayment-delete?view=graph-rest-beta) | None | Delete a customer payment. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| amount | Decimal | Specifies the total amount \(including VAT\) that the customer payment consists of. |
| appliesToInvoiceId | GUID | The unique ID of the invoice that the payment is related to. |
| appliesToInvoiceNumber | String | The number of the invoice that the payment is related to. Maximum supported size is 20 characters. |
| comment | String | A user specified comment on the customer payment. Maximum supported size is 250 characters. |
| contactId | String | The exchange contact ID for the given customer. If a customer id isn't specified, we'll use the contact id to find it. Maximum supported size is 250 characters. |
| customerId | GUID | The unique ID of the customer that the payment is related to. |
| customerNumber | String | The number of the customer that the payment is related to. Maximum supported size is 20 characters. |
| description | String | The description of the customer payment, provided by the user or autocreated. Maximum supported size is 50 characters. |
| documentNumber | String | Specifies a document number for the customer payment. Maximum supported size is 20 characters. |
| externalDocumentNumber | String | Specifies an external document number for the customer payment. Maximum supported size is 20 characters. |
| id | GUID | The unique ID of the customer payment. Non-editable. |
| journalDisplayName | String | The customer payment journal in which the payment record is a line. |
| lastModifiedDateTime | Datetime | The last datetime the customer payment was modified. Read-Only. |
| lineNumber | Integer | The number of the customer payment. |
| postingDate | Date | The date that the customer payment is posted. |

## Relationships

A customer payment is a subpage of a customer payment journal. It can't be accessed directly.

A customer payment can be a "Parent Entity" of the dimension lines.

A Customer \(customerId\) must exist in the Customers table.

An Invoice \(appliesToInvoiceId\) must exist in the Sales Invoices Table.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "amount": "Decimal",
  "appliesToInvoiceId": "GUID",
  "appliesToInvoiceNumber": "String",
  "comment": "String",
  "contactId": "String",
  "customerId": "GUID",
  "customerNumber": "String",
  "description": "String",
  "documentNumber": "String",
  "externalDocumentNumber": "String",
  "id": "GUID",
  "journalDisplayName": "String",
  "lastModifiedDateTime": "Datetime",
  "lineNumber": "Integer",
  "postingDate": "Date"
}
```
