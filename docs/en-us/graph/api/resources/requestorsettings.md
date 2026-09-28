<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/requestorsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# requestorSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Used for the **requestorSettings** property of an [access package assignment policy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta). Provides additional settings to select who can create a request for an access package on that policy.

| Who can request | scopeType | allowedRequestors collection |
| :--- | :--- | :--- |
| No one | `NoSubjects` | empty array |
| Specific individual user in your directory | `SpecificDirectorySubjects` | [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-beta) |
| Users in your directory who are members of a group | `SpecificDirectorySubjects` | [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-beta) |
| Users in your directory with `userType` value of `member` | `AllExistingDirectoryMemberUsers` | empty array |
| Users in your directory | `AllExistingDirectorySubjects` | empty array |
| Users in specific connected organizations | `SpecificConnectedOrganizationSubjects` | [connectedOrganizationMembers](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganizationmembers?view=graph-rest-beta) |
| Users from any connected organizations that have the state property of the connected organization set to `configured`. | `AllConfiguredConnectedOrganizationSubjects` | empty array |
| Any user | `AllExternalSubjects` | empty array |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| scopeType | String | Who can request. One of `NoSubjects`, `SpecificDirectorySubjects`, `SpecificConnectedOrganizationSubjects`, `AllConfiguredConnectedOrganizationSubjects`, `AllExistingConnectedOrganizationSubjects`, `AllExistingDirectoryMemberUsers`, `AllExistingDirectorySubjects` or `AllExternalSubjects`. |
| acceptRequests | Boolean | Indicates whether new requests are accepted on this policy. |
| allowedRequestors | [userSet](https://learn.microsoft.com/en-us/graph/api/resources/userset?view=graph-rest-beta) collection | The users who are allowed to request on this policy, which can be [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-beta), [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-beta), and [connectedOrganizationMembers](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganizationmembers?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "scopeType": "SpecificDirectorySubjects",
  "acceptRequests": true,
  "allowedRequestors": [
       {
         "@odata.type": "#microsoft.graph.groupMembers",
         "isBackup": false,
         "id": "string (identifier)",
         "description": "Authorized requestors"
       }
   ]
}
```
