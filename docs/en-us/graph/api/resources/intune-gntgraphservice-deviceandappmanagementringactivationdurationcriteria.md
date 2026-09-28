<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringactivationdurationcriteria?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementRingActivationDurationCriteria resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Criteria for specifying time duration to wait for activating current Ring relative to overall deployment start time.

Inherits from [deviceAndAppManagementRingActivationCriteria](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringactivationcriteria?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| duration | Duration | Duration to wait relative to start of deployment assignment/deployment template for the current ring to get activated |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementRingActivationDurationCriteria",
  "duration": "String (duration)"
}
```
