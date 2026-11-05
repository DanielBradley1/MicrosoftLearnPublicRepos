<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-post-customemojis?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Create teamworkCustomEmoji

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [custom emoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) in the teamwork messaging of the organization, which adds the custom emoji to Teams for the tenant. The emoji image is provided as base64-encoded content bytes.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkCustomEmoji.Create | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkCustomEmoji.Create.All | Teamwork.Migrate.All |

## HTTP request

```http
POST /teamwork/messaging/customEmojis
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) object.

The following table lists the properties that are required when you create a custom emoji.

| Property | Type | Description |
| :--- | :--- | :--- |
| contentBytes | Binary | The base64-encoded image content for the emoji. Supported formats include PNG and GIF. |
| contentType | String | The media type of the custom emoji content, such as `image/png` or `image/gif`. |
| displayName | String | The unique display name of the custom emoji. Key. Must be unique and must not conflict with existing emoji names. |

## Response

If successful, this method returns a `201 Created` response code and a [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request to upload a custom emoji.

```msgraph
POST https://graph.microsoft.com/beta/teamwork/messaging/customEmojis
Content-Type: application/json

{
    "displayName": "thumbsup_custom",
    "contentBytes": "iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAYAAABXAvmHAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAOxAAADsQBlSsOGwAABGhJREFU...",
    "contentType": "image/png"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#teamwork/messaging/customEmojis/$entity",
    "id": "01ZPGUWVOZAD7SNI6IYPC3QOQWMDMZQO6U",
    "displayName": "thumbsup_custom",
    "contentBytes": "iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAYAAABXAvmHAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAOxAAADsQBlSsOGwAABGhJREFU...",
    "contentType": "image/png",
    "createdDateTime": "2026-06-10T12:00:00Z",
    "createdBy": {
        "user": {
            "id": "670374fa-3b0e-4a3b-9d33-0e1bc5ff1956",
            "displayName": "Adele Vance"
        }
    }
}
```

## Related content

- [List customEmojis](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-list-customemojis?view=graph-rest-beta)
- [Get teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/teamworkcustomemoji-get?view=graph-rest-beta)
- [Delete teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/teamworkcustomemoji-delete?view=graph-rest-beta)
