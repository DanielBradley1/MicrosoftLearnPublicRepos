<!-- Source: https://learn.microsoft.com/en-us/graph/api/page-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# Update page

Namespace: microsoft.graph

Update the content of a OneNote page.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Notes.ReadWrite | Notes.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Notes.ReadWrite | Not available. |
| Application | Notes.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /me/onenote/pages/{id}/content
PATCH /users/{id | userPrincipalName}/onenote/pages/{id}/content
PATCH /groups/{id}/onenote/pages/{id}/content
PATCH /sites/{id}/onenote/pages/{id}/content
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | `application/json` |

## Request body

In the request body, supply an array of [patchContentCommand](https://learn.microsoft.com/en-us/graph/api/resources/patchcontentcommand?view=graph-rest-1.0) objects that represent the changes to the page. For more information and examples, see [Update OneNote pages](https://learn.microsoft.com/en-us/graph/onenote-update-page).

## Response

If successful, this method returns a `204 No Content` response code. No JSON data is returned for a PATCH request.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/me/onenote/pages/{id}/content
Content-type: application/json

[
   {
    'target':'#para-id',
    'action':'insert',
    'position':'before',
    'content':'<img src="image-url-or-part-name" alt="image-alt-text" />'
  }, 
  {
    'target':'#list-id',
    'action':'append',
    'content':'<li>new-page-content</li>'
  }
]
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = [
   {
    \'target\':\'#para-id\',
    \'action\':\'insert\',
    \'position\':\'before\',
    \'content\':\'<img src='image-url-or-part-name' alt='image-alt-text' />\'
  }, 
  {
    \'target\':\'#list-id\',
    \'action\':\'append\',
    \'content\':\'<li>new-page-content</li>\'
  }
];

await client.api('/me/onenote/pages/{id}/content')
	.update(stream);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
