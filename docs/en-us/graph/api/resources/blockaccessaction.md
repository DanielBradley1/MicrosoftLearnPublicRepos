<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/blockaccessaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# blockAccessAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a DLP action that explicitly blocks access to the content that triggered the rule match.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.security.dlpAction | The type of DLP action. Possible values are `notifyUser`, `blockAccess`, `restrictAccess`, `generateAlert`, `generateIncidentReportAction`, `sPBlockAnonymousAccess`, `sPRuntimeAccessControl`, `sPSharingNotifyUser`, and `sPSharingGenerateIncidentReport`. Inherited from [dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.blockAccessAction",
  "action": "blockAccess"
}
```
