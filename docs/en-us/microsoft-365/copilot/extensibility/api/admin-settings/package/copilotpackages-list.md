<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list -->
<!-- Sitemap-Last-Modified: 2026-09-28 -->

# List packages

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Retrieves a list of all packages available in the tenant.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotPackages.Read.All | CopilotPackages.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotPackages.Read.All | CopilotPackages.ReadWrite.All |

## HTTP request

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}.` Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

### Optional query parameters

This method supports the `$filter` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. The following properties are supported with the `$filter` OData query parameter. For examples of using the `$filter` query parameter, see [Examples](#examples).

| Parameter | Type | Description |
| --- | --- | --- |
| `supportedHosts` | string | Filter by supported host \(`Copilot`, `Outlook`, `Teams`, `M365`\) |
| `elementTypes` | string | Filter by element type \(`Bots`, `DeclarativeAgent`, `CustomEngineAgent`\) |
| `lastModifiedDateTime` | datetime | Filter by last updated date/time, using `ge` or `le` |
| `platform` | string | Filter by platform \(`Copilot Studio`, `Microsoft 365 Copilot Agent Builder`\) |
| `requestStatus` | [copilotPackageRequestStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#copilotpackagerequeststatus-enumeration) | Filter by request status, using `pending` \(see [Filter by request properties](#filter-by-request-properties)\) |
| `requestType` | [copilotPackageRequestType](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#copilotpackagerequesttype-enumeration) | Filter by the kind of request \(see [Filter by request properties](#filter-by-request-properties)\) |

#### Filter by request properties

The `requestStatus` and `requestType` properties describe a request that a user in the organization submitted for a package. Filtering on either property returns the packages that users requested.

Unfiltered `GET /copilot/admin/catalog/packages` behavior is unchanged.

The following filter expressions are supported:

- `requestStatus eq 'pending'`, which selects the open request queue. Other `requestStatus` members aren't supported in a filter.
- A single `eq` comparison on `requestType`, against one of the `publish`, `activate`, `access`, or `update` members. Don't filter on the `unknownFutureValue` sentinel member.
- Those two comparisons joined with `and`.
- Either or both of those comparisons combined with a `lastModifiedDateTime` bound. Supply one `ge` bound, one `le` bound, or both to express an inclusive range.

You can write the `and` conjuncts in any order.

A `lastModifiedDateTime` bound applies to the package's `lastModifiedDateTime` value, which is the same value returned for that property. It doesn't filter on when a user submitted the request. A package that has no `lastModifiedDateTime` value doesn't match while a bound is present.

Filtering on `lastModifiedDateTime` by itself is ordinary catalog behavior and doesn't return the request queue.

The following aren't supported and return `400 Bad Request`:

- Combining a request property with `supportedHosts`, `elementTypes`, or `platform`.
- The `eq`, `gt`, or `lt` operator on `lastModifiedDateTime`, or more than one `lastModifiedDateTime` bound in the same direction, such as two `ge` bounds.
- The `or`, `ne`, and `contains` operators.
- `$count` with a request filter.

The request properties aren't sortable.

`requestType` and `requestStatus` are evolvable enumerations, so a later version of the service can return a member that your client doesn't recognize. For more information, see [Handling future members in evolvable enumerations](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations).

#### Paging a filtered collection

Paging is server-driven, so the service determines how many entries each page contains. Treat `@odata.nextLink` as an opaque URL: request it exactly as it's returned, without adding or modifying query options.

Important

For paged responses, use `@odata.nextLink` as the continuation signal. Continue requesting the opaque `@odata.nextLink` until it's absent. Don't infer completion from a response body when an `@odata.nextLink` is present.

Responses to a request that filters on a request property don't include an `@odata.count` property. For more information, see [Paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [copilotPackage](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage) objects in the response body.

### Examples

#### Example 1: List all packages

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Diligent Teams Document Uploader",
      "type": "external",
      "shortDescription": "Allows direct upload of documents from Microsoft Office into Diligent Teams for sharing",
      "isBlocked": false,
      "supportedHosts": ["outlook", "word", "excel", "powerPoint"],
      "lastModifiedDateTime": "2023-11-20T19:02:02.241Z",
      "publisher": "Diligent Corporation",
      "availableTo": "all",
      "deployedTo": "none",
      "elementTypes": ["officeAddIn"],
      "platform": "web",
      "version": "1.0.0",
      "manifestVersion": "1.1",
      "manifestId": "diligent-teams-uploader",
      "appId": "aaaaaaaa-1111-2222-3333-bbbbbbbbbbbb",
      "assetId": "asset-00001"
    }
  ]
}
```

#### Example 2: List packages filtered by supported host

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=supportedHosts/any(h:h eq 'Word')
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=supportedHosts/any(h:h eq 'Word')
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-cb65-505a-3d42-156df75a4xxy",
      "displayName": "Contoso Document Formatter",
      "type": "external",
      "shortDescription": "Formats Word documents according to company style guide",
      "isBlocked": false,
      "supportedHosts": ["Word"],
      "lastModifiedDateTime": "2025-10-06T00:07:20.1467852Z",
      "availableTo": "all",
      "deployedTo": "all"
    }
  ]
}
```

#### Example 3: List packages filtered by element type

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=elementTypes/any(h:h eq 'OfficeAddIns')
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=elementTypes/any(h:h eq 'OfficeAddIns')
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-505a-3492-9871-134df75a4xxy",
      "displayName": "Northwind Traders Account Lookup",
      "type": "external",
      "shortDescription": "Look up customer account details in Outlook and add them to email",
      "isBlocked": false,
      "supportedHosts": ["Outlook"],
      "lastModifiedDateTime": "2025-10-06T00:07:20.1467852Z",
      "availableTo": "all",
      "deployedTo": "all"
    }
  ]
}
```

