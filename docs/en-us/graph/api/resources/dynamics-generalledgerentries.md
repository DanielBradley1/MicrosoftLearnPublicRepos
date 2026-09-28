<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-generalledgerentries?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# generalLedgerEntry resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a general ledger entry in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get general ledger entries](https://learn.microsoft.com/en-us/graph/api/dynamics-generalledgerentries-get?view=graph-rest-beta) | generalLedgerEntry | Get a general ledger entry object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountId | GUID | Specifies the account ID of the general ledger entry. |
| accountNumber | string | Specifies the account number of the general ledger entry. The maximum size is 20 characters. |
| creditAmount | numeric | Specifies the credit amount of the general ledger entry. |
| debitAmount | numeric | Specifies the debit amount of the general ledger entry. |
| description | string | Specifies the description of the general ledger entry. The maximum size is 50 characters. |
| documentNumber | string | Specifies the document number of the general ledger entry. The maximum size is 20 characters. |
| documentType | string | Specifies the document type of the general ledger entry. |
| id | numeric | The unique identifier for the general ledger entry. |
| lastModifiedDateTime | datetime | The last date time when the general ledger entry was modified. |
| postingDate | date | Specifies the posting date of the general ledger entry. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "accountId": "GUID",
  "accountNumber": "String",
  "creditAmount": "Decimal",
  "debitAmount": "Decimal",
  "description": "String",
  "documentNumber": "String",
  "documentType": "String",
  "id": "Int",
  "lastModifiedDateTime": "Datetime",
  "postingDate": "Date"
}
```
