<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-complextypes?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# complex types JSON

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

These are the various complex types in Dynamics 365 Business Central. You can see usage of these complex types in the various individual methods that make use of them.

## Postal address

Represents a Postal Address complex type in Dynamics 365 Business Central.

### Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| street | string | Postal address street. |
| city | string | Postal address city. |
| state | string | Postal address state. |
| countryLetterCode | string | Postal address country letter code \(two character word\) |
| postalCode | string | Postal address post code |

```json
"PostalAddress" 
{ 
"street": "string",
"city": "string", 
"state": "string", 
"countryLetterCode": "string", 
"postalCode": "string" 
} 
```
