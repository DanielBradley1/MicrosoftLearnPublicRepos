<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryobject-getmemberobjects?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-03-17 -->

# directoryObject: getMemberObjects

Namespace: microsoft.graph

Return all IDs for the groups, administrative units, and directory roles that an object of one of the following types is a member of:

- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0)
- [organizational contact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0)
- [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0)
- [directory object](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0)

This function is transitive. Only users and role-enabled groups can be members of directory roles.

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

Memberships for a directory object

```http
POST /directoryObjects/{id}/getMemberObjects
```

Memberships for the signed-in user.

```http
POST /me/getMemberObjects
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Memberships for other user.

```http
POST /users/{id | userPrincipalName}/getMemberObjects
```

Memberships for a group

```http
POST /groups/{id}/getMemberObjects
```

Memberships for a service principal

```http
POST /servicePrincipals/{id}/getMemberObjects
```

Memberships for an organizational contact

```http
POST /contacts/{id}/getMemberObjects
```

Memberships for a device

```http
POST /devices/{id}/getMemberObjects
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| securityEnabledOnly | Boolean | `true` to specify that only security groups that the entity is a member of should be returned; `false` to specify that all groups, administrative units, and directory roles that the entity is a member of should be returned. |

## Response

If successful, this method returns `200 OK` response code and String collection object in the response body.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/directoryObjects/{object-id}/getMemberObjects
Content-type: application/json

{
  "securityEnabledOnly": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryObjects.Item.GetMemberObjects;

var requestBody = new GetMemberObjectsPostRequestBody
{
	SecurityEnabledOnly = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryObjects["{directoryObject-id}"].GetMemberObjects.PostAsGetMemberObjectsPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectoryobjects "github.com/microsoftgraph/msgraph-sdk-go/directoryobjects"
	  //other-imports
)

requestBody := graphdirectoryobjects.NewGetMemberObjectsPostRequestBody()
securityEnabledOnly := true
requestBody.SetSecurityEnabledOnly(&securityEnabledOnly) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getMemberObjects, err := graphClient.DirectoryObjects().ByDirectoryObjectId("directoryObject-id").GetMemberObjects().PostAsGetMemberObjectsPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directoryobjects.item.getmemberobjects.GetMemberObjectsPostRequestBody getMemberObjectsPostRequestBody = new com.microsoft.graph.directoryobjects.item.getmemberobjects.GetMemberObjectsPostRequestBody();
getMemberObjectsPostRequestBody.setSecurityEnabledOnly(true);
var result = graphClient.directoryObjects().byDirectoryObjectId("{directoryObject-id}").getMemberObjects().post(getMemberObjectsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const string = {
  securityEnabledOnly: true
};

await client.api('/directoryObjects/{object-id}/getMemberObjects')
	.post(string);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\Item\GetMemberObjects\GetMemberObjectsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetMemberObjectsPostRequestBody();
$requestBody->setSecurityEnabledOnly(true);

$result = $graphServiceClient->directoryObjects()->byDirectoryObjectId('directoryObject-id')->getMemberObjects()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

$params = @{
	securityEnabledOnly = $true
}

Get-MgDirectoryObjectMemberObject -DirectoryObjectId $directoryObjectId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directoryobjects.item.get_member_objects.get_member_objects_post_request_body import GetMemberObjectsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetMemberObjectsPostRequestBody(
	security_enabled_only = True,
)

result = await graph_client.directory_objects.by_directory_object_id('directoryObject-id').get_member_objects.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(Edm.String)",
    "value": [
        "fee2c45b-915a-4a64-b130-f4eb9e75525e",
        "4fe90ae7-065a-478b-9400-e0a0e1cbd540",
        "c9ee2d50-9e8a-4352-b97c-4c2c99557c22",
        "e0c3beaf-eeb4-43d8-abc5-94f037a65697"
    ]
}
```
