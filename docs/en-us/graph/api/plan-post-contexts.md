<!-- Source: https://learn.microsoft.com/en-us/graph/api/plan-post-contexts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Create planContextLink

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new planContextLink object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/planner/plans_v2/{planId}/contexts
POST /users/{usersId}/planner/plans_v2/{planId}/contexts
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) object.

You can specify the following properties when creating a **planContextLink**.

| Property | Type | Description |
| :--- | :--- | :--- |
| key | String | Identifier for the context the plan is surfaced in. Optional. |
| displayNameSegments | String collection | Display name segments used to render where the plan is surfaced. Optional. |
| webUrl | String | URL of the surface where the plan is displayed. Optional. |
| associationType | String | Describes how the plan is associated with the surface. Optional. |
| displayAs | plannerPlanContextType | How the context link should be displayed. The possible values are: `teamsTab`, `sharePointPage`, `meetingNotes`, `other`, `unknownFutureValue`, `loopPage`, `project`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `loopPage` , `project`. Optional. |
| isActive | Boolean | Indicates whether the context link is currently active. Optional. |
| customLinkText | String | Custom text used to render the link, if provided. Optional. |
| ownerAppId | String | Application ID of the app that owns the surface the plan is linked from. Optional. |
| isCreation | Boolean | Indicates whether this context link represents the original creation surface for the plan. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/contexts
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.planContextLink",
  "key": "19:abcdef1234567890abcdef1234567890@thread.tacv2",
  "displayNameSegments": [
    "Contoso Project"
  ],
  "webUrl": "https://teams.microsoft.com/l/entity/com.microsoft.teamspace.tab.planner/tab-contoso-project",
  "associationType": "primary",
  "displayAs": "teamsTab",
  "isActive": true,
  "customLinkText": "Project plan",
  "ownerAppId": "4d1c9a3e-7b52-4f8a-9d31-6c2e8f4b9a17",
  "isCreation": true
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.planContextLink",
  "id": "901187ee-a684-eeaa-61d0-b0fb4774cdab",
  "key": "String",
  "displayNameSegments": [
    "String"
  ],
  "webUrl": "String",
  "associationType": "String",
  "displayAs": "String",
  "isActive": "Boolean",
  "customLinkText": "String",
  "ownerAppId": "String",
  "isCreation": "Boolean",
  "createdDateTime": "String (timestamp)"
}
```
