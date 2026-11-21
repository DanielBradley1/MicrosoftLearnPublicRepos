<!-- Source: https://learn.microsoft.com/en-us/graph/api/plan-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Update plan

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a plan object.

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
PATCH /planner/plans_v2/{planId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The complete ETag of the resource to update or delete. Required. |

Use the complete ETag returned by the latest read of this resource as the `If-Match` value. Don't construct or compare ETags yourself. A missing, invalid, or no-longer-usable ETag results in `412 Precondition Failed`. A conflicting change can result in `409 Conflict`; read the resource again and reconcile the changes before retrying. An older ETag doesn't necessarily fail when the service can merge nonconflicting changes.

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Title of the plan. |
| calendar | [planCalendar](https://learn.microsoft.com/en-us/graph/api/resources/plancalendar?view=graph-rest-beta) | Working-time calendar settings for the plan. |
| planView | [planView](https://learn.microsoft.com/en-us/graph/api/resources/planview?view=graph-rest-beta) | Plan-scoped view settings, including category definitions. |
| contentSensitivityLabelAssignment | [contentSensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/resources/contentsensitivitylabelassignment?view=graph-rest-beta) | The sensitivity label assigned to content associated with the plan. |
| sharedWithContainers | [plannerSharedWithContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannersharedwithcontainer?view=graph-rest-beta) collection | The list of containers \(for example, additional groups or channels\) that the plan is shared with. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |

Send only the properties that you want to change. Don't include immutable or service-populated properties from a GET response.

## Response

If successful, this method returns a `200 OK` response code and an updated [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/planner/plans_v2/{planId}
If-Match: {etag}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "displayName": "Product launch - phase 2"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.plan",
  "id": "da037802-c736-af41-ff32-789862c95bd9",
  "displayName": "Product launch - phase 2",
  "container": {
    "containerId": "5d5a917d-aef4-4fdc-bc99-6048a39aa329",
    "containerType": "group"
  }
}
```
