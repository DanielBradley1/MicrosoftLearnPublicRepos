<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/physicalofficeaddress?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# physicalOfficeAddress resource type

Namespace: microsoft.graph

Represents the business address of a resource such as an organizational contact.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| city | String | The city. |
| countryOrRegion | String | The country or region. It's a free-format string value, for example, "United States". |
| officeLocation | String | Office location such as building and office number for an organizational contact. |
| postalCode | String | The postal code. |
| state | String | The state. |
| street | String | The street. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "city": "string",
  "countryOrRegion": "string",
  "officeLocation": "string",
  "postalCode": "string",
  "state": "string",
  "street": "string"
}
```
