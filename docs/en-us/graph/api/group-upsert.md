<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-upsert?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-12 -->

# Upsert group

Namespace: microsoft.graph

Create a new [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object if it doesn't exist, or update the properties of an existing [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object. You can create or update the following types of group:

- Microsoft 365 group \(unified group\)
- Security group

By default, this operation returns only a subset of the properties for each group. For a list of properties that are returned by default, see the [Properties](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties) section of the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) resource. To get properties that are *not* returned by default, do a [GET operation](https://learn.microsoft.com/en-us/graph/api/group-get?view=graph-rest-1.0) and specify the properties in a `$select` OData query option.

> **Note**: To create a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0), first create a group then add a team to it. For more information, see [Create team](https://learn.microsoft.com/en-us/graph/api/team-put-teams?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group.ReadWrite.All | Directory.ReadWrite.All |

In order for an app with Group.Create permission to create a group with owners or members, it must have the privileges to read the object type that it wants to assign as the group owner or member. Therefore:

- The app can assign itself as the group's owner or member.
- To create the group with users as owners or members, the app must have at least the *User.Read.All* permission.
- To create the group with other service principals as owners or members, the app must have at least the *Application.Read.All* permission.
- To create the group with either users or service principals as owners or members, the app must have at least the *Directory.Read.All* permission.

## HTTP request

```http
PATCH /groups(uniqueName='uniqueName')
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Prefer | `create-if-missing`. Required for upsert behavior, otherwise the request is treated as an update operation. |

## Request body

In the request body, supply a JSON representation of the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). Specify other writable properties as necessary for your group on creation or update.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name to display in the address book for the group. Maximum length is 256 characters. Required. |
| mailEnabled | Boolean | Set to `true` for mail-enabled groups. Required. |
| mailNickname | String | The mail alias for the group, unique for Microsoft 365 groups in the organization. Maximum length is 64 characters. This property can contain only characters in the [ASCII character set 0 - 127](https://learn.microsoft.com/en-us/office/vba/language/reference/user-interface-help/character-set-0127) except the following characters: ` @ () \\ [] " ; : <> , SPACE`. Required. |
| securityEnabled | Boolean | Set to `true` for security-enabled groups, including Microsoft 365 groups. Required. **Note:** Groups created using the Microsoft Entra admin center or the Azure portal always have **securityEnabled** initially set to `true`. |

Important

- Creating a group using the **Group.Create** application permission without specifying owners creates the group anonymously and the group isn't modifiable. Add owners to the group while creating it to specify owners who can modify the group.
- Creating a Microsoft 365 group programmatically with an app-only context and without specifying owners creates the group anonymously. Doing so can result in the associated SharePoint Online site not being created automatically until further manual action is taken.
- A non-admin user can't add themselves to the group owners collection. For more information, see the related [known issue](https://learn.microsoft.com/en-us/graph/known-issues#non-admin-user-cant-add-self-as-group-owner-during-group-creation-or-update).
- The following properties can't be set in the initial POST request and must be set in a subsequent PATCH request: **accessType**, **allowExternalSenders**, **autoSubscribeNewMembers**, **hideFromAddressLists**, **hideFromOutlookClients**, **isFavorite**, **isSubscribedByMail**, **unseenConversationsCount**, **unseenCount**, **unseenMessagesCount**.

Because the **group** resource supports [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview), you can add custom properties with your own data to the group while creating it.

### groupTypes options

Use the **groupTypes** property to control the type of group and its membership, as shown.

| Type of group | Assigned membership | Dynamic membership |
| :--- | :--- | :--- |
| Microsoft 365 \(aka unified group\) | `["Unified"]` | `["Unified","DynamicMembership"]` |
| Dynamic | `[]` \(*null*\) | `["DynamicMembership"]` |

## Response

If an object with the **uniqueName** doesn't exist, this method returns a `201 Created` response code and a new [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object in the response body.

If an object with **uniqueName** doesn't exist and the `Prefer: create-if-missing` header is *not* specified, this method returns a `404 Not Found` error code.

If an object with the **uniqueName** already exists, this method updates the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object and returns a `204 No Content` response code.

## Examples

### Example 1: Create a Microsoft 365 group if it doesn't exist

The following example creates a Microsoft 365 group because a group with the specified **uniqueName** value doesn't exist. Because the owners aren't specified, the calling user is automatically added as the owner of the group.

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
PATCH https://graph.microsoft.com/v1.0/groups(uniqueName='uniqueName')
Content-type: application/json
Prefer: create-if-missing

{
  "description": "Self help community for golf",
  "displayName": "Golf Assist",
  "groupTypes": [
    "Unified"
  ],
  "mailEnabled": true,
  "mailNickname": "golfassist",
  "securityEnabled": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	Description = "Self help community for golf",
	DisplayName = "Golf Assist",
	GroupTypes = new List<string>
	{
		"Unified",
	},
	MailEnabled = true,
	MailNickname = "golfassist",
	SecurityEnabled = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.GroupsWithUniqueName("{uniqueName}").PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "create-if-missing");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphgroupswithuniquename "github.com/microsoftgraph/msgraph-sdk-go/groupswithuniquename"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "create-if-missing")

