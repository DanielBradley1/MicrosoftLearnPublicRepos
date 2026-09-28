<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restrictaccessactionbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-21 -->

# restrictAccessActionBase resource type

Namespace: microsoft.graph

Abstract base type representing a data loss prevention \(DLP\) action that restricts access to content based on policy evaluation.

Use [restrictaccessaction](https://learn.microsoft.com/en-us/graph/api/resources/restrictaccessaction?view=graph-rest-1.0) to explicitly restrict access to the content. Inherits from [dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.security.dlpAction | The type of DLP action. Inherited from [dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-1.0). The possible values are: `notifyUser`, `blockAccess`, `deviceRestriction`, `browserRestriction`, `unknownFutureValue`, `restrictAccess`, `generateAlert`, `generateIncidentReportAction`, `sPBlockAnonymousAccess`, `sPRuntimeAccessControl`, `sPSharingNotifyUser`, `sPSharingGenerateIncidentReport`, `restrictWebGrounding`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `restrictAccess`, `generateAlert`, `generateIncidentReportAction`, `sPBlockAnonymousAccess`, `sPRuntimeAccessControl`, `sPSharingNotifyUser`, `sPSharingGenerateIncidentReport`, `restrictWebGrounding`. |
| restrictionAction | microsoft.graph.security.restrictionAction | Action for the app to take. The possible values are: `warn`, `audit`, `block`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restrictAccessActionBase",
  "action": "String",
  "restrictionAction": "String"
}
```
