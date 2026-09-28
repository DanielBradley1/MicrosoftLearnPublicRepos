<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageautomaticrequestsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageAutomaticRequestSettings resource type

Namespace: microsoft.graph

Specifies information about an automatic access package assignment. This object is configured in the **automaticRequestSettings** property of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gracePeriodBeforeAccessRemoval | Duration | The duration for which access must be retained before the target's access is revoked once they leave the allowed target scope. |
| removeAccessWhenTargetLeavesAllowedTargets | Boolean | Indicates whether automatic assignment must be removed for targets who move out of the allowed target scope. |
| requestAccessForAllowedTargets | Boolean | If set to `true`, automatic assignments will be created for targets in the allowed target scope. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAutomaticRequestSettings",
  "requestAccessForAllowedTargets": "Boolean",
  "removeAccessWhenTargetLeavesAllowedTargets": "Boolean",
  "gracePeriodBeforeAccessRemoval": "String (duration)"
}
```
