<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-customerpaymentsjournal?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# customerPaymentsJournal resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a customer payment journal in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get customer payments journal](https://learn.microsoft.com/en-us/graph/api/dynamics-customerpaymentsjournal-get?view=graph-rest-beta) | customerPaymentJournals | Gets a customer payment journal. |
| [Create customer payments journal](https://learn.microsoft.com/en-us/graph/api/dynamics-create-customerpaymentsjournal?view=graph-rest-beta) | customerPaymentJournals | Creates a customer payment journal. |
| [Update customer payments journal](https://learn.microsoft.com/en-us/graph/api/dynamics-customerpaymentsjournal-update?view=graph-rest-beta) | customerPaymentJournals | Updates a customer payment journal. |
| [Delete customer payments journal](https://learn.microsoft.com/en-us/graph/api/dynamics-customerpaymentsjournal-delete?view=graph-rest-beta) | none | Deletes a customer payment journal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the customer payment journal. Non-editable. |
| code | string, maximum size 10 | The code of the customer payment journal. |
| displayName | string, maximum size 50 | The display name of the customer payment journal. |
| lastModifiedDateTime | datetime | The last datetime the customer payment journal was modified. Read-Only. |

## Relationships

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "GUID",
  "code": "String",
  "displayName": "String",
  "lastModifiedDateTime": "datetime"
}
```
