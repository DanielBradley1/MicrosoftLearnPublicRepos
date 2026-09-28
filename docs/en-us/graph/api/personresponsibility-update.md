<!-- Source: https://learn.microsoft.com/en-us/graph/api/personresponsibility-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Update personResponsibility

Namespace: microsoft.graph

Update the properties of a [personResponsibility](https://learn.microsoft.com/en-us/graph/api/resources/personresponsibility?view=graph-rest-beta) object in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Read | AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy, User.Read.All, User.ReadBasic.All, User.ReadWrite, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | User.Read | User.ReadWrite |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /me/responsibilities/{id}
PATCH /users/{id | userPrincipalName}/responsibilities/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [personResponsibility](https://learn.microsoft.com/en-us/graph/api/resources/personresponsibility?view=graph-rest-beta) object.

The following table lists the properties that are required when you create the [personResponsibility](https://learn.microsoft.com/en-us/graph/api/resources/personresponsibility?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| collaborationTags | String collection | Contains experience scenario tags a user has associated with the interest. Allowed values in the collection are: `askMeAbout`, `ableToMentor`, `wantsToLearn`, `wantsToImprove`. |
| description | String | Description of the responsibility. |
| displayName | String | Contains a friendly name for the responsibility. |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| webUrl | String | Contains a link to a web page or resource about the responsibility. |

## Response

If successful, this method returns a `200 OK` response code and an updated [personResponsibility](https://learn.microsoft.com/en-us/graph/api/resources/personresponsibility?view=graph-rest-beta) object in the response body.

## Examples

### Request

```http
PATCH https://graph.microsoft.com/beta/me/responsibilities/0fb4c1e3-c1e3-0fb4-e3c1-b40fe3c1b40f
Content-Type: application/json

{
  "collaborationTags": [
    "askMeAbout"
  ]
}
```

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "0fb4c1e3-c1e3-0fb4-e3c1-b40fe3c1b40f",
  "allowedAudiences": "organization",
  "inference": null,
  "createdDateTime": "2020-07-06T06:34:12.2294868Z",
  "createdBy": {
    "application": null,
    "device": null,
    "user": {
      "displayName": "Innocenty Popov",
      "id": "db789417-4ccb-41d1-a0a9-47b01a09ea49"
    }
  },
  "lastModifiedDateTime": "2020-07-06T06:34:12.2294868Z",
  "lastModifiedBy": {
    "application": null,
    "device": null,
    "user": {
      "displayName": "Innocenty Popov",
      "id": "db789417-4ccb-41d1-a0a9-47b01a09ea49"
    }
  },
  "source": null,
  "description": "Member of the Microsoft API Council",
  "displayName": "API Council",
  "webUrl": null,
  "collaborationTags": [
    "askMeAbout"
  ]
}
```
