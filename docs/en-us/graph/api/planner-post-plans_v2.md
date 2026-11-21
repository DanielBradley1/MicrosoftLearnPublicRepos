<!-- Source: https://learn.microsoft.com/en-us/graph/api/planner-post-plans_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Create plan

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new plan object.

## API availability

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
| container | [planContainer](https://learn.microsoft.com/en-us/graph/api/resources/plancontainer?view=graph-rest-beta) | Identifies the group, Teams channel, or user that owns the plan. Required. Immutable after creation. |
| calendar | [planCalendar](https://learn.microsoft.com/en-us/graph/api/resources/plancalendar?view=graph-rest-beta) | Working-time calendar settings for the plan. Optional. |
| planView | [planView](https://learn.microsoft.com/en-us/graph/api/resources/planview?view=graph-rest-beta) | Plan-scoped view settings, including category definitions. Optional. |
| contentSensitivityLabelAssignment | [contentSensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/resources/contentsensitivitylabelassignment?view=graph-rest-beta) | The sensitivity label assigned to content associated with the plan. Optional. |
| sharedWithContainers | [plannerSharedWithContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannersharedwithcontainer?view=graph-rest-beta) collection | The list of containers \(for example, additional groups or channels\) that the plan is shared with. Optional. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. Optional. |
| contexts | [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) collection | Context links to create with the plan by using a deep insert. Optional. |
| links | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) collection | Content links to create with the plan by using a deep insert. Optional. |

Supply **container** when creating the plan; it can't be changed afterward. Don't include service-generated audit metadata, **archivalInfo**, **duration**, or **hasChat**.

To create a plan and supported related objects in one request, include **contexts** or **links** as arrays. This is a **deep insert**, not a standalone create operation on either child resource. Support for these collections doesn't imply support for arbitrary nested objects, such as tasks, buckets, or goals. Feature availability depends on the plan's capabilities.

## Response

If successful, this method returns a `201 Created` response code and a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create a plan

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/planner/plans_v2
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "displayName": "Product Launch Plan",
  "container": {
    "containerId": "5d5a917d-aef4-4fdc-bc99-6048a39aa329",
    "containerType": "group"
  },
  "sharedWithContainers": []
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "id": "da037802-c736-af41-ff32-789862c95bd9",
  "displayName": "Product Launch Plan",
  "container": {
    "containerId": "5d5a917d-aef4-4fdc-bc99-6048a39aa329",
    "containerType": "group"
  }
}
```

### Example 2: Create a plan with a context link

#### Request

This request creates a plan and a context link to its SharePoint project page. Replace **containerId** with the ID of an accessible Microsoft 365 group.

```http
POST https://graph.microsoft.com/beta/planner/plans_v2
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "displayName": "Product launch",
  "container": {
    "containerType": "group",
    "containerId": "5d5a917d-aef4-4fdc-bc99-6048a39aa329"
  },
  "contexts": [
    {
      "key": "launch-project-page",
      "displayAs": "sharePointPage",
      "webUrl": "https://contoso.sharepoint.com/sites/launch/SitePages/planning.aspx",
      "displayNameSegments": ["Product launch", "Planning"],
      "associationType": "created",
      "isActive": true
    }
  ]
}
```

#### Response

The following response is shortened. To read the created context link, get the returned plan with `$expand=contexts`.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "id": "da037802-c736-af41-ff32-789862c95bd9",
  "displayName": "Product launch",
  "container": {
    "containerType": "group",
    "containerId": "5d5a917d-aef4-4fdc-bc99-6048a39aa329"
  }
}
```
