<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# iosVppEBookAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign an iOS VPP EBook to a group.

Inherits from [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosVppEBookAssignments](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebookassignment-list?view=graph-rest-1.0) | [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0) collection | List properties and relationships of the [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0) objects. |
| [Get iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebookassignment-get?view=graph-rest-1.0) | [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0) | Read properties and relationships of the [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0) object. |
| [Create iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebookassignment-create?view=graph-rest-1.0) | [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0) | Create a new [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0) object. |
| [Delete iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebookassignment-delete?view=graph-rest-1.0) | None | Deletes a [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0). |
| [Update iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebookassignment-update?view=graph-rest-1.0) | [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0) | Update the properties of a [iosVppEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebookassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | The assignment target for eBook. Inherited from [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) |
| installIntent | [installIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-installintent?view=graph-rest-1.0) | The install intent for eBook. Inherited from [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0). The possible values are: `available`, `required`, `uninstall`, `availableWithoutEnrollment`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosVppEBookAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.deviceAndAppManagementAssignmentTarget"
  },
  "installIntent": "String"
}
```
