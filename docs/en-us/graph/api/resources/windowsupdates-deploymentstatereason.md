<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentstatereason?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# deploymentStateReason resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A reason for a particular deployment state.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | microsoft.graph.windowsUpdates.deploymentStateReasonValue | Specifies a reason for the deployment state. The possible values are: `scheduledByOfferWindow`, `offeringByRequest`, `pausedByRequest`, `pausedByMonitoring`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `faultedByContentOutdated`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.deploymentStateReason",
  "value": "String"
}
```
