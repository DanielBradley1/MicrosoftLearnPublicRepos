<!-- Source: https://learn.microsoft.com/en-us/graph/api/customfieldvalue-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Update customFieldValue

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a customFieldValue object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /me/planner/plans_v2/{planId}/tasks/{taskId}/customFieldValues/{customFieldValueId}
PATCH /users/{usersId}/planner/plans_v2/{planId}/tasks/{taskId}/customFieldValues/{customFieldValueId}
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
| customFieldDefinitionId | String | ID of the customFieldDefinition this value is for. Immutable after creation. Optional. |
| value | String | The value of the custom field, formatted according to the field's valueType. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/tasks/{taskId}/customFieldValues/{customFieldValueId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.customFieldValue",
  "customFieldDefinitionId": "d7f4b8a2-6c31-4d9a-8f21-2b6a9d4e7c31",
  "value": "42500"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.customFieldValue",
  "id": "32618015-76cd-34e6-561e-21ced3b2077b",
  "customFieldDefinitionId": "String",
  "value": "String"
}
```