configuration := &graphgroupswithuniquename.GroupsWithUniqueNameRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewGroup()
description := "Self help community for golf"
requestBody.SetDescription(&description) 
displayName := "Golf Assist"
requestBody.SetDisplayName(&displayName) 
groupTypes := []string {
	"Unified",
}
requestBody.SetGroupTypes(groupTypes)
mailEnabled := true
requestBody.SetMailEnabled(&mailEnabled) 
mailNickname := "golfassist"
requestBody.SetMailNickname(&mailNickname) 
securityEnabled := false
requestBody.SetSecurityEnabled(&securityEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
uniqueName := "{uniqueName}"
groups, err := graphClient.GroupsWithUniqueName(&uniqueName).Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
group.setDescription("Self help community for golf");
group.setDisplayName("Golf Assist");
LinkedList<String> groupTypes = new LinkedList<String>();
groupTypes.add("Unified");
group.setGroupTypes(groupTypes);
group.setMailEnabled(true);
group.setMailNickname("golfassist");
group.setSecurityEnabled(false);
Group result = graphClient.groupsWithUniqueName("{uniqueName}").patch(group, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "create-if-missing");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups(uniqueName='{uniqueName}')\GroupsWithUniqueNameRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$requestBody->setDescription('Self help community for golf');
$requestBody->setDisplayName('Golf Assist');
$requestBody->setGroupTypes(['Unified', 	]);
$requestBody->setMailEnabled(true);
$requestBody->setMailNickname('golfassist');
$requestBody->setSecurityEnabled(false);
$requestConfiguration = new GroupsWithUniqueNameRequestBuilderPatchRequestConfiguration();
$headers = [
		'Prefer' => 'create-if-missing',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->groupsWithUniqueName('{uniqueName}', )->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	description = "Self help community for golf"
	displayName = "Golf Assist"
	groupTypes = @(
	"Unified"
)
mailEnabled = $true
mailNickname = "golfassist"
securityEnabled = $false
}

Update-MgGroupByUniqueName -BodyParameter $params -UniqueName $uniqueNameId 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups(unique_name='{unique_name}').groups_with_unique_name_request_builder import GroupsWithUniqueNameRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	description = "Self help community for golf",
	display_name = "Golf Assist",
	group_types = [
		"Unified",
	],
	mail_enabled = True,
	mail_nickname = "golfassist",
	security_enabled = False,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "create-if-missing")


