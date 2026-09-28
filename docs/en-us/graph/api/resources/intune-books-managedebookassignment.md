<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# managedEBookAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign a eBook to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedEBookAssignments](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookassignment-list?view=graph-rest-1.0) | [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) collection | List properties and relationships of the [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) objects. |
| [Get managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookassignment-get?view=graph-rest-1.0) | [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) | Read properties and relationships of the [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) object. |
| [Create managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookassignment-create?view=graph-rest-1.0) | [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) | Create a new [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) object. |
| [Delete managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookassignment-delete?view=graph-rest-1.0) | None | Deletes a [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0). |
| [Update managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebookassignment-update?view=graph-rest-1.0) | [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) | Update the properties of a [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | The assignment target for eBook. |
| installIntent | [installIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-installintent?view=graph-rest-1.0) | The install intent for eBook. The possible values are: `available`, `required`, `uninstall`, `availableWithoutEnrollment`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedEBookAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.allLicensedUsersAssignmentTarget"
  },
  "installIntent": "String"
}
```
