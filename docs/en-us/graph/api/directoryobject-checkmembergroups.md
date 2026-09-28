<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmembergroups?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# directoryObject: checkMemberGroups

Namespace: microsoft.graph

Check for membership in a specified list of [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) IDs, and return from that list the IDs of groups where a specified object is a member. The specified object can be of one of the following types:

- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0)
- [organizational contact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0)
- [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0)
- [directory object](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0)

This function is transitive.

You can check up to a maximum of 20 groups per request. This function supports all groups provisioned in Microsoft Entra ID. Because Microsoft 365 groups cannot contain other groups, membership in a Microsoft 365 group is always direct.

Important

Microsoft Graph evaluates the **groupIds** collection as a single request. If the request is invalid \(for example, a malformed group ID\), the entire request fails. If the caller doesn't have access to evaluate certain groups \(for example, groups with hidden membership\), the response might include only the groups that the caller is authorized to evaluate.

Note

Response time depends on your tenant's directory structure, including group nesting depth and membership size. Microsoft Graph doesn't publish latency targets for transitive membership APIs.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Group memberships for a directory object

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | Directory.ReadWrite.All |

Note

The *Directory.\** permissions allow you to retrieve any supported directory object type via this API. To retrieve only a specific type, you can use permissions specific to the resource.

### Group memberships for the signed-in user

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Read | User.ReadBasic.All and GroupMember.Read.All, User.Read.All and GroupMember.Read.All, User.ReadBasic.All and Group.Read.All, User.Read.All and Group.Read.All, Directory.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

### Group memberships for other users

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.ReadBasic.All and GroupMember.Read.All | User.Read.All and GroupMember.Read.All, User.ReadBasic.All and Group.Read.All, User.Read.All and Group.Read.All, Directory.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User.ReadBasic.All and GroupMember.Read.All | User.Read.All and GroupMember.Read.All, User.Read.All and Group.Read.All, Directory.Read.All |

### Group memberships for a group

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | GroupMember.Read.All | Group.Read.All, Directory.Read.All, Group.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | GroupMember.Read.All | Group.Read.All, Directory.Read.All, Group.ReadWrite.All, Directory.ReadWrite.All |

### Group memberships for a service principal

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.Read.All | Directory.Read.All, Application.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.Read.All | Directory.Read.All, Application.ReadWrite.All, Directory.ReadWrite.All |

### Group memberships for an organizational contact

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | Directory.ReadWrite.All |

### Group memberships for a device

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Device.Read.All | Device.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Device.Read.All | Device.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

Important

