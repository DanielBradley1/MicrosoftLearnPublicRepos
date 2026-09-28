<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# intuneBrandingProfileAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This entity contains the properties used to assign a branding profile to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List intuneBrandingProfileAssignments](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofileassignment-list?view=graph-rest-beta) | [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) collection | List properties and relationships of the [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) objects. |
| [Get intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofileassignment-get?view=graph-rest-beta) | [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) | Read properties and relationships of the [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) object. |
| [Create intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofileassignment-create?view=graph-rest-beta) | [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) | Create a new [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) object. |
| [Delete intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofileassignment-delete?view=graph-rest-beta) | None | Deletes a [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta). |
| [Update intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofileassignment-update?view=graph-rest-beta) | [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) | Update the properties of a [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | Assignment target that the branding profile is assigned to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.intuneBrandingProfileAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
