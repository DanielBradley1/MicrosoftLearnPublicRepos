<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-vendor?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# vendor resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a vendor in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get vendor](https://learn.microsoft.com/en-us/graph/api/dynamics-vendor-get?view=graph-rest-beta) | vendor | Gets a vendor object. |
| [Create vendor](https://learn.microsoft.com/en-us/graph/api/dynamics-create-vendor?view=graph-rest-beta) | vendor | Creates a vendor object. |
| [Update vendor](https://learn.microsoft.com/en-us/graph/api/dynamics-vendor-update?view=graph-rest-beta) | vendor | Updates a vendor object. |
| [Delete vendor](https://learn.microsoft.com/en-us/graph/api/dynamics-vendor-delete?view=graph-rest-beta) | none | Deletes a vendor object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the vendor. Non-editable. |
| number | string | The vendor number. |
| displayName | string | The vendor's display name. |
| address | [NAV.PostalAddress](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-complextypes?view=graph-rest-beta) | The vendor's address. |
| phoneNumber | string | The vendor's telephone number. |
| email | string | The vendor's email address. |
| website | string | The vendor's website address. |
| taxRegistrationNumber | string | The vendor's tax registration number. |
| currencyId | GUID | The default currency code ID for the vendor. |
| currencyCode | string | The default currency code for the vendor. |
| irs1099Code | string | Specifies a 1099 code for the vendor. US only. |
| paymentTermsId | GUID | The default payment terms ID for the vendor. |
| paymentMethodId | GUID | The default payment method ID for the vendor. |
| taxLiable | Boolean | Specifies if the vendor is liable for tax. |
| blocked | string | Specifies which transactions with the vendor that can't be posted. Accepted values are blank, Payment or All |
| balance | decimal | The vendor's balance. Read-Only. |
| lastModifiedDateTime | datetime | The last datetime the vendor was modified. Read-Only. |

## Relationships

None

## JSON representation

Here's a JSON representation of the vendor.

```json
{
  "id": "GUID",
  "number": "string",
  "displayName": "string",
  "address": "NAV.PostalAddress",
  "phoneNumber": "string",
  "email": "string",
  "website": "string",
  "taxRegistrationNumber": "string",
  "currencyId": "GUID",
  "currencyCode": "string",
  "irs1099Code": "string",
  "paymentTermsId": "GUID",
  "paymentMethodId": "GUID",
  "taxLiable": "Boolean",
  "blocked": "string",
  "balance": "decimal",
  "lastModifiedDateTime": "datetime"
}
```
