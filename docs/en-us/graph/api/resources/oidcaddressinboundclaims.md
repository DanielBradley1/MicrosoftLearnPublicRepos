<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/oidcaddressinboundclaims?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-23 -->

# oidcAddressInboundClaims resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

After the custom identity provider sends an ID token back to Microsoft Entra, Microsoft Entra maps the claims from a token to the claims that Microsoft Entra recognizes and uses.

You can configure the following standard OpenID Connect \(OIDC\) address claims with the claims your identity provider provides in the ID Token.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| country | String | Country name. |
| locality | String | City or locality. |
| postal\_code | String | Zip code or postal code. |
| region | String | Country name. |
| street\_address | String | Full mailing address, formatted for display or use on a mailing label. This field MAY contain multiple lines, separated by newlines. Newlines can be represented either as a carriage return/line feed pair \("\\r\\n"\) or as a single line feed character \("\\n"\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oidcAddressInboundClaims",
  "street_address": "String",
  "locality": "String",
  "region": "String",
  "postal_code": "String",
  "country": "String"
}
```
