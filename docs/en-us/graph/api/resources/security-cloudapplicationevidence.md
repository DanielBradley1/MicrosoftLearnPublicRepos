<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-cloudapplicationevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# cloudApplicationEvidence resource type

Namespace: microsoft.graph.security

A cloud application that is reported in the alert.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | Int64 | Unique identifier of the application. |
| displayName | String | Name of the application. |
| instanceId | Int64 | Identifier of the instance of the Software as a Service \(SaaS\) application. |
| instanceName | String | Name of the instance of the SaaS application. |
| saasAppId | Int64 | The identifier of the SaaS application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.cloudApplicationEvidence",
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
  "appId": "Integer",
  "displayName": "String",
  "instanceId": "Integer",
  "instanceName": "String",
  "saasAppId": "Integer"
}
```
