<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-allotment-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Get allotment

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of an [allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Permissions to get an **allotment** as an admin:

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudLicensing.Read | Directory.Read.All, Directory.ReadWrite.All, CloudLicensing.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudLicensing.Read.All | Directory.Read.All, Directory.ReadWrite.All |

```http
GET /admin/cloudLicensing/allotments/{allotmentId}
GET /admin/cloudLicensing/assignments/{assignmentId}/allotment
```

Permissions to get an **allotment** for a user:

```http
GET /users/{userId}/cloudLicensing/assignments/{assignmentId}/allotment
GET /me/cloudLicensing/assignments/{assignmentId}/allotment
GET /users/{userId}/cloudLicensing/waitingMembers/{waitingMemberId}/allotment
GET /me/cloudLicensing/waitingMembers/{waitingMemberId}/allotment
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User-CloudLicensing.Read | CloudLicensing.Read, CloudLicensing.Read.All, User-CloudLicensing.Read.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User-CloudLicensing.Read.All | CloudLicensing.Read.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

Permissions to get an **allotment** for a group:

```http
GET /groups/{groupId}/cloudLicensing/assignments/{assignmentId}/allotment
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-CloudLicensing.Read | CloudLicensing.Read, CloudLicensing.Read.All, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-CloudLicensing.Read.All | CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

## HTTP request

To get an allotment for the signed-in user using delegated \(`/me`\) permissions:

```http
GET /me/cloudLicensing/assignments/{assignmentId}/allotment
GET /me/cloudLicensing/waitingMembers/{waitingMemberId}/allotment
```

To get an allotment using either delegated or application permissions:

```http
GET /admin/cloudLicensing/allotments/{allotmentId}
GET /admin/cloudLicensing/assignments/{assignmentId}/allotment
GET /groups/{groupId}/cloudLicensing/assignments/{assignmentId}/allotment
GET /users/{userId}/cloudLicensing/assignments/{assignmentId}/allotment
GET /users/{userId}/cloudLicensing/waitingMembers/{waitingMemberId}/allotment
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

If successful, this method returns a `200 OK` response code and a [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.CloudLicensing.Allotments["{allotment-id}"].GetAsync();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
allotments, err := graphClient.Admin().CloudLicensing().Allotments().ByAllotmentId("allotment-id").Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.cloudlicensing.Allotment result = graphClient.admin().cloudLicensing().allotments().byAllotmentId("{allotment-id}").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let allotment = await client.api('/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->cloudLicensing()->allotments()->byAllotmentId('allotment-id')->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.cloud_licensing.allotments.by_allotment_id('allotment-id').get()
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
  "value": {
    "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
    "id": "fde42873-30b6-436b-b361-21af5a6b84ae",
    "allottedUnits": 100,
    "assignableTo": "user,group",
    "consumedUnits": 84,
    "services": [
      {
        "@odata.type": "#microsoft.graph.cloudLicensing.service",
        "assignableTo": "user,group",
        "planId": "f4f2f6de-6830-442b-a433-e92249faebe2",
        "planName": "TeamsEss"
      }
    ],
    "skuId": "f245ecc8-75af-4f8e-b61f-27d8114de5f3",
    "skuPartNumber": "Teams_Ess",
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
}
```
