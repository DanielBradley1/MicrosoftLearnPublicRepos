<!-- Source: https://learn.microsoft.com/en-us/graph/api/goal-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Update goal

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a goal object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /me/planner/plans_v2/{planId}/goals/{goalId}
PATCH /users/{usersId}/planner/plans_v2/{planId}/goals/{goalId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Title of the goal. Required. |
| planId | String | ID of the plan that contains the goal. Required, and immutable after creation. Required. |
| status | plannerGoalStatus | Progress status of the goal. The possible values are: `notStarted`, `onTrack`, `behind`, `atRisk`, `closed`, `unknownFutureValue`. Optional. |
| priority | Int32 | Priority of the goal. Required. |
| startDate | Date | Date the goal starts. Optional. |
| finishDate | Date | Date the goal is targeted to finish. Optional. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | Additional details or notes about the goal. Optional. |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta) | Information about whether the entity is archived, and when it was archived. Optional. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/goals/{goalId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.goal",
  "displayName": "Increase customer satisfaction",
  "planId": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31",
  "status": "onTrack",
  "priority": 3,
  "startDate": "2026-01-01",
  "finishDate": "2026-12-31",
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.goal",
  "id": "9935021b-eda4-2af0-bcc7-8bd400583aa0",
  "displayName": "String",
  "planId": "String",
  "status": "String",
  "priority": "Integer",
  "startDate": "Date",
  "finishDate": "Date",
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "capabilities": {
    "@odata.type": "microsoft.graph.goalCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
