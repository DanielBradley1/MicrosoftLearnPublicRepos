<!-- Source: https://learn.microsoft.com/en-us/graph/api/itemactivity-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-22 -->

# List activities

Namespace: microsoft.graph

List the recent [activities](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) that took place on a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), item, or within an item hierarchy.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.Read | Files.Read.All, Files.ReadWrite, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.Read.All | Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |

## HTTP request

```http
GET /drives/{drive-id}/activities
GET /drives/{drive-id}/items/{item-id}/activities
GET /sites/{site-id}/lists/{list-id}/activities
GET /sites/{site-id}/lists/{list-id}/items/{item-id}/activities
```

## Optional query parameters

This method doesn't support [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [itemActivity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/v1.0/drives/b!kjtJnMGCeEeNkZsY18PtOiNjCV0Z9s9Fqyly8jKvPEB2kal9T5pOT5y7TXClirlE/items/01BYE5RZZ3CIHERNM6RZELODVGWI5T4B76/activities
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let activities = await client.api('/drives/b!kjtJnMGCeEeNkZsY18PtOiNjCV0Z9s9Fqyly8jKvPEB2kal9T5pOT5y7TXClirlE/items/01BYE5RZZ3CIHERNM6RZELODVGWI5T4B76/activities')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "id": "EJalEvjV1EgIYFQAAAAAAA==",
            "access": {},
            "activityDateTime": "2017-07-29T18:34:40Z",
            "actor": {
                "user": {
                    "displayName": "Xavier Wilke"
                }
            }
        },
        {
            "id": "cInT6/fV1EgFYFQAAAAAAA==",
            "access": {},
            "activityDateTime": "2017-07-29T16:23:35Z",
            "actor": {
                "user": {
                    "displayName": "Judith Clemons"
                }
            }
        },
        {
            "id": "EBJa0vPV1EjFX1QAAAAAAA==",
            "access": {},
            "activityDateTime": "2017-07-28T20:14:14Z",
            "actor": {
                "user": {
                    "displayName": "Misty Suarez"
                }
            }
        }
    ]
}
```
