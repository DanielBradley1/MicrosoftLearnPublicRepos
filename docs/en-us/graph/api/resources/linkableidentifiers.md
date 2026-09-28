<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/linkableidentifiers?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# linkableIdentifiers resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes a set of token claims used to link together all the authentication artifacts issued from a single interactive root authentication. This object is configured in the **linkableIdentifiers** property of [auditActivityInitiator](https://learn.microsoft.com/en-us/graph/api/resources/auditactivityinitiator?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceId | String | Represents a unique identifier for the device from which a user is interacting with an application. |
| sessionId | String | Represents a unique identifier for an entire session and is generated when a user does interactive authentication. This ID helps link all authentication artifacts issued from a single root authentication. |
| tokenDetails | [tokenDetails](https://learn.microsoft.com/en-us/graph/api/resources/tokendetails?view=graph-rest-beta) | Property that represents an access token's unique identifier and the time when the token was issued. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.linkableIdentifiers",
  "sessionId": "String",
  "deviceId": "String",
  "tokenDetails": {
    "@odata.type": "microsoft.graph.tokenDetails"
  }
}
```
