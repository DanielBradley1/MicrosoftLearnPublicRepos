<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-update-customproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Update the custom properties of a fileStorageContainer

Namespace: microsoft.graph

Update one or multiple custom properties on a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). Only the **value**, **isSearchable**, and **isPatternToken** attributes of custom properties can be updated. Only the custom properties specified in the request body are updated. If a custom property specified in the request body doesn't exist on the container, it will be created.

Updating a custom property to a `null` value deletes the property from the container.

The application calling this API must have read and write permissions to the **fileStorageContainer** for the respective container type.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | Not available. |
| Delegated \(personal Microsoft account\) | FileStorageContainer.Selected | Not available. |
| Application | FileStorageContainer.Selected | Not available. |

In addition to Microsoft Graph permissions, your app also must have the necessary container-type level permission or permissions to call this API. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container-type level permissions, see [SharePoint Embedded Authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

## HTTP request

```http
PATCH /storage/fileStorage/containers/{containerId}/customProperties
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the custom properties to be updated and the new values for the relevant fields.

The following properties on custom properties can be modified.

| Property | Type | Description |
| :--- | :--- | :--- |
| isPatternToken | Boolean | Indicates whether **value** is a `urlTemplate` pattern \(for example, a token such as `{itemId}` used to configure redirect behavior when opening files\), rather than a literal value that consumers must resolve before use. |
| isSearchable | Boolean | Indicates whether the property is searchable. |
| value | String | The value of the custom property. |

## Response

If successful, this action returns a `200 OK` response code.

## Examples

### Request

The following example updates the `value` property of the custom properties `clientUniqeId` and `color`. Note that `isSearchable` for `clientUniqueId` was set to `true` before calling this API.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/customProperties
Content-type: application/json

{
  "clientUniqueId": {
    "value": "c5d88310-1fc7-49be-80ca-e7d7a11e638b"
  },
  "color": {
    "value": "green"
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerCustomPropertyDictionary = {
  clientUniqueId: {
    value: 'c5d88310-1fc7-49be-80ca-e7d7a11e638b'
  },
  color: {
    value: 'green'
  }
};

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/customProperties')
	.update(fileStorageContainerCustomPropertyDictionary);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 Ok

{
  "clientUniqueId": {
    "value": "c5d88310-1fc7-49be-80ca-e7d7a11e638b",
    "isSearchable": true
  },
  "color": {
    "value": "green",
    "isSearchable": false
  }
}
```
