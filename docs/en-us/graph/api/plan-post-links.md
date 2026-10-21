<!-- Source: https://learn.microsoft.com/en-us/graph/api/plan-post-links?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Create contentLink for a plan

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new contentLink object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /users/{usersId}/planner/plans_v2/{planId}/links
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) object.

You can specify the following properties when creating a **contentLink**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display label for the link. Optional. |
| linkType | contentLinkType | Type of content the link points to. The possible values are: `documentReference`, `webReference`, `unknownFutureValue`. Optional. |
| webUrl | String | URL the link points to. Optional. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/users/{usersId}/planner/plans_v2/{planId}/links
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.contentLink",
  "displayName": "Design specs",
  "linkType": "documentReference",
  "webUrl": "https://www.contoso.com/docs/design-specs.docx",
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
  "@odata.type": "#microsoft.graph.contentLink",
  "id": "eb8b65f4-318a-9e90-8af9-67a53027e563",
  "displayName": "String",
  "linkType": "String",
  "webUrl": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "capabilities": {
    "@odata.type": "microsoft.graph.contentLinkCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
