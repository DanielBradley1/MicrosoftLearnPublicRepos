<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groups-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-09 -->

# Manage groups in Microsoft Graph

Groups in Microsoft Graph are containers for principals like users, devices, or applications that share access to resources. They make access management easier by grouping principals instead of managing them individually.

The [group resource type](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) in Microsoft Graph provides APIs to create and manage supported group types and their functionalities.

Note

- You can only create groups using work or school accounts. Personal Microsoft accounts don't support groups.
- All group-related operations in Microsoft Graph need administrator consent.

## Types of groups supported in Microsoft Graph

Microsoft Graph supports these types of groups:

- [Microsoft 365 Groups](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/office-365-groups)
- Security groups
- Mail-enabled security groups
- Distribution groups

Note

[Dynamic distribution groups](https://learn.microsoft.com/en-us/exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups?view=exchserver-2019&preserve-view=true) aren't supported in Microsoft Graph.

The following table shows how to identify types of groups using their properties and whether they can be managed through the Microsoft Graph groups API. The core differentiators are the values in the **groupTypes**, **mailEnabled**, and **securityEnabled** properties of a group.

| Type | groupTypes | mailEnabled | securityEnabled | Managed via Microsoft Graph |
| --- | --- | --- | --- | --- |
| [Microsoft 365 Groups](#microsoft-365-groups) | `["Unified"]` | `true` | `true` or `false` | Yes |
| [Security groups](#security-groups-and-mail-enabled-security-groups) | `[]` | `false` | `true` | Yes |
| [Mail-enabled security groups](#security-groups-and-mail-enabled-security-groups) | `[]` | `true` | `true` | No \(read-only\) |
| Distribution groups | `[]` | `true` | `false` | No \(read-only\) |

For more information, see [Compare groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/compare-groups).

## Microsoft 365 Groups

Microsoft 365 Groups are designed for collaboration and provide access to shared resources like:

- Outlook conversations and calendar.
- SharePoint files and team site.
- OneNote notebook.
- Planner plans.
- Intune device management.

Here's an example of a Microsoft 365 group in JSON format:

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups/$entity",
    "id": "4c5ee71b-e6a5-4343-9e2c-4244bc7e0938",
    "displayName": "OutlookGroup101",
    "groupTypes": ["Unified"],
    "mailEnabled": true,
    "securityEnabled": false,
    "mail": "outlookgroup101@service.microsoft.com",
    "visibility": "Public"
}
```

To learn more about Microsoft 365 Groups, see [Overview of Microsoft 365 Groups in Microsoft Graph](https://learn.microsoft.com/en-us/graph/microsoft365-groups-concept-overview).

## Security groups and mail-enabled security groups

**Security groups** control access to resources. They can include users, other groups, devices, and service principals.

**Mail-enabled security groups** function like security groups but also allow email communication. These groups are read-only in Microsoft Graph. For more information, see [Manage mail-enabled security groups](https://learn.microsoft.com/en-us/exchange/recipients/mail-enabled-security-groups).

Example of a security group in JSON format:

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.group",
    "id": "f87faa71-57a8-4c14-91f0-517f54645106",
    "displayName": "SecurityGroup101",
    "groupTypes": [],
    "mailEnabled": false,
    "securityEnabled": true
}
```

## Group ownership

Groups can have one or more owners who manage the group. Owners can be users or service principals. We recommend assigning at least two owners to a group to ensure continuity.

### Ownerless group policy

When a group loses its sole owner, it becomes ownerless and can no longer be managed effectively. Use the [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) resource to configure a tenant-level policy that automatically sends actionable notification emails to active members of ownerless groups, prompting them to accept ownership. Administrators can configure the notification duration, the maximum number of members to notify, and control ownership eligibility by using security groups. For more information, see [Get ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/ownerlessgrouppolicy-get?view=graph-rest-1.0) and [Create or update ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/ownerlessgrouppolicy-upsert?view=graph-rest-1.0).

## Group membership

Groups can have static or dynamic memberships. Dynamic membership uses rules to automatically add or remove members based on their properties. Not all object types can be members of Microsoft 365 and security groups.

The following table shows the types of members that can be added to either security groups or Microsoft 365 groups.

| Object type | Member of security group | Member of Microsoft 365 group |
| --- | --- | --- |
| User | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) |
| Security group | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |
| Microsoft 365 group | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |
| Device | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |
| Service principal | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |
| Organizational contact | ![Can be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) | ![Cannot be group member](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) |

### Dynamic membership

Dynamic membership means principals are added or removed from the group based on their properties. For example, a group can be set to include all users in the "Marketing" department. When a user is added to that department, they're automatically added to the group. Similarly, if a user leaves the department, they're removed from the group.

Only users and devices can be members of a dynamic group. Dynamic membership requires a Microsoft Entra ID P1 license for each unique user in a dynamic group.

The membership rule is defined using the [Microsoft Entra ID dynamic group rule syntax](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership).

Example of a dynamic membership rule:

```json
"membershipRule": "user.department -eq \"Marketing\""
```

Dynamic membership requires the `"DynamicMembership"` value in the **groupTypes** property. The dynamic membership rule can be turned on or off through the **membershipRuleProcessingState** property. You can update a group from static membership to dynamic membership.

Example request to create a dynamic Microsoft 365 group:

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
    "description": "Marketing department folks",
    "displayName": "Marketing department",
    "groupTypes": [
        "Unified",
        "DynamicMembership"
    ],
    "mailEnabled": true,
    "mailNickname": "marketing",
    "securityEnabled": false,
    "membershipRule": "user.department -eq \"Marketing\"",
    "membershipRuleProcessingState": "on"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	Description = "Marketing department folks",
	DisplayName = "Marketing department",
	GroupTypes = new List<string>
	{
		"Unified",
		"DynamicMembership",
	},
	MailEnabled = true,
	MailNickname = "marketing",
	SecurityEnabled = false,
	MembershipRule = "user.department -eq \"Marketing\"",
	MembershipRuleProcessingState = "on",
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
description := "Marketing department folks"
requestBody.SetDescription(&description) 
displayName := "Marketing department"
requestBody.SetDisplayName(&displayName) 
groupTypes := []string {
	"Unified",
	"DynamicMembership",
}
requestBody.SetGroupTypes(groupTypes)
mailEnabled := true
requestBody.SetMailEnabled(&mailEnabled) 
mailNickname := "marketing"
requestBody.SetMailNickname(&mailNickname) 
securityEnabled := false
requestBody.SetSecurityEnabled(&securityEnabled) 
membershipRule := "user.department -eq \"Marketing\""
requestBody.SetMembershipRule(&membershipRule) 
membershipRuleProcessingState := "on"
requestBody.SetMembershipRuleProcessingState(&membershipRuleProcessingState) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
group.setDescription("Marketing department folks");
group.setDisplayName("Marketing department");
LinkedList<String> groupTypes = new LinkedList<String>();
groupTypes.add("Unified");
groupTypes.add("DynamicMembership");
group.setGroupTypes(groupTypes);
group.setMailEnabled(true);
group.setMailNickname("marketing");
group.setSecurityEnabled(false);
group.setMembershipRule("user.department -eq \"Marketing\"");
group.setMembershipRuleProcessingState("on");
Group result = graphClient.groups().post(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
    description: 'Marketing department folks',
    displayName: 'Marketing department',
    groupTypes: [
        'Unified',
        'DynamicMembership'
    ],
    mailEnabled: true,
    mailNickname: 'marketing',
    securityEnabled: false,
    membershipRule: 'user.department -eq \"Marketing\"',
    membershipRuleProcessingState: 'on'
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
$requestBody->setDescription('Marketing department folks');
$requestBody->setDisplayName('Marketing department');
$requestBody->setGroupTypes(['Unified', 'DynamicMembership', 	]);
$requestBody->setMailEnabled(true);
$requestBody->setMailNickname('marketing');
$requestBody->setSecurityEnabled(false);
$requestBody->setMembershipRule('user.department -eq \"Marketing\"');
$requestBody->setMembershipRuleProcessingState('on');

$result = $graphServiceClient->groups()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	description = "Marketing department folks"
	displayName = "Marketing department"
	groupTypes = @(
	"Unified"
"DynamicMembership"
)
mailEnabled = $true
mailNickname = "marketing"
securityEnabled = $false
membershipRule = "user.department -eq "Marketing""
membershipRuleProcessingState = "on"
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
	description = "Marketing department folks",
	display_name = "Marketing department",
	group_types = [
		"Unified",
		"DynamicMembership",
	],
	mail_enabled = True,
	mail_nickname = "marketing",
	security_enabled = False,
	membership_rule = "user.department -eq \"Marketing\"",
	membership_rule_processing_state = "on",
)

result = await graph_client.groups.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

The request returns a `201 Created` response code and the newly created group object in the response body.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups/$entity",
    "id": "6f7cd676-5445-47c4-9c2b-c47da4671da2",
    "createdDateTime": "2023-01-20T07:00:31Z",
    "description": "Marketing department folks",
    "displayName": "Marketing department",
    "groupTypes": [
        "Unified",
        "DynamicMembership"
    ],
    "mail": "marketing@contoso.com",
    "mailEnabled": true,
    "mailNickname": "marketing",
    "membershipRule": "user.department -eq \"Marketing\"",
    "membershipRuleProcessingState": "On"
}
```

## Other group settings

You can configure other settings for groups, such as:

| Setting | Description | Applies to |
| --- | --- | --- |
| [Group expiration](https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0) | Configure an expiration policy so that Microsoft 365 groups are automatically deleted after a specified period, unless renewed. | Microsoft 365 groups |
| [Group settings](https://learn.microsoft.com/en-us/graph/group-directory-settings) | Configure behaviors for groups using setting templates. Setting templates include: **Group.Unified** for Microsoft 365 group settings \(such as naming policies, guest access, and sensitivity labels\), **Group.Unified.Guest** for Microsoft 365 guest settings, **Group.Security** for cloud security group settings \(such as enabling sensitivity labels\), and **Group.Security.Policies** for cloud security settings. | Microsoft 365 groups and cloud security groups |
| [On-premises synchronization settings](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) | Configure on-premises directory synchronization settings. | Security and Microsoft 365 groups |

## Group search limitations for guests in organizations

Apps can search for groups in an organization's directory by querying the `/groups` resource \(for example, `https://graph.microsoft.com/v1.0/groups`\). This capability is available to administrators and members, but not to guests.

Guests, depending on the permissions granted to the app, can view the profile of a specific group \(for example, `https://graph.microsoft.com/v1.0/group/fc06287e-d082-4aab-9d5e-d6fd0ed7c8bc`\). However, they can't perform queries on the `/groups` resource that return multiple results.

Members generally have broader access to group resources, while guests have restricted permissions, limiting their access to certain group features. For more information, see [Compare member and guest default permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions?context=graph%2Fcontext#compare-member-and-guest-default-permissions).

With appropriate permissions, apps can access group profiles through navigation properties, such as `/groups/{id}/members`.

## Group-based licensing

Group-based licensing allows you to assign one or more product licenses to a Microsoft Entra group. Group members, including any new members, automatically inherit the licenses. When members leave the group, their licenses are automatically removed. This feature is only available for security groups and Microsoft 365 Groups with **securityEnabled** set to `true`.

For more information, see [What is group-based licensing in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/fundamentals/concept-group-based-licensing).

## Properties stored outside the main data store

Most group resource data is stored in Microsoft Entra ID, but some properties, such as **autoSubscribeNewMembers** and **allowExternalSenders**, are stored in Microsoft Exchange. These properties can't be included in the same Create or Update request body as other group properties.

Additionally, properties stored outside the main data store aren't supported for [change tracking](https://learn.microsoft.com/en-us/graph/delta-query-overview). Changes to these properties don't appear in delta query responses.

The following group properties are stored outside the main data store:  
**accessType**, **allowExternalSenders**, **autoSubscribeNewMembers**, **cloudLicensing**, **hideFromAddressLists**, **hideFromOutlookClients**, **isFavorite**, **isSubscribedByMail**, **unseenConversationsCount**, **unseenCount**, **unseenMessagesCount**, **membershipRuleProcessingStatus**, **isArchived**.

## Common use cases for the groups API

The Microsoft Graph groups API supports these common operations:

| Use case | API operations |
| --- | --- |
| **Create and manage groups** | [Create](https://learn.microsoft.com/en-us/graph/api/group-post-groups?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/group-list?view=graph-rest-1.0), [update](https://learn.microsoft.com/en-us/graph/api/group-update?view=graph-rest-1.0), and [delete](https://learn.microsoft.com/en-us/graph/api/group-delete?view=graph-rest-1.0) |
| **Manage group membership** | [List members](https://learn.microsoft.com/en-us/graph/api/group-list-members?view=graph-rest-1.0), [add member](https://learn.microsoft.com/en-us/graph/api/group-post-members?view=graph-rest-1.0), and [remove member](https://learn.microsoft.com/en-us/graph/api/group-delete-members?view=graph-rest-1.0) |
| **Manage group ownership** | [List owners](https://learn.microsoft.com/en-us/graph/api/group-list-owners?view=graph-rest-1.0), [add owner](https://learn.microsoft.com/en-us/graph/api/group-post-members?view=graph-rest-1.0), and [remove owner](https://learn.microsoft.com/en-us/graph/api/group-delete-members?view=graph-rest-1.0) |
| **Microsoft 365 group functionality** | [Manage conversations](https://learn.microsoft.com/en-us/graph/api/group-post-conversations?view=graph-rest-1.0), [calendar events](https://learn.microsoft.com/en-us/graph/api/group-post-events?view=graph-rest-1.0), [OneNote notebooks](https://learn.microsoft.com/en-us/graph/api/onenote-post-notebooks?view=graph-rest-1.0), and [enable for Teams](https://learn.microsoft.com/en-us/graph/api/team-put-teams?view=graph-rest-1.0) |

## Microsoft Entra roles for managing groups

To manage groups, the signed-in user must have the appropriate Microsoft Graph permissions and be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with supported permissions. *Groups Administrator* is the main role for managing groups, but other roles such as *User Administrator*, *Exchange Administrator*, and *Directory Writers* can also manage groups with varying levels of permissions.

The least privileged roles for managing groups are:

- Directory Writers
- Groups Administrator
- User Administrator

For more information, see [Least privileged roles to manage groups](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/delegate-by-task#groups).

## Next step

[Start working with groups](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)

## See also

- [Best practices for managing groups in the cloud](https://learn.microsoft.com/en-us/entra/fundamentals/concept-learn-about-groups#best-practices-for-managing-groups-in-the-cloud)
