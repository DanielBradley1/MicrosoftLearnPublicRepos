<!-- Source: https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-policies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# List policies \(for an AWS authorization system\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

List all [awsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/awspolicy?view=graph-rest-beta) objects and their properties for a specific AWS authorization system. An AWS policy is an object in AWS that defines the permissions of the associated entity or resource. When a principal, such as a user, makes a request, the policies and their associated permissions determine whether the request is allowed or denied.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies
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

If successful, this method returns a `200 OK` response code and a collection of [awsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/awspolicy?view=graph-rest-beta) objects in the response body.

## Examples

### Example 1: List all policies for an AWS account

#### Request

The following request lists all the policies for an AWS authorization system.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let policies = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies",
  "value": [
    {
      "id": "YXJuOmF3czppYW06OmF3czpwb2xpY3kvQWRtaW5pc3RyYXRvckFjY2Vzcw==",
      "externalId": "arn:aws:iam::aws:policy/AdministratorAccess",
      "displayName": "AdministratorAccess",
      "awsPolicyType": "system"
    },
    {
      "id": "YXJuOmF3czppYW06OjEyMzQ1Njc4OTAxMjpwb2xpY3kvQUFBLWxpc3RQdXRHZXRBbGxCdWNrZXRz",
      "externalId": "arn:aws:iam::123456789012:policy/AAA-listPutGetAllBuckets",
      "displayName": "AAA-listPutGetAllBuckets",
      "awsPolicyType": "custom"
    }
  ]
}
```

### Example 2: List all policies in an AWS authorization system with a specific name

#### Request

The following request lists all policies named `AdministratorAccess` in an AWS authorization system.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies?$filter=displayName eq 'AdministratorAccess'
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let policies = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies')
	.version('beta')
	.filter('displayName eq \'AdministratorAccess\'')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies",
  "value": [
    {
      "id": "YXJuOmF3czppYW06OmF3czpwb2xpY3kvQWRtaW5pc3RyYXRvckFjY2Vzcw==",
      "externalId": "arn:aws:iam::aws:policy/AdministratorAccess",
      "displayName": "AdministratorAccess",
      "awsPolicyType": "system"
    }
  ]
}
```

### Example 3: List all policies in an AWS authorization system with names containing a specific string

#### Request

The following request lists all policies in an AWS authorization system where the policy name contains the word `Buckets`.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies?$filter=contains(displayName, 'Buckets')
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let policies = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies')
	.version('beta')
	.filter('contains(displayName, \'Buckets\')')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies",
  "value": [
    {
      "id": "YXJuOmF3czppYW06OjM3NzU5NjEzMTc3NDpwb2xpY3kvQUFBLWxpc3RQdXRHZXRBbGxCdWNrZXRz",
      "externalId": "arn:aws:iam::377596131774:policy/AAA-listPutGetAllBuckets",
      "displayName": "AAA-listPutGetAllBuckets",
      "awsPolicyType": "custom"
    }
  ]
}
```

### Example 4: List all custom policies in an AWS authorization system.

#### Request

The following example requests all custom policies in an AWS authorization system.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies?$filter=type eq 'custom'
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies",
  "value": [
    {
      "id": "YXJuOmF3czppYW06OjM3NzU5NjEzMTc3NDpwb2xpY3kvQUFBLWxpc3RQdXRHZXRBbGxCdWNrZXRz",
      "externalId": "arn:aws:iam::377596131774:policy/AAA-listPutGetAllBuckets",
      "displayName": "AAA-listPutGetAllBuckets",
      "awsPolicyType": "custom"
    },
    {
      "id": "YXJuOmF3czppb2xpY3kvQzU5NjEzMTc3NDpwb2xpY3kvQUFBLWxp",
      "externalId": "arn:aws:iam::377596131774:policy/BBB-GetAllBuckets",
      "displayName": "BBB-GetAllBuckets",
      "awsPolicyType": "custom"
    }
  ]
}
```
