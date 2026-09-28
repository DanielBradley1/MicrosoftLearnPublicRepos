<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-cloudlogonrequestevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-01 -->

# cloudLogonRequestEvidence resource type

Namespace: microsoft.graph.security

Represents a cloud sign-in request for an account.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| requestId | String | The unique identifier for the sign-in request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.cloudLogonRequestEvidence",
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
  "requestId": "String"
}
```
