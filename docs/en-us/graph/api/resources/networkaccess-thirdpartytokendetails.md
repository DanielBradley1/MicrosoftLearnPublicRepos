<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-thirdpartytokendetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-11 -->

# thirdPartyTokenDetails resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details about third-party tokens used in network access transactions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationDateTime | DateTimeOffset | Time the token will expire. |
| issuedAtDateTime | DateTimeOffset | Time the token was issued at. |
| uniqueTokenIdentifier | String | Unique token identifier. |
| validFromDateTime | DateTimeOffset | Time the token is valid from. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.thirdPartyTokenDetails",
  "uniqueTokenIdentifier": "String",
  "issuedAtDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "validFromDateTime": "String (timestamp)"
}
```
