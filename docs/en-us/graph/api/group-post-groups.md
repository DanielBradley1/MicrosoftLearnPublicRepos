<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-post-groups?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# Create group

Namespace: microsoft.graph

Create a new [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) as specified in the request body. You can create the following types of groups:

- Microsoft 365 group \(unified group\)
- Security group

This operation returns by default only a subset of the properties for each group. These default properties are noted in the [Properties](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties) section.

To get properties that are *not* returned by default, do a [GET operation](https://learn.microsoft.com/en-us/graph/api/group-get?view=graph-rest-1.0) and specify the properties in a `$select` OData query option.

> **Note**: Although Microsoft Teams is built on Microsoft 365 groups, you can't currently create a team via this API. You can use the other group APIs to manage a team that has been created in the Microsoft Teams UI.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.ReadWrite.All | Directory.ReadWrite.All, Group-PreferredDataLocation.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group.Create | Directory.ReadWrite.All, Group-PreferredDataLocation.ReadWrite.All, Group.ReadWrite.All |

For an app, create a group with owners or members while it has the *Group.Create* permission, the app must have the privileges to read the object type that it wants to assign as the group owner or member. Therefore:

- The app can assign itself as the group's owner or member.
- To create the group with users as owners or members, the app must have at least the *User.Read.All* permission.
- To create the group with other service principals as owners or members, the app must have at least the *Application.Read.All* permission.
- To create the group with either users or service principals as owners or members, the app must have at least the *Directory.Read.All* permission.

## HTTP request

```http
POST /groups
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). Specify other writable properties as necessary for your group.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name to display in the address book for the group. Maximum length: 256 characters. Required. |
| mailEnabled | Boolean | Set to `true` for mail-enabled groups. Required. |
| mailNickname | String | The mail alias for the group, unique for Microsoft 365 groups in the organization. Maximum length is 64 characters. This property can contain only characters in the [ASCII character set 0 - 127](https://learn.microsoft.com/en-us/office/vba/language/reference/user-interface-help/character-set-0127) except the following characters: ` @ () \\ [] " ; : <> , SPACE`. Required. |
| securityEnabled | Boolean | Set to `true` for security-enabled groups, including Microsoft 365 groups. Required. **Note:** Groups created using the Microsoft Entra admin center or the Azure portal always have **securityEnabled** initially set to `true`. |

Important

- Creating a group using the **Group.Create** application permission without specifying owners creates the group anonymously and the group isn't modifiable. Add owners to the group while creating it so the owners can manage the group.
- Creating a Microsoft 365 group in an app-only context and without specifying owners creates the group anonymously. Doing so can result in the associated SharePoint Online site not being created automatically until further manual action is taken.
- Creating a Microsoft 365 or security group in a delegated context, signed in as a non-admin user, and without specifying owners automatically adds the calling user as the group owner. An admin user is automatically added as the group owner of a Microsoft 365 group they create but not of a security group.
- A non-admin user can't add themselves to the group owners collection. For more information, see the related [known issue](https://learn.microsoft.com/en-us/graph/known-issues#non-admin-user-cant-add-self-as-group-owner-during-group-creation-or-update).
- The following properties can't be set in the initial POST request and must be set in a subsequent PATCH request: **accessType**, **allowExternalSenders**, **autoSubscribeNewMembers**, **hideFromAddressLists**, **hideFromOutlookClients**, **isFavorite**, **isSubscribedByMail**, **unseenConversationsCount**, **unseenCount**, **unseenMessagesCount**.

### groupTypes options

Use the **groupTypes** property to control the type of group and its membership, as shown.

| Type of group | Assigned membership | Dynamic membership |
| :--- | :--- | :--- |
| Microsoft 365 \(aka unified group\) | `["Unified"]` | `["Unified","DynamicMembership"]` |
| Dynamic | `[]` \(*null*\) | `["DynamicMembership"]` |

## Response

If successful, this method returns a `201 Created` response code and a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object in the response body. The response includes only the default properties of the group.

## Examples

### Example 1: Create a Microsoft 365 group

The following example creates a Microsoft 365 group. Because the owners aren't specified, the calling user is automatically added as the owner of the group.

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
POST https://graph.microsoft.com/v1.0/groups
Content-type: application/json

{
  "description": "Self help community for library",
  "displayName": "Library Assist",
  "groupTypes": [
    "Unified"
  ],
  "mailEnabled": true,
  "mailNickname": "library",
  "securityEnabled": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	Description = "Self help community for library",
	DisplayName = "Library Assist",
	GroupTypes = new List<string>
	{
		"Unified",
	},
	MailEnabled = true,
	MailNickname = "library",
	SecurityEnabled = false,
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
description := "Self help community for library"
requestBody.SetDescription(&description) 
displayName := "Library Assist"
requestBody.SetDisplayName(&displayName) 
groupTypes := []string {
	"Unified",
}
requestBody.SetGroupTypes(groupTypes)
mailEnabled := true
requestBody.SetMailEnabled(&mailEnabled) 
mailNickname := "library"
requestBody.SetMailNickname(&mailNickname) 
securityEnabled := false
requestBody.SetSecurityEnabled(&securityEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
group.setDescription("Self help community for library");
group.setDisplayName("Library Assist");
LinkedList<String> groupTypes = new LinkedList<String>();
groupTypes.add("Unified");
group.setGroupTypes(groupTypes);
group.setMailEnabled(true);
group.setMailNickname("library");
group.setSecurityEnabled(false);
Group result = graphClient.groups().post(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
  description: 'Self help community for library',
  displayName: 'Library Assist',
  groupTypes: [
    'Unified'
  ],
  mailEnabled: true,
  mailNickname: 'library',
  securityEnabled: false
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
$requestBody->setDescription('Self help community for library');
$requestBody->setDisplayName('Library Assist');
$requestBody->setGroupTypes(['Unified', 	]);
$requestBody->setMailEnabled(true);
$requestBody->setMailNickname('library');
$requestBody->setSecurityEnabled(false);

$result = $graphServiceClient->groups()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	description = "Self help community for library"
	displayName = "Library Assist"
	groupTypes = @(
	"Unified"
)
mailEnabled = $true
mailNickname = "library"
securityEnabled = $false
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
	description = "Self help community for library",
	display_name = "Library Assist",
	group_types = [
		"Unified",
	],
	mail_enabled = True,
	mail_nickname = "library",
	security_enabled = False,
)

result = await graph_client.groups.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The value of the **preferredDataLocation** property is inherited from the group creator's preferred data location.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "b320ee12-b1cd-4cca-b648-a437be61c5cd",
      "deletedDateTime": null,
      "classification": null,
      "createdDateTime": "2018-12-22T00:51:37Z",
      "description": "Self help community for library",
      "displayName": "Library Assist",
      "groupTypes": [
          "Unified"
      ],
      "mail": "library7423@contoso.com",
      "mailEnabled": true,
      "mailNickname": "library",
      "onPremisesLastSyncDateTime": null,
      "onPremisesSecurityIdentifier": null,
      "onPremisesSyncEnabled": null,
      "preferredDataLocation": "CAN",
      "proxyAddresses": [
          "SMTP:library7423@contoso.com"
      ],
      "renewedDateTime": "2018-12-22T00:51:37Z",
      "resourceBehaviorOptions": [],
      "resourceProvisioningOptions": [],
      "securityEnabled": false,
      "visibility": "Public",
      "onPremisesProvisioningErrors": []
}
```

### Example 2: Create a group with owners and members

The following example creates a Security group with an owner and members specified. A maximum of 20 relationships, such as owners and members, can be added as part of group creation. You can subsequently add more members by using the [add member](https://learn.microsoft.com/en-us/graph/api/group-post-members?view=graph-rest-1.0) API or JSON batching.

A non-admin user can't add themselves to the group owners collection. For more information, see the related [known issue](https://learn.microsoft.com/en-us/graph/known-issues#non-admin-user-cant-add-self-as-group-owner-during-group-creation-or-update).

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
POST https://graph.microsoft.com/v1.0/groups
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
groups, err := graphClient.Groups().Post(context.Background(), requestBody, nil)
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
Group result = graphClient.groups().post(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
  description: 'Group with designated owner and members',
  displayName: 'Operations group',
  groupTypes: [
  ],
  mailEnabled: false,
  mailNickname: 'operations2019',
  securityEnabled: true,
  'owners@odata.bind': [
    'https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2'
  ],
  'members@odata.bind': [
    'https://graph.microsoft.com/v1.0/users/ff7cb387-6688-423c-8188-3da9532a73cc',
    'https://graph.microsoft.com/v1.0/users/69456242-0067-49d3-ba96-9de6f2728e14'
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

$result = $graphServiceClient->groups()->post($requestBody)->wait();
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

New-MgGroup -BodyParameter $params
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

result = await graph_client.groups.post(request_body)
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
    "@odata.id": "https://graph.microsoft.com/v2/84841066-274d-4ec0-a5c1-276be684bdd3/directoryObjects/21d05557-b7b6-418f-86fa-a3118d751be4/Microsoft.DirectoryServices.Group",
    "id": "21d05557-b7b6-418f-86fa-a3118d751be4",
    "deletedDateTime": null,
    "classification": null,
    "createdDateTime": "2021-09-21T07:09:14Z",
    "description": "Group with designated owner and members",
    "displayName": "Operations group",
    "expirationDateTime": null,
    "groupTypes": [],
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
    "renewedDateTime": "2021-09-21T07:09:14Z",
    "resourceBehaviorOptions": [],
    "resourceProvisioningOptions": [],
    "securityEnabled": true,
    "securityIdentifier": "S-1-12-1-567301463-1099937718-295959174-3827004813",
    "theme": null,
    "visibility": null,
    "onPremisesProvisioningErrors": []
}
```

### Example 3: Create a Microsoft 365 group that can be assigned to a Microsoft Entra role

#### Request

The following example shows a request. The calling user must be assigned the *RoleManagement.ReadWrite.Directory* permission to set the **isAssignableToRole** property or update the membership of such groups.

A group with **isAssignableToRole** property set to `true` can't be of dynamic membership type, its **securityEnabled** must be set to `true`, and **visibility** can only be `Private`.

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

> **Note:** A group with **isAssignableToRole** property set to `true` cannot be of dynamic membership type and cannot have an owner. For more information, see [Using a group to manage Microsoft Entra role assignments](https://go.microsoft.com/fwlink/?linkid=2103037).

#### Response

The following example shows the response. It includes only default properties. The value of the **preferredDataLocation** property is inherited from the group creator's preferred data location.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups/$entity",
    "@odata.id": "https://graph.microsoft.com/v2/84841066-274d-4ec0-a5c1-276be684bdd3/directoryObjects/55ea2e8c-757f-4f2d-be9e-53c22e8c6a54/Microsoft.DirectoryServices.Group",
    "id": "55ea2e8c-757f-4f2d-be9e-53c22e8c6a54",
    "deletedDateTime": null,
    "classification": null,
    "createdDateTime": "2021-09-21T07:23:06Z",
    "createdByAppId": "de8bc8b5-d9f9-48b1-a8ad-b748da725064",
    "organizationId": "84841066-274d-4ec0-a5c1-276be684bdd3",
    "description": "Group assignable to a role",
    "displayName": "Role assignable group",
    "expirationDateTime": null,
    "groupTypes": [
        "Unified"
    ],
    "infoCatalogs": [],
    "isAssignableToRole": true,
    "mail": "contosohelpdeskadministrators@contoso.com",
    "mailEnabled": true,
    "mailNickname": "contosohelpdeskadministrators",
    "membershipRule": null,
    "membershipRuleProcessingState": null,
    "onPremisesDomainName": null,
    "onPremisesLastSyncDateTime": null,
    "onPremisesNetBiosName": null,
    "onPremisesSamAccountName": null,
    "onPremisesSecurityIdentifier": null,
    "onPremisesSyncEnabled": null,
    "preferredDataLocation": "EU",
    "preferredLanguage": null,
    "proxyAddresses": [
        "SMTP:contosohelpdeskadministrators@contoso.com"
    ],
    "renewedDateTime": "2021-09-21T07:23:06Z",
    "resourceBehaviorOptions": [],
    "resourceProvisioningOptions": [],
    "securityEnabled": true,
    "securityIdentifier": "S-1-12-1-1441410700-1328379263-3260260030-1416268846",
    "theme": null,
    "visibility": "Private",
    "writebackConfiguration": {
        "isEnabled": null,
        "onPremisesGroupType": null
    },
    "onPremisesProvisioningErrors": []
}
```
