<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryobject-getbyids?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# directoryObject: getByIds

Namespace: microsoft.graph

Return the directory objects specified in a list of IDs. Only [a subset of user properties are returned by default in v1.0](https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#common-properties).

Some common uses for this function are to:

- Resolve IDs returned by functions \(that return collections of IDs\) such as [getMemberObjects](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmemberobjects?view=graph-rest-1.0) or [getMemberGroups](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmembergroups?view=graph-rest-1.0) to their backing directory objects.
- Resolve IDs persisted in an external store by the application to their backing directory objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | Not available. |

Important

When an application queries a relationship that returns a **directoryObject** type collection, if it doesn't have permission to read a certain resource type, members of that type are returned but with limited information. For example, only the **@odata.type** property for the object type and the **id** is returned, while other properties are indicated as `null`. With this behavior, applications can request the least privileged permissions they need, rather than rely on the set of *Directory.*\* permissions. For details, see [Limited information returned for inaccessible member objects](https://learn.microsoft.com/en-us/graph/permissions-overview#limited-information-returned-for-inaccessible-member-objects).

## HTTP request

```http
POST /directoryObjects/getByIds
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| ids | String collection | A collection of IDs for which to return objects. The IDs are GUIDs, represented as strings. You can specify up to 1000 IDs. |
| types | String collection | A collection of resource types that specifies the set of resource collections to search. If not specified, the default is [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0), which contains all of the resource types defined in the directory. Any object that derives from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) may be specified in the collection; for example: [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0), and [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) objects.  <br>  <br>To search for references to a [Cloud Solution Provider](https://partner.microsoft.com/cloud-solution-provider) partner organization specify [directoryObjectPartnerReference](https://learn.microsoft.com/en-us/graph/api/resources/directoryobjectpartnerreference?view=graph-rest-1.0). If not specified, the default is [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0), which contains all of the resource types defined in the directory, except for references to a [Cloud Solution Provider](https://partner.microsoft.com/cloud-solution-provider) partner organization.  <br>  <br>The values are not case-sensitive. |

## Response

If successful, this method returns a `200 OK` response code and a string collection object in the response body.

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
POST https://graph.microsoft.com/v1.0/directoryObjects/getByIds
Content-type: application/json

{
    "ids": [
        "84b80893-8749-40a3-97b7-68513b600544",
        "5d6059b6-368d-45f8-91e1-8e07d485f1d0",
        "0b944de3-e0fc-4774-a49a-b135213725ef",
        "b75a5ab2-fe55-4463-bd31-d21ad555c6e0"
    ],
    "types": [
        "user",
        "group",
        "device"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryObjects.GetByIds;

var requestBody = new GetByIdsPostRequestBody
{
	Ids = new List<string>
	{
		"84b80893-8749-40a3-97b7-68513b600544",
		"5d6059b6-368d-45f8-91e1-8e07d485f1d0",
		"0b944de3-e0fc-4774-a49a-b135213725ef",
		"b75a5ab2-fe55-4463-bd31-d21ad555c6e0",
	},
	Types = new List<string>
	{
		"user",
		"group",
		"device",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryObjects.GetByIds.PostAsGetByIdsPostResponseAsync(requestBody);
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

requestBody := graphdirectoryobjects.NewGetByIdsPostRequestBody()
ids := []string {
	"84b80893-8749-40a3-97b7-68513b600544",
	"5d6059b6-368d-45f8-91e1-8e07d485f1d0",
	"0b944de3-e0fc-4774-a49a-b135213725ef",
	"b75a5ab2-fe55-4463-bd31-d21ad555c6e0",
}
requestBody.SetIds(ids)
types := []string {
	"user",
	"group",
	"device",
}
requestBody.SetTypes(types)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getByIds, err := graphClient.DirectoryObjects().GetByIds().PostAsGetByIdsPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directoryobjects.getbyids.GetByIdsPostRequestBody getByIdsPostRequestBody = new com.microsoft.graph.directoryobjects.getbyids.GetByIdsPostRequestBody();
LinkedList<String> ids = new LinkedList<String>();
ids.add("84b80893-8749-40a3-97b7-68513b600544");
ids.add("5d6059b6-368d-45f8-91e1-8e07d485f1d0");
ids.add("0b944de3-e0fc-4774-a49a-b135213725ef");
ids.add("b75a5ab2-fe55-4463-bd31-d21ad555c6e0");
getByIdsPostRequestBody.setIds(ids);
LinkedList<String> types = new LinkedList<String>();
types.add("user");
types.add("group");
types.add("device");
getByIdsPostRequestBody.setTypes(types);
var result = graphClient.directoryObjects().getByIds().post(getByIdsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
    ids: [
        '84b80893-8749-40a3-97b7-68513b600544',
        '5d6059b6-368d-45f8-91e1-8e07d485f1d0',
        '0b944de3-e0fc-4774-a49a-b135213725ef',
        'b75a5ab2-fe55-4463-bd31-d21ad555c6e0'
    ],
    types: [
        'user',
        'group',
        'device'
    ]
};

await client.api('/directoryObjects/getByIds')
	.post(directoryObject);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\GetByIds\GetByIdsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetByIdsPostRequestBody();
$requestBody->setIds(['84b80893-8749-40a3-97b7-68513b600544', '5d6059b6-368d-45f8-91e1-8e07d485f1d0', '0b944de3-e0fc-4774-a49a-b135213725ef', 'b75a5ab2-fe55-4463-bd31-d21ad555c6e0', 	]);
$requestBody->setTypes(['user', 'group', 'device', 	]);

$result = $graphServiceClient->directoryObjects()->getByIds()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

$params = @{
	ids = @(
	"84b80893-8749-40a3-97b7-68513b600544"
"5d6059b6-368d-45f8-91e1-8e07d485f1d0"
"0b944de3-e0fc-4774-a49a-b135213725ef"
"b75a5ab2-fe55-4463-bd31-d21ad555c6e0"
)
types = @(
"user"
"group"
"device"
)
}

Get-MgDirectoryObjectById -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directoryobjects.get_by_ids.get_by_ids_post_request_body import GetByIdsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetByIdsPostRequestBody(
	ids = [
		"84b80893-8749-40a3-97b7-68513b600544",
		"5d6059b6-368d-45f8-91e1-8e07d485f1d0",
		"0b944de3-e0fc-4774-a49a-b135213725ef",
		"b75a5ab2-fe55-4463-bd31-d21ad555c6e0",
	],
	types = [
		"user",
		"group",
		"device",
	],
)

result = await graph_client.directory_objects.get_by_ids.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryObjects",
    "value": [
      {
        "@odata.type": "#microsoft.graph.user",
        "id": "84b80893-8749-40a3-97b7-68513b600544",
        "displayName": "Trevor Jones"
      },
      {
        "@odata.type": "#microsoft.graph.user",
        "id": "5d6059b6-368d-45f8-91e1-8e07d485f1d0",
        "displayName": "Billy Smith"
      },
      {
         "@odata.type": "#microsoft.graph.group",
         "id": "0b944de3-e0fc-4774-a49a-b135213725ef",
         "description": "Pineview School Staff",
         "groupTypes": [
             "Unified"
         ]
      },
      {
         "@odata.type": "#microsoft.graph.device",
         "id": "b75a5ab2-fe55-4463-bd31-d21ad555c6e0",
         "displayName": "e8ba4e98c000002",
         "deviceId": "4c299165-6e8f-4b45-a5ba-c5d250a707ff"
      }
    ]
}
```
