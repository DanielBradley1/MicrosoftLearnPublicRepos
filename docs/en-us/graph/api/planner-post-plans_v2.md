<!-- Source: https://learn.microsoft.com/en-us/graph/api/planner-post-plans_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Create plan\_v2

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new plan object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /planner/plans_v2
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) object.

You can specify the following properties when creating a **plan**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Title of the plan. Required. |
| container | [planContainer](https://learn.microsoft.com/en-us/graph/api/resources/plancontainer?view=graph-rest-beta) | Identifies the group, Teams channel, or user that owns the plan. Required, and immutable after creation. Optional. |
| calendar | [planCalendar](https://learn.microsoft.com/en-us/graph/api/resources/plancalendar?view=graph-rest-beta) | Working-time calendar settings for the plan. Optional. |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta) | Information about whether the entity is archived, and when it was archived. Optional. |
| planView | [planView](https://learn.microsoft.com/en-us/graph/api/resources/planview?view=graph-rest-beta) | Plan-scoped view settings, including category definitions. Optional. |
| contentSensitivityLabelAssignment | [contentSensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/resources/contentsensitivitylabelassignment?view=graph-rest-beta) | The sensitivity label assigned to content associated with the plan. Optional. |
| hasChat | Boolean | Indicates whether the plan has an associated chat. Optional. |
| duration | Int32 | Duration of the plan, in days. Optional. |
| sharedWithContainers | [plannerSharedWithContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannersharedwithcontainer?view=graph-rest-beta) collection | The list of containers \(for example, additional groups or channels\) that the plan is shared with. Optional. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/planner/plans_v2
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "displayName": "Product Launch Plan",
  "container": {
    "@odata.type": "microsoft.graph.planContainer"
  },
  "calendar": {
    "@odata.type": "microsoft.graph.planCalendar"
  },
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "planView": {
    "@odata.type": "microsoft.graph.planView"
  },
  "contentSensitivityLabelAssignment": {
    "@odata.type": "microsoft.graph.contentSensitivityLabelAssignment"
  },
  "hasChat": true,
  "duration": 30,
  "sharedWithContainers": [
    {
      "@odata.type": "microsoft.graph.plannerSharedWithContainer"
    }
  ],
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "id": "da037802-c736-af41-ff32-789862c95bd9",
  "displayName": "String",
  "container": {
    "@odata.type": "microsoft.graph.planContainer"
  },
  "calendar": {
    "@odata.type": "microsoft.graph.planCalendar"
  },
  "creationInfo": {
    "@odata.type": "microsoft.graph.creationInfo"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "planView": {
    "@odata.type": "microsoft.graph.planView"
  },
  "contentSensitivityLabelAssignment": {
    "@odata.type": "microsoft.graph.contentSensitivityLabelAssignment"
  },
  "hasChat": "Boolean",
  "duration": "Integer",
  "sharedWithContainers": [
    {
      "@odata.type": "microsoft.graph.plannerSharedWithContainer"
    }
  ],
  "capabilities": {
    "@odata.type": "microsoft.graph.planCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
