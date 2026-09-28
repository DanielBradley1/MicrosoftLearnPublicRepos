<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-patch-columns?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# Upsert columns

Namespace: microsoft.graph

Upsert \(create or update\) up to 20 [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) objects on a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) in a single request. Delta patch allows the caller to perform multiple operations \(create, update\) on up to 20 columns with a single request.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | FileStorageContainer.Manage.All |
| Delegated \(personal Microsoft account\) | FileStorageContainer.Selected | Not available. |
| Application | FileStorageContainer.Selected | Not available. |

In addition to Microsoft Graph permissions, your app also must have the necessary container-type level permission or permissions to call this API. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container-type level permissions, see [SharePoint Embedded Authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

## HTTP request

```http
PATCH /storage/fileStorage/containers/{containerId}/columns
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON object with the following properties.

| Name | Type | Description |
| :--- | :--- | :--- |
| @context | String | OData annotation that identifies the payload type. Must be set to `#$delta` to signal a delta patch operation. Required. |
| value | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | A collection of up to 20 **columnDefinition** objects to process. Required. |

Each entry in the **value** collection represents one operation on a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0). The presence of the **id** property determines how the entry is interpreted:

- **Create**: Omit the **id** property. Specify the **name** property and the column type property \(for example, **boolean**, **text**, **choice**\).
- **Update**: Include the **id** of the existing column and the properties to update.

## Response

If successful, this method returns a `200 OK` response code and a collection of [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) objects in the response body. Columns that are processed successfully include the full **columnDefinition** object. Failed items include a **@Core.DataModificationException** annotation with error details.

This API might also return the following error response codes for the entire request:

| HTTP code | Description |
| :--- | :--- |
| 400 | Bad request. |
| 401 | Request lacks valid authentication credentials. |
| 403 | Provided authentication credentials are valid but insufficient to perform requested operation. |
| 404 | Container doesn't exist. |
| 423 | Container is locked. For example, the container is archived. |

## Examples

### Request

The following example shows a single delta patch request that mixes create and update items in one call. Items without an ID are treated as create operations; items with an ID are treated as update operations. Items that fail are reported inline with a **@Core.DataModificationException** annotation. The remaining items still succeed.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/columns
Content-Type: application/json

{
  "@context": "#$delta",
  "value": [
    {
      "id": "aec21c58-7f1f-4875-b438-d47ef622306c",
      "isSearchable": false
    },
    {
      "id": "aec21c58-7f1f-4875-b438-d47df622306c",
      "isSearchable": false
    },
    {
      "name": "booleanColumn1234",
      "boolean": {}
    },
    {
      "name": "booleanColumn33",
      "boolean": {}
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const columns = {
  '@context': '#$delta',
  value: [
    {
      id: 'aec21c58-7f1f-4875-b438-d47ef622306c',
      isSearchable: false
    },
    {
      id: 'aec21c58-7f1f-4875-b438-d47df622306c',
      isSearchable: false
    },
    {
      name: 'booleanColumn1234',
      boolean: {}
    },
    {
      name: 'booleanColumn33',
      boolean: {}
    }
  ]
};

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/columns')
	.update(columns);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response. The response includes one item for each item in the request, in the same order. In this example, the first request item is an update operation that succeeds, the second request item is an update operation that fails because no column with that ID exists, the third request item is a create operation that succeeds, and the fourth request item is a create operation that fails because a column with that name already exists.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#storage/fileStorage/containers('b%21ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z')/columns/$delta",
  "value": [
    {
      "@odata.etag": "\"4\"",
      "description": "",
      "displayName": "booleanColumn8",
      "id": "aec21c58-7f1f-4875-b438-d47ef622306c",
      "indexed": false,
      "isSearchable": false,
      "isDeletable": true,
      "isSealed": false,
      "name": "booleanColumn8",
      "readOnly": false,
      "type": "boolean",
      "boolean": {}
    },
    {
      "@Core.DataModificationException": {
        "@odata.type": "#Org.OData.Core.V1.DataModificationExceptionType",
        "failedOperation": "Update",
        "responseCode": 404,
        "info": {
          "code": "NotFound",
          "message": "Item not found."
        }
      },
      "id": "aec21c58-7f1f-4875-b438-d47df622306c",
      "type": "unknownFutureValue"
    },
    {
      "@odata.etag": "\"1\"",
      "description": "",
      "displayName": "booleanColumn1234",
      "id": "7eac4ae0-afe9-4a02-8cfa-9369558b44db",
      "indexed": false,
      "isSearchable": false,
      "isDeletable": true,
      "isSealed": false,
      "name": "booleanColumn1234",
      "readOnly": false,
      "type": "boolean",
      "boolean": {}
    },
    {
      "@Core.DataModificationException": {
        "@odata.type": "#Org.OData.Core.V1.DataModificationExceptionType",
        "failedOperation": "Create",
        "responseCode": 409,
        "info": {
          "code": "Conflict",
          "message": "A field with the specified name already exists"
        }
      },
      "id": "00000000-0000-0000-0000-000000000000",
      "name": "booleanColumn33",
      "type": "unknownFutureValue",
      "boolean": {}
    }
  ]
}
```
