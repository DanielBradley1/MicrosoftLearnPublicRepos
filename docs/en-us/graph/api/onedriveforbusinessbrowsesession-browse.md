<!-- Source: https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessbrowsesession-browse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# oneDriveForBusinessBrowseSession: browse

Namespace: microsoft.graph

Browse the files and folders within the [oneDriveForBusinessBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessbrowsesession?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.ReadWrite.All | Not available. |

Note

In the delegated flow, only users with the *SharePoint Backup Administrator* role can access this API.

## HTTP request

```http
POST /solutions/backupRestore/oneDriveForBusinessBrowseSessions/{oneDriveForBusinessBrowseSessionId}/browse
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

To get top browsable locations, in the request body, supply an empty JSON object `{}` for this method to get the list of the top browsable locations.

To browse a specify scope, in the request body, supply a JSON representation of the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| browseLocationItemKey | String | The item key of the location that you want to browse. Optional. |
| browseResourceType | [browsableResourceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#browsableresourcetype-values) | The type of the browsable location. The possible values are: `none`, `site`, `documentLibrary`, `folder`, `unknownFutureValue`. Optional. |
| filter | String | The search expression. Optional. |
| orderBy | [browseQueryOrder](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#browsequeryorder-values) | Specifies the order in which the response is returned. Optional. |

The following table shows examples of possible formats for the **filter** expression. The filter is supported only on the **name** property.

| Property | Operator | Example |
| :--- | :--- | :--- |
| name | `-contains` | `(name -contains 'contoso')` |

## Response

If successful, this function returns a `200 OK` response code and a collection of [browseQueryResponseItem](https://learn.microsoft.com/en-us/graph/api/resources/browsequeryresponseitem?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Get top browsable locations

The following example shows how to get the top browsable locations.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessBrowseSessions/K74iLNw55YTzbgnba0zxZROipFxnManccFpzecIrjuaypwA/browse
Content-Type: application/json

{}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const browseQueryResponseItem = {};

await client.api('/solutions/backupRestore/oneDriveForBusinessBrowseSessions/K74iLNw55YTzbgnba0zxZROipFxnManccFpzecIrjuaypwA/browse')
	.post(browseQueryResponseItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.browseQueryResponseItem)",
  "@odata.count": 1,
  "value": [
    {
      "itemKey": "18473961-eedf-4151-94a7-fd8eb4aec0d7,62ff7090-d987-4711-9d5c-74c9452a192f",
      "name": "user0",
      "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com",
      "type": "site"
    }
  ]
}
```

### Example 2: Browse a specific resource

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessBrowseSessions/m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE/browse

{
    "browseLocationItemKey": "f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e",
    "browseResourceType": "site"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const browseQueryResponseItem = {
    browseLocationItemKey: 'f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e',
    browseResourceType: 'site'
};

await client.api('/solutions/backupRestore/oneDriveForBusinessBrowseSessions/m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE/browse')
	.post(browseQueryResponseItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.browseQueryResponseItem)",
    "@odata.count": 10,
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessBrowseSessions/m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE/browse?$skiptoken=eyJ0eXBlIjoiRm9sZGVyIiwiZmlsdGVyIjoiIiwiaXRlbWtleSI6ImJiMjgxZjcyLWY3Y2MtNDM3OS1iMjk1LTBjNjEyNTMxMjdhZiw3NzA0MmZjYi03NGUzLTQ2YWEtOGE1My0wNWY5NzM5ZWJkZjQsMDdhNzEyNWEtMTVlMy00MDJkLWJlYjktZWU2NTQwZjdmNWJjLGE3MWUyZWZjLThmNTctNGIzOS1hNGE5LTNhNGU2MmZkMDM3YiIsInNraXB0b2tlbiI6IlVHRm5aV1E5VkZKVlJTWndYMU52Y25SQ1pXaGhkbWx2Y2owd0puQmZTVVE5TVRZNUpsSnZiM1JHYjJ4a1pYSTlKVEptY0dWeWMyOXVZV3dsTW1aMWMyVnlNQ1UxWm1FNE16QmxaR0ZrT1RBMU1EZzBPVzFoYm1selpIWXdOeVUxWm05dWJXbGpjbTl6YjJaMEpUVm1ZMjl0SlRKbVJHOWpkVzFsYm5SekpUSm1ZWEJwIn0",
    "value": [
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,2db4d4a9-7a10-409d-acfb-136101b43ba8",
            "name": "objectdelete-onedriveforbusinessbrowsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-onedriveforbusinessbrowsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2594"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,e3cca06d-b45d-4e98-bd16-c57a4563776f",
            "name": "objectdelete-browsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-browsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2411"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,cd692efa-0297-4a98-a39b-ec568a118f35",
            "name": "objectdelete-onedriveforbusinessrestoresessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-onedriveforbusinessrestoresessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2605"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,24c84b57-692b-40b3-b0b0-9cb8613b4398",
            "name": "objectdelete-restoresessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-restoresessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2422"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,b74f9233-27a7-4d49-a723-c9a4ab717d2d",
            "name": "objectdelete-exchangerestoresessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-exchangerestoresessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2484"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,4f20a6c4-c999-4ee8-9552-ca6a7fc46edf",
            "name": "objectdelete-onedriveforbusinessbrowsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-onedriveforbusinessbrowsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2493"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,92d28cdf-82b4-4964-b6fa-fd61240acf6c",
            "name": "objectdelete-sharepointrestoresessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-sharepointrestoresessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2504"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,cbd8e3c8-d0da-40a8-8eb8-51699268d6cf",
            "name": "objectenable.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectenable.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2853"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,45cccd01-511c-4705-97b6-8884d2397e3c",
            "name": "objectget.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectget.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2966"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,ef0ebe75-df09-43d0-91b6-705f03e0b006",
            "name": "objectlist-browsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectlist-browsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "3254"
        }
    ]
}
```

### Example 3: Browse items with nextLink.

We get the nextLink in the response of first POST api call as shown above and subsequent pages are fetched using the nextlink.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessBrowseSessions/m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE/browse?$skiptoken=nextFetchToken
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let browse = await client.api('/solutions/backupRestore/oneDriveForBusinessBrowseSessions/m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE/browse')
	.skiptoken('nextFetchToken')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.browseQueryResponseItem)",
    "@odata.count": 10,
    "value": [
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,2db4d4a9-7a10-409d-acfb-136101b43ba8",
            "name": "objectdelete-onedriveforbusinessbrowsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-onedriveforbusinessbrowsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2594"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,e3cca06d-b45d-4e98-bd16-c57a4563776f",
            "name": "objectdelete-browsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-browsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2411"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,cd692efa-0297-4a98-a39b-ec568a118f35",
            "name": "objectdelete-onedriveforbusinessrestoresessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-onedriveforbusinessrestoresessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2605"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,24c84b57-692b-40b3-b0b0-9cb8613b4398",
            "name": "objectdelete-restoresessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-restoresessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2422"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,b74f9233-27a7-4d49-a723-c9a4ab717d2d",
            "name": "objectdelete-exchangerestoresessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-exchangerestoresessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2484"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,4f20a6c4-c999-4ee8-9552-ca6a7fc46edf",
            "name": "objectdelete-onedriveforbusinessbrowsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-onedriveforbusinessbrowsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2493"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,92d28cdf-82b4-4964-b6fa-fd61240acf6c",
            "name": "objectdelete-sharepointrestoresessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-sharepointrestoresessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2504"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,cbd8e3c8-d0da-40a8-8eb8-51699268d6cf",
            "name": "objectenable.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectenable.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2853"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,2db4d4a9-7a10-409d-acfb-136101b43ba8",
            "name": "objectdelete-onedriveforbusinessbrowsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-onedriveforbusinessbrowsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2594"
        },
        {
            "itemKey": "bb281f72-f7cc-4379-b295-0c61253127af,77042fcb-74e3-46aa-8a53-05f9739ebdf4,07a7125a-15e3-402d-beb9-ee6540f7f5bc,e3cca06d-b45d-4e98-bd16-c57a4563776f",
            "name": "objectdelete-browsesessions.md",
            "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents/api/objectdelete-browsesessions.md",
            "type": "file",
            "itemsCount": 0,
            "sizeInBytes": "2411"
        },
    ]
}
```
