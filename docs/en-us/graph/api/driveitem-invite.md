<!-- Source: https://learn.microsoft.com/en-us/graph/api/driveitem-invite?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-07 -->

# driveItem: invite

Namespace: microsoft.graph

Send a sharing invitation for a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0). A sharing invitation provides permissions to the recipients and, optionally, sends them an email to notify them that the item was shared.

Important

- Permissions can’t be created or modified on the root **driveItem** of [drives](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) with a **driveType** of `personal` \(OneDrive for home\).
- *New* guests can't be invited using app-only access. Existing guests can be invited using app-only requests.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Files.ReadWrite.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Files.ReadWrite.All |
| Application | Files.ReadWrite.All | Sites.ReadWrite.All |

Note

SharePoint Embedded requires the `FileStorageContainer.Selected` permission to access the content of the container. This permission is different from the ones mentioned previously. In addition to Microsoft Graph permissions, your app must have the necessary [container type permissions](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/auth#container-type-application-permissions) to call this API. For more information, see [SharePoint Embedded authentication and authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth).

## HTTP request

```http
POST /drives/{drive-id}/items/{item-id}/invite
POST /groups/{group-id}/drive/items/{item-id}/invite
POST /me/drive/items/{item-id}/invite
POST /sites/{siteId}/drive/items/{itemId}/invite
POST /users/{userId}/drive/items/{itemId}/invite
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

```json
{
  "requireSignIn": false,
  "sendInvitation": false,
  "roles": [ "read | write"],
  "recipients": [
    { "@odata.type": "microsoft.graph.driveRecipient" },
    { "@odata.type": "microsoft.graph.driveRecipient" }
  ],
  "message": "string"
}
```

| Parameter | Type | Description |
| :--- | :--- | :--- |
| recipients | [driveRecipient](https://learn.microsoft.com/en-us/graph/api/resources/driverecipient?view=graph-rest-1.0) collection | A collection of recipients who receive access and the sharing invitation. |
| message | String | A plain text formatted message that is included in the sharing invitation. Maximum length 2,000 characters. |
| requireSignIn | Boolean | Specifies whether the recipient of the invitation is required to sign-in to view the shared item. |
| sendInvitation | Boolean | If true, a [sharing link](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0#sharing-links) is sent to the recipient. Otherwise, a permission is granted directly without sending a notification. |
| roles | String collection | Specifies the roles that are to be granted to the recipients of the sharing invitation. |
| expirationDateTime | DateTimeOffset | Specifies the **dateTime** after which the permission expires. For OneDrive for work or school and SharePoint, **expirationDateTime** is only applicable for **sharingLink** permissions. Available on OneDrive for work or school, SharePoint, and premium personal OneDrive accounts. |
| password | String | The password set on the invite by the creator. Optional and OneDrive for home only. |
| retainInheritedPermissions | Boolean | Optional. If `true` \(default\), any existing inherited permissions are retained on the shared item when sharing this item for the first time. If `false`, all existing permissions are removed when sharing for the first time. Not supported with SharePoint Embedded. |

## Response

If successful, this method returns a `200 OK` response code and a collection of [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) objects in the response body.

For more information about how errors are returned, see [Error responses](https://learn.microsoft.com/en-us/graph/errors).

### Partial success response

When inviting multiple recipients, it's possible for the notification to succeed for some and fail for others. In this case, the service returns a partial success response with a `207 Multi-Status` status code. When partial success is returned, the response for each failed recipient contains an **error** object with information about what went wrong and how to fix it. For more information, see [Example 2](#example-2-send-sharing-invitation-with-partial-success).

### Send invitation notification errors

The following table shows some other errors that your app might encounter within the nested **innererror** objects when sending notification fails. Apps aren't required to handle these errors.

| Code | Description |
| :--- | :--- |
| accountVerificationRequired | Account verification is required to unblock sending notifications. |
| hipCheckRequired | Need to solve HIP \(Host Intrusion Prevention\) check to unblock sending notifications. |
| exchangeInvalidUser | Current user's mailbox wasn't found. |
| exchangeOutOfMailboxQuota | Out of quota. |
| exchangeMaxRecipients | Exceeded maximum number of recipients that can be sent notifications at the same time. |

> **Note:** The service can add new error codes or stop returning old ones at any time.

## Examples

### Example 1: Send a sharing invitation

The following example shows how to send a sharing invitation to a user with the email address `ryan@contoso.com`, including a message regarding a file under collaboration. The invitation grants Ryan read-write access to the file.

#### Request

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
POST https://graph.microsoft.com/v1.0/me/drive/items/{item-id}/invite
Content-type: application/json

{
  "recipients": [
    {
      "email": "ryan@contoso.com"
    }
  ],
  "message": "Here's the file that we're collaborating on.",
  "requireSignIn": true,
  "sendInvitation": true,
  "roles": [ "write" ],
  "password": "password123",
  "expirationDateTime": "2018-07-15T14:00:00.000Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Drives.Item.Items.Item.Invite;
using Microsoft.Graph.Models;

var requestBody = new InvitePostRequestBody
{
	Recipients = new List<DriveRecipient>
	{
		new DriveRecipient
		{
			Email = "ryan@contoso.com",
		},
	},
	Message = "Here's the file that we're collaborating on.",
	RequireSignIn = true,
	SendInvitation = true,
	Roles = new List<string>
	{
		"write",
	},
	Password = "password123",
	ExpirationDateTime = "2018-07-15T14:00:00.000Z",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Invite.PostAsInvitePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-sdk-go/drives"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphdrives.NewInvitePostRequestBody()


driveRecipient := graphmodels.NewDriveRecipient()
email := "ryan@contoso.com"
driveRecipient.SetEmail(&email) 

recipients := []graphmodels.DriveRecipientable {
	driveRecipient,
}
requestBody.SetRecipients(recipients)
message := "Here's the file that we're collaborating on."
requestBody.SetMessage(&message) 
requireSignIn := true
requestBody.SetRequireSignIn(&requireSignIn) 
sendInvitation := true
requestBody.SetSendInvitation(&sendInvitation) 
roles := []string {
	"write",
}
requestBody.SetRoles(roles)
password := "password123"
requestBody.SetPassword(&password) 
expirationDateTime := "2018-07-15T14:00:00.000Z"
requestBody.SetExpirationDateTime(&expirationDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
invite, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Invite().PostAsInvitePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.drives.item.items.item.invite.InvitePostRequestBody invitePostRequestBody = new com.microsoft.graph.drives.item.items.item.invite.InvitePostRequestBody();
LinkedList<DriveRecipient> recipients = new LinkedList<DriveRecipient>();
DriveRecipient driveRecipient = new DriveRecipient();
driveRecipient.setEmail("ryan@contoso.com");
recipients.add(driveRecipient);
invitePostRequestBody.setRecipients(recipients);
invitePostRequestBody.setMessage("Here's the file that we're collaborating on.");
invitePostRequestBody.setRequireSignIn(true);
invitePostRequestBody.setSendInvitation(true);
LinkedList<String> roles = new LinkedList<String>();
roles.add("write");
invitePostRequestBody.setRoles(roles);
invitePostRequestBody.setPassword("password123");
invitePostRequestBody.setExpirationDateTime("2018-07-15T14:00:00.000Z");
var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").invite().post(invitePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  recipients: [
    {
      email: 'ryan@contoso.com'
    }
  ],
  message: 'Here\'s the file that we\'re collaborating on.',
  requireSignIn: true,
  sendInvitation: true,
  roles: [ 'write' ],
  password: 'password123',
  expirationDateTime: '2018-07-15T14:00:00.000Z'
};

await client.api('/me/drive/items/{item-id}/invite')
	.post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Invite\InvitePostRequestBody;
use Microsoft\Graph\Generated\Models\DriveRecipient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InvitePostRequestBody();
$recipientsDriveRecipient1 = new DriveRecipient();
$recipientsDriveRecipient1->setEmail('ryan@contoso.com');
$recipientsArray []= $recipientsDriveRecipient1;
$requestBody->setRecipients($recipientsArray);

$requestBody->setMessage('Here\'s the file that we\'re collaborating on.');
$requestBody->setRequireSignIn(true);
$requestBody->setSendInvitation(true);
$requestBody->setRoles(['write', ]);
$requestBody->setPassword('password123');
$requestBody->setExpirationDateTime('2018-07-15T14:00:00.000Z');

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->invite()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	recipients = @(
		@{
			email = "ryan@contoso.com"
		}
	)
	message = "Here's the file that we're collaborating on."
	requireSignIn = $true
	sendInvitation = $true
	roles = @(
	"write"
)
password = "password123"
expirationDateTime = "2018-07-15T14:00:00.000Z"
}

Invoke-MgInviteDriveItem -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.invite.invite_post_request_body import InvitePostRequestBody
from msgraph.generated.models.drive_recipient import DriveRecipient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InvitePostRequestBody(
	recipients = [
		DriveRecipient(
			email = "ryan@contoso.com",
		),
	],
	message = "Here's the file that we're collaborating on.",
	require_sign_in = True,
	send_invitation = True,
	roles = [
		"write",
	],
	password = "password123",
	expiration_date_time = "2018-07-15T14:00:00.000Z",
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').invite.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "@deprecated.GrantedTo": "GrantedTo has been deprecated. Refer to GrantedToV2",
      "grantedTo": {
        "user": {
          "displayName": "Robin Danielsen",
          "id": "42F177F1-22C0-4BE3-900D-4507125C5C20"
        }
      },
      "grantedToV2": {
        "user": {
          "id": "42F177F1-22C0-4BE3-900D-4507125C5C20",
          "displayName": "Robin Danielsen"
        },
        "siteUser": {
          "id": "1",
          "displayName": "Robin Danielsen",
          "loginName": "Robin Danielsen"
        }
      },
      "hasPassword": true,
      "id": "CCFC7CA3-7A19-4D57-8CEF-149DB9DDFA62",
      "invitation": {
        "email": "robin@contoso.com",
        "signInRequired": true
      },
      "roles": [ "write" ],
      "expirationDateTime": "2018-07-15T14:00:00.000Z"
    }
  ]
}
```

### Example 2: Send sharing invitation with partial success

The following example shows a request that partially succeeds.

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
POST https://graph.microsoft.com/v1.0/me/drive/items/{item-id}/invite
Content-type: application/json

{
  "recipients": [
    {
      "email": "helga@contoso.com"
    },
    {
      "email": "robin@contoso.com"
    }
  ],
  "message": "Here's the file that we're collaborating on.",
  "requireSignIn": true,
  "sendInvitation": true,
  "roles": [ "write" ],
  "password": "password123",
  "expirationDateTime": "2018-07-15T14:00:00.000Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Drives.Item.Items.Item.Invite;
using Microsoft.Graph.Models;

var requestBody = new InvitePostRequestBody
{
	Recipients = new List<DriveRecipient>
	{
		new DriveRecipient
		{
			Email = "helga@contoso.com",
		},
		new DriveRecipient
		{
			Email = "robin@contoso.com",
		},
	},
	Message = "Here's the file that we're collaborating on.",
	RequireSignIn = true,
	SendInvitation = true,
	Roles = new List<string>
	{
		"write",
	},
	Password = "password123",
	ExpirationDateTime = "2018-07-15T14:00:00.000Z",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Invite.PostAsInvitePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-sdk-go/drives"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphdrives.NewInvitePostRequestBody()


driveRecipient := graphmodels.NewDriveRecipient()
email := "helga@contoso.com"
driveRecipient.SetEmail(&email) 
driveRecipient1 := graphmodels.NewDriveRecipient()
email := "robin@contoso.com"
driveRecipient1.SetEmail(&email) 

recipients := []graphmodels.DriveRecipientable {
	driveRecipient,
	driveRecipient1,
}
requestBody.SetRecipients(recipients)
message := "Here's the file that we're collaborating on."
requestBody.SetMessage(&message) 
requireSignIn := true
requestBody.SetRequireSignIn(&requireSignIn) 
sendInvitation := true
requestBody.SetSendInvitation(&sendInvitation) 
roles := []string {
	"write",
}
requestBody.SetRoles(roles)
password := "password123"
requestBody.SetPassword(&password) 
expirationDateTime := "2018-07-15T14:00:00.000Z"
requestBody.SetExpirationDateTime(&expirationDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
invite, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Invite().PostAsInvitePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.drives.item.items.item.invite.InvitePostRequestBody invitePostRequestBody = new com.microsoft.graph.drives.item.items.item.invite.InvitePostRequestBody();
LinkedList<DriveRecipient> recipients = new LinkedList<DriveRecipient>();
DriveRecipient driveRecipient = new DriveRecipient();
driveRecipient.setEmail("helga@contoso.com");
recipients.add(driveRecipient);
DriveRecipient driveRecipient1 = new DriveRecipient();
driveRecipient1.setEmail("robin@contoso.com");
recipients.add(driveRecipient1);
invitePostRequestBody.setRecipients(recipients);
invitePostRequestBody.setMessage("Here's the file that we're collaborating on.");
invitePostRequestBody.setRequireSignIn(true);
invitePostRequestBody.setSendInvitation(true);
LinkedList<String> roles = new LinkedList<String>();
roles.add("write");
invitePostRequestBody.setRoles(roles);
invitePostRequestBody.setPassword("password123");
invitePostRequestBody.setExpirationDateTime("2018-07-15T14:00:00.000Z");
var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").invite().post(invitePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  recipients: [
    {
      email: 'helga@contoso.com'
    },
    {
      email: 'robin@contoso.com'
    }
  ],
  message: 'Here\'s the file that we\'re collaborating on.',
  requireSignIn: true,
  sendInvitation: true,
  roles: [ 'write' ],
  password: 'password123',
  expirationDateTime: '2018-07-15T14:00:00.000Z'
};

await client.api('/me/drive/items/{item-id}/invite')
	.post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Invite\InvitePostRequestBody;
use Microsoft\Graph\Generated\Models\DriveRecipient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InvitePostRequestBody();
$recipientsDriveRecipient1 = new DriveRecipient();
$recipientsDriveRecipient1->setEmail('helga@contoso.com');
$recipientsArray []= $recipientsDriveRecipient1;
$recipientsDriveRecipient2 = new DriveRecipient();
$recipientsDriveRecipient2->setEmail('robin@contoso.com');
$recipientsArray []= $recipientsDriveRecipient2;
$requestBody->setRecipients($recipientsArray);

$requestBody->setMessage('Here\'s the file that we\'re collaborating on.');
$requestBody->setRequireSignIn(true);
$requestBody->setSendInvitation(true);
$requestBody->setRoles(['write', ]);
$requestBody->setPassword('password123');
$requestBody->setExpirationDateTime('2018-07-15T14:00:00.000Z');

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->invite()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	recipients = @(
		@{
			email = "helga@contoso.com"
		}
		@{
			email = "robin@contoso.com"
		}
	)
	message = "Here's the file that we're collaborating on."
	requireSignIn = $true
	sendInvitation = $true
	roles = @(
	"write"
)
password = "password123"
expirationDateTime = "2018-07-15T14:00:00.000Z"
}

Invoke-MgInviteDriveItem -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.invite.invite_post_request_body import InvitePostRequestBody
from msgraph.generated.models.drive_recipient import DriveRecipient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InvitePostRequestBody(
	recipients = [
		DriveRecipient(
			email = "helga@contoso.com",
		),
		DriveRecipient(
			email = "robin@contoso.com",
		),
	],
	message = "Here's the file that we're collaborating on.",
	require_sign_in = True,
	send_invitation = True,
	roles = [
		"write",
	],
	password = "password123",
	expiration_date_time = "2018-07-15T14:00:00.000Z",
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').invite.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the partial response.

```http
HTTP/1.1 207 Multi-Status
Content-type: application/json

{
  "value": [
    {
      "grantedTo": {
        "user": {
          "displayName": "Helga Hammeren",
          "id": "5D8CA5D0-FFF8-4A97-B0A6-8F5AEA339681"
        }
      },
      "id": "1EFG7CA3-7A19-4D57-8CEF-149DB9DDFA62",
      "invitation": {
        "email": "helga@contoso.com",
        "signInRequired": true
      },
      "roles": [ "write" ],
      "error": {
        "code":"notAllowed",
        "message":"Account verification needed to unblock sending emails.",
        "localizedMessage": "Kontobestätigung erforderlich, um das Senden von E-Mails zu entsperren.",
        "fixItUrl":"http://g.live.com/8SESkydrive/VerifyAccount",
        "innererror":{
          "code":"accountVerificationRequired"
        }
      }
    },
    {
      "grantedTo": {
        "user": {
          "displayName": "Robin Danielsen",
          "id": "42F177F1-22C0-4BE3-900D-4507125C5C20"
        }
      },
      "id": "CCFC7CA3-7A19-4D57-8CEF-149DB9DDFA62",
      "invitation": {
        "email": "robin@contoso.com",
        "signInRequired": true
      },
      "roles": [ "write" ],
      "expirationDateTime": "2018-07-15T14:00:00.000Z"
    }
  ]
}
```

## Related content

For a list of available roles, see [roles property values](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0#roles-property-values).
