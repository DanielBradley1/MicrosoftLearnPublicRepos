<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailsearchfolder-post-userconfigurations?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create userConfiguration

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxConfigItem.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | MailboxConfigItem.ReadWrite | Not available. |
| Application | MailboxConfigItem.ReadWrite | Not available. |

## HTTP request

```http
POST /me/mailFolders/{mailFolderId}/userConfigurations
POST /users/{usersId}/mailFolders/{mailFolderId}/userConfigurations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) object.

You can specify the following properties when you create a **userConfiguration**.

| Property | Type | Description |
| :--- | :--- | :--- |
| binaryData | Binary | Arbitrary binary data. Optional. |
| id | String | The unique key. |
| structuredData | [structuredDataEntry](https://learn.microsoft.com/en-us/graph/api/resources/structureddataentry?view=graph-rest-beta) collection | Key-value pairs of supported data types. Optional. |
| xmlData | Binary | Binary data for storing serialized XML. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/me/mailFolders/inbox/userConfigurations
Content-Type: application/json

{
  "id": "MyApp",
  "binaryData": "SGVsbG8=",
  "xmlData": "V29ybGQ=",
  "structuredData": [
    {
      "keyEntry": {
        "type": "byte",
        "values": [
          "100"
        ]
      },
      "valueEntry": {
        "type": "boolean",
        "values": [
          "true"
        ]
      }
    },
    {
      "keyEntry": {
        "type": "integer32",
        "values": [
          "-32"
        ]
      },
      "valueEntry": {
        "type": "integer64",
        "values": [
          "64"
        ]
      }
    },
    {
      "keyEntry": {
        "type": "unsignedInteger32",
        "values": [
          "32"
        ]
      },
      "valueEntry": {
        "type": "unsignedInteger64",
        "values": [
          "64"
        ]
      }
    },
    {
      "keyEntry": {
        "type": "string",
        "values": [
          "DateTime"
        ]
      },
      "valueEntry": {
        "type": "dateTime",
        "values": [
          "2025-10-23T01:23:45.0000000+00:00"
        ]
      }
    },
    {
      "keyEntry": {
        "type": "byteArray",
        "values": [
          "AQECAwUI"
        ]
      },
      "valueEntry": {
        "type": "stringArray",
        "values": [
          "Hello",
          "World"
        ]
      }
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const userConfiguration = {
  id: 'MyApp',
  binaryData: 'SGVsbG8=',
  xmlData: 'V29ybGQ=',
  structuredData: [
    {
      keyEntry: {
        type: 'byte',
        values: [
          '100'
        ]
      },
      valueEntry: {
        type: 'boolean',
        values: [
          'true'
        ]
      }
    },
    {
      keyEntry: {
        type: 'integer32',
        values: [
          '-32'
        ]
      },
      valueEntry: {
        type: 'integer64',
        values: [
          '64'
        ]
      }
    },
    {
      keyEntry: {
        type: 'unsignedInteger32',
        values: [
          '32'
        ]
      },
      valueEntry: {
        type: 'unsignedInteger64',
        values: [
          '64'
        ]
      }
    },
    {
      keyEntry: {
        type: 'string',
        values: [
          'DateTime'
        ]
      },
      valueEntry: {
        type: 'dateTime',
        values: [
          '2025-10-23T01:23:45.0000000+00:00'
        ]
      }
    },
    {
      keyEntry: {
        type: 'byteArray',
        values: [
          'AQECAwUI'
        ]
      },
      valueEntry: {
        type: 'stringArray',
        values: [
          'Hello',
          'World'
        ]
      }
    }
  ]
};

await client.api('/me/mailFolders/inbox/userConfigurations')
	.version('beta')
	.post(userConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('f42c50f8-1300-48a0-93d4-6481acda7efb')/mailFolders('inbox')/userConfigurations/$entity",
  "id": "MyApp",
  "binaryData": "SGVsbG8=",
  "xmlData": "V29ybGQ=",
  "structuredData": [
    {
      "keyEntry": {
        "type": "byte",
        "values": [
          "100"
        ]
      },
      "valueEntry": {
        "type": "boolean",
        "values": [
          "true"
        ]
      }
    },
    {
      "keyEntry": {
        "type": "integer32",
        "values": [
          "-32"
        ]
      },
      "valueEntry": {
        "type": "integer64",
        "values": [
          "64"
        ]
      }
    },
    {
      "keyEntry": {
        "type": "unsignedInteger32",
        "values": [
          "32"
        ]
      },
      "valueEntry": {
        "type": "unsignedInteger64",
        "values": [
          "64"
        ]
      }
    },
    {
      "keyEntry": {
        "type": "string",
        "values": [
          "DateTime"
        ]
      },
      "valueEntry": {
        "type": "dateTime",
        "values": [
          "2025-10-23T01:23:45.0000000+00:00"
        ]
      }
    },
    {
      "keyEntry": {
        "type": "byteArray",
        "values": [
          "AQECAwUI"
        ]
      },
      "valueEntry": {
        "type": "stringArray",
        "values": [
          "Hello",
          "World"
        ]
      }
    }
  ]
}
```
