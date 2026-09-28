<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-countriesregions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-20 -->

# countryRegion resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a countryRegion object in Dynamics 365 Business Central, which is part of an address.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/dynamics-countriesregions-get?view=graph-rest-beta) | countryRegion | Get a Countries/Regions. |
| [Create](https://learn.microsoft.com/en-us/graph/api/dynamics-create-countriesregions?view=graph-rest-beta) | countryRegion | Create a Countries/Regions. |
| [Patch](https://learn.microsoft.com/en-us/graph/api/dynamics-countriesregions-update?view=graph-rest-beta) | countryRegion | Update a Countries/Regions. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/dynamics-countriesregions-delete?view=graph-rest-beta) | none | Delete a Countries/Regions. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the country/region. Non-editable. |
| code | string | Specifies the code of the country/region. |
| displayName | string | Specifies the display name of the country/region. |
| addressFormat | string | Specifies the format of the address that is displayed on external-facing documents. You link an address format to a country/region code so that external-facing documents based on cards or documents with that country/region code use the specified address format. |
| lastModifiedDateTime | datetime | The last datetime the country/region was modified. Read-Only. |

## Relationships

None

## JSON representation

Here is a JSON representation of the countriesRegions.

```json
{
  "id": "GUID",
  "code": "string",
  "displayName": "string",
  "addressFormat": "string",
  "lastModifiedDateTime": "datetime"
}
```
