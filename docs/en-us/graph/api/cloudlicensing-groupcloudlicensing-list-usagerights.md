<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-groupcloudlicensing-list-usagerights?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-21 -->

# List usageRights for group

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) objects granted to a group.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-UsageRight.Read.All | Directory.Read.All, Directory.ReadWrite.All, Group-CloudLicensing.Read, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, User.Read.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-UsageRight.Read.All | Directory.Read.All, Directory.ReadWrite.All, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, User.Read.All, User.ReadWrite.All |

## HTTP request

```http
GET /groups/{groupId}/cloudLicensing/usageRights
```

## Optional query parameters

This method supports the `$select`, `$top`, `$expand`, and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The following examples show how to get usage rights information for groups based on specific filters:

```http
GET /groups/0003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights?$filter=skuId eq 639dec6b-bb19-468b-871c-c5c441c4b0cb
GET /groups/0003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights?$filter=skuId in (639dec6b-bb19-468b-871c-c5c441c4b0cb, a403ebcc-fae0-4ca2-8c8c-7a907fd6c235)
GET /groups/0003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights?$filter=services/any(c:c/planId eq 113feb6c-3fe4-4440-bddc-54d774bf0318)
GET /groups/0003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights?$filter=services/any(c:c/planId in (113feb6c-3fe4-4440-bddc-54d774bf0318, 2049e525-b859-401b-b2a0-e0a31c4b1fe4))
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) objects in the response body.

## Examples

### Example 1: Get all usage rights for a group

The following example shows how to get all usage rights granted to a group.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/groups/0003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let usageRights = await client.api('/groups/0003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights')
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
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
      "id": "1e373a1d-1f05-28cf-bfc0-ee0ecfd3db15",
      "skuId": "639dec6b-bb19-468b-871c-c5c441c4b0cb",
      "skuPartNumber": "Microsoft_365_Copilot",
      "services": [
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,group",
          "planId": "fe6c28b3-d468-44ea-bbd0-a10a5167435c",
          "planName": "COPILOT_STUDIO_IN_COPILOT_FOR_M365"
        }
      ]
    }
  ]
}
```

### Example 2: Get all usage rights for a group with a specific service plan

The following example shows how to get all usage rights granted to a group for a specific service plan.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```msgraph
GET https://graph.microsoft.com/beta/groups/0003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights?$filter=services/any(c:c/planId eq 113feb6c-3fe4-4440-bddc-54d774bf0318)
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let usageRights = await client.api('/groups/0003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights')
	.version('beta')
	.filter('services/any(c:c/planId eq 113feb6c-3fe4-4440-bddc-54d774bf0318)')
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
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
      "id": "5bbc716a-f73f-4cc1-bf16-53d38b407b8f",
      "skuId": "75398b2a-b060-4057-9ae2-9eb00ef68579",
      "skuPartNumber": "Copilot_Pro",
      "services": [
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "group",
          "planId": "113feb6c-3fe4-4440-bddc-54d774bf0318",
          "planName": "EXCHANGE_S_FOUNDATION"
        }
      ]
    }
  ]
}
```
