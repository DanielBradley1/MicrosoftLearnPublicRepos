<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-post-members?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Add members

Namespace: microsoft.graph

Add a member to a security or Microsoft 365 [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). When using the API to add multiple members in one request, you can add up to only 20 members.

Note

This request might have replication delays for groups that were recently created. When a group is created, it can take a short time for the object to fully replicate across Microsoft Entra ID directory replicas. During this window, requests to add members to the group might return a `400 Bad Request` error with the message: *"The source resource object or one of the objects being referenced don't exist."*

To mitigate this behavior:

- **Retry after a brief delay** — wait a few seconds and retry the request. The delay is typically brief.

For more information, see [Designing for Eventual Consistency for Microsoft Entra](https://devblogs.microsoft.com/identity/designing-for-eventual-consistency-for-microsoft-entra/).

The following table shows the types of members that can be added to either security groups or Microsoft 365 groups.

| Object type | Member of security group | Member of Microsoft 365 group |
| --- | --- | --- |
| User | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) |
| Security group | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |
| Microsoft 365 group | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |
| Device | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |
| Service principal | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |
| Organizational contact | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following table shows the least privileged permission that's required by each resource type when calling this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | GroupMember.ReadWrite.All and Device.Read.All | Not supported. | GroupMember.ReadWrite.All and Device.ReadWrite.All |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | GroupMember.ReadWrite.All | Not supported. | GroupMember.ReadWrite.All |
| [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | GroupMember.ReadWrite.All and OrgContact.Read.All | Not supported. | GroupMember.ReadWrite.All and OrgContact.Read.All |
| [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | GroupMember.ReadWrite.All and Application.ReadWrite.All | Not supported. | GroupMember.ReadWrite.All and Application.ReadWrite.All |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | GroupMember.ReadWrite.All | Not supported. | GroupMember.ReadWrite.All |

Important

In delegated scenarios, the signed-in user must also be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with the `microsoft.directory/groups/members/update` role permission. The following roles are the least privileged roles that are supported for this operation, except for role-assignable groups:

- Group owners
- Directory Writers
- Groups Administrator
- Identity Governance Administrator
- User Administrator
- Exchange Administrator - only for Microsoft 365 groups
- SharePoint Administrator - only for Microsoft 365 groups
- Teams Administrator - only for Microsoft 365 groups
- Yammer Administrator - only for Microsoft 365 groups
- Intune Administrator - only for security groups

To add members to a role-assignable group, the app must also be assigned the *RoleManagement.ReadWrite.Directory* permission and the calling user must be assigned a supported Microsoft Entra role. *Privileged Role Administrator* is the least privileged role that is supported for this operation.

## HTTP request

```http
POST /groups/{group-id}/members/$ref
PATCH /groups/{group-id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

When using the `POST /groups/{group-id}/members/$ref` syntax, supply a JSON object that contains an **@odata.id** property with a reference by ID to a supported group member object type.

When using the `PATCH /groups/{group-id}` syntax, supply a JSON object that contains a **members@odata.bind** property with one or more references by IDs to a supported group member object type. That is:

- For Microsoft 365 groups, only `https://graph.microsoft.com/v1.0/directoryObjects/{id}` and `https://graph.microsoft.com/v1.0/groups/{id}` is allowed where `{id}` must be a user because only users can members of Microsoft 365 groups.
- For security groups, the following ID references are allowed:

  - `https://graph.microsoft.com/v1.0/directoryObjects/{id}` where `{id}` must belong to a user, security group, device, service principal, or organizational contact.
  - `https://graph.microsoft.com/v1.0/groups/{id}` where `{id}` must belong to another security group. Microsoft 365 groups can't be members of security groups.
  - `https://graph.microsoft.com/v1.0/devices/{id}` where `{id}` belongs to a device.
  - `https://graph.microsoft.com/v1.0/servicePrincipal/{id}` where `{id}` belongs to a service principal.
  - `https://graph.microsoft.com/v1.0/orgContact/{id}` where `{id}` belongs to an organizational contact.

## Response

If successful, this method returns a `204 No Content` response code. It returns a `400 Bad Request` response code when the object is already a member of the group, is unsupported as a group member, or when the group was recently created and hasn't fully replicated \(error message: *"The source resource object or one of the objects being referenced don't exist."* — retry after a brief delay\). It returns a `404 Not Found` response code when the object being added doesn't exist. It returns `403 Forbidden` in one of the following scenarios:

- You're attempting to add a member to a [group that can't be managed through Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/groups-overview?view=graph-rest-1.0#types-of-groups-supported-in-microsoft-graph). This API supports only security and Microsoft 365 groups.
- You're attempting to add a member you don't have permissions to add. Refer to the preceding [Permissions](#permissions) section for the permissions required to add different member types.
- You're attempting to add a member to a role-assignable group and you don't have the required permissions.

## Examples

### Example 1: Add a member to a group

#### Request

The following example shows a request that uses the **directoryObjects** reference to add a member to a group.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/groups/{group-id}/members/$ref
Content-type: application/json

{
  "@odata.id": "https://graph.microsoft.com/v1.0/directoryObjects/{id}"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ReferenceCreate
{
	OdataId = "https://graph.microsoft.com/v1.0/directoryObjects/{id}",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Groups["{group-id}"].Members.Ref.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewReferenceCreate()
odataId := "https://graph.microsoft.com/v1.0/directoryObjects/{id}"
requestBody.SetOdataId(&odataId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Groups().ByGroupId("group-id").Members().Ref().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.ReferenceCreate referenceCreate = new com.microsoft.graph.models.ReferenceCreate();
referenceCreate.setOdataId("https://graph.microsoft.com/v1.0/directoryObjects/{id}");
graphClient.groups().byGroupId("{group-id}").members().ref().post(referenceCreate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
  '@odata.id': 'https://graph.microsoft.com/v1.0/directoryObjects/{id}'
};

await client.api('/groups/{group-id}/members/$ref')
	.post(directoryObject);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ReferenceCreate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReferenceCreate();
$requestBody->setOdataId('https://graph.microsoft.com/v1.0/directoryObjects/{id}');

$graphServiceClient->groups()->byGroupId('group-id')->members()->ref()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	"@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/{id}"
}

New-MgGroupMemberByRef -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.reference_create import ReferenceCreate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReferenceCreate(
	odata_id = "https://graph.microsoft.com/v1.0/directoryObjects/{id}",
)

await graph_client.groups.by_group_id('group-id').members.ref.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Add multiple members to a group in a single request

This example shows how to add multiple members to a group with OData bind support in a PATCH operation. Up to 20 members can be added in a single request. If an error condition exists in the request body, no members are added and the appropriate response code is returned.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/groups/{group-id}
Content-type: application/json

{
  "members@odata.bind": [
    "https://graph.microsoft.com/v1.0/directoryObjects/{id}",
    "https://graph.microsoft.com/v1.0/directoryObjects/{id}",
    "https://graph.microsoft.com/v1.0/directoryObjects/{id}"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"members@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
				"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
				"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGroup()
additionalData := map[string]interface{}{
	odataBind := []string {
		"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
		"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
		"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
	}
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().ByGroupId("group-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> membersOdataBind = new LinkedList<String>();
membersOdataBind.add("https://graph.microsoft.com/v1.0/directoryObjects/{id}");
membersOdataBind.add("https://graph.microsoft.com/v1.0/directoryObjects/{id}");
membersOdataBind.add("https://graph.microsoft.com/v1.0/directoryObjects/{id}");
additionalData.put("members@odata.bind", membersOdataBind);
group.setAdditionalData(additionalData);
Group result = graphClient.groups().byGroupId("{group-id}").patch(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
  'members@odata.bind': [
    'https://graph.microsoft.com/v1.0/directoryObjects/{id}',
    'https://graph.microsoft.com/v1.0/directoryObjects/{id}',
    'https://graph.microsoft.com/v1.0/directoryObjects/{id}'
    ]
};

await client.api('/groups/{group-id}')
	.update(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$additionalData = [
	'members@odata.bind' => [
'https://graph.microsoft.com/v1.0/directoryObjects/{id}', 'https://graph.microsoft.com/v1.0/directoryObjects/{id}', 'https://graph.microsoft.com/v1.0/directoryObjects/{id}', ],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->byGroupId('group-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	"members@odata.bind" = @(
	"https://graph.microsoft.com/v1.0/directoryObjects/{id}"
"https://graph.microsoft.com/v1.0/directoryObjects/{id}"
"https://graph.microsoft.com/v1.0/directoryObjects/{id}"
)
}

Update-MgGroup -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	additional_data = {
			"members@odata_bind" : [
				"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
				"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
				"https://graph.microsoft.com/v1.0/directoryObjects/{id}",
			],
	}
)

result = await graph_client.groups.by_group_id('group-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of the id of the directoryObject, user, or group object you want to add.

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

## Related content

- [Add member to team](https://learn.microsoft.com/en-us/graph/api/team-post-members?view=graph-rest-1.0)
- [Update member's role in team](https://learn.microsoft.com/en-us/graph/api/team-update-members?view=graph-rest-1.0)
- [Remove member from team](https://learn.microsoft.com/en-us/graph/api/team-delete-members?view=graph-rest-1.0)
