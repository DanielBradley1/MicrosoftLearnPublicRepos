<!-- Source: https://learn.microsoft.com/en-us/graph/api/invitation-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-18 -->

# Create invitation

Namespace: microsoft.graph

Use this API to create a new [invitation](https://learn.microsoft.com/en-us/graph/api/resources/invitation?view=graph-rest-1.0) or reset the redemption status for a guest user who already redeemed their invitation. The invitation adds the external user to the organization as part of B2B collaboration. B2B collaboration is supported in both Microsoft Entra External ID in workforce and external tenants.

When creating a new invitation, you have several options available:

1. On invitation creation, Microsoft Graph can automatically send an invitation email directly to the invited user, or your app can use the **inviteRedeemUrl** returned in the response to craft your own invitation \(through your communication mechanism of choice\) to the invited user. If you decide to have Microsoft Graph send an invitation email automatically, you can specify the content and language of the email by using [invitedUserMessageInfo](https://learn.microsoft.com/en-us/graph/api/resources/invitedusermessageinfo?view=graph-rest-1.0).
2. When the user is invited, a user entity \(of **userType** `Guest`\) is created and can be used to control access to resources. The invited user has to go through the redemption process to access any resources they have been invited to.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Invite.All | Directory.ReadWrite.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User.Invite.All | Directory.ReadWrite.All, User.ReadWrite.All |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. The following least privileged roles are supported for this operation:

- To invite guests:

  - Both nonadmin member users and guest users can invite guests if the tenant admin hasn't restricted the [default user permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions?toc=%2Fgraph%2Ftoc.json).
  - Guest Inviter, Directory Writers, or User Administrator.

- To reset the redemption status: Helpdesk Administrator or User Administrator.
- Application permissions \(app-only\) don't work if B2B invitations are disabled on the tenant.
- When resetting the redemption status for a guest user, the *User.ReadWrite.All* permission is the least privileged permission for the operation.

## HTTP request

```http
POST /invitations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of an [invitation](https://learn.microsoft.com/en-us/graph/api/resources/invitation?view=graph-rest-1.0) object.

The following table lists the parameters that are required when you create an invitation.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| invitedUserEmailAddress | string | The email address of the user you're inviting. |
| inviteRedirectUrl | string | The URL that the user will be redirected to after redemption. |

## Response

If successful, this method returns `201 Created` response code and an [invitation](https://learn.microsoft.com/en-us/graph/api/resources/invitation?view=graph-rest-1.0) object in the response body.

## Example

### Example 1: Invite a guest user

#### Request

The following example shows a request to add and invite a guest user.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/invitations
Content-type: application/json

{
  "invitedUserEmailAddress": "admin@fabrikam.com",
  "inviteRedirectUrl": "https://myapp.contoso.com"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Invitation
{
	InvitedUserEmailAddress = "admin@fabrikam.com",
	InviteRedirectUrl = "https://myapp.contoso.com",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Invitations.PostAsync(requestBody);
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

requestBody := graphmodels.NewInvitation()
invitedUserEmailAddress := "admin@fabrikam.com"
requestBody.SetInvitedUserEmailAddress(&invitedUserEmailAddress) 
inviteRedirectUrl := "https://myapp.contoso.com"
requestBody.SetInviteRedirectUrl(&inviteRedirectUrl) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
invitations, err := graphClient.Invitations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Invitation invitation = new Invitation();
invitation.setInvitedUserEmailAddress("admin@fabrikam.com");
invitation.setInviteRedirectUrl("https://myapp.contoso.com");
Invitation result = graphClient.invitations().post(invitation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const invitation = {
  invitedUserEmailAddress: 'admin@fabrikam.com',
  inviteRedirectUrl: 'https://myapp.contoso.com'
};

await client.api('/invitations')
	.post(invitation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Invitation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Invitation();
$requestBody->setInvitedUserEmailAddress('admin@fabrikam.com');
$requestBody->setInviteRedirectUrl('https://myapp.contoso.com');

$result = $graphServiceClient->invitations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	invitedUserEmailAddress = "admin@fabrikam.com"
	inviteRedirectUrl = "https://myapp.contoso.com"
}

New-MgInvitation -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.invitation import Invitation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Invitation(
	invited_user_email_address = "admin@fabrikam.com",
	invite_redirect_url = "https://myapp.contoso.com",
)

result = await graph_client.invitations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#invitations/$entity",
    "id": "9071bfde-35e0-47d2-a582-d244ab1b4af6",
    "inviteRedeemUrl": "https://login.microsoftonline.com/redeem?rd=https%3a%2f%2finvitations.microsoft.com%2fredeem%...d%26ver%3d2.0",
    "invitedUserDisplayName": null,
    "invitedUserType": "Guest",
    "invitedUserEmailAddress": "admin@fabrikam.com",
    "sendInvitationMessage": false,
    "resetRedemption": false,
    "inviteRedirectUrl": "https://myapp.contoso.com",
    "status": "PendingAcceptance",
    "invitedUserMessageInfo": {
        "messageLanguage": null,
        "customizedMessageBody": null,
        "ccRecipients": [
            {
                "emailAddress": {
                    "name": null,
                    "address": null
                }
            }
        ]
    },
    "invitedUser": {
        "id": "cbb896f9-8306-49d0-b56b-b8e39cd28825",
        "userPrincipalName": "admin_fabrikam.com#EXT#@doc.onmicrosoft.com"
    }
}
```

### Example 2: Reset the redemption status of a guest user

#### Request

The following example shows a request to reset the redemption status of a guest user. The request changes the user's email address, but keeps their current user ID. Before running the request, you must add the new email address the **otherMails** property of the existing guest [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/invitations
Content-type: application/json

{
    "invitedUserEmailAddress": "AdeleV@fabrikam.com",
    "inviteRedirectUrl": "https://myapp.contoso.com",
    "invitedUser": {
        "id": "264e6d50-eaec-461e-b187-873b1bcf855f"
    },
    "resetRedemption": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Invitation
{
	InvitedUserEmailAddress = "AdeleV@fabrikam.com",
	InviteRedirectUrl = "https://myapp.contoso.com",
	InvitedUser = new User
	{
		Id = "264e6d50-eaec-461e-b187-873b1bcf855f",
	},
	ResetRedemption = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Invitations.PostAsync(requestBody);
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

requestBody := graphmodels.NewInvitation()
invitedUserEmailAddress := "AdeleV@fabrikam.com"
requestBody.SetInvitedUserEmailAddress(&invitedUserEmailAddress) 
inviteRedirectUrl := "https://myapp.contoso.com"
requestBody.SetInviteRedirectUrl(&inviteRedirectUrl) 
invitedUser := graphmodels.NewUser()
id := "264e6d50-eaec-461e-b187-873b1bcf855f"
invitedUser.SetId(&id) 
requestBody.SetInvitedUser(invitedUser)
resetRedemption := true
requestBody.SetResetRedemption(&resetRedemption) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
invitations, err := graphClient.Invitations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Invitation invitation = new Invitation();
invitation.setInvitedUserEmailAddress("AdeleV@fabrikam.com");
invitation.setInviteRedirectUrl("https://myapp.contoso.com");
User invitedUser = new User();
invitedUser.setId("264e6d50-eaec-461e-b187-873b1bcf855f");
invitation.setInvitedUser(invitedUser);
invitation.setResetRedemption(true);
Invitation result = graphClient.invitations().post(invitation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const invitation = {
    invitedUserEmailAddress: 'AdeleV@fabrikam.com',
    inviteRedirectUrl: 'https://myapp.contoso.com',
    invitedUser: {
        id: '264e6d50-eaec-461e-b187-873b1bcf855f'
    },
    resetRedemption: true
};

await client.api('/invitations')
	.post(invitation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Invitation;
use Microsoft\Graph\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Invitation();
$requestBody->setInvitedUserEmailAddress('AdeleV@fabrikam.com');
$requestBody->setInviteRedirectUrl('https://myapp.contoso.com');
$invitedUser = new User();
$invitedUser->setId('264e6d50-eaec-461e-b187-873b1bcf855f');
$requestBody->setInvitedUser($invitedUser);
$requestBody->setResetRedemption(true);

$result = $graphServiceClient->invitations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	invitedUserEmailAddress = "AdeleV@fabrikam.com"
	inviteRedirectUrl = "https://myapp.contoso.com"
	invitedUser = @{
		id = "264e6d50-eaec-461e-b187-873b1bcf855f"
	}
	resetRedemption = $true
}

New-MgInvitation -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.invitation import Invitation
from msgraph.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Invitation(
	invited_user_email_address = "AdeleV@fabrikam.com",
	invite_redirect_url = "https://myapp.contoso.com",
	invited_user = User(
		id = "264e6d50-eaec-461e-b187-873b1bcf855f",
	),
	reset_redemption = True,
)

result = await graph_client.invitations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#invitations/$entity",
    "id": "46d72876-dba6-4a05-b9ec-118faf16c4b7",
    "inviteRedeemUrl": "https://login.microsoftonline.com/redeem?rd=https%3a%2f%2finvitations.microsoft.com%2fredeem%2f%3fte...3d2.0",
    "invitedUserDisplayName": null,
    "invitedUserType": "Guest",
    "invitedUserEmailAddress": "AdeleV@fabrikam.com",
    "sendInvitationMessage": false,
    "resetRedemption": true,
    "inviteRedirectUrl": "https://myapp.contoso.com",
    "status": "PendingAcceptance",
    "invitedUserMessageInfo": {
        "messageLanguage": null,
        "customizedMessageBody": null,
        "ccRecipients": [
            {
                "emailAddress": {
                    "name": null,
                    "address": null
                }
            }
        ]
    },
    "invitedUser": {
        "id": "264e6d50-eaec-461e-b187-873b1bcf855f",
        "userPrincipalName": "AdeleV_fabrikam.com#EXT#@doc.onmicrosoft.com"
    }
}
```
