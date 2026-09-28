<!-- Source: https://learn.microsoft.com/en-us/graph/api/workbookdocumenttask-list-changes?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# List workbookDocumentTaskChanges

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/drive/items/{id}/workbook/worksheets/{id}/tasks/{id}/changes
GET /me/drive/items/{id}/workbook/comments/{id}/task/changes
```

## Optional query parameters

This method supports the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Workbook-Session-Id | Workbook session ID that determines if changes are persisted or not. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) objects in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/drive/root/workbook/worksheets/D5667D8C-B814-4748-B942-9C41BCC9BBB1/tasks/47B4663E-612F-4E06-B2E6-E8EBE819CBB6/changes
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let changes = await client.api('/drive/root/workbook/worksheets/D5667D8C-B814-4748-B942-9C41BCC9BBB1/tasks/47B4663E-612F-4E06-B2E6-E8EBE819CBB6/changes')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK

{
  "value": [
    {
      "changedBy": {
        "id": "6463a5ce-2119-4198-9f2a-628761df4a62",
        "displayName": "Mike Smith",
        "email": "mikesmith@contoso.com"
      },
      "createdDateTime": "2020-09-01T18:36:49.2407981Z",
      "id": "57A21473-7238-3CE0-BCB6-A55E4909AA98",
      "type": "create"
    },
    {
      "changedBy": {
        "id": "6463a5ce-2119-4198-9f2a-628761df4a62",
        "displayName": "Mike Smith",
        "email": "mikesmith@contoso.com"
      },
      "createdDateTime": "2020-09-01T18:36:49.2407981Z",
      "id": "97A21473-8339-4BF0-BCB6-F55E4909FFB8",
      "type": "assign",
      "assignee": {
        "id": "1e9955d2-6acd-45bf-86d3-b546fdc795eb",
        "displayName": "Joe Doe",
        "email": "joedoe@contoso.com"
      }
    },
    {
      "changedBy": {
        "id": "6463a5ce-2119-4198-9f2a-628761df4a62",
        "displayName": "Mike Smith",
        "email": "mikesmith@contoso.com"
      },
      "createdDateTime": "2020-09-01T18:36:49.2407981Z",
      "id": "26950968-F917-4C2C-BB46-4845D0F7171B",
      "type": "SetTitle",
      "title": "This is a task title"
    }
  ]
}
```
