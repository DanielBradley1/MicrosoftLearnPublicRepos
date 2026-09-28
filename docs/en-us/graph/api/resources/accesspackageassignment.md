<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-03 -->

# accessPackageAssignment resource type

Namespace: microsoft.graph

In [Microsoft Entra Entitlement Management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package assignment is an assignment of an access package to a particular subject and time range. For example, an access package assignment can state that user Alice is assigned access via the access package Sales for the period January 2019 through July 2019.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-assignments?view=graph-rest-1.0) | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) collection | Retrieve a list of **accessPackageAssignment** objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accesspackageassignment-get?view=graph-rest-1.0) | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) | Retrieve a **accessPackageAssignment** object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/accesspackageassignment-filterbycurrentuser?view=graph-rest-1.0) | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) collection | Retrieve the list of **accessPackageAssignment** objects filtered on the signed-in user. |
| [Reprocess](https://learn.microsoft.com/en-us/graph/api/accesspackageassignment-reprocess?view=graph-rest-1.0) | None | Automatically reevaluate and enforce a user's assignments for a specific access package. |
| [Check other access](https://learn.microsoft.com/en-us/graph/api/accesspackageassignment-additionalaccess?view=graph-rest-1.0) | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) collection | Retrieve a list of **accessPackageAssignment** objects indicating potential separation of duties conflicts or access to incompatible access packages. |

Note

To create, update or remove an access package assignment for a user, use the [create an accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-assignmentrequests?view=graph-rest-1.0) method.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customExtensionCalloutInstances | [customExtensionCalloutInstance](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutinstance?view=graph-rest-1.0) collection | Information about all the custom extension calls that were made during the access package assignment workflow. |
| expiredDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | Read-only. |
| schedule | [entitlementManagementSchedule](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementschedule?view=graph-rest-1.0) | When the access assignment is to be in place. Read-only. |
| state | accessPackageAssignmentState | The state of the access package assignment. The possible values are: `delivering`, `partiallyDelivered`, `delivered`, `expired`, `deliveryFailed`, `unknownFutureValue`. Read-only. Supports `$filter` \(`eq`\). |
| status | String | More information about the assignment lifecycle. Possible values include `Delivering`, `Delivered`, `AutoAssignmentInGracePeriod`, `NearExpiry1DayNotificationTriggered`, or `ExpiredNotificationTriggered`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackage | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | Read-only. Nullable. Supports `$filter` \(`eq`\) on the **id** property and `$expand` query parameters. |
| target | [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-1.0) | The subject of the access package assignment. Read-only. Nullable. Supports `$expand`. Supports `$filter` \(`eq`\) on **objectId**. |
| assignmentPolicy | [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) | Read-only. Supports `$filter` \(`eq`\) on the **id** property and `$expand` query parameters. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignment",
  "expiredDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "schedule": {
    "@odata.type": "microsoft.graph.entitlementManagementSchedule"
  },
  "state": "String",
  "status": "String"
}
```
