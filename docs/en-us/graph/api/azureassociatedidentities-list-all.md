<!-- Source: https://learn.microsoft.com/en-us/graph/api/azureassociatedidentities-list-all?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# List all \(Azure identities\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Get a list of the [azureIdentity](https://learn.microsoft.com/en-us/graph/api/resources/azureidentity?view=graph-rest-beta) objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/all
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$count`, `$top`, and `$skipToken` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [azureIdentity](https://learn.microsoft.com/en-us/graph/api/resources/azureidentity?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/all
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let all = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/all')
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
  "value": [
    {
      "@odata.type": "#microsoft.graph.azureUser",
      "id": "YWxpY2VAY29udG9zby5jb20",
      "externalId": "alice@contoso.com",
      "displayName": "alice",
      "source": {
          "@odata.type": "#microsoft.graph.aadSource",
          "domain": "contoso.com",
          "identityProviderType": "aad"
      }
    },
    {
      "@odata.type": "#microsoft.graph.azureServicePrincipal",
      "id": "NDVjM2I2YmYtNTBjNS00MmQyLWJkNmItMGNjY2ZjZmE2NjNl",
      "externalId": "45c3b6bf-50c5-42d2-bd6b-0cccfcfa663e",
      "displayName": "Test Application",
      "source": {
        "@odata.type": "#microsoft.graph.azureSource",
        "identityProviderType": "azure",
        "subscriptionId": "2c47abb7-ade6-4700-9a19-ac8c191a2ab8"
      }
    },
    {
      "@odata.type": "#microsoft.graph.azureManagedIdentity",
      "id": "YWJkNjM1ZTUtNTUyOC00NTY1LThjYWYtZjJjNjBmNGY4MGY4",
      "externalId": "abd635e5-5528-4565-8caf-f2c60f4f80f8",
      "displayName": "managedIdentity2",
      "source": {
        "@odata.type": "#microsoft.graph.azureSource",
        "identityProviderType": "azure",
        "subscriptionId": "00f7dcae-97f9-492b-af2e-36eb35b613af"
      }
    }
  ]
}
```