result = await graph_client.groups_with_unique_name("{uniqueName}").patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The value of the **preferredDataLocation** property is inherited from the group creator's preferred data location.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups/$entity",
    "id": "45b7d2e7-b882-4a80-ba97-10b7a63b8fa4",
    "deletedDateTime": null,
    "classification": null,
    "createdDateTime": "2018-12-22T02:21:05Z",
    "description": "Self help community for golf",
    "displayName": "Golf Assist",
    "expirationDateTime": null,
    "groupTypes": [
        "Unified"
    ],
    "isAssignableToRole": null,
    "mail": "golfassist@contoso.com",
    "mailEnabled": true,
    "mailNickname": "golfassist",
    "membershipRule": null,
    "membershipRuleProcessingState": null,
    "onPremisesLastSyncDateTime": null,
    "onPremisesSecurityIdentifier": null,
    "onPremisesSyncEnabled": null,
    "preferredDataLocation": "CAN",
    "preferredLanguage": null,
    "proxyAddresses": [
        "SMTP:golfassist@contoso.onmicrosoft.com"
    ],
    "renewedDateTime": "2018-12-22T02:21:05Z",
    "resourceBehaviorOptions": [],
    "resourceProvisioningOptions": [],
    "securityEnabled": false,
    "securityIdentifier": "S-1-12-1-1753967289-1089268234-832641959-555555555",
    "theme": null,
    "visibility": "Public",
    "uniqueName": "uniqueName",
    "onPremisesProvisioningErrors": []
}
```

### Example 2: Create a security group with an owner and members if it doesn't exist

The following example creates a security group with an owner and members specified because a group with the specified **uniqueName** value doesn't exist. A maximum of 20 relationships, such as owners and members, can be added as part of group creation. You can subsequently add multiple more members by using the [add member](https://learn.microsoft.com/en-us/graph/api/group-post-members?view=graph-rest-1.0) API or JSON batching.

A non-admin user can't add themselves to the group owners collection. For more information, see the related [known issue](https://learn.microsoft.com/en-us/graph/known-issues#non-admin-user-cant-add-self-as-group-owner-during-group-creation-or-update).

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
PATCH https://graph.microsoft.com/v1.0/groups(uniqueName='uniqueName')
Content-Type: application/json

{
  "description": "Group with designated owner and members",
  "displayName": "Operations group",
  "groupTypes": [
  ],
  "mailEnabled": false,
  "mailNickname": "operations2019",
  "securityEnabled": true,
  "owners@odata.bind": [
    "https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2"
  ],
  "members@odata.bind": [
    "https://graph.microsoft.com/v1.0/users/ff7cb387-6688-423c-8188-3da9532a73cc",
    "https://graph.microsoft.com/v1.0/users/69456242-0067-49d3-ba96-9de6f2728e14"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	Description = "Group with designated owner and members",
	DisplayName = "Operations group",
	GroupTypes = new List<string>
	{
	},
	MailEnabled = false,
	MailNickname = "operations2019",
	SecurityEnabled = true,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"owners@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2",
			}
		},
		{
			"members@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/v1.0/users/ff7cb387-6688-423c-8188-3da9532a73cc",
				"https://graph.microsoft.com/v1.0/users/69456242-0067-49d3-ba96-9de6f2728e14",
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.GroupsWithUniqueName("{uniqueName}").PatchAsync(requestBody);
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
description := "Group with designated owner and members"
requestBody.SetDescription(&description) 
displayName := "Operations group"
requestBody.SetDisplayName(&displayName) 
groupTypes := []string {

}
requestBody.SetGroupTypes(groupTypes)
mailEnabled := false
requestBody.SetMailEnabled(&mailEnabled) 
mailNickname := "operations2019"
requestBody.SetMailNickname(&mailNickname) 
securityEnabled := true
requestBody.SetSecurityEnabled(&securityEnabled) 
additionalData := map[string]interface{}{
	odataBind := []string {
		"https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2",
	}
	odataBind := []string {
		"https://graph.microsoft.com/v1.0/users/ff7cb387-6688-423c-8188-3da9532a73cc",
		"https://graph.microsoft.com/v1.0/users/69456242-0067-49d3-ba96-9de6f2728e14",
	}
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
uniqueName := "{uniqueName}"
groups, err := graphClient.GroupsWithUniqueName(&uniqueName).Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
group.setDescription("Group with designated owner and members");
group.setDisplayName("Operations group");
LinkedList<String> groupTypes = new LinkedList<String>();
group.setGroupTypes(groupTypes);
group.setMailEnabled(false);
group.setMailNickname("operations2019");
group.setSecurityEnabled(true);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> ownersOdataBind = new LinkedList<String>();
ownersOdataBind.add("https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2");
additionalData.put("owners@odata.bind", ownersOdataBind);
LinkedList<String> membersOdataBind = new LinkedList<String>();
membersOdataBind.add("https://graph.microsoft.com/v1.0/users/ff7cb387-6688-423c-8188-3da9532a73cc");
membersOdataBind.add("https://graph.microsoft.com/v1.0/users/69456242-0067-49d3-ba96-9de6f2728e14");
additionalData.put("members@odata.bind", membersOdataBind);
group.setAdditionalData(additionalData);
Group result = graphClient.groupsWithUniqueName("{uniqueName}").patch(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$requestBody->setDescription('Group with designated owner and members');
$requestBody->setDisplayName('Operations group');
$requestBody->setGroupTypes([	]);
$requestBody->setMailEnabled(false);
$requestBody->setMailNickname('operations2019');
$requestBody->setSecurityEnabled(true);
$additionalData = [
	'owners@odata.bind' => [
'https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2', ],
	'members@odata.bind' => [
'https://graph.microsoft.com/v1.0/users/ff7cb387-6688-423c-8188-3da9532a73cc', 'https://graph.microsoft.com/v1.0/users/69456242-0067-49d3-ba96-9de6f2728e14', ],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groupsWithUniqueName('{uniqueName}', )->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	description = "Group with designated owner and members"
	displayName = "Operations group"
	groupTypes = @(
	)
	mailEnabled = $false
	mailNickname = "operations2019"
	securityEnabled = $true
	"owners@odata.bind" = @(
	"https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2"
)
"members@odata.bind" = @(
"https://graph.microsoft.com/v1.0/users/ff7cb387-6688-423c-8188-3da9532a73cc"
"https://graph.microsoft.com/v1.0/users/69456242-0067-49d3-ba96-9de6f2728e14"
)
}

Update-MgGroupByUniqueName -BodyParameter $params -UniqueName $uniqueNameId 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	description = "Group with designated owner and members",
	display_name = "Operations group",
	group_types = [
	],
	mail_enabled = False,
	mail_nickname = "operations2019",
	security_enabled = True,
	additional_data = {
			"owners@odata_bind" : [
				"https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2",
			],
			"members@odata_bind" : [
				"https://graph.microsoft.com/v1.0/users/ff7cb387-6688-423c-8188-3da9532a73cc",
				"https://graph.microsoft.com/v1.0/users/69456242-0067-49d3-ba96-9de6f2728e14",
			],
	}
)

result = await graph_client.groups_with_unique_name("{uniqueName}").patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows a successful response. It includes only default properties. You can subsequently get the **owners** or **members** navigation properties of the group to verify the owner or members. The value of the **preferredDataLocation** property is inherited from the group creator's preferred data location.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups/$entity",
    "@odata.id": "https://graph.microsoft.com/v2/84841066-274d-4ec0-a5c1-276be684bdd3/directoryObjects/1226170d-83d5-49b8-99ab-d1ab3d91333e/Microsoft.DirectoryServices.Group",
    "id": "1226170d-83d5-49b8-99ab-d1ab3d91333e",
    "deletedDateTime": null,
    "classification": null,
    "createdDateTime": "2021-09-21T07:14:44Z",
    "createdByAppId": "de8bc8b5-d9f9-48b1-a8ad-b748da725064",
    "organizationId": "84841066-274d-4ec0-a5c1-276be684bdd3",
    "description": "Group with designated owner and members",
    "displayName": "Operations group",
    "expirationDateTime": null,
    "groupTypes": [],
    "infoCatalogs": [],
    "isAssignableToRole": null,
    "mail": null,
    "mailEnabled": false,
    "mailNickname": "operations2019",
    "membershipRule": null,
    "membershipRuleProcessingState": null,
    "onPremisesDomainName": null,
    "onPremisesLastSyncDateTime": null,
    "onPremisesNetBiosName": null,
    "onPremisesSamAccountName": null,
    "onPremisesSecurityIdentifier": null,
    "onPremisesSyncEnabled": null,
    "preferredDataLocation": null,
    "preferredLanguage": null,
    "proxyAddresses": [],
    "renewedDateTime": "2021-09-21T07:14:44Z",
    "resourceBehaviorOptions": [],
    "resourceProvisioningOptions": [],
    "securityEnabled": true,
    "securityIdentifier": "S-1-12-1-304486157-1236829141-2882644889-1043566909",
    "theme": null,
    "uniqueName": "uniqueName",
    "visibility": null,
    "writebackConfiguration": {
        "isEnabled": null,
        "onPremisesGroupType": null
    },
    "onPremisesProvisioningErrors": []
}
```

