<!-- Source: https://learn.microsoft.com/en-us/graph/api/application-setverifiedpublisher?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# application: setVerifiedPublisher

Namespace: microsoft.graph

Set the [verifiedPublisher](https://learn.microsoft.com/en-us/graph/api/resources/verifiedpublisher?view=graph-rest-1.0) on an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). For more information, including prerequisites to setting a verified publisher, see [Publisher verification](https://learn.microsoft.com/en-us/azure/active-directory/develop/publisher-verification-overview).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- A non-admin member or guest who has default user permissions, unless [the tenant admin restricted access](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#restrict-member-users-default-permissions).
- Application Developer. This role can create apps even when the admin restricted access to members and guests. The principal with this role is assigned ownership of the app they create.
- Directory Writers. This role can update extension properties.
- Hybrid Identity Administrator. This role can update only basic properties.
- Security Administrator
- Cloud Application Administrator
- Application Administrator

In delegated scenarios using work or school accounts, the following privileges are supported for managing agent identity blueprints:

- The signed-in user is the owner, or
- The signed-in user is assigned the *Agent ID Administrator* role.

## HTTP request

You can address the application using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

```http
POST /applications/{id}/setVerifiedPublisher
POST /applications(appId='{appId}')/setVerifiedPublisher
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide the following required properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| verifiedPublisherId | string | The Microsoft Partner Network ID \(MPNID\) of the verified publisher to be set on the application, from the publisher's Partner Center account. |

## Response

If successful, this method returns a `204 No Content` response code.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/applications/{id}/setVerifiedPublisher
Content-type: application/json

{
    "verifiedPublisherId": "1234567"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Applications.Item.SetVerifiedPublisher;

var requestBody = new SetVerifiedPublisherPostRequestBody
{
	VerifiedPublisherId = "1234567",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Applications["{application-id}"].SetVerifiedPublisher.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphapplications "github.com/microsoftgraph/msgraph-sdk-go/applications"
	  //other-imports
)

requestBody := graphapplications.NewSetVerifiedPublisherPostRequestBody()
verifiedPublisherId := "1234567"
requestBody.SetVerifiedPublisherId(&verifiedPublisherId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Applications().ByApplicationId("application-id").SetVerifiedPublisher().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.applications.item.setverifiedpublisher.SetVerifiedPublisherPostRequestBody setVerifiedPublisherPostRequestBody = new com.microsoft.graph.applications.item.setverifiedpublisher.SetVerifiedPublisherPostRequestBody();
setVerifiedPublisherPostRequestBody.setVerifiedPublisherId("1234567");
graphClient.applications().byApplicationId("{application-id}").setVerifiedPublisher().post(setVerifiedPublisherPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setVerifiedPublisher = {
    verifiedPublisherId: '1234567'
};

await client.api('/applications/{id}/setVerifiedPublisher')
	.post(setVerifiedPublisher);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Applications\Item\SetVerifiedPublisher\SetVerifiedPublisherPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SetVerifiedPublisherPostRequestBody();
$requestBody->setVerifiedPublisherId('1234567');

$graphServiceClient->applications()->byApplicationId('application-id')->setVerifiedPublisher()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	verifiedPublisherId = "1234567"
}

Set-MgApplicationVerifiedPublisher -ApplicationId $applicationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.applications.item.set_verified_publisher.set_verified_publisher_post_request_body import SetVerifiedPublisherPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SetVerifiedPublisherPostRequestBody(
	verified_publisher_id = "1234567",
)

await graph_client.applications.by_application_id('application-id').set_verified_publisher.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
