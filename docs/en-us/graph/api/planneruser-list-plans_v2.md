<!-- Source: https://learn.microsoft.com/en-us/graph/api/planneruser-list-plans_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# List plans\_v2 for a user

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) objects associated with the user.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.Read | Tasks.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /users/{usersId}/planner/plans_v2
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/users/{usersId}/planner/plans_v2
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
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
  ]
}
```