#### Example 4: List packages by last updated date/time

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=lastModifiedDateTime ge 2026-01-01T00:00:00.0000000Z
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=lastModifiedDateTime ge 2026-01-01T00:00:00.0000000Z
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Contoso HR Agent",
      "type": "custom",
      "shortDescription": "Agent that can answer HR questions",
      "isBlocked": false,
      "supportedHosts": ["Copilot"],
      "lastModifiedDateTime": "2026-01-06T00:07:20.1467852Z",
      "availableTo": "all",
      "deployedTo": "all"
    }
  ]
}
```

#### Example 5: List all agents

To list all agents, use a filter for `supportedHosts` that contains `Copilot`

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=supportedHosts/any(h:h eq 'Copilot')
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=supportedHosts/any(h:h eq 'Copilot')
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Contoso HR Agent",
      "type": "custom",
      "shortDescription": "Agent that can answer HR questions",
      "isBlocked": false,
      "supportedHosts": ["Copilot"],
      "lastModifiedDateTime": "2026-01-06T00:07:20.1467852Z",
      "availableTo": "all",
      "deployedTo": "all"
    }
  ]
}
```

#### Example 6: List packages that users requested

##### Request

The following example shows a request that returns the packages with an open request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=requestStatus eq 'pending'
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=requestStatus eq 'pending'
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Contoso HR Agent",
      "type": "custom",
      "shortDescription": "Agent that can answer HR questions",
      "isBlocked": false,
      "supportedHosts": ["Copilot"],
      "lastModifiedDateTime": "2026-08-06T00:07:20.1467852Z",
      "availableTo": "none",
      "deployedTo": "none",
      "requestType": "publish",
      "requestStatus": "pending"
    },
    {
      "id": "P_38cd4yy2-71de-4f6b-9c05-284ef86b5zzt",
      "displayName": "Northwind Traders Account Lookup",
      "type": "external",
      "shortDescription": "Look up customer account details in Outlook and add them to email",
      "isBlocked": false,
      "supportedHosts": ["Outlook"],
      "lastModifiedDateTime": "2026-08-11T18:22:04.5510000Z",
      "availableTo": "some",
      "deployedTo": "some",
      "requestType": "update",
      "requestStatus": "pending"
    }
  ]
}
```

#### Example 7: List packages that users asked to publish

##### Request

The following example shows a request that returns only the packages that users asked to publish.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=requestType eq 'publish'
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=requestType eq 'publish'
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Contoso HR Agent",
      "type": "custom",
      "shortDescription": "Agent that can answer HR questions",
      "isBlocked": false,
      "supportedHosts": ["Copilot"],
      "lastModifiedDateTime": "2026-08-06T00:07:20.1467852Z",
      "availableTo": "none",
      "deployedTo": "none",
      "requestType": "publish",
      "requestStatus": "pending"
    }
  ]
}
```

#### Example 8: Combine both request filters

##### Request

The following example shows a request that combines the two request properties with `and`.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=requestStatus eq 'pending' and requestType eq 'publish'
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=requestStatus eq 'pending' and requestType eq 'publish'
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Contoso HR Agent",
      "type": "custom",
      "shortDescription": "Agent that can answer HR questions",
      "isBlocked": false,
      "supportedHosts": ["Copilot"],
      "lastModifiedDateTime": "2026-08-06T00:07:20.1467852Z",
      "availableTo": "none",
      "deployedTo": "none",
      "requestType": "publish",
      "requestStatus": "pending"
    }
  ]
}
```

#### Example 9: List pending requests by `lastModifiedDateTime`

##### Request

The following example shows a request that returns the packages with an open request whose `lastModifiedDateTime` value is on or after a date.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=requestStatus eq 'pending' and lastModifiedDateTime ge 2026-08-10T00:00:00.0000000Z
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=requestStatus eq 'pending' and lastModifiedDateTime ge 2026-08-10T00:00:00.0000000Z
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_38cd4yy2-71de-4f6b-9c05-284ef86b5zzt",
      "displayName": "Northwind Traders Account Lookup",
      "type": "external",
      "shortDescription": "Look up customer account details in Outlook and add them to email",
      "isBlocked": false,
      "supportedHosts": ["Outlook"],
      "lastModifiedDateTime": "2026-08-11T18:22:04.5510000Z",
      "availableTo": "some",
      "deployedTo": "some",
      "requestType": "update",
      "requestStatus": "pending"
    }
  ]
}
```

#### Example 10: List a request type within a `lastModifiedDateTime` range

##### Request

The following example shows a request that returns the packages that users asked to publish, limited to those whose `lastModifiedDateTime` value falls within an inclusive range.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=requestType eq 'publish' and lastModifiedDateTime ge 2026-08-01T00:00:00.0000000Z and lastModifiedDateTime le 2026-08-31T23:59:59.9999999Z
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=requestType eq 'publish' and lastModifiedDateTime ge 2026-08-01T00:00:00.0000000Z and lastModifiedDateTime le 2026-08-31T23:59:59.9999999Z
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Contoso HR Agent",
      "type": "custom",
      "shortDescription": "Agent that can answer HR questions",
      "isBlocked": false,
      "supportedHosts": ["Copilot"],
      "lastModifiedDateTime": "2026-08-06T00:07:20.1467852Z",
      "availableTo": "none",
      "deployedTo": "none",
      "requestType": "publish",
      "requestStatus": "pending"
    }
  ]
}
```
