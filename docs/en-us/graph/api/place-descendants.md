<!-- Source: https://learn.microsoft.com/en-us/graph/api/place-descendants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# place: descendants

Namespace: microsoft.graph

Get all the descendants of a specific type under a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

Note

- Before you can use this API, ensure that the Places settings are properly configured. For more information, see [Prerequisites for Places list and descendant APIs](https://learn.microsoft.com/en-us/graph/api/resources/places-api-overview?view=graph-rest-1.0#prerequisites-for-places-list-and-descendant-apis).
- This method can't return more than 2,500 places.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Place.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Place.Read.All | Not available. |

## HTTP request

```http
GET /places/{id}/descendants/{placeType}
```

> **Note:** `{placeType}` can be any supported place type such as `microsoft.graph.building`, `microsoft.graph.floor`, `microsoft.graph.section`, `microsoft.graph.room`, `microsoft.graph.workspace`, and `microsoft.graph.desk`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) collection in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/places/ca163ae1-14a3-4e2a-8a97-5f82d672186f/descendants/microsoft.graph.desk
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let desk = await client.api('/places/ca163ae1-14a3-4e2a-8a97-5f82d672186f/descendants/microsoft.graph.desk')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "530f7900-8063-4daf-9cc1-168cb3ac26e9",
      "placeId": "530f7900-8063-4daf-9cc1-168cb3ac26e9",
      "displayName": "desk 5",
      "parentId": "ca163ae1-14a3-4e2a-8a97-5f82d672186f",
      "isWheelChairAccessible": false,
      "mode": { "@odata.type": "#microsoft.graph.dropInPlaceMode" }
    },
    {
      "id": "57289959-4add-4270-872b-cc93ca099ce5",
      "placeId": "57289959-4add-4270-872b-cc93ca099ce5",
      "displayName": "desk 6",
      "parentId": "ca163ae1-14a3-4e2a-8a97-5f82d672186f",
      "isWheelChairAccessible": true,
      "mailboxDetails": {
        "externalDirectoryObjectId": "6abaaee5-b796-48d0-be3d-0aa980258321",
        "emailAddress": "desk54a4fce541749088182888@contoso.com"
      },
      "mode": {
        "@odata.type": "#microsoft.graph.reservablePlaceMode"
      }
    }
  ]
}
```
