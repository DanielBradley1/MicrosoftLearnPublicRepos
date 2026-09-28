<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-27 -->

# Update group

Namespace: microsoft.graph

Update the properties of a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) object.

Note

When you use `members@odata.bind` to add members via `PATCH`, this request might have replication delays for groups that were recently created. It can take a short time for the group object to fully replicate across Microsoft Entra ID directory replicas. During this window, requests to add members to the group might return a `400 Bad Request` error with the message: *"The source resource object or one of the objects being referenced don't exist."*

To mitigate this behavior:

- **Retry after a brief delay** — wait a few seconds and retry the request. The delay is typically brief.

For more information, see [Designing for Eventual Consistency for Microsoft Entra](https://devblogs.microsoft.com/identity/designing-for-eventual-consistency-for-microsoft-entra/).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-NestingSupport.ReadWrite.All | Directory.ReadWrite.All, Group-PreferredDataLocation.ReadWrite.All, Group.ManageProtection.All, Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-NestingSupport.ReadWrite.All | Directory.ReadWrite.All, Group-PreferredDataLocation.ReadWrite.All, Group.ManageProtection.All, Group.ReadWrite.All |

### Permissions for specific scenarios

- *Group-NestingSupport.ReadWrite.All* is the least privileged permission to update the **disableNesting** property.
- *Group.ManageProtection.All* delegated permission is the least privileged permission to update the **assignedLabels** property for cloud security groups. App-only scenarios aren't supported.

## HTTP request

```http
PATCH /groups/{id}
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply *only* the values for properties that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| allowExternalSenders | Boolean | Default is `false`. Indicates whether people external to the organization can send messages to the group. |
| assignedLabels | [assignedLabel](https://learn.microsoft.com/en-us/graph/api/resources/assignedlabel?view=graph-rest-1.0) collection | The list of sensitivity label pairs \(label ID, label name\) associated with a Microsoft 365 group or a cloud security group. Requires a Microsoft Entra ID P1 license. This property can be specified during group creation or update. However, for cloud security groups, it's immutable once set.  <br><br><br>- For Microsoft 365 groups, this property can be updated only in delegated scenarios where the caller requires both the Microsoft Graph permission and [a supported administrator role](https://learn.microsoft.com/en-us/purview/get-started-with-sensitivity-labels#permissions-required-to-create-and-manage-sensitivity-labels).<br>- *Group.ManageProtection.All* delegated permission is the least privileged permission to update this property for cloud security groups. App-only scenarios aren't supported.<br>- See [Key differences from Microsoft 365 group labeling](https://learn.microsoft.com/en-us/entra/identity/users/groups-sensitivity-labels#key-differences-from-microsoft-365-group-labeling) to learn more about managing this property for Microsoft 365 vs. cloud security groups. |
| autoSubscribeNewMembers | Boolean | Default is `false`. Indicates whether new members added to the group will be auto-subscribed to receive email notifications. **autoSubscribeNewMembers** can't be `true` when **subscriptionEnabled** is set to `false` on the group. |
| description | String | An optional description for the group. |
| displayName | String | The display name for the group. This property is required when a group is created and it cannot be cleared during updates. |
| mailNickname | String | The mail alias for the group, unique for Microsoft 365 groups in the organization. Maximum length is 64 characters. This property can contain only characters in the [ASCII character set 0 - 127](https://learn.microsoft.com/en-us/office/vba/language/reference/user-interface-help/character-set-0127) except the following: ` @ () \\ [] " ; : . <> , SPACE`. |
| preferredDataLocation | String | The preferred data location for the Microsoft 365 group. To update this property, the calling user must be assigned at least one of the following Microsoft Entra roles:  <br><br><br>- User Account Administrator<br>- Directory Writer<br>- Exchange Administrator<br>- SharePoint Administrator<br><br>  <br>For more information about this property, see [OneDrive Online Multi-Geo](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-introduction). |
| securityEnabled | Boolean | Specifies whether the group is a security group. |
| uniqueName | String | The unique identifier that can be assigned to a group and used as an alternate key. Can updated only if `null` and is immutable once set. |
| visibility | String | Specifies the visibility of a Microsoft 365 group. The possible values are: **Private**, **Public**, or empty \(which is interpreted as **Public**\). |

Important

- To update these properties \(**accessType**, **allowExternalSenders**, **autoSubscribeNewMembers**, **hideFromAddressLists**, **hideFromOutlookClients**, **isFavorite**, **isSubscribedByMail**, **unseenConversationsCount**, **unseenCount**, **unseenMessagesCount**\), you must:

  - Specify them in their own PATCH request without including other properties from the previous table
  - Have the Group.ReadWrite.All permission \(*Directory.ReadWrite.All* is not supported for these properties\)

- Only a subset of the group API that pertains to core group administration and management supports application and delegated permissions. All other members of the group API, including updating **autoSubscribeNewMembers**, support only delegated permissions.
- The rules for updating mail-enabled security groups in Microsoft Exchange Server can be complex; to learn more, see [Manage mail-enabled security groups in Exchange Server](https://learn.microsoft.com/en-us/Exchange/recipients/mail-enabled-security-groups).
- Application permissions are not supported when updating assignedLabels. *Group.ManageProtection.All* is the least privileged permission to update **assignedLabels** for cloud security groups.

### Manage extensions and associated data

Use this API to manage the [directory, schema, and open extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview) and their data for groups, as follows:

- Add, update and store data in the extensions for an existing group.
- For directory and schema extensions, remove any stored data by setting the value of the custom extension property to `null`. For open extensions, use the [Delete open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-delete) API.

## Response

If successful, this method returns a `204 No Content` response code—except a `200 OK` response code when updating the following properties: **accessType**, **allowExternalSenders**, **autoSubscribeNewMembers**, **hideFromAddressLists**, **hideFromOutlookClients**, **isFavorite**, **isSubscribedByMail**, **unseenConversationsCount**, **unseenCount**, **unseenMessagesCount**.

### Errors

| Status code | Error code | Error message | Description |
| --- | --- | --- | --- |
| `400 Bad Request` | `Request_BadRequest` | "The source resource object or one of the objects being referenced don't exist." | The group was recently created and hasn't fully replicated across all directory replicas. This error is specific to link-write operations \(adding members via `members@odata.bind`\). Retry the request after a brief delay. |

## Example

The following example shows how to update a group.

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
PATCH https://graph.microsoft.com/v1.0/groups/0d09007d-45b2-458c-b180-880dde3a302e
Content-type: application/json

{
  "description": "Library Assist - ADC",
  "displayName": "Library Assist - ADC",
  "mailNickname": "library-help-adc"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	Description = "Library Assist - ADC",
	DisplayName = "Library Assist - ADC",
	MailNickname = "library-help-adc",
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
description := "Library Assist - ADC"
requestBody.SetDescription(&description) 
displayName := "Library Assist - ADC"
requestBody.SetDisplayName(&displayName) 
mailNickname := "library-help-adc"
requestBody.SetMailNickname(&mailNickname) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().ByGroupId("group-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
group.setDescription("Library Assist - ADC");
group.setDisplayName("Library Assist - ADC");
group.setMailNickname("library-help-adc");
Group result = graphClient.groups().byGroupId("{group-id}").patch(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
  description: 'Library Assist - ADC',
  displayName: 'Library Assist - ADC',
  mailNickname: 'library-help-adc'
};

await client.api('/groups/0d09007d-45b2-458c-b180-880dde3a302e')
	.update(group);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$requestBody->setDescription('Library Assist - ADC');
$requestBody->setDisplayName('Library Assist - ADC');
$requestBody->setMailNickname('library-help-adc');

$result = $graphServiceClient->groups()->byGroupId('group-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	description = "Library Assist - ADC"
	displayName = "Library Assist - ADC"
	mailNickname = "library-help-adc"
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
	description = "Library Assist - ADC",
	display_name = "Library Assist - ADC",
	mail_nickname = "library-help-adc",
)

result = await graph_client.groups.by_group_id('group-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
