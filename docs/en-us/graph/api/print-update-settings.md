<!-- Source: https://learn.microsoft.com/en-us/graph/api/print-update-settings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# Update printSettings

Namespace: microsoft.graph

Update tenant-wide settings for the Universal Print service.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrintSettings.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /print/settings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for the relevant [printSettings](https://learn.microsoft.com/en-us/graph/api/resources/printsettings?view=graph-rest-1.0) fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| documentConversionEnabled | Boolean | Specifies whether document conversion is enabled for the tenant. If document conversion is enabled, Universal Print service automatically converts documents into a format compatible with the printer \(for example, XPS to PDF\) when needed. |
| printerDiscoverySettings | [printerDiscoverySettings](https://learn.microsoft.com/en-us/graph/api/resources/printerdiscoverysettings?view=graph-rest-1.0) | Specifies settings that affect printer discovery when using Universal Print. |

## Response

If successful, this method returns a `204 No Content` response code and an empty response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/print/settings
Content-type: application/json

{
  "documentConversionEnabled": true
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const printSettings = {
  documentConversionEnabled: true
};

await client.api('/print/settings')
	.update(printSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
