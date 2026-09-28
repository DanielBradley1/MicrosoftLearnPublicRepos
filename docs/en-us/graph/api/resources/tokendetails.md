<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tokendetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# tokenDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes a complex property that represents an access token's unique identifier and the time when the token was issued. **uniqueTokenIdentifier** is unique for every access token. This object is configured in the **tokenDetails** property of [linkableIdentifiers](https://learn.microsoft.com/en-us/graph/api/resources/linkableidentifiers?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| issuedAtDateTime | DateTimeOffset | Represents when the authentication for this token occurred. |
| uniqueTokenIdentifier | String | Represents the token identifier claim. This ID is a unique per-token identifier that is case-sensitive. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tokenDetails",
  "uniqueTokenIdentifier": "String",
  "issuedAtDateTime": "String (timestamp)"
}
```
