<!-- Source: https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list-actions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# List actions \(for an Azure authorization system\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

List the [azureAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemtypeaction?view=graph-rest-beta) objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$count`, `$top`, and `$skipToken` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [azureAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemtypeaction?view=graph-rest-beta) objects in the response body.

## Examples

### Example 1: List all actions in the Azure authorization system

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions",
  "value": [
    {
      "id": "TWljcm9zb2Z0LlN0b3JhZ2UvY2hlY2tuYW1lYXZhaWxhYmlsaXR5L3JlYWQ=",
      "externalId": "Microsoft.Storage/checknameavailability/read",
      "resourceTypes": ["checknameavailability"],
      "severity": "normal",
      "actionType": "read",
      "service": {
        "id": "Microsoft.Storage"
      }
    },
    {
      "id": "TWljcm9zb2Z0LlN0b3JhZ2UvbG9jYXRpb25zL2RlbGV0ZVZpcnR1YWxOZXR3b3JrT3JTdWJuZXRzL2FjdGlvbg==",
      "externalId": "Microsoft.Storage/locations/deleteVirtualNetworkOrSubnets/action",
      "resourceTypes": ["locations"],
      "severity": "normal",
      "actionType": null,
      "service": {
        "id": "Microsoft.Storage"
      }
    },
    {
      "id": "TWljcm9zb2Z0LlN0b3JhZ2Uvb3BlcmF0aW9ucy9yZWFk",
      "externalId": "Microsoft.Storage/operations/read",
      "resourceTypes": ["operations"],
      "severity": "normal",
      "actionType": "read",
      "service": {
        "id": "Microsoft.Storage"
      }
    }
  ]
}
```

### Example 2: List actions for a service in the Azure authorization system

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions?$filter=service/id eq 'Microsoft.Storage'
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions')
	.version('beta')
	.filter('service/id eq \'Microsoft.Storage\'')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions?$filter=service/id eq 'Microsoft.Storage'",
  "value": [
    {
      "id": "TWljcm9zb2Z0LlN0b3JhZ2UvY2hlY2tuYW1lYXZhaWxhYmlsaXR5L3JlYWQ=",
      "externalId": "Microsoft.Storage/checknameavailability/read",
      "resourceTypes": ["checknameavailability"],
      "severity": "normal",
      "actionType": "read",
      "service": {
        "id": "Microsoft.Storage"
      }
    },
    {
      "id": "TWljcm9zb2Z0LlN0b3JhZ2UvbG9jYXRpb25zL2RlbGV0ZVZpcnR1YWxOZXR3b3JrT3JTdWJuZXRzL2FjdGlvbg==",
      "externalId": "Microsoft.Storage/locations/deleteVirtualNetworkOrSubnets/action",
      "resourceTypes": ["locations"],
      "severity": "normal",
      "actionType": null,
      "service": {
        "id": "Microsoft.Storage"
      }
    },
    {
      "id": "TWljcm9zb2Z0LlN0b3JhZ2Uvb3BlcmF0aW9ucy9yZWFk",
      "externalId": "Microsoft.Storage/operations/read",
      "resourceTypes": ["operations"],
      "severity": "normal",
      "actionType": "read",
      "service": {
        "id": "Microsoft.Storage"
      }
    }
  ]
}
```
