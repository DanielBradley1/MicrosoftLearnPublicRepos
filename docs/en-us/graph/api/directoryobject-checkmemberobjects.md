<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmemberobjects?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-03-17 -->

# directoryObject: checkMemberObjects

Namespace: microsoft.graph

Check for membership in a list of group IDs, administrative unit IDs, or directory role IDs, for the IDs of the specified

- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0)
- [organizational contact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0)
- [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0)
- [directory object](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

This method is transitive.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Memberships for a directory object

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | Directory.ReadWrite.All |

Note

The *Directory.\** permissions allow you to retrieve any supported directory object type via this API. To retrieve only a specific type, you can use permissions specific to the resource.

### Memberships for the signed-in user

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Read | User.Read.All, Directory.Read.All, User.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

### Memberships for other users

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.ReadBasic.All and GroupMember.Read.All | User.Read.All, Directory.Read.All, User.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User.ReadBasic.All and GroupMember.Read.All | User.Read.All, Directory.Read.All, User.ReadWrite.All, Directory.ReadWrite.All |

### Memberships for a group

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | GroupMember.Read.All | Group.Read.All, Directory.Read.All, Group.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | GroupMember.Read.All | Group.Read.All, Directory.Read.All, Group.ReadWrite.All, Directory.ReadWrite.All |

### Memberships for a service principal

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.Read.All | Directory.Read.All, Application.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.Read.All | Directory.Read.All, Application.ReadWrite.All, Directory.ReadWrite.All |

### Memberships for an organizational contact

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | Directory.ReadWrite.All |

### Memberships for a device

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Device.Read.All | Device.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Device.Read.All | Device.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

## HTTP request

Memberships for a directory object.

```http
POST /directoryObjects/{id}/checkMemberObjects
```

Memberships for the signed-in user.

```http
POST /me/checkMemberObjects
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Memberships for other users.

```http
POST /users/{id | userPrincipalName}/checkMemberObjects
```

Memberships for a group.

```http
POST /groups/{id}/checkMemberObjects
```

Memberships for a service principal.

```http
POST /servicePrincipals/{id}/checkMemberObjects
```

Memberships for an organizational contact.

```http
POST /contacts/{id}/checkMemberObjects
```

Memberships for a device.

```http
POST /devices/{id}/checkMemberObjects
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| ids | String collection | A collection that contains the object IDs of the groups, administrative units, directory roles, or roleTemplate IDs of directory roles, in which to check membership. You can specify up to 20 objects. |

## Response

If successful, this method returns a `200 OK` response code and a new String collection object in the response body.

## Examples

The following is an example of how to call this API.

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
POST https://graph.microsoft.com/v1.0/me/checkMemberObjects
Content-type: application/json

{
  "ids": [
    "80a963dd-84af-4eb8-b2a6-781e444d4fb0",
    "62e90394-69f5-4237-9190-012177145e10",
    "86a64f51-3a64-4cc6-a8c8-6b8f000c0f52",
    "ac38546e-ddf3-437a-ac5c-27a94cd7a0f1"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.CheckMemberObjects;

var requestBody = new CheckMemberObjectsPostRequestBody
{
	Ids = new List<string>
	{
		"80a963dd-84af-4eb8-b2a6-781e444d4fb0",
		"62e90394-69f5-4237-9190-012177145e10",
		"86a64f51-3a64-4cc6-a8c8-6b8f000c0f52",
		"ac38546e-ddf3-437a-ac5c-27a94cd7a0f1",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.CheckMemberObjects.PostAsCheckMemberObjectsPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

requestBody := graphusers.NewItemCheckMemberObjectsPostRequestBody()
ids := []string {
	"80a963dd-84af-4eb8-b2a6-781e444d4fb0",
	"62e90394-69f5-4237-9190-012177145e10",
	"86a64f51-3a64-4cc6-a8c8-6b8f000c0f52",
	"ac38546e-ddf3-437a-ac5c-27a94cd7a0f1",
}
requestBody.SetIds(ids)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
checkMemberObjects, err := graphClient.Me().CheckMemberObjects().PostAsCheckMemberObjectsPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.checkmemberobjects.CheckMemberObjectsPostRequestBody checkMemberObjectsPostRequestBody = new com.microsoft.graph.users.item.checkmemberobjects.CheckMemberObjectsPostRequestBody();
LinkedList<String> ids = new LinkedList<String>();
ids.add("80a963dd-84af-4eb8-b2a6-781e444d4fb0");
ids.add("62e90394-69f5-4237-9190-012177145e10");
ids.add("86a64f51-3a64-4cc6-a8c8-6b8f000c0f52");
ids.add("ac38546e-ddf3-437a-ac5c-27a94cd7a0f1");
checkMemberObjectsPostRequestBody.setIds(ids);
var result = graphClient.me().checkMemberObjects().post(checkMemberObjectsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const string = {
  ids: [
    '80a963dd-84af-4eb8-b2a6-781e444d4fb0',
    '62e90394-69f5-4237-9190-012177145e10',
    '86a64f51-3a64-4cc6-a8c8-6b8f000c0f52',
    'ac38546e-ddf3-437a-ac5c-27a94cd7a0f1'
  ]
};

await client.api('/me/checkMemberObjects')
	.post(string);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\CheckMemberObjects\CheckMemberObjectsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CheckMemberObjectsPostRequestBody();
$requestBody->setIds(['80a963dd-84af-4eb8-b2a6-781e444d4fb0', '62e90394-69f5-4237-9190-012177145e10', '86a64f51-3a64-4cc6-a8c8-6b8f000c0f52', 'ac38546e-ddf3-437a-ac5c-27a94cd7a0f1', 	]);

$result = $graphServiceClient->me()->checkMemberObjects()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users.Actions

$params = @{
	ids = @(
	"80a963dd-84af-4eb8-b2a6-781e444d4fb0"
"62e90394-69f5-4237-9190-012177145e10"
"86a64f51-3a64-4cc6-a8c8-6b8f000c0f52"
"ac38546e-ddf3-437a-ac5c-27a94cd7a0f1"
)
}

# A UPN can also be used as -UserId.
Confirm-MgUserMemberObject -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.check_member_objects.check_member_objects_post_request_body import CheckMemberObjectsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CheckMemberObjectsPostRequestBody(
	ids = [
		"80a963dd-84af-4eb8-b2a6-781e444d4fb0",
		"62e90394-69f5-4237-9190-012177145e10",
		"86a64f51-3a64-4cc6-a8c8-6b8f000c0f52",
		"ac38546e-ddf3-437a-ac5c-27a94cd7a0f1",
	],
)

result = await graph_client.me.check_member_objects.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    "80a963dd-84af-4eb8-b2a6-781e444d4fb0", 
    "62e90394-69f5-4237-9190-012177145e10"
  ]
}
```
