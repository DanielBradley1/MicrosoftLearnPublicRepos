<!-- Source: https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-getuserownedobjects?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# List deleted items \(directory objects\) owned by a user

Namespace: microsoft.graph

Retrieve a list of recently deleted [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) and [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) objects owned by the specified user.

This API returns up to 1,000 deleted objects owned by the user, sorted by ID, and doesn't support pagination.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.Read.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group.Read.All | Group.ReadWrite.All |

## HTTP request

```http
POST /directory/deletedItems/getUserOwnedObjects
```

## Request headers

| Name | Description |
| --- | --- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

The request body requires the following parameters:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| userId | String | ID of the owner. |
| type | String | Type of owned objects to return; `Group` and `Application` are currently the only supported values. |

## Response

Successful requests return `200 OK` response codes; the response object includes [directory \(deleted items\)](https://learn.microsoft.com/en-us/graph/api/resources/directory?view=graph-rest-1.0) properties.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/directory/deletedItems/getUserOwnedObjects
Content-type: application/json

{
  "userId":"55ac777c-109e-4022-b58c-470c8fcb6892",
  "type":"Group"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
  userId: '55ac777c-109e-4022-b58c-470c8fcb6892',
  type: 'Group'
};

await client.api('/directory/deletedItems/getUserOwnedObjects')
	.post(directoryObject);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response. Note: This response object may be truncated for brevity. All supported properties are returned from actual calls.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.group",
      "id": "bfa7033a-7367-4644-85f5-95aaf385cbd7",
      "deletedDateTime": "2018-04-01T12:39:16Z",
      "classification": null,
      "createdDateTime": "2017-03-22T12:39:16Z",
      "description": null,
      "displayName": "Test",
      "groupTypes": [
        "Unified"
      ],
      "mail": "Test@contoso.com",
      "mailEnabled": true,
      "mailNickname": "Test",
      "membershipRule": null,
      "membershipRuleProcessingState": null,
      "preferredDataLocation": null,
      "preferredLanguage": null,
      "proxyAddresses": [
        "SMTP:Test@contoso.com"
      ],
      "renewedDateTime": "2017-09-22T22:30:39Z",
      "securityEnabled": false,
      "theme": null,
      "visibility": "Public"
    }
  ]
}
```
