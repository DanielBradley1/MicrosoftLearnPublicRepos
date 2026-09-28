<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailboxfolder-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Update mailboxFolder

Namespace: microsoft.graph

Update [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) properties such as the **displayName** within a mailbox.

Note

The folder **type** can't be updated. Instead, the folder needs to be deleted and a new folder can be created.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxFolder.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MailboxFolder.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}
PATCH /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}/childFolders/{mailboxFolderId}
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
| displayName | String | The display name of the folder. |

## Response

If successful, this method returns a `200 OK` response code and an updated [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows how to update certain folder properties of a mailbox folder.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0648f21@aab09c93/folders/AAMkAGVmMDEzM

{
  "displayName": "Announcements",
  "singleValueExtendedProperties": [
        {
            "id": "String 0x3001",
            "value": "Announcements"
        }
    ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mailboxFolder = {
  displayName: 'Announcements',
  singleValueExtendedProperties: [
        {
            id: 'String 0x3001',
            value: 'Announcements'
        }
    ]
};

await client.api('/admin/exchange/mailboxes/MBX:e0648f21@aab09c93/folders/AAMkAGVmMDEzM')
	.update(mailboxFolder);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 179

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/exchange/mailboxes('MBX%3A73c326ef%402829ab8a')/folders/$entity",
  "id": "AQMkAGUw==",
  "displayName": "Announcements",
  "parentFolderId": "AQMkAGUc==",
  "parentMailboxUrl": "https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0648f21@aab09c93",
  "childFolderCount": 0,
  "totalItemCount": 0,
  "wellKnownName": null,
  "type": "IPF.Note"
}
```
