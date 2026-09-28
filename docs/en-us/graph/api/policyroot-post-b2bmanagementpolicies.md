<!-- Source: https://learn.microsoft.com/en-us/graph/api/policyroot-post-b2bmanagementpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Create b2bManagementPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.B2BManagementPolicy | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.B2BManagementPolicy | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Administrator* is the only role supported for this operation.

## HTTP request

```http
POST /policies/b2bManagementPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) object.

You can specify the following properties when creating a **b2bManagementPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and Time when the policy object was deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). Optional. |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for a policy. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). Required. |
| description | String | Description for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). Required. |
| displayName | String | Display name for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). Required. |
| isOrganizationDefault | Boolean | If set to true, activates this policy. There can be many policies for the same policy type, but only one can be activated as the organization default. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/policies/b2bManagementPolicies
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.b2bManagementPolicy",
  "deletedDateTime": null,
  "description": "Policy used for B2B features",
  "displayName": "Policy1",
  "definition": [
    "{
      'B2BManagementPolicy':{
        'version':1,
        'invitationsAllowedAndBlocked':{
                        'AllowedDomains': ['microsoft.com', 'live.com'],
                        'BlockedDomains': ['bing.com']
                    }
        }
    }"
  ],
  "isOrganizationDefault": true
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const b2bManagementPolicy = {
  '@odata.type': '#microsoft.graph.b2bManagementPolicy',
  deletedDateTime: null,
  description: 'Policy used for B2B features',
  displayName: 'Policy1',
  definition: [
    "{
      \'B2BManagementPolicy\':{
        \'version\':1,
        \'invitationsAllowedAndBlocked\':{
                        \'AllowedDomains\': [\'microsoft.com\', \'live.com\'],
                        \'BlockedDomains\': [\'bing.com\']
                    }
        }
    }"
  ],
  isOrganizationDefault: true
};

await client.api('/policies/b2bManagementPolicies')
	.version('beta')
	.post(b2bManagementPolicy);
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
  "@odata.type": "#microsoft.graph.b2bManagementPolicy",
  "id": "f596ef0d-42f9-0359-1aaa-12d02b38802a",
  "deletedDateTime": null,
  "description": "Policy used for B2B features",
  "displayName": "Policy1",
  "definition": [
    "{
      'B2BManagementPolicy':{
        'version':1,
        'invitationsAllowedAndBlocked':{
                        'AllowedDomains': ['microsoft.com', 'live.com'],
                        'BlockedDomains': ['bing.com']
                    }
        }
    }"
  ],
  "isOrganizationDefault": true
}
```
