<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-companyinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# companyInformation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the information specified for the current company in Dynamics 365 Business Central, such as name, address, email address, and website address.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get company information](https://learn.microsoft.com/en-us/graph/api/dynamics-companyinformation-get?view=graph-rest-beta) | companyInformation | Gets a company information. |
| [Update company information](https://learn.microsoft.com/en-us/graph/api/dynamics-companyinformation-update?view=graph-rest-beta) | companyInformation | Updates a company information. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the company. Non-editable. |
| displayName | string | The company's display name. |
| address | [NAV.PostalAddress](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-complextypes?view=graph-rest-beta) | The company's address. View the complex type for more details. |
| phoneNumber | string | The company's telephone number. |
| faxNumber | string | The company's fax number. |
| email | string | The company's email address. |
| website | string | The company's website address. |
| taxRegistrationNumber | string | The company's tax registration number. |
| currencyCode | string | The currency the company does business in. Read-Only. |
| currentFiscalYearStartDate | date | The company's current fiscal year start date. Read-Only. |
| industry | string | The industry the company is part of. |
| picture | stream | The company logo. Read-Only. |
| businessProfileId | string | The business profile ID linked to the Financials company. Read-Only. |
| lastModifiedDateTime | datetime | The last datetime the company was modified. Read-Only. |

## Relationships

None

## JSON representation

Here's a JSON representation of the companyInformation

```json
{
  "id": "GUID",
  "displayName": "string",
  "address": "NAV.PostalAddress",
  "phoneNumber": "string",
  "faxNumber": "string",
  "email": "string",
  "website": "string",
  "taxRegistrationNumber": "string",
  "currencyCode": "string",
  "currentFiscalYearStartDate": "date",
  "industry": "string",
  "picture": "stream",
  "businessProfileId": "string",
  "lastModifiedDateTime": "datetime"
}
```