### Example 3: Update an existing group

In this example, the specified group already exists, so the operation is treated as an update.

A non-admin user can't add themselves to the group owners collection. For more information, see the related [known issue](https://learn.microsoft.com/en-us/graph/known-issues#non-admin-user-cant-add-self-as-group-owner-during-group-creation-or-update).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/groups
Content-Type: application/json

{
    "description": "Group assignable to a role",
    "displayName": "Role assignable group",
    "groupTypes": [
        "Unified"
    ],
    "isAssignableToRole": true,
    "mailEnabled": true,
    "securityEnabled": true,
    "mailNickname": "contosohelpdeskadministrators",
    "owners@odata.bind": [
        "https://graph.microsoft.com/v1.0/users/99e44b05-c10b-4e95-a523-e2732bbaba1e"
    ],
    "members@odata.bind": [
        "https://graph.microsoft.com/v1.0/users/6ea91a8d-e32e-41a1-b7bd-d2d185eed0e0",
        "https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	Description = "Group assignable to a role",
	DisplayName = "Role assignable group",
	GroupTypes = new List<string>
	{
		"Unified",
	},
	IsAssignableToRole = true,
	MailEnabled = true,
	SecurityEnabled = true,
	MailNickname = "contosohelpdeskadministrators",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"owners@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/v1.0/users/99e44b05-c10b-4e95-a523-e2732bbaba1e",
			}
		},
		{
			"members@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/v1.0/users/6ea91a8d-e32e-41a1-b7bd-d2d185eed0e0",
				"https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups.PostAsync(requestBody);
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
description := "Group assignable to a role"
requestBody.SetDescription(&description) 
displayName := "Role assignable group"
requestBody.SetDisplayName(&displayName) 
groupTypes := []string {
	"Unified",
}
requestBody.SetGroupTypes(groupTypes)
isAssignableToRole := true
requestBody.SetIsAssignableToRole(&isAssignableToRole) 
mailEnabled := true
requestBody.SetMailEnabled(&mailEnabled) 
securityEnabled := true
requestBody.SetSecurityEnabled(&securityEnabled) 
mailNickname := "contosohelpdeskadministrators"
requestBody.SetMailNickname(&mailNickname) 
additionalData := map[string]interface{}{
	odataBind := []string {
		"https://graph.microsoft.com/v1.0/users/99e44b05-c10b-4e95-a523-e2732bbaba1e",
	}
	odataBind := []string {
		"https://graph.microsoft.com/v1.0/users/6ea91a8d-e32e-41a1-b7bd-d2d185eed0e0",
		"https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
	}
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
group.setDescription("Group assignable to a role");
group.setDisplayName("Role assignable group");
LinkedList<String> groupTypes = new LinkedList<String>();
groupTypes.add("Unified");
group.setGroupTypes(groupTypes);
group.setIsAssignableToRole(true);
group.setMailEnabled(true);
group.setSecurityEnabled(true);
group.setMailNickname("contosohelpdeskadministrators");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> ownersOdataBind = new LinkedList<String>();
ownersOdataBind.add("https://graph.microsoft.com/v1.0/users/99e44b05-c10b-4e95-a523-e2732bbaba1e");
additionalData.put("owners@odata.bind", ownersOdataBind);
LinkedList<String> membersOdataBind = new LinkedList<String>();
membersOdataBind.add("https://graph.microsoft.com/v1.0/users/6ea91a8d-e32e-41a1-b7bd-d2d185eed0e0");
membersOdataBind.add("https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e");
additionalData.put("members@odata.bind", membersOdataBind);
group.setAdditionalData(additionalData);
Group result = graphClient.groups().post(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
    description: 'Group assignable to a role',
    displayName: 'Role assignable group',
    groupTypes: [
        'Unified'
    ],
    isAssignableToRole: true,
    mailEnabled: true,
    securityEnabled: true,
    mailNickname: 'contosohelpdeskadministrators',
    'owners@odata.bind': [
        'https://graph.microsoft.com/v1.0/users/99e44b05-c10b-4e95-a523-e2732bbaba1e'
    ],
    'members@odata.bind': [
        'https://graph.microsoft.com/v1.0/users/6ea91a8d-e32e-41a1-b7bd-d2d185eed0e0',
        'https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e'
    ]
};

await client.api('/groups')
	.post(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$requestBody->setDescription('Group assignable to a role');
$requestBody->setDisplayName('Role assignable group');
$requestBody->setGroupTypes(['Unified', 	]);
$requestBody->setIsAssignableToRole(true);
$requestBody->setMailEnabled(true);
$requestBody->setSecurityEnabled(true);
$requestBody->setMailNickname('contosohelpdeskadministrators');
$additionalData = [
	'owners@odata.bind' => [
'https://graph.microsoft.com/v1.0/users/99e44b05-c10b-4e95-a523-e2732bbaba1e', ],
	'members@odata.bind' => [
'https://graph.microsoft.com/v1.0/users/6ea91a8d-e32e-41a1-b7bd-d2d185eed0e0', 'https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e', ],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	description = "Group assignable to a role"
	displayName = "Role assignable group"
	groupTypes = @(
	"Unified"
)
isAssignableToRole = $true
mailEnabled = $true
securityEnabled = $true
mailNickname = "contosohelpdeskadministrators"
"owners@odata.bind" = @(
"https://graph.microsoft.com/v1.0/users/99e44b05-c10b-4e95-a523-e2732bbaba1e"
)
"members@odata.bind" = @(
"https://graph.microsoft.com/v1.0/users/6ea91a8d-e32e-41a1-b7bd-d2d185eed0e0"
"https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e"
)
}

New-MgGroup -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	description = "Group assignable to a role",
	display_name = "Role assignable group",
	group_types = [
		"Unified",
	],
	is_assignable_to_role = True,
	mail_enabled = True,
	security_enabled = True,
	mail_nickname = "contosohelpdeskadministrators",
	additional_data = {
			"owners@odata_bind" : [
				"https://graph.microsoft.com/v1.0/users/99e44b05-c10b-4e95-a523-e2732bbaba1e",
			],
			"members@odata_bind" : [
				"https://graph.microsoft.com/v1.0/users/6ea91a8d-e32e-41a1-b7bd-d2d185eed0e0",
				"https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
			],
	}
)

result = await graph_client.groups.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The value of the **preferredDataLocation** property is inherited from the group creator's preferred data location.

```http
HTTP/1.1 204 No Content
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions \(preview\)](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions \(preview\)](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
