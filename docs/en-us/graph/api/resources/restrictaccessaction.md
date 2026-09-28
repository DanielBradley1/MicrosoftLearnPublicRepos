<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restrictaccessaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# restrictAccessAction resource type

Namespace: microsoft.graph

Represents a DLP action that explicitly restricts access to the content that triggered the rule match.

Inherits from [restrictAccessActionBase](https://learn.microsoft.com/en-us/graph/api/resources/restrictaccessactionbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.security.dlpAction | The type of DLP action. Inherited from [dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-1.0).The possible values are: `notifyUser`, `blockAccess`, `deviceRestriction`, `browserRestriction`, `unknownFutureValue`, `restrictAccess`, `generateAlert`, `generateIncidentReportAction`, `sPBlockAnonymousAccess`, `sPRuntimeAccessControl`, `sPSharingNotifyUser`, `sPSharingGenerateIncidentReport`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `restrictAccess`, `generateAlert`, `generateIncidentReportAction`, `sPBlockAnonymousAccess`, `sPRuntimeAccessControl`, `sPSharingNotifyUser`, `sPSharingGenerateIncidentReport`. |
| restrictionAction | microsoft.graph.security.restrictionAction | Action for the app to take. Inherited from [restrictAccessActionBase](https://learn.microsoft.com/en-us/graph/api/resources/restrictaccessactionbase?view=graph-rest-1.0). The possible values are: `warn`, `audit`, `block`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restrictAccessAction",
  "action": "String",
  "restrictionAction": "String"
}
```
