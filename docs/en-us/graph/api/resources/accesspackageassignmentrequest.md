<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-11 -->

# accessPackageAssignmentRequest resource type

Namespace: microsoft.graph

In [Microsoft Entra Entitlement Management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package assignment request is created by or on behalf of a user who wants to obtain an access package assignment. If the request is successful, with any necessary approvals, the user receives an access package assignment, and is the subject of that resulting access package assignment. Microsoft Entra ID also creates access package assignment requests automatically for tracking access removal.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-assignmentrequests?view=graph-rest-1.0) | [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) collection | Retrieve a list of **accesspackageassignmentrequest** objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-assignmentrequests?view=graph-rest-1.0) | [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) | Creates a new **accessPackageAssignmentRequest** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentrequest-get?view=graph-rest-1.0) | [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) | Read properties and relationships of an **accessPackageAssignmentRequest** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentrequest-delete?view=graph-rest-1.0) | None | Delete an **accessPackageAssignmentRequest**. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentrequest-cancel?view=graph-rest-1.0) | [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) collection | Cancel an **accessPackageAssignmentRequest** object that is in a cancelable state. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentrequest-filterbycurrentuser?view=graph-rest-1.0) | [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) collection | Retrieve the list of **accessPackageAssignmentRequest** objects filtered on the signed-in user. |
| [Reprocess](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentrequest-reprocess?view=graph-rest-1.0) | None | Automatically retry a user’s request for access to an access package. |
| [Resume](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentrequest-resume?view=graph-rest-1.0) | None | Resume a user's access package request after waiting for a callback from a custom extension. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| answers | [accessPackageAnswer](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswer?view=graph-rest-1.0) collection | Answers provided by the requestor to [accessPackageQuestions](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) asked of them at the time of request. |
| completedDateTime | DateTimeOffset | The date of the end of processing, either successful or failure, of a request. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| customExtensionCalloutInstances | [customExtensionCalloutInstance](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutinstance?view=graph-rest-1.0) collection | Information about all the custom extension calls that were made during the access package assignment workflow. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Supports `$filter`. |
| id | String | Read-only. |
| justification | String | The requestor's supplied justification. |
| requestType | accessPackageRequestType | The type of the request. The possible values are: `notSpecified`, `userAdd`, `userUpdate`, `userRemove`, `adminAdd`, `adminUpdate`, `adminRemove`, `systemAdd`, `systemUpdate`, `systemRemove`, `onBehalfAdd` \(not supported\), `unknownFutureValue`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `approverRemove`. Requests from the user have a **requestType** of `userAdd`, `userUpdate`, or `userRemove`. This property can't be changed once set. |
| schedule | [entitlementManagementSchedule](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementschedule?view=graph-rest-1.0) | The range of dates that access is to be assigned to the requestor. This property can't be changed once set, but a new schedule for an assignment can be included in another `userUpdate` or `adminUpdate` assignment request. |
| state | accessPackageRequestState | The state of the request. The possible values are: `submitted`, `pendingApproval`, `delivering`, `delivered`, `deliveryFailed`, `denied`, `scheduled`, `canceled`, `partiallyDelivered`, `unknownFutureValue`. Read-only. Supports `$filter` \(`eq`\). |
| status | String | More information on the request processing status. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackage | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | The access package associated with the accessPackageAssignmentRequest. An access package defines the collections of resource roles and the policies for how one or more users can get access to those resources. Read-only. Nullable.  <br>  <br>Supports `$expand`. |
| assignment | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) | For a **requestType** of `userAdd` or `adminAdd`, this is an access package assignment requested to be created. For a **requestType** of `userRemove`, `adminRemove`, `approverRemove`, or `systemRemove`, this has the `id` property of an existing assignment to be removed.  <br>  <br>Supports `$expand`. |
| requestor | [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-1.0) | The subject who requested or, if a direct assignment, was assigned. Read-only. Nullable. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentRequest",
  "completedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "requestType": "String",
  "justification": "String",
  "schedule": {
    "@odata.type": "microsoft.graph.entitlementManagementSchedule"
  },
  "state": "String",
  "status": "String",
  "answers": [
    {
      "@odata.type": "microsoft.graph.accessPackageAnswerString"
    }
  ]

}
```
