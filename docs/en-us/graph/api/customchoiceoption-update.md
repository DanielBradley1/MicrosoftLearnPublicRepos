<!-- Source: https://learn.microsoft.com/en-us/graph/api/customchoiceoption-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Update customChoiceOption

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a customChoiceOption object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /me/planner/plans_v2/{planId}/customFieldDefinitions/{customFieldDefinitionId}/choiceOptions/{customChoiceOptionId}
PATCH /users/{usersId}/planner/plans_v2/{planId}/customFieldDefinitions/{customFieldDefinitionId}/choiceOptions/{customChoiceOptionId}
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
| displayName | String | Display text of the choice option. Optional. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/customFieldDefinitions/{customFieldDefinitionId}/choiceOptions/{customChoiceOptionId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.customChoiceOption",
  "displayName": "High",
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
  "@odata.type": "#microsoft.graph.customChoiceOption",
  "id": "2eb17e1c-d4c2-52c5-9207-d5e023b47665",
  "displayName": "String",
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