To evaluate membership in groups with [hidden membership](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#group-visibility-options), additional access is required:

- **Application permissions**: The app must have the `Member.Read.Hidden` permissions.
- **Delegated permissions**: The signed-in user must be a member of the hidden-membership group.

If neither condition is met, hidden-membership groups aren't evaluated and those group IDs are omitted from the response.

## HTTP request

Group memberships for a directory object \(user, group, service principal, or organizational contact\).

```http
POST /directoryObjects/{id}/checkMemberGroups
```

Group memberships for the signed-in user.

```http
POST /me/checkMemberGroups
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Group memberships for other users.

```http
POST /users/{id | userPrincipalName}/checkMemberGroups
```

Group memberships for a group.

```http
POST /groups/{id}/checkMemberGroups
```

Group memberships for a service principal.

```http
POST /servicePrincipals/{id}/checkMemberGroups
```

Group memberships for an organizational contact.

```http
POST /contacts/{id}/checkMemberGroups
```

Group memberships for a device.

```http
POST /devices/{id}/checkMemberGroups
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
| groupIds | String collection | A collection that contains the object IDs of the groups in which to check membership. Up to 20 groups may be specified. |

## Response

If successful, this method returns `200 OK` response code and String collection object in the response body.

## Examples

### Example 1: Check group memberships for a directory object

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/directoryObjects/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e/checkMemberGroups
Content-type: application/json

{
    "groupIds": [
        "f448435d-3ca7-4073-8152-a1fd73c0fd09",
        "bd7c6263-4dd5-4ae8-8c96-556e1c0bece6",
        "93670da6-d731-4366-94b5-abed40b6016b",
        "f5484ab1-4d4d-41ec-a9b8-754b3957bfc7",
        "c9103f26-f3cf-4004-a611-2a14e81b8f79"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryObjects.Item.CheckMemberGroups;

var requestBody = new CheckMemberGroupsPostRequestBody
{
	GroupIds = new List<string>
	{
		"f448435d-3ca7-4073-8152-a1fd73c0fd09",
		"bd7c6263-4dd5-4ae8-8c96-556e1c0bece6",
		"93670da6-d731-4366-94b5-abed40b6016b",
		"f5484ab1-4d4d-41ec-a9b8-754b3957bfc7",
		"c9103f26-f3cf-4004-a611-2a14e81b8f79",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryObjects["{directoryObject-id}"].CheckMemberGroups.PostAsCheckMemberGroupsPostResponseAsync(requestBody);
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

requestBody := graphdirectoryobjects.NewCheckMemberGroupsPostRequestBody()
groupIds := []string {
	"f448435d-3ca7-4073-8152-a1fd73c0fd09",
	"bd7c6263-4dd5-4ae8-8c96-556e1c0bece6",
	"93670da6-d731-4366-94b5-abed40b6016b",
	"f5484ab1-4d4d-41ec-a9b8-754b3957bfc7",
	"c9103f26-f3cf-4004-a611-2a14e81b8f79",
}
requestBody.SetGroupIds(groupIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
checkMemberGroups, err := graphClient.DirectoryObjects().ByDirectoryObjectId("directoryObject-id").CheckMemberGroups().PostAsCheckMemberGroupsPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directoryobjects.item.checkmembergroups.CheckMemberGroupsPostRequestBody checkMemberGroupsPostRequestBody = new com.microsoft.graph.directoryobjects.item.checkmembergroups.CheckMemberGroupsPostRequestBody();
LinkedList<String> groupIds = new LinkedList<String>();
groupIds.add("f448435d-3ca7-4073-8152-a1fd73c0fd09");
groupIds.add("bd7c6263-4dd5-4ae8-8c96-556e1c0bece6");
groupIds.add("93670da6-d731-4366-94b5-abed40b6016b");
groupIds.add("f5484ab1-4d4d-41ec-a9b8-754b3957bfc7");
groupIds.add("c9103f26-f3cf-4004-a611-2a14e81b8f79");
checkMemberGroupsPostRequestBody.setGroupIds(groupIds);
var result = graphClient.directoryObjects().byDirectoryObjectId("{directoryObject-id}").checkMemberGroups().post(checkMemberGroupsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const string = {
    groupIds: [
        'f448435d-3ca7-4073-8152-a1fd73c0fd09',
        'bd7c6263-4dd5-4ae8-8c96-556e1c0bece6',
        '93670da6-d731-4366-94b5-abed40b6016b',
        'f5484ab1-4d4d-41ec-a9b8-754b3957bfc7',
        'c9103f26-f3cf-4004-a611-2a14e81b8f79'
    ]
};

await client.api('/directoryObjects/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e/checkMemberGroups')
	.post(string);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\Item\CheckMemberGroups\CheckMemberGroupsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CheckMemberGroupsPostRequestBody();
$requestBody->setGroupIds(['f448435d-3ca7-4073-8152-a1fd73c0fd09', 'bd7c6263-4dd5-4ae8-8c96-556e1c0bece6', '93670da6-d731-4366-94b5-abed40b6016b', 'f5484ab1-4d4d-41ec-a9b8-754b3957bfc7', 'c9103f26-f3cf-4004-a611-2a14e81b8f79', 	]);

$result = $graphServiceClient->directoryObjects()->byDirectoryObjectId('directoryObject-id')->checkMemberGroups()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

$params = @{
	groupIds = @(
	"f448435d-3ca7-4073-8152-a1fd73c0fd09"
"bd7c6263-4dd5-4ae8-8c96-556e1c0bece6"
"93670da6-d731-4366-94b5-abed40b6016b"
"f5484ab1-4d4d-41ec-a9b8-754b3957bfc7"
"c9103f26-f3cf-4004-a611-2a14e81b8f79"
)
}

Confirm-MgDirectoryObjectMemberGroup -DirectoryObjectId $directoryObjectId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directoryobjects.item.check_member_groups.check_member_groups_post_request_body import CheckMemberGroupsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CheckMemberGroupsPostRequestBody(
	group_ids = [
		"f448435d-3ca7-4073-8152-a1fd73c0fd09",
		"bd7c6263-4dd5-4ae8-8c96-556e1c0bece6",
		"93670da6-d731-4366-94b5-abed40b6016b",
		"f5484ab1-4d4d-41ec-a9b8-754b3957bfc7",
		"c9103f26-f3cf-4004-a611-2a14e81b8f79",
	],
)

result = await graph_client.directory_objects.by_directory_object_id('directoryObject-id').check_member_groups.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(Edm.String)",
    "value": [
        "f448435d-3ca7-4073-8152-a1fd73c0fd09",
        "93670da6-d731-4366-94b5-abed40b6016b",
        "f5484ab1-4d4d-41ec-a9b8-754b3957bfc7",
        "c9103f26-f3cf-4004-a611-2a14e81b8f79"
    ]
}
```

### Example 2: Check group memberships for the signed-in user

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/checkMemberGroups
Content-type: application/json

{
  "groupIds": [
        "fee2c45b-915a-4a64b130f4eb9e75525e",
        "4fe90ae065a-478b9400e0a0e1cbd540"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.CheckMemberGroups;

var requestBody = new CheckMemberGroupsPostRequestBody
{
	GroupIds = new List<string>
	{
		"fee2c45b-915a-4a64b130f4eb9e75525e",
		"4fe90ae065a-478b9400e0a0e1cbd540",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.CheckMemberGroups.PostAsCheckMemberGroupsPostResponseAsync(requestBody);
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

requestBody := graphusers.NewItemCheckMemberGroupsPostRequestBody()
groupIds := []string {
	"fee2c45b-915a-4a64b130f4eb9e75525e",
	"4fe90ae065a-478b9400e0a0e1cbd540",
}
requestBody.SetGroupIds(groupIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
checkMemberGroups, err := graphClient.Me().CheckMemberGroups().PostAsCheckMemberGroupsPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.checkmembergroups.CheckMemberGroupsPostRequestBody checkMemberGroupsPostRequestBody = new com.microsoft.graph.users.item.checkmembergroups.CheckMemberGroupsPostRequestBody();
LinkedList<String> groupIds = new LinkedList<String>();
groupIds.add("fee2c45b-915a-4a64b130f4eb9e75525e");
groupIds.add("4fe90ae065a-478b9400e0a0e1cbd540");
checkMemberGroupsPostRequestBody.setGroupIds(groupIds);
var result = graphClient.me().checkMemberGroups().post(checkMemberGroupsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const string = {
  groupIds: [
        'fee2c45b-915a-4a64b130f4eb9e75525e',
        '4fe90ae065a-478b9400e0a0e1cbd540'
  ]
};

await client.api('/me/checkMemberGroups')
	.post(string);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\CheckMemberGroups\CheckMemberGroupsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CheckMemberGroupsPostRequestBody();
$requestBody->setGroupIds(['fee2c45b-915a-4a64b130f4eb9e75525e', '4fe90ae065a-478b9400e0a0e1cbd540', 	]);

$result = $graphServiceClient->me()->checkMemberGroups()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users.Actions

$params = @{
	groupIds = @(
	"fee2c45b-915a-4a64b130f4eb9e75525e"
"4fe90ae065a-478b9400e0a0e1cbd540"
)
}

# A UPN can also be used as -UserId.
Confirm-MgUserMemberGroup -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.check_member_groups.check_member_groups_post_request_body import CheckMemberGroupsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CheckMemberGroupsPostRequestBody(
	group_ids = [
		"fee2c45b-915a-4a64b130f4eb9e75525e",
		"4fe90ae065a-478b9400e0a0e1cbd540",
	],
)

result = await graph_client.me.check_member_groups.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(Edm.String)",
  "value": [
        "fee2c45b-915a-4a64-b130-f4eb9e75525e"
  ]
}
```
