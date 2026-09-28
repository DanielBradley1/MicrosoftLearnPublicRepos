<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-configurationmanagercollectionassignmenttarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# configurationManagerCollectionAssignmentTarget resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an assignment to a Configuration Manager Collection.

Inherits from [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| collectionId | String | The collection Id that is the target of the assignment. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.configurationManagerCollectionAssignmentTarget",
  "collectionId": "String"
}
```
