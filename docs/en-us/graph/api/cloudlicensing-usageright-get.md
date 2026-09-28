<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-usageright-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Get usageRight

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the properties and relationships of a [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) or [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta).

## Permissions

The following tables show the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Permissions to get a **usageRight** for a user:

```http
GET /me/cloudLicensing/usageRights/{usageRightId}
GET /users/{userId}/cloudLicensing/usageRights/{usageRightId}
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User-UsageRight.Read | User.Read, User.Read.All, User.ReadWrite, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All, User-CloudLicensing.Read.All, User-CloudLicensing.Read, User-UsageRight.Read.All, User-UsageRight.Read |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User-UsageRight.Read.All | User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All, User-CloudLicensing.Read.All, User-UsageRight.Read.All |

Permissions to get a **usageRight** for a group:

```http
GET /groups/{groupId}/cloudLicensing/usageRights/{usageRightId}
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-UsageRight.Read.All | Directory.Read.All, Directory.ReadWrite.All, Group-CloudLicensing.Read, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, User.Read.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-UsageRight.Read.All | Directory.Read.All, Directory.ReadWrite.All, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, User.Read.All, User.ReadWrite.All |

## HTTP request

To get a usage right for the signed-in user using delegated \(`/me`\) permissions:

```http
GET /me/cloudLicensing/usageRights/{usageRightId}
```

To get a usage right for a specific user or group using either delegated or application permissions:

```http
GET /users/{userId}/cloudLicensing/usageRights/{usageRightId}
GET /groups/{groupId}/cloudLicensing/usageRights/{usageRightId}
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Get a usageRight for a user

The following example shows how to get a usage right for a user.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/usageRights/i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let usageRight = await client.api('/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/usageRights/i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3')
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
  "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
  "id": "i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3",
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
```

### Example 2: Get a usageRight for a group

The following example shows how to get a usage right for a group.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```msgraph
GET https://graph.microsoft.com/beta/groups/1003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights/j6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby4
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let usageRight = await client.api('/groups/1003985b-dfc1-4f42-97d4-65f70a335ca8/cloudLicensing/usageRights/j6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby4')
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
  "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
  "id": "j6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby4",
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
```

### Example 3: Get a usageRight with assignments for a user

The following example shows how to get a usage right and its assignments for a user.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
GET https://graph.microsoft.com/beta/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/usageRights/i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3?$expand=assignments($select=id)
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let usageRight = await client.api('/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/usageRights/i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3')
	.version('beta')
	.expand('assignments($select=id)')
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
  "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
  "id": "i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3",
  "skuId": "639dec6b-bb19-468b-871c-c5c441c4b0cb",
  "skuPartNumber": "Microsoft_365_Copilot",
  "services": [
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "user,group",
      "planId": "fe6c28b3-d468-44ea-bbd0-a10a5167435c",
      "planName": "COPILOT_STUDIO_IN_COPILOT_FOR_M365"
    }
  ],
  "assignments": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "405ee855-dd74-f695-8d7e-be35a6788fe8"
    }
  ]
}
```

### Example 4: Get a usageRight with allotments for a user

The following example shows how to get a usage right and its allotments for a user.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [JavaScript](#tabpanel_4_javascript)

```http
GET https://graph.microsoft.com/beta/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/usageRights/i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3?$expand=allotments($select=id,allottedUnits,consumedUnits,subscriptions)
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let usageRight = await client.api('/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/usageRights/i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3')
	.version('beta')
	.expand('allotments($select=id,allottedUnits,consumedUnits,subscriptions)')
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
  "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
  "id": "i6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby3",
  "skuId": "639dec6b-bb19-468b-871c-c5c441c4b0cb",
  "skuPartNumber": "Microsoft_365_Copilot",
  "services": [
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "user,group",
      "planId": "fe6c28b3-d468-44ea-bbd0-a10a5167435c",
      "planName": "COPILOT_STUDIO_IN_COPILOT_FOR_M365"
    }
  ],
  "allotments": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
      "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
      "allottedUnits": 100,
      "consumedUnits": 50,
      "subscriptions": [
        {
          "@odata.type": "#microsoft.graph.cloudLicensing.subscription",
          "subscriptionId": "f196adf8-75fa-8e4f-c61d-42d8114de4f4",
          "nextLifecycleDate": "2025-09-30T00:00:00.000Z",
          "startDate": "2025-07-18T00:00:00.000Z",
          "state": "active",
          "tags": "none"
        }
      ]
    }
  ]
}
```
