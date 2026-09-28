<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-agedaccountsreceivable?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# agedAccountsReceivable resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an agedAccountsReceivable object in Dynamics 365 Business Central, which is showing the aging of a customer account.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get aged accounts payable](https://learn.microsoft.com/en-us/graph/api/dynamics-agedaccountsreceivable-get?view=graph-rest-beta) | agedAccountsReceivable | Get agedAccountsReceivable object |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customerId | GUID | The unique ID of customer. |
| customerNumber | string | Specifies customer's number. |
| name | string | Specifies customer's name. |
| currencyCode | string | Specifies the currency. |
| balanceDue | numeric | Specifies the customer's total balance. |
| currentAmount | numeric | Specifies balance for the current aging period. |
| period1Amount | numeric | Specifies balance in the first aging period. |
| period2Amount | numeric | Specifies balance in the second aging period. |
| period3Amount | numeric | Specifies balance in the third aging period. |
| agedAsOfDate | date | Specifies period start date used to calculate aging periods. |
| periodLengthFilter | string | Specifies the length of the periods. Acceptable time units include: D, WD, W, M, Q, and Y. C, meaning current time unit based on date, can be specified as a prefix to the time unit. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "customerId": "GUID",
    "customerNumber": "string",
    "name": "string",
    "currencyCode": "string",
    "balanceDue": "decimal",
    "currentAmount": "decimal",
    "period1Amount": "decimal",
    "period2Amount": "decimal",
    "period3Amount": "decimal",
    "agedAsOfDate": "date",
    "periodLengthFilter": "string"
}
```
