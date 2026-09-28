<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# physicalAddress resource type

Namespace: microsoft.graph

Represents the street address of a resource such as a contact or event.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| city | String | The city. |
| countryOrRegion | String | The country or region. It's a free-format string value, for example, "United States". |
| postalCode | String | The postal code. |
| state | String | The state. |
| street | String | The street. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "city": "string",
  "countryOrRegion": "string",
  "postalCode": "string",
  "state": "string",
  "street": "string"
}
```
