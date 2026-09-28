<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-oauthapplicationevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# oauthApplicationEvidence resource type

Namespace: microsoft.graph.security

An OAuth application that is reported in the alert.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | Unique identifier of the application. |
| displayName | String | Name of the application. |
| objectId | String | The unique identifier of the application object in Azure AD. |
| publisher | String | The name of the application publisher. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.oauthApplicationEvidence",
  "createdDateTime": "String (timestamp)",
  "verdict": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": [
    "String"
  ],
  "tags": [
    "String"
  ],
  "appId": "String",
  "displayName": "String",
  "objectId": "String",
  "publisher": "String"
}
```
