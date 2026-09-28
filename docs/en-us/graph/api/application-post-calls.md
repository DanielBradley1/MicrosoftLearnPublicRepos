<!-- Source: https://learn.microsoft.com/en-us/graph/api/application-post-calls?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create call

Namespace: microsoft.graph

Create [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) enables your bot to create a new outgoing peer-to-peer or group call, or join an existing meeting. You need to [register the calling bot](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/calls-and-meetings/registering-calling-bot) and go through the list of permissions needed.

This API supports the following PSTN scenarios:

- Incoming call to bot's PSTN number and then bot invites another PSTN.
- Incoming call to bot's PSTN number and then bot transfer to another PSTN.
- Incoming call to bot's PSTN number and then bot redirects to another PSTN.
- Incoming call to bot's instance identifier and then bot invites another PSTN.
- Incoming call to bot's instance identifier and then bot transfer to another PSTN.
- Incoming call to bot's instance identifier and then bot redirects to another PSTN.
- Incoming call to bot's instance identifier from Scheduled Meeting and then bot invites PSTN.
- Outgoing call from bot \(with instance identifier\) to a PSTN.
- P2P call between bot and another peer \(Teams user, PSTN\), bot invites another PSTN.
- P2P call between bot and another peer \(Teams user, PSTN\), bot invites another Teams user.
- Bot join the scheduled meeting and then invite PSTN.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Calls.JoinGroupCalls.Chat | Calls.Initiate.All, Calls.InitiateGroupCall.All, Calls.JoinGroupCall.All, Calls.JoinGroupCallAsGuest.All |

Note

- For a call with app-hosted media, you need the Calls.AccessMedia.All permission in addition to one of the permissions listed in the previous table.
- The Calls.JoinGroupCalls.Chat permission uses [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

Cloud Video Interop solutions that are [Certified for Microsoft Teams](https://learn.microsoft.com/en-us/MicrosoftTeams/cloud-video-interop) have permission to call this API to join meetings for which they have meeting join links, similar to external users joining through a browser.

## HTTP request

```http
POST /communications/calls
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a peer-to-peer VoIP call with service-hosted media

> **Note:** This call needs the Calls.Initiate.All permission.

#### Request

The following example shows a request that makes a peer-to-peer call between the bot and the specified user. In this example, the service hosts the media. The values of authorization token, callback URL, application ID, application name, user ID, user name, and tenant ID must be replaced with actual values to make the example work.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "callbackUri": "https://bot.contoso.com/callback",
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "John",
          "id": "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "callOptions": {
    "@odata.type": "#microsoft.graph.outgoingCallOptions",
    "isContentSharingNotificationEnabled": true,
    "isDeltaRosterEnabled": true,
    "isInteractiveRosterEnabled": true
  },
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	CallbackUri = "https://bot.contoso.com/callback",
	Targets = new List<InvitationParticipantInfo>
	{
		new InvitationParticipantInfo
		{
			OdataType = "#microsoft.graph.invitationParticipantInfo",
			Identity = new IdentitySet
			{
				OdataType = "#microsoft.graph.identitySet",
				User = new Identity
				{
					OdataType = "#microsoft.graph.identity",
					DisplayName = "John",
					Id = "112f7296-5fa4-42ca-bae8-6a692b15d4b8",
				},
			},
		},
	},
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	CallOptions = new OutgoingCallOptions
	{
		OdataType = "#microsoft.graph.outgoingCallOptions",
		IsContentSharingNotificationEnabled = true,
		IsDeltaRosterEnabled = true,
		IsInteractiveRosterEnabled = true,
	},
	MediaConfig = new ServiceHostedMediaConfig
	{
		OdataType = "#microsoft.graph.serviceHostedMediaConfig",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 


invitationParticipantInfo := graphmodels.NewInvitationParticipantInfo()
identity := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
displayName := "John"
user.SetDisplayName(&displayName) 
id := "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
user.SetId(&id) 
identity.SetUser(user)
invitationParticipantInfo.SetIdentity(identity)

targets := []graphmodels.InvitationParticipantInfoable {
	invitationParticipantInfo,
}
requestBody.SetTargets(targets)
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
callOptions := graphmodels.NewOutgoingCallOptions()
isContentSharingNotificationEnabled := true
callOptions.SetIsContentSharingNotificationEnabled(&isContentSharingNotificationEnabled) 
isDeltaRosterEnabled := true
callOptions.SetIsDeltaRosterEnabled(&isDeltaRosterEnabled) 
isInteractiveRosterEnabled := true
callOptions.SetIsInteractiveRosterEnabled(&isInteractiveRosterEnabled) 
requestBody.SetCallOptions(callOptions)
mediaConfig := graphmodels.NewServiceHostedMediaConfig()
requestBody.SetMediaConfig(mediaConfig)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setCallbackUri("https://bot.contoso.com/callback");
LinkedList<InvitationParticipantInfo> targets = new LinkedList<InvitationParticipantInfo>();
InvitationParticipantInfo invitationParticipantInfo = new InvitationParticipantInfo();
invitationParticipantInfo.setOdataType("#microsoft.graph.invitationParticipantInfo");
IdentitySet identity = new IdentitySet();
identity.setOdataType("#microsoft.graph.identitySet");
Identity user = new Identity();
user.setOdataType("#microsoft.graph.identity");
user.setDisplayName("John");
user.setId("112f7296-5fa4-42ca-bae8-6a692b15d4b8");
identity.setUser(user);
invitationParticipantInfo.setIdentity(identity);
targets.add(invitationParticipantInfo);
call.setTargets(targets);
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
OutgoingCallOptions callOptions = new OutgoingCallOptions();
callOptions.setOdataType("#microsoft.graph.outgoingCallOptions");
callOptions.setIsContentSharingNotificationEnabled(true);
callOptions.setIsDeltaRosterEnabled(true);
callOptions.setIsInteractiveRosterEnabled(true);
call.setCallOptions(callOptions);
ServiceHostedMediaConfig mediaConfig = new ServiceHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.serviceHostedMediaConfig");
call.setMediaConfig(mediaConfig);
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  callbackUri: 'https://bot.contoso.com/callback',
  targets: [
    {
      '@odata.type': '#microsoft.graph.invitationParticipantInfo',
      identity: {
        '@odata.type': '#microsoft.graph.identitySet',
        user: {
          '@odata.type': '#microsoft.graph.identity',
          displayName: 'John',
          id: '112f7296-5fa4-42ca-bae8-6a692b15d4b8'
        }
      }
    }
  ],
  requestedModalities: [
    'audio'
  ],
  callOptions: {
    '@odata.type': '#microsoft.graph.outgoingCallOptions',
    isContentSharingNotificationEnabled: true,
    isDeltaRosterEnabled: true,
    isInteractiveRosterEnabled: true
  },
  mediaConfig: {
    '@odata.type': '#microsoft.graph.serviceHostedMediaConfig'
  }
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\InvitationParticipantInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\OutgoingCallOptions;
use Microsoft\Graph\Generated\Models\ServiceHostedMediaConfig;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$targetsInvitationParticipantInfo1 = new InvitationParticipantInfo();
$targetsInvitationParticipantInfo1->setOdataType('#microsoft.graph.invitationParticipantInfo');
$targetsInvitationParticipantInfo1Identity = new IdentitySet();
$targetsInvitationParticipantInfo1Identity->setOdataType('#microsoft.graph.identitySet');
$targetsInvitationParticipantInfo1IdentityUser = new Identity();
$targetsInvitationParticipantInfo1IdentityUser->setOdataType('#microsoft.graph.identity');
$targetsInvitationParticipantInfo1IdentityUser->setDisplayName('John');
$targetsInvitationParticipantInfo1IdentityUser->setId('112f7296-5fa4-42ca-bae8-6a692b15d4b8');
$targetsInvitationParticipantInfo1Identity->setUser($targetsInvitationParticipantInfo1IdentityUser);
$targetsInvitationParticipantInfo1->setIdentity($targetsInvitationParticipantInfo1Identity);
$targetsArray []= $targetsInvitationParticipantInfo1;
$requestBody->setTargets($targetsArray);

$requestBody->setRequestedModalities([new Modality('audio'),]);
$callOptions = new OutgoingCallOptions();
$callOptions->setOdataType('#microsoft.graph.outgoingCallOptions');
$callOptions->setIsContentSharingNotificationEnabled(true);
$callOptions->setIsDeltaRosterEnabled(true);
$callOptions->setIsInteractiveRosterEnabled(true);
$requestBody->setCallOptions($callOptions);
$mediaConfig = new ServiceHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.serviceHostedMediaConfig');
$requestBody->setMediaConfig($mediaConfig);

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	callbackUri = "https://bot.contoso.com/callback"
	targets = @(
		@{
			"@odata.type" = "#microsoft.graph.invitationParticipantInfo"
			identity = @{
				"@odata.type" = "#microsoft.graph.identitySet"
				user = @{
					"@odata.type" = "#microsoft.graph.identity"
					displayName = "John"
					id = "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
				}
			}
		}
	)
	requestedModalities = @(
	"audio"
)
callOptions = @{
	"@odata.type" = "#microsoft.graph.outgoingCallOptions"
	isContentSharingNotificationEnabled = $true
	isDeltaRosterEnabled = $true
	isInteractiveRosterEnabled = $true
}
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.serviceHostedMediaConfig"
}
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.invitation_participant_info import InvitationParticipantInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.outgoing_call_options import OutgoingCallOptions
from msgraph.generated.models.service_hosted_media_config import ServiceHostedMediaConfig
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	callback_uri = "https://bot.contoso.com/callback",
	targets = [
		InvitationParticipantInfo(
			odata_type = "#microsoft.graph.invitationParticipantInfo",
			identity = IdentitySet(
				odata_type = "#microsoft.graph.identitySet",
				user = Identity(
					odata_type = "#microsoft.graph.identity",
					display_name = "John",
					id = "112f7296-5fa4-42ca-bae8-6a692b15d4b8",
				),
			),
		),
	],
	requested_modalities = [
		Modality.Audio,
	],
	call_options = OutgoingCallOptions(
		odata_type = "#microsoft.graph.outgoingCallOptions",
		is_content_sharing_notification_enabled = True,
		is_delta_roster_enabled = True,
		is_interactive_roster_enabled = True,
	),
	media_config = ServiceHostedMediaConfig(
		odata_type = "#microsoft.graph.serviceHostedMediaConfig",
	),
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2e1a0b00-2db4-4022-9570-243709c565ab
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
      }
    },
    "countryCode": null,
    "endpointType": null,
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "John",
          "id": "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
        }
      },
      "endpointType": null,
      "replacesCallId": null
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
      {
        "uri": "https://cdn.contoso.com/beep.wav",
        "resourceId": "f8971b04-b53e-418c-9222-c82ce681a582"
      },
      {
        "uri": "https://cdn.contoso.com/cool.wav",
        "resourceId": "86dc814b-c172-4428-9112-60f8ecae1edb"
      }
    ]
  },
  "myParticipantId": "499ff390-7a72-40e8-83a0-8fac6295ae7e",
  "id": "2e1a0b00-2db4-4022-9570-243709c565ab",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
  "subject": null,
  "ringingTimeoutInSeconds": null,
  "mediaState": null,
  "resultInfo": null,
  "answeredBy": null,
  "chatInfo": null,
  "meetingInfo": null,
  "transcription": null,
  "callOptions": {
    "@odata.type": "#microsoft.graph.outgoingCallOptions",
    "isContentSharingNotificationEnabled": true,
    "isDeltaRosterEnabled": true,
    "isInteractiveRosterEnabled": true
  },
  "toneInfo": null
}
```

#### Notification - establishing

```http
POST https://bot.contoso.com/callback
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/2e1a0b00-2db4-4022-9570-243709c565ab",
      "callbackUri": "https://bot.contoso.com/callback",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "establishing",
        "id": "2e1a0b00-2db4-4022-9570-243709c565ab"
      }
    }
  ]
}
```

> **Note:** Call establishing/established notifications may arrive out of order.

#### Notification - established

```http
POST https://bot.contoso.com/callback
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/2e1a0b00-b3c5-4b0f-99b3-c133bc1e6116",
      "callbackUri": "https://bot.contoso.com/callback",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "established",
        "direction": "outgoing",
        "id": "2e1a0b00-b3c5-4b0f-99b3-c133bc1e6116"
      }
    }
  ]
}
```

> **Note:** Call establishing/established notifications may arrive out of order.

#### Notification - content sharing started

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "created",
      "resourceUrl": "/communications/calls/421f4c00-4436-4c3a-9d9a-c4924cf98e67/contentsharingsessions",
      "resourceData": [
        {
          "@odata.type": "#microsoft.graph.contentSharingSession",
          "id": "F7D9EF30FF0A9BD3F64B274387FB8FF8E96B6CFBA8F87F8305A74DE99AF007BC"
        }
      ]
    }
  ]
}
```

#### Notification - content sharing updated

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/421f4c00-4436-4c3a-9d9a-c4924cf98e67/contentsharingsessions",
      "resourceData": [
        {
          "@odata.type": "#microsoft.graph.contentSharingSession",
          "id": "F7D9EF30FF0A9BD3F64B274387FB8FF8E96B6CFBA8F87F8305A74DE99AF007BC"
        }
      ]
    }
  ]
}
```

#### Notification - content sharing ended

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "deleted",
      "resourceUrl": "/communications/calls/421f4c00-4436-4c3a-9d9a-c4924cf98e67/contentsharingsessions",
      "resourceData": [
        {
          "@odata.type": "#microsoft.graph.contentSharingSession",
          "id": "F7D9EF30FF0A9BD3F64B274387FB8FF8E96B6CFBA8F87F8305A74DE99AF007BC"
        }
      ]
    }
  ]
}
```

### Example 2: Create peer-to-peer VoIP call with application hosted media

> **Note**: This example needs Calls.Initiate.All and Calls.AccessMedia.All permissions.

#### Request

The following example shows a request that makes a peer-to-peer call between the bot and the specified user. In this example, the media is hosted locally by the application. The values of authorization token, callback URL, application ID, application name, user ID, user name, and tenant ID must be replaced with actual values to make the example work.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "callbackUri": "https://bot.contoso.com/callback",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
      }
    },
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "John",
          "id": "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
 "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration>"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	CallbackUri = "https://bot.contoso.com/callback",
	Source = new ParticipantInfo
	{
		OdataType = "#microsoft.graph.participantInfo",
		Identity = new IdentitySet
		{
			OdataType = "#microsoft.graph.identitySet",
			Application = new Identity
			{
				OdataType = "#microsoft.graph.identity",
				DisplayName = "Calling Bot",
				Id = "2891555a-92ff-42e6-80fa-6e1300c6b5c6",
			},
		},
		Region = null,
		LanguageId = null,
	},
	Targets = new List<InvitationParticipantInfo>
	{
		new InvitationParticipantInfo
		{
			OdataType = "#microsoft.graph.invitationParticipantInfo",
			Identity = new IdentitySet
			{
				OdataType = "#microsoft.graph.identitySet",
				User = new Identity
				{
					OdataType = "#microsoft.graph.identity",
					DisplayName = "John",
					Id = "112f7296-5fa4-42ca-bae8-6a692b15d4b8",
				},
			},
		},
	},
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new AppHostedMediaConfig
	{
		OdataType = "#microsoft.graph.appHostedMediaConfig",
		Blob = "<Media Session Configuration>",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
source := graphmodels.NewParticipantInfo()
identity := graphmodels.NewIdentitySet()
application := graphmodels.NewIdentity()
displayName := "Calling Bot"
application.SetDisplayName(&displayName) 
id := "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
application.SetId(&id) 
identity.SetApplication(application)
source.SetIdentity(identity)
region := null
source.SetRegion(&region) 
languageId := null
source.SetLanguageId(&languageId) 
requestBody.SetSource(source)


invitationParticipantInfo := graphmodels.NewInvitationParticipantInfo()
identity := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
displayName := "John"
user.SetDisplayName(&displayName) 
id := "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
user.SetId(&id) 
identity.SetUser(user)
invitationParticipantInfo.SetIdentity(identity)

targets := []graphmodels.InvitationParticipantInfoable {
	invitationParticipantInfo,
}
requestBody.SetTargets(targets)
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewAppHostedMediaConfig()
blob := "<Media Session Configuration>"
mediaConfig.SetBlob(&blob) 
requestBody.SetMediaConfig(mediaConfig)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setCallbackUri("https://bot.contoso.com/callback");
ParticipantInfo source = new ParticipantInfo();
source.setOdataType("#microsoft.graph.participantInfo");
IdentitySet identity = new IdentitySet();
identity.setOdataType("#microsoft.graph.identitySet");
Identity application = new Identity();
application.setOdataType("#microsoft.graph.identity");
application.setDisplayName("Calling Bot");
application.setId("2891555a-92ff-42e6-80fa-6e1300c6b5c6");
identity.setApplication(application);
source.setIdentity(identity);
source.setRegion(null);
source.setLanguageId(null);
call.setSource(source);
LinkedList<InvitationParticipantInfo> targets = new LinkedList<InvitationParticipantInfo>();
InvitationParticipantInfo invitationParticipantInfo = new InvitationParticipantInfo();
invitationParticipantInfo.setOdataType("#microsoft.graph.invitationParticipantInfo");
IdentitySet identity1 = new IdentitySet();
identity1.setOdataType("#microsoft.graph.identitySet");
Identity user = new Identity();
user.setOdataType("#microsoft.graph.identity");
user.setDisplayName("John");
user.setId("112f7296-5fa4-42ca-bae8-6a692b15d4b8");
identity1.setUser(user);
invitationParticipantInfo.setIdentity(identity1);
targets.add(invitationParticipantInfo);
call.setTargets(targets);
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
AppHostedMediaConfig mediaConfig = new AppHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.appHostedMediaConfig");
mediaConfig.setBlob("<Media Session Configuration>");
call.setMediaConfig(mediaConfig);
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  callbackUri: 'https://bot.contoso.com/callback',
  source: {
    '@odata.type': '#microsoft.graph.participantInfo',
    identity: {
      '@odata.type': '#microsoft.graph.identitySet',
      application: {
        '@odata.type': '#microsoft.graph.identity',
        displayName: 'Calling Bot',
        id: '2891555a-92ff-42e6-80fa-6e1300c6b5c6'
      }
    },
    region: null,
    languageId: null
  },
  targets: [
    {
      '@odata.type': '#microsoft.graph.invitationParticipantInfo',
      identity: {
        '@odata.type': '#microsoft.graph.identitySet',
        user: {
          '@odata.type': '#microsoft.graph.identity',
          displayName: 'John',
          id: '112f7296-5fa4-42ca-bae8-6a692b15d4b8'
        }
      }
    }
  ],
  requestedModalities: [
    'audio'
  ],
 mediaConfig: {
    '@odata.type': '#microsoft.graph.appHostedMediaConfig',
    blob: '<Media Session Configuration>'
  }
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\ParticipantInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\InvitationParticipantInfo;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\AppHostedMediaConfig;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$source = new ParticipantInfo();
$source->setOdataType('#microsoft.graph.participantInfo');
$sourceIdentity = new IdentitySet();
$sourceIdentity->setOdataType('#microsoft.graph.identitySet');
$sourceIdentityApplication = new Identity();
$sourceIdentityApplication->setOdataType('#microsoft.graph.identity');
$sourceIdentityApplication->setDisplayName('Calling Bot');
$sourceIdentityApplication->setId('2891555a-92ff-42e6-80fa-6e1300c6b5c6');
$sourceIdentity->setApplication($sourceIdentityApplication);
$source->setIdentity($sourceIdentity);
$source->setRegion(null);
$source->setLanguageId(null);
$requestBody->setSource($source);
$targetsInvitationParticipantInfo1 = new InvitationParticipantInfo();
$targetsInvitationParticipantInfo1->setOdataType('#microsoft.graph.invitationParticipantInfo');
$targetsInvitationParticipantInfo1Identity = new IdentitySet();
$targetsInvitationParticipantInfo1Identity->setOdataType('#microsoft.graph.identitySet');
$targetsInvitationParticipantInfo1IdentityUser = new Identity();
$targetsInvitationParticipantInfo1IdentityUser->setOdataType('#microsoft.graph.identity');
$targetsInvitationParticipantInfo1IdentityUser->setDisplayName('John');
$targetsInvitationParticipantInfo1IdentityUser->setId('112f7296-5fa4-42ca-bae8-6a692b15d4b8');
$targetsInvitationParticipantInfo1Identity->setUser($targetsInvitationParticipantInfo1IdentityUser);
$targetsInvitationParticipantInfo1->setIdentity($targetsInvitationParticipantInfo1Identity);
$targetsArray []= $targetsInvitationParticipantInfo1;
$requestBody->setTargets($targetsArray);

$requestBody->setRequestedModalities([new Modality('audio'),]);
$mediaConfig = new AppHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.appHostedMediaConfig');
$mediaConfig->setBlob('<Media Session Configuration>');
$requestBody->setMediaConfig($mediaConfig);

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	callbackUri = "https://bot.contoso.com/callback"
	source = @{
		"@odata.type" = "#microsoft.graph.participantInfo"
		identity = @{
			"@odata.type" = "#microsoft.graph.identitySet"
			application = @{
				"@odata.type" = "#microsoft.graph.identity"
				displayName = "Calling Bot"
				id = "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
			}
		}
		region = $null
		languageId = $null
	}
	targets = @(
		@{
			"@odata.type" = "#microsoft.graph.invitationParticipantInfo"
			identity = @{
				"@odata.type" = "#microsoft.graph.identitySet"
				user = @{
					"@odata.type" = "#microsoft.graph.identity"
					displayName = "John"
					id = "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
				}
			}
		}
	)
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.appHostedMediaConfig"
	blob = "<Media Session Configuration>"
}
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.participant_info import ParticipantInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.invitation_participant_info import InvitationParticipantInfo
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.app_hosted_media_config import AppHostedMediaConfig
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	callback_uri = "https://bot.contoso.com/callback",
	source = ParticipantInfo(
		odata_type = "#microsoft.graph.participantInfo",
		identity = IdentitySet(
			odata_type = "#microsoft.graph.identitySet",
			application = Identity(
				odata_type = "#microsoft.graph.identity",
				display_name = "Calling Bot",
				id = "2891555a-92ff-42e6-80fa-6e1300c6b5c6",
			),
		),
		region = None,
		language_id = None,
	),
	targets = [
		InvitationParticipantInfo(
			odata_type = "#microsoft.graph.invitationParticipantInfo",
			identity = IdentitySet(
				odata_type = "#microsoft.graph.identitySet",
				user = Identity(
					odata_type = "#microsoft.graph.identity",
					display_name = "John",
					id = "112f7296-5fa4-42ca-bae8-6a692b15d4b8",
				),
			),
		),
	],
	requested_modalities = [
		Modality.Audio,
	],
	media_config = AppHostedMediaConfig(
		odata_type = "#microsoft.graph.appHostedMediaConfig",
		blob = "<Media Session Configuration>",
	),
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

> **Note:** For peer-to-peer calls, the expected notifications are for call state changes only.

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2e1a0b00-2db4-4022-9570-243709c565ab
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
      }
    },
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "John",
          "id": "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration>",
  },
  "myParticipantId": "499ff390-7a72-40e8-83a0-8fac6295ae7e",
  "id": "2e1a0b00-2db4-4022-9570-243709c565ab",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
  "subject": null,
  "ringingTimeoutInSeconds": null,
  "mediaState": null,
  "resultInfo": null,
  "answeredBy": null,
  "chatInfo": null,
  "meetingInfo": null,
  "transcription": null,
  "toneInfo": null
}
```

### Example 3: Create a group call with service hosted media

This supports up to 5 VoIP users. The example shows how to create a group call with two VoIP users.

> **Note:** This example call needs the `Calls.InitiateGroupCalls.All` permission. The group call created doesn't support chat or recording.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "direction": "outgoing",
  "subject": "Create a group call with service hosted media",
  "callbackUri": "https://bot.contoso.com/callback",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "TestBot",
        "id": "dd3885da-f9ab-486b-bfae-85de3d445555"
      }
    }
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "user1",
          "id": "98da8a1a-1b87-452c-a713-65d3f10b5555"
        }
      }
    },
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "user2",
          "id": "bf5aae9a-d11d-47a8-93b1-782504c95555"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "removeFromDefaultAudioGroup": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	Direction = CallDirection.Outgoing,
	Subject = "Create a group call with service hosted media",
	CallbackUri = "https://bot.contoso.com/callback",
	Source = new ParticipantInfo
	{
		OdataType = "#microsoft.graph.participantInfo",
		Identity = new IdentitySet
		{
			OdataType = "#microsoft.graph.identitySet",
			Application = new Identity
			{
				OdataType = "#microsoft.graph.identity",
				DisplayName = "TestBot",
				Id = "dd3885da-f9ab-486b-bfae-85de3d445555",
			},
		},
	},
	Targets = new List<InvitationParticipantInfo>
	{
		new InvitationParticipantInfo
		{
			OdataType = "#microsoft.graph.invitationParticipantInfo",
			Identity = new IdentitySet
			{
				OdataType = "#microsoft.graph.identitySet",
				User = new Identity
				{
					OdataType = "#microsoft.graph.identity",
					DisplayName = "user1",
					Id = "98da8a1a-1b87-452c-a713-65d3f10b5555",
				},
			},
		},
		new InvitationParticipantInfo
		{
			OdataType = "#microsoft.graph.invitationParticipantInfo",
			Identity = new IdentitySet
			{
				OdataType = "#microsoft.graph.identitySet",
				User = new Identity
				{
					OdataType = "#microsoft.graph.identity",
					DisplayName = "user2",
					Id = "bf5aae9a-d11d-47a8-93b1-782504c95555",
				},
			},
		},
	},
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new ServiceHostedMediaConfig
	{
		OdataType = "#microsoft.graph.serviceHostedMediaConfig",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"removeFromDefaultAudioGroup" , false
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
direction := graphmodels.OUTGOING_CALLDIRECTION 
requestBody.SetDirection(&direction) 
subject := "Create a group call with service hosted media"
requestBody.SetSubject(&subject) 
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
source := graphmodels.NewParticipantInfo()
identity := graphmodels.NewIdentitySet()
application := graphmodels.NewIdentity()
displayName := "TestBot"
application.SetDisplayName(&displayName) 
id := "dd3885da-f9ab-486b-bfae-85de3d445555"
application.SetId(&id) 
identity.SetApplication(application)
source.SetIdentity(identity)
requestBody.SetSource(source)


invitationParticipantInfo := graphmodels.NewInvitationParticipantInfo()
identity := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
displayName := "user1"
user.SetDisplayName(&displayName) 
id := "98da8a1a-1b87-452c-a713-65d3f10b5555"
user.SetId(&id) 
identity.SetUser(user)
invitationParticipantInfo.SetIdentity(identity)
invitationParticipantInfo1 := graphmodels.NewInvitationParticipantInfo()
identity := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
displayName := "user2"
user.SetDisplayName(&displayName) 
id := "bf5aae9a-d11d-47a8-93b1-782504c95555"
user.SetId(&id) 
identity.SetUser(user)
invitationParticipantInfo1.SetIdentity(identity)

targets := []graphmodels.InvitationParticipantInfoable {
	invitationParticipantInfo,
	invitationParticipantInfo1,
}
requestBody.SetTargets(targets)
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewServiceHostedMediaConfig()
additionalData := map[string]interface{}{
	removeFromDefaultAudioGroup := false
mediaConfig.SetRemoveFromDefaultAudioGroup(&removeFromDefaultAudioGroup) 
}
mediaConfig.SetAdditionalData(additionalData)
requestBody.SetMediaConfig(mediaConfig)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setDirection(CallDirection.Outgoing);
call.setSubject("Create a group call with service hosted media");
call.setCallbackUri("https://bot.contoso.com/callback");
ParticipantInfo source = new ParticipantInfo();
source.setOdataType("#microsoft.graph.participantInfo");
IdentitySet identity = new IdentitySet();
identity.setOdataType("#microsoft.graph.identitySet");
Identity application = new Identity();
application.setOdataType("#microsoft.graph.identity");
application.setDisplayName("TestBot");
application.setId("dd3885da-f9ab-486b-bfae-85de3d445555");
identity.setApplication(application);
source.setIdentity(identity);
call.setSource(source);
LinkedList<InvitationParticipantInfo> targets = new LinkedList<InvitationParticipantInfo>();
InvitationParticipantInfo invitationParticipantInfo = new InvitationParticipantInfo();
invitationParticipantInfo.setOdataType("#microsoft.graph.invitationParticipantInfo");
IdentitySet identity1 = new IdentitySet();
identity1.setOdataType("#microsoft.graph.identitySet");
Identity user = new Identity();
user.setOdataType("#microsoft.graph.identity");
user.setDisplayName("user1");
user.setId("98da8a1a-1b87-452c-a713-65d3f10b5555");
identity1.setUser(user);
invitationParticipantInfo.setIdentity(identity1);
targets.add(invitationParticipantInfo);
InvitationParticipantInfo invitationParticipantInfo1 = new InvitationParticipantInfo();
invitationParticipantInfo1.setOdataType("#microsoft.graph.invitationParticipantInfo");
IdentitySet identity2 = new IdentitySet();
identity2.setOdataType("#microsoft.graph.identitySet");
Identity user1 = new Identity();
user1.setOdataType("#microsoft.graph.identity");
user1.setDisplayName("user2");
user1.setId("bf5aae9a-d11d-47a8-93b1-782504c95555");
identity2.setUser(user1);
invitationParticipantInfo1.setIdentity(identity2);
targets.add(invitationParticipantInfo1);
call.setTargets(targets);
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
ServiceHostedMediaConfig mediaConfig = new ServiceHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.serviceHostedMediaConfig");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("removeFromDefaultAudioGroup", false);
mediaConfig.setAdditionalData(additionalData);
call.setMediaConfig(mediaConfig);
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  direction: 'outgoing',
  subject: 'Create a group call with service hosted media',
  callbackUri: 'https://bot.contoso.com/callback',
  source: {
    '@odata.type': '#microsoft.graph.participantInfo',
    identity: {
      '@odata.type': '#microsoft.graph.identitySet',
      application: {
        '@odata.type': '#microsoft.graph.identity',
        displayName: 'TestBot',
        id: 'dd3885da-f9ab-486b-bfae-85de3d445555'
      }
    }
  },
  targets: [
    {
      '@odata.type': '#microsoft.graph.invitationParticipantInfo',
      identity: {
        '@odata.type': '#microsoft.graph.identitySet',
        user: {
          '@odata.type': '#microsoft.graph.identity',
          displayName: 'user1',
          id: '98da8a1a-1b87-452c-a713-65d3f10b5555'
        }
      }
    },
    {
      '@odata.type': '#microsoft.graph.invitationParticipantInfo',
      identity: {
        '@odata.type': '#microsoft.graph.identitySet',
        user: {
          '@odata.type': '#microsoft.graph.identity',
          displayName: 'user2',
          id: 'bf5aae9a-d11d-47a8-93b1-782504c95555'
        }
      }
    }
  ],
  requestedModalities: [
    'audio'
  ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.serviceHostedMediaConfig',
    removeFromDefaultAudioGroup: false
  }
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\CallDirection;
use Microsoft\Graph\Generated\Models\ParticipantInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\InvitationParticipantInfo;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\ServiceHostedMediaConfig;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setDirection(new CallDirection('outgoing'));
$requestBody->setSubject('Create a group call with service hosted media');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$source = new ParticipantInfo();
$source->setOdataType('#microsoft.graph.participantInfo');
$sourceIdentity = new IdentitySet();
$sourceIdentity->setOdataType('#microsoft.graph.identitySet');
$sourceIdentityApplication = new Identity();
$sourceIdentityApplication->setOdataType('#microsoft.graph.identity');
$sourceIdentityApplication->setDisplayName('TestBot');
$sourceIdentityApplication->setId('dd3885da-f9ab-486b-bfae-85de3d445555');
$sourceIdentity->setApplication($sourceIdentityApplication);
$source->setIdentity($sourceIdentity);
$requestBody->setSource($source);
$targetsInvitationParticipantInfo1 = new InvitationParticipantInfo();
$targetsInvitationParticipantInfo1->setOdataType('#microsoft.graph.invitationParticipantInfo');
$targetsInvitationParticipantInfo1Identity = new IdentitySet();
$targetsInvitationParticipantInfo1Identity->setOdataType('#microsoft.graph.identitySet');
$targetsInvitationParticipantInfo1IdentityUser = new Identity();
$targetsInvitationParticipantInfo1IdentityUser->setOdataType('#microsoft.graph.identity');
$targetsInvitationParticipantInfo1IdentityUser->setDisplayName('user1');
$targetsInvitationParticipantInfo1IdentityUser->setId('98da8a1a-1b87-452c-a713-65d3f10b5555');
$targetsInvitationParticipantInfo1Identity->setUser($targetsInvitationParticipantInfo1IdentityUser);
$targetsInvitationParticipantInfo1->setIdentity($targetsInvitationParticipantInfo1Identity);
$targetsArray []= $targetsInvitationParticipantInfo1;
$targetsInvitationParticipantInfo2 = new InvitationParticipantInfo();
$targetsInvitationParticipantInfo2->setOdataType('#microsoft.graph.invitationParticipantInfo');
$targetsInvitationParticipantInfo2Identity = new IdentitySet();
$targetsInvitationParticipantInfo2Identity->setOdataType('#microsoft.graph.identitySet');
$targetsInvitationParticipantInfo2IdentityUser = new Identity();
$targetsInvitationParticipantInfo2IdentityUser->setOdataType('#microsoft.graph.identity');
$targetsInvitationParticipantInfo2IdentityUser->setDisplayName('user2');
$targetsInvitationParticipantInfo2IdentityUser->setId('bf5aae9a-d11d-47a8-93b1-782504c95555');
$targetsInvitationParticipantInfo2Identity->setUser($targetsInvitationParticipantInfo2IdentityUser);
$targetsInvitationParticipantInfo2->setIdentity($targetsInvitationParticipantInfo2Identity);
$targetsArray []= $targetsInvitationParticipantInfo2;
$requestBody->setTargets($targetsArray);

$requestBody->setRequestedModalities([new Modality('audio'),]);
$mediaConfig = new ServiceHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.serviceHostedMediaConfig');
$additionalData = [
'removeFromDefaultAudioGroup' => false,
];
$mediaConfig->setAdditionalData($additionalData);
$requestBody->setMediaConfig($mediaConfig);

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	direction = "outgoing"
	subject = "Create a group call with service hosted media"
	callbackUri = "https://bot.contoso.com/callback"
	source = @{
		"@odata.type" = "#microsoft.graph.participantInfo"
		identity = @{
			"@odata.type" = "#microsoft.graph.identitySet"
			application = @{
				"@odata.type" = "#microsoft.graph.identity"
				displayName = "TestBot"
				id = "dd3885da-f9ab-486b-bfae-85de3d445555"
			}
		}
	}
	targets = @(
		@{
			"@odata.type" = "#microsoft.graph.invitationParticipantInfo"
			identity = @{
				"@odata.type" = "#microsoft.graph.identitySet"
				user = @{
					"@odata.type" = "#microsoft.graph.identity"
					displayName = "user1"
					id = "98da8a1a-1b87-452c-a713-65d3f10b5555"
				}
			}
		}
		@{
			"@odata.type" = "#microsoft.graph.invitationParticipantInfo"
			identity = @{
				"@odata.type" = "#microsoft.graph.identitySet"
				user = @{
					"@odata.type" = "#microsoft.graph.identity"
					displayName = "user2"
					id = "bf5aae9a-d11d-47a8-93b1-782504c95555"
				}
			}
		}
	)
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.serviceHostedMediaConfig"
	removeFromDefaultAudioGroup = $false
}
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.call_direction import CallDirection
from msgraph.generated.models.participant_info import ParticipantInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.invitation_participant_info import InvitationParticipantInfo
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.service_hosted_media_config import ServiceHostedMediaConfig
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	direction = CallDirection.Outgoing,
	subject = "Create a group call with service hosted media",
	callback_uri = "https://bot.contoso.com/callback",
	source = ParticipantInfo(
		odata_type = "#microsoft.graph.participantInfo",
		identity = IdentitySet(
			odata_type = "#microsoft.graph.identitySet",
			application = Identity(
				odata_type = "#microsoft.graph.identity",
				display_name = "TestBot",
				id = "dd3885da-f9ab-486b-bfae-85de3d445555",
			),
		),
	),
	targets = [
		InvitationParticipantInfo(
			odata_type = "#microsoft.graph.invitationParticipantInfo",
			identity = IdentitySet(
				odata_type = "#microsoft.graph.identitySet",
				user = Identity(
					odata_type = "#microsoft.graph.identity",
					display_name = "user1",
					id = "98da8a1a-1b87-452c-a713-65d3f10b5555",
				),
			),
		),
		InvitationParticipantInfo(
			odata_type = "#microsoft.graph.invitationParticipantInfo",
			identity = IdentitySet(
				odata_type = "#microsoft.graph.identitySet",
				user = Identity(
					odata_type = "#microsoft.graph.identity",
					display_name = "user2",
					id = "bf5aae9a-d11d-47a8-93b1-782504c95555",
				),
			),
		),
	],
	requested_modalities = [
		Modality.Audio,
	],
	media_config = ServiceHostedMediaConfig(
		odata_type = "#microsoft.graph.serviceHostedMediaConfig",
		additional_data = {
				"remove_from_default_audio_group" : False,
		}
	),
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "subject": "Create a group call with service hosted media",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d17646-3110-40b1-bae6-e9ac6c3f74",
  "callRoutes": [],
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "TestBot",
        "id": "dd3885da-f9ab-486b-bfae-85de3d445555"
      }
    },
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "user1",
          "id": "98da8a1a-1b87-452c-a713-65d3f10b5555"
        }
      }
    },
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "user2",
          "id": "bf5aae9a-d11d-47a8-93b1-782504c95555"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "activeModalities": [],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
  },
  "routingPolicies": [],
  "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a",
  "id": "2f1a1100-b174-40a0-aba7-0b405e01ed92",
  "myParticipantId": "c9a65b85-a223-44ae-8cdb-29395458323f",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
}
```

### Example 4: Create a group call with application hosted media

This supports up to 5 VoIP users. The example shows how to create a group call with two VoIP users.

> **Note:** This example call needs the `Calls.InitiateGroupCalls.All` permission. The group call created doesn't support chat or recording.

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "direction": "outgoing",
  "subject": "Create a group call with application hosted media",
  "callbackUri": "https://bot.contoso.com/callback",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "TestBot",
        "id": "dd3885da-f9ab-486b-bfae-85de3d445555"
      }
    }
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "user1",
          "id": "98da8a1a-1b87-452c-a713-65d3f10b5555"
        }
      }
    },
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "user2",
          "id": "bf5aae9a-d11d-47a8-93b1-782504c95555"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "removeFromDefaultAudioGroup": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	Direction = CallDirection.Outgoing,
	Subject = "Create a group call with application hosted media",
	CallbackUri = "https://bot.contoso.com/callback",
	Source = new ParticipantInfo
	{
		OdataType = "#microsoft.graph.participantInfo",
		Identity = new IdentitySet
		{
			OdataType = "#microsoft.graph.identitySet",
			Application = new Identity
			{
				OdataType = "#microsoft.graph.identity",
				DisplayName = "TestBot",
				Id = "dd3885da-f9ab-486b-bfae-85de3d445555",
			},
		},
	},
	Targets = new List<InvitationParticipantInfo>
	{
		new InvitationParticipantInfo
		{
			OdataType = "#microsoft.graph.invitationParticipantInfo",
			Identity = new IdentitySet
			{
				OdataType = "#microsoft.graph.identitySet",
				User = new Identity
				{
					OdataType = "#microsoft.graph.identity",
					DisplayName = "user1",
					Id = "98da8a1a-1b87-452c-a713-65d3f10b5555",
				},
			},
		},
		new InvitationParticipantInfo
		{
			OdataType = "#microsoft.graph.invitationParticipantInfo",
			Identity = new IdentitySet
			{
				OdataType = "#microsoft.graph.identitySet",
				User = new Identity
				{
					OdataType = "#microsoft.graph.identity",
					DisplayName = "user2",
					Id = "bf5aae9a-d11d-47a8-93b1-782504c95555",
				},
			},
		},
	},
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new AppHostedMediaConfig
	{
		OdataType = "#microsoft.graph.appHostedMediaConfig",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"removeFromDefaultAudioGroup" , false
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
direction := graphmodels.OUTGOING_CALLDIRECTION 
requestBody.SetDirection(&direction) 
subject := "Create a group call with application hosted media"
requestBody.SetSubject(&subject) 
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
source := graphmodels.NewParticipantInfo()
identity := graphmodels.NewIdentitySet()
application := graphmodels.NewIdentity()
displayName := "TestBot"
application.SetDisplayName(&displayName) 
id := "dd3885da-f9ab-486b-bfae-85de3d445555"
application.SetId(&id) 
identity.SetApplication(application)
source.SetIdentity(identity)
requestBody.SetSource(source)


invitationParticipantInfo := graphmodels.NewInvitationParticipantInfo()
identity := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
displayName := "user1"
user.SetDisplayName(&displayName) 
id := "98da8a1a-1b87-452c-a713-65d3f10b5555"
user.SetId(&id) 
identity.SetUser(user)
invitationParticipantInfo.SetIdentity(identity)
invitationParticipantInfo1 := graphmodels.NewInvitationParticipantInfo()
identity := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
displayName := "user2"
user.SetDisplayName(&displayName) 
id := "bf5aae9a-d11d-47a8-93b1-782504c95555"
user.SetId(&id) 
identity.SetUser(user)
invitationParticipantInfo1.SetIdentity(identity)

targets := []graphmodels.InvitationParticipantInfoable {
	invitationParticipantInfo,
	invitationParticipantInfo1,
}
requestBody.SetTargets(targets)
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewAppHostedMediaConfig()
additionalData := map[string]interface{}{
	removeFromDefaultAudioGroup := false
mediaConfig.SetRemoveFromDefaultAudioGroup(&removeFromDefaultAudioGroup) 
}
mediaConfig.SetAdditionalData(additionalData)
requestBody.SetMediaConfig(mediaConfig)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setDirection(CallDirection.Outgoing);
call.setSubject("Create a group call with application hosted media");
call.setCallbackUri("https://bot.contoso.com/callback");
ParticipantInfo source = new ParticipantInfo();
source.setOdataType("#microsoft.graph.participantInfo");
IdentitySet identity = new IdentitySet();
identity.setOdataType("#microsoft.graph.identitySet");
Identity application = new Identity();
application.setOdataType("#microsoft.graph.identity");
application.setDisplayName("TestBot");
application.setId("dd3885da-f9ab-486b-bfae-85de3d445555");
identity.setApplication(application);
source.setIdentity(identity);
call.setSource(source);
LinkedList<InvitationParticipantInfo> targets = new LinkedList<InvitationParticipantInfo>();
InvitationParticipantInfo invitationParticipantInfo = new InvitationParticipantInfo();
invitationParticipantInfo.setOdataType("#microsoft.graph.invitationParticipantInfo");
IdentitySet identity1 = new IdentitySet();
identity1.setOdataType("#microsoft.graph.identitySet");
Identity user = new Identity();
user.setOdataType("#microsoft.graph.identity");
user.setDisplayName("user1");
user.setId("98da8a1a-1b87-452c-a713-65d3f10b5555");
identity1.setUser(user);
invitationParticipantInfo.setIdentity(identity1);
targets.add(invitationParticipantInfo);
InvitationParticipantInfo invitationParticipantInfo1 = new InvitationParticipantInfo();
invitationParticipantInfo1.setOdataType("#microsoft.graph.invitationParticipantInfo");
IdentitySet identity2 = new IdentitySet();
identity2.setOdataType("#microsoft.graph.identitySet");
Identity user1 = new Identity();
user1.setOdataType("#microsoft.graph.identity");
user1.setDisplayName("user2");
user1.setId("bf5aae9a-d11d-47a8-93b1-782504c95555");
identity2.setUser(user1);
invitationParticipantInfo1.setIdentity(identity2);
targets.add(invitationParticipantInfo1);
call.setTargets(targets);
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
AppHostedMediaConfig mediaConfig = new AppHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.appHostedMediaConfig");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("removeFromDefaultAudioGroup", false);
mediaConfig.setAdditionalData(additionalData);
call.setMediaConfig(mediaConfig);
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  direction: 'outgoing',
  subject: 'Create a group call with application hosted media',
  callbackUri: 'https://bot.contoso.com/callback',
  source: {
    '@odata.type': '#microsoft.graph.participantInfo',
    identity: {
      '@odata.type': '#microsoft.graph.identitySet',
      application: {
        '@odata.type': '#microsoft.graph.identity',
        displayName: 'TestBot',
        id: 'dd3885da-f9ab-486b-bfae-85de3d445555'
      }
    }
  },
  targets: [
    {
      '@odata.type': '#microsoft.graph.invitationParticipantInfo',
      identity: {
        '@odata.type': '#microsoft.graph.identitySet',
        user: {
          '@odata.type': '#microsoft.graph.identity',
          displayName: 'user1',
          id: '98da8a1a-1b87-452c-a713-65d3f10b5555'
        }
      }
    },
    {
      '@odata.type': '#microsoft.graph.invitationParticipantInfo',
      identity: {
        '@odata.type': '#microsoft.graph.identitySet',
        user: {
          '@odata.type': '#microsoft.graph.identity',
          displayName: 'user2',
          id: 'bf5aae9a-d11d-47a8-93b1-782504c95555'
        }
      }
    }
  ],
  requestedModalities: [
    'audio'
  ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.appHostedMediaConfig',
    removeFromDefaultAudioGroup: false
  }
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\CallDirection;
use Microsoft\Graph\Generated\Models\ParticipantInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\InvitationParticipantInfo;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\AppHostedMediaConfig;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setDirection(new CallDirection('outgoing'));
$requestBody->setSubject('Create a group call with application hosted media');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$source = new ParticipantInfo();
$source->setOdataType('#microsoft.graph.participantInfo');
$sourceIdentity = new IdentitySet();
$sourceIdentity->setOdataType('#microsoft.graph.identitySet');
$sourceIdentityApplication = new Identity();
$sourceIdentityApplication->setOdataType('#microsoft.graph.identity');
$sourceIdentityApplication->setDisplayName('TestBot');
$sourceIdentityApplication->setId('dd3885da-f9ab-486b-bfae-85de3d445555');
$sourceIdentity->setApplication($sourceIdentityApplication);
$source->setIdentity($sourceIdentity);
$requestBody->setSource($source);
$targetsInvitationParticipantInfo1 = new InvitationParticipantInfo();
$targetsInvitationParticipantInfo1->setOdataType('#microsoft.graph.invitationParticipantInfo');
$targetsInvitationParticipantInfo1Identity = new IdentitySet();
$targetsInvitationParticipantInfo1Identity->setOdataType('#microsoft.graph.identitySet');
$targetsInvitationParticipantInfo1IdentityUser = new Identity();
$targetsInvitationParticipantInfo1IdentityUser->setOdataType('#microsoft.graph.identity');
$targetsInvitationParticipantInfo1IdentityUser->setDisplayName('user1');
$targetsInvitationParticipantInfo1IdentityUser->setId('98da8a1a-1b87-452c-a713-65d3f10b5555');
$targetsInvitationParticipantInfo1Identity->setUser($targetsInvitationParticipantInfo1IdentityUser);
$targetsInvitationParticipantInfo1->setIdentity($targetsInvitationParticipantInfo1Identity);
$targetsArray []= $targetsInvitationParticipantInfo1;
$targetsInvitationParticipantInfo2 = new InvitationParticipantInfo();
$targetsInvitationParticipantInfo2->setOdataType('#microsoft.graph.invitationParticipantInfo');
$targetsInvitationParticipantInfo2Identity = new IdentitySet();
$targetsInvitationParticipantInfo2Identity->setOdataType('#microsoft.graph.identitySet');
$targetsInvitationParticipantInfo2IdentityUser = new Identity();
$targetsInvitationParticipantInfo2IdentityUser->setOdataType('#microsoft.graph.identity');
$targetsInvitationParticipantInfo2IdentityUser->setDisplayName('user2');
$targetsInvitationParticipantInfo2IdentityUser->setId('bf5aae9a-d11d-47a8-93b1-782504c95555');
$targetsInvitationParticipantInfo2Identity->setUser($targetsInvitationParticipantInfo2IdentityUser);
$targetsInvitationParticipantInfo2->setIdentity($targetsInvitationParticipantInfo2Identity);
$targetsArray []= $targetsInvitationParticipantInfo2;
$requestBody->setTargets($targetsArray);

$requestBody->setRequestedModalities([new Modality('audio'),]);
$mediaConfig = new AppHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.appHostedMediaConfig');
$additionalData = [
'removeFromDefaultAudioGroup' => false,
];
$mediaConfig->setAdditionalData($additionalData);
$requestBody->setMediaConfig($mediaConfig);

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	direction = "outgoing"
	subject = "Create a group call with application hosted media"
	callbackUri = "https://bot.contoso.com/callback"
	source = @{
		"@odata.type" = "#microsoft.graph.participantInfo"
		identity = @{
			"@odata.type" = "#microsoft.graph.identitySet"
			application = @{
				"@odata.type" = "#microsoft.graph.identity"
				displayName = "TestBot"
				id = "dd3885da-f9ab-486b-bfae-85de3d445555"
			}
		}
	}
	targets = @(
		@{
			"@odata.type" = "#microsoft.graph.invitationParticipantInfo"
			identity = @{
				"@odata.type" = "#microsoft.graph.identitySet"
				user = @{
					"@odata.type" = "#microsoft.graph.identity"
					displayName = "user1"
					id = "98da8a1a-1b87-452c-a713-65d3f10b5555"
				}
			}
		}
		@{
			"@odata.type" = "#microsoft.graph.invitationParticipantInfo"
			identity = @{
				"@odata.type" = "#microsoft.graph.identitySet"
				user = @{
					"@odata.type" = "#microsoft.graph.identity"
					displayName = "user2"
					id = "bf5aae9a-d11d-47a8-93b1-782504c95555"
				}
			}
		}
	)
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.appHostedMediaConfig"
	removeFromDefaultAudioGroup = $false
}
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.call_direction import CallDirection
from msgraph.generated.models.participant_info import ParticipantInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.invitation_participant_info import InvitationParticipantInfo
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.app_hosted_media_config import AppHostedMediaConfig
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	direction = CallDirection.Outgoing,
	subject = "Create a group call with application hosted media",
	callback_uri = "https://bot.contoso.com/callback",
	source = ParticipantInfo(
		odata_type = "#microsoft.graph.participantInfo",
		identity = IdentitySet(
			odata_type = "#microsoft.graph.identitySet",
			application = Identity(
				odata_type = "#microsoft.graph.identity",
				display_name = "TestBot",
				id = "dd3885da-f9ab-486b-bfae-85de3d445555",
			),
		),
	),
	targets = [
		InvitationParticipantInfo(
			odata_type = "#microsoft.graph.invitationParticipantInfo",
			identity = IdentitySet(
				odata_type = "#microsoft.graph.identitySet",
				user = Identity(
					odata_type = "#microsoft.graph.identity",
					display_name = "user1",
					id = "98da8a1a-1b87-452c-a713-65d3f10b5555",
				),
			),
		),
		InvitationParticipantInfo(
			odata_type = "#microsoft.graph.invitationParticipantInfo",
			identity = IdentitySet(
				odata_type = "#microsoft.graph.identitySet",
				user = Identity(
					odata_type = "#microsoft.graph.identity",
					display_name = "user2",
					id = "bf5aae9a-d11d-47a8-93b1-782504c95555",
				),
			),
		),
	],
	requested_modalities = [
		Modality.Audio,
	],
	media_config = AppHostedMediaConfig(
		odata_type = "#microsoft.graph.appHostedMediaConfig",
		additional_data = {
				"remove_from_default_audio_group" : False,
		}
	),
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "subject": "Create a group call with app hosted media",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "callRoutes": [],
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "TestBot",
        "id": "dd3885da-f9ab-486b-bfae-85de3d445555"
      }
    },
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "user1",
          "id": "98da8a1a-1b87-452c-a713-65d3f10b5555"
        }
      }
    },
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "user": {
          "@odata.type": "#microsoft.graph.identity",
          "displayName": "user2",
          "id": "bf5aae9a-d11d-47a8-93b1-782504c95555"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "activeModalities": [],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration>",
    "removeFromDefaultAudioGroup": false
  },
  "routingPolicies": [],
  "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a",
  "id": "2f1a1100-b174-40a0-aba7-0b405e01ed92",
  "myParticipantId": "c9a65b85-a223-44ae-8cdb-29395458323f",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
}
```

### Example 5: Join scheduled meeting with service hosted media

To join the scheduled meeting, you need to get the thread ID, message ID, organizer ID, and the tenant ID in which the meeting is scheduled. You can get this information by using the [Get onlineMeeting](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-get?view=graph-rest-1.0) API.

The values of authorization token, callback URL, application ID, application name, user ID, user name, and tenant ID must be replaced along with the details obtained from the [Get onlineMeeting](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-get?view=graph-rest-1.0) API with actual values to make the example work.

> **Note:** This example needs the `Calls.JoinGroupCalls.All` permission.

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "callbackUri": "https://bot.contoso.com/callback",
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
     {
       "uri": "https://cdn.contoso.com/beep.wav",
       "resourceId": "f8971b04-b53e-418c-9222-c82ce681a582"
     },
     {
       "uri": "https://cdn.contoso.com/cool.wav",
       "resourceId": "86dc814b-c172-4428-9112-60f8ecae1edb"
     }
    ],
  },
  "chatInfo": {
    "@odata.type": "#microsoft.graph.chatInfo",
    "threadId": "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
    "messageId": "0"
  },
  "meetingInfo": {
    "@odata.type": "#microsoft.graph.organizerMeetingInfo",
    "organizer": {
      "@odata.type": "#microsoft.graph.identitySet",
      "user": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
        "displayName": "Bob",
        "tenantId":"86dc81db-c112-4228-9222-63f3esaa1edb"
      }
    },
    "allowConversationWithoutHost": true
  },
  "tenantId":"86dc81db-c112-4228-9222-63f3esaa1edb"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	CallbackUri = "https://bot.contoso.com/callback",
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new ServiceHostedMediaConfig
	{
		OdataType = "#microsoft.graph.serviceHostedMediaConfig",
		PreFetchMedia = new List<MediaInfo>
		{
			new MediaInfo
			{
				Uri = "https://cdn.contoso.com/beep.wav",
				ResourceId = "f8971b04-b53e-418c-9222-c82ce681a582",
			},
			new MediaInfo
			{
				Uri = "https://cdn.contoso.com/cool.wav",
				ResourceId = "86dc814b-c172-4428-9112-60f8ecae1edb",
			},
		},
	},
	ChatInfo = new ChatInfo
	{
		OdataType = "#microsoft.graph.chatInfo",
		ThreadId = "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
		MessageId = "0",
	},
	MeetingInfo = new OrganizerMeetingInfo
	{
		OdataType = "#microsoft.graph.organizerMeetingInfo",
		Organizer = new IdentitySet
		{
			OdataType = "#microsoft.graph.identitySet",
			User = new Identity
			{
				OdataType = "#microsoft.graph.identity",
				Id = "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
				DisplayName = "Bob",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"tenantId" , "86dc81db-c112-4228-9222-63f3esaa1edb"
					},
				},
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"allowConversationWithoutHost" , true
			},
		},
	},
	TenantId = "86dc81db-c112-4228-9222-63f3esaa1edb",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewServiceHostedMediaConfig()


mediaInfo := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/beep.wav"
mediaInfo.SetUri(&uri) 
resourceId := "f8971b04-b53e-418c-9222-c82ce681a582"
mediaInfo.SetResourceId(&resourceId) 
mediaInfo1 := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/cool.wav"
mediaInfo1.SetUri(&uri) 
resourceId := "86dc814b-c172-4428-9112-60f8ecae1edb"
mediaInfo1.SetResourceId(&resourceId) 

preFetchMedia := []graphmodels.MediaInfoable {
	mediaInfo,
	mediaInfo1,
}
mediaConfig.SetPreFetchMedia(preFetchMedia)
requestBody.SetMediaConfig(mediaConfig)
chatInfo := graphmodels.NewChatInfo()
threadId := "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2"
chatInfo.SetThreadId(&threadId) 
messageId := "0"
chatInfo.SetMessageId(&messageId) 
requestBody.SetChatInfo(chatInfo)
meetingInfo := graphmodels.NewOrganizerMeetingInfo()
organizer := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
id := "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96"
user.SetId(&id) 
displayName := "Bob"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"tenantId" : "86dc81db-c112-4228-9222-63f3esaa1edb", 
}
user.SetAdditionalData(additionalData)
organizer.SetUser(user)
meetingInfo.SetOrganizer(organizer)
additionalData := map[string]interface{}{
	allowConversationWithoutHost := true
meetingInfo.SetAllowConversationWithoutHost(&allowConversationWithoutHost) 
}
meetingInfo.SetAdditionalData(additionalData)
requestBody.SetMeetingInfo(meetingInfo)
tenantId := "86dc81db-c112-4228-9222-63f3esaa1edb"
requestBody.SetTenantId(&tenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setCallbackUri("https://bot.contoso.com/callback");
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
ServiceHostedMediaConfig mediaConfig = new ServiceHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.serviceHostedMediaConfig");
LinkedList<MediaInfo> preFetchMedia = new LinkedList<MediaInfo>();
MediaInfo mediaInfo = new MediaInfo();
mediaInfo.setUri("https://cdn.contoso.com/beep.wav");
mediaInfo.setResourceId("f8971b04-b53e-418c-9222-c82ce681a582");
preFetchMedia.add(mediaInfo);
MediaInfo mediaInfo1 = new MediaInfo();
mediaInfo1.setUri("https://cdn.contoso.com/cool.wav");
mediaInfo1.setResourceId("86dc814b-c172-4428-9112-60f8ecae1edb");
preFetchMedia.add(mediaInfo1);
mediaConfig.setPreFetchMedia(preFetchMedia);
call.setMediaConfig(mediaConfig);
ChatInfo chatInfo = new ChatInfo();
chatInfo.setOdataType("#microsoft.graph.chatInfo");
chatInfo.setThreadId("19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2");
chatInfo.setMessageId("0");
call.setChatInfo(chatInfo);
OrganizerMeetingInfo meetingInfo = new OrganizerMeetingInfo();
meetingInfo.setOdataType("#microsoft.graph.organizerMeetingInfo");
IdentitySet organizer = new IdentitySet();
organizer.setOdataType("#microsoft.graph.identitySet");
Identity user = new Identity();
user.setOdataType("#microsoft.graph.identity");
user.setId("5810cede-f3cc-42eb-b2c1-e9bd5d53ec96");
user.setDisplayName("Bob");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("tenantId", "86dc81db-c112-4228-9222-63f3esaa1edb");
user.setAdditionalData(additionalData);
organizer.setUser(user);
meetingInfo.setOrganizer(organizer);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("allowConversationWithoutHost", true);
meetingInfo.setAdditionalData(additionalData1);
call.setMeetingInfo(meetingInfo);
call.setTenantId("86dc81db-c112-4228-9222-63f3esaa1edb");
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  callbackUri: 'https://bot.contoso.com/callback',
  requestedModalities: [
    'audio'
  ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.serviceHostedMediaConfig',
    preFetchMedia: [
     {
       uri: 'https://cdn.contoso.com/beep.wav',
       resourceId: 'f8971b04-b53e-418c-9222-c82ce681a582'
     },
     {
       uri: 'https://cdn.contoso.com/cool.wav',
       resourceId: '86dc814b-c172-4428-9112-60f8ecae1edb'
     }
    ],
  },
  chatInfo: {
    '@odata.type': '#microsoft.graph.chatInfo',
    threadId: '19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2',
    messageId: '0'
  },
  meetingInfo: {
    '@odata.type': '#microsoft.graph.organizerMeetingInfo',
    organizer: {
      '@odata.type': '#microsoft.graph.identitySet',
      user: {
        '@odata.type': '#microsoft.graph.identity',
        id: '5810cede-f3cc-42eb-b2c1-e9bd5d53ec96',
        displayName: 'Bob',
        tenantId: '86dc81db-c112-4228-9222-63f3esaa1edb'
      }
    },
    allowConversationWithoutHost: true
  },
  tenantId: '86dc81db-c112-4228-9222-63f3esaa1edb'
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\ServiceHostedMediaConfig;
use Microsoft\Graph\Generated\Models\MediaInfo;
use Microsoft\Graph\Generated\Models\ChatInfo;
use Microsoft\Graph\Generated\Models\OrganizerMeetingInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$requestBody->setRequestedModalities([new Modality('audio'),	]);
$mediaConfig = new ServiceHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.serviceHostedMediaConfig');
$preFetchMediaMediaInfo1 = new MediaInfo();
$preFetchMediaMediaInfo1->setUri('https://cdn.contoso.com/beep.wav');
$preFetchMediaMediaInfo1->setResourceId('f8971b04-b53e-418c-9222-c82ce681a582');
$preFetchMediaArray []= $preFetchMediaMediaInfo1;
$preFetchMediaMediaInfo2 = new MediaInfo();
$preFetchMediaMediaInfo2->setUri('https://cdn.contoso.com/cool.wav');
$preFetchMediaMediaInfo2->setResourceId('86dc814b-c172-4428-9112-60f8ecae1edb');
$preFetchMediaArray []= $preFetchMediaMediaInfo2;
$mediaConfig->setPreFetchMedia($preFetchMediaArray);

$requestBody->setMediaConfig($mediaConfig);
$chatInfo = new ChatInfo();
$chatInfo->setOdataType('#microsoft.graph.chatInfo');
$chatInfo->setThreadId('19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2');
$chatInfo->setMessageId('0');
$requestBody->setChatInfo($chatInfo);
$meetingInfo = new OrganizerMeetingInfo();
$meetingInfo->setOdataType('#microsoft.graph.organizerMeetingInfo');
$meetingInfoOrganizer = new IdentitySet();
$meetingInfoOrganizer->setOdataType('#microsoft.graph.identitySet');
$meetingInfoOrganizerUser = new Identity();
$meetingInfoOrganizerUser->setOdataType('#microsoft.graph.identity');
$meetingInfoOrganizerUser->setId('5810cede-f3cc-42eb-b2c1-e9bd5d53ec96');
$meetingInfoOrganizerUser->setDisplayName('Bob');
$additionalData = [
'tenantId' => '86dc81db-c112-4228-9222-63f3esaa1edb',
];
$meetingInfoOrganizerUser->setAdditionalData($additionalData);
$meetingInfoOrganizer->setUser($meetingInfoOrganizerUser);
$meetingInfo->setOrganizer($meetingInfoOrganizer);
$additionalData = [
'allowConversationWithoutHost' => true,
];
$meetingInfo->setAdditionalData($additionalData);
$requestBody->setMeetingInfo($meetingInfo);
$requestBody->setTenantId('86dc81db-c112-4228-9222-63f3esaa1edb');

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	callbackUri = "https://bot.contoso.com/callback"
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.serviceHostedMediaConfig"
	preFetchMedia = @(
		@{
			uri = "https://cdn.contoso.com/beep.wav"
			resourceId = "f8971b04-b53e-418c-9222-c82ce681a582"
		}
		@{
			uri = "https://cdn.contoso.com/cool.wav"
			resourceId = "86dc814b-c172-4428-9112-60f8ecae1edb"
		}
	)
}
chatInfo = @{
	"@odata.type" = "#microsoft.graph.chatInfo"
	threadId = "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2"
	messageId = "0"
}
meetingInfo = @{
	"@odata.type" = "#microsoft.graph.organizerMeetingInfo"
	organizer = @{
		"@odata.type" = "#microsoft.graph.identitySet"
		user = @{
			"@odata.type" = "#microsoft.graph.identity"
			id = "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96"
			displayName = "Bob"
			tenantId = "86dc81db-c112-4228-9222-63f3esaa1edb"
		}
	}
	allowConversationWithoutHost = $true
}
tenantId = "86dc81db-c112-4228-9222-63f3esaa1edb"
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.service_hosted_media_config import ServiceHostedMediaConfig
from msgraph.generated.models.media_info import MediaInfo
from msgraph.generated.models.chat_info import ChatInfo
from msgraph.generated.models.organizer_meeting_info import OrganizerMeetingInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	callback_uri = "https://bot.contoso.com/callback",
	requested_modalities = [
		Modality.Audio,
	],
	media_config = ServiceHostedMediaConfig(
		odata_type = "#microsoft.graph.serviceHostedMediaConfig",
		pre_fetch_media = [
			MediaInfo(
				uri = "https://cdn.contoso.com/beep.wav",
				resource_id = "f8971b04-b53e-418c-9222-c82ce681a582",
			),
			MediaInfo(
				uri = "https://cdn.contoso.com/cool.wav",
				resource_id = "86dc814b-c172-4428-9112-60f8ecae1edb",
			),
		],
	),
	chat_info = ChatInfo(
		odata_type = "#microsoft.graph.chatInfo",
		thread_id = "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
		message_id = "0",
	),
	meeting_info = OrganizerMeetingInfo(
		odata_type = "#microsoft.graph.organizerMeetingInfo",
		organizer = IdentitySet(
			odata_type = "#microsoft.graph.identitySet",
			user = Identity(
				odata_type = "#microsoft.graph.identity",
				id = "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
				display_name = "Bob",
				additional_data = {
						"tenant_id" : "86dc81db-c112-4228-9222-63f3esaa1edb",
				}
			),
		),
		additional_data = {
				"allow_conversation_without_host" : True,
		}
	),
	tenant_id = "86dc81db-c112-4228-9222-63f3esaa1edb",
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
      }
    },
    "region": null,
    "languageId": null
  },
  "targets": [],
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
     {
       "uri": "https://cdn.contoso.com/beep.wav",
       "resourceId": "f8971b04-b53e-418c-9222-c82ce681a582"
     },
     {
       "uri": "https://cdn.contoso.com/cool.wav",
       "resourceId": "86dc814b-c172-4428-9112-60f8ecae1edb"
     }
    ],
  },
  "chatInfo": {
    "@odata.type": "#microsoft.graph.chatInfo",
    "threadId": "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
    "messageId": "0",
    "replyChainMessageId": null
  },
  "meetingInfo": {
    "@odata.type": "#microsoft.graph.organizerMeetingInfo",
    "organizer": {
      "@odata.type": "#microsoft.graph.identitySet",
      "user": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
        "displayName": "Bob"
      }
    },
    "allowConversationWithoutHost": true
  },
  "transcription": null,
  "myParticipantId": "05491616-385f-44a8-9974-18cc5f9933c1",
  "id": "2f1a1100-b174-40a0-aba7-0b405e01ed92",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
  "ringingTimeoutInSeconds": null,
  "mediaState": null,
  "subject": null,
  "resultInfo": null,
  "answeredBy": null,
  "toneInfo": null
}
```

#### Notification - establishing

```http
POST https://bot.contoso.com/callback
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92",
        "callbackUri": "https://bot.contoso.com/callback",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "establishing",
        "chatInfo": {
          "@odata.type": "#microsoft.graph.chatInfo",
          "threadId": "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
          "messageId": "0"
        },
        "meetingInfo": {
          "@odata.type": "#microsoft.graph.organizerMeetingInfo",
          "organizer": {
            "@odata.type": "#microsoft.graph.identitySet",
            "user": {
              "@odata.type": "#microsoft.graph.identity",
              "id": "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
              "displayName": "Bob"
            }
          },
          "allowConversationWithoutHost": true
        },
        "id": "2f1a1100-b174-40a0-aba7-0b405e01ed92"
      }
    }
  ]
}
```

> **Note:** Call establishing/established notifications may arrive out of order.

#### Notification - established

```http
POST https://bot.contoso.com/callback
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92",
      "callbackUri": "https://bot.contoso.com/callback",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "established",
        "chatInfo": {
          "@odata.type": "#microsoft.graph.chatInfo",
          "threadId": "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
          "messageId": "0"
        },
        "meetingInfo": {
          "@odata.type": "#microsoft.graph.organizerMeetingInfo",
          "organizer": {
            "@odata.type": "#microsoft.graph.identitySet",
            "user": {
              "@odata.type": "#microsoft.graph.identity",
              "id": "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
              "displayName": "Bob"
            }
          },
          "allowConversationWithoutHost": true
        },
        "id": "2f1a1100-b174-40a0-aba7-0b405e01ed92"
      }
    }
  ]
}
```

> **Note:** Call establishing/established notifications may arrive out of order.

#### Notification - roster

```http
POST https://bot.contoso.com/callback
Content-Type: application/json
```

##### Delta roster disabled \(default\)

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92/participants",
      "callbackUri": "https://bot.contoso.com/callback",
      "resourceData": [
        {
          "@odata.type": "#microsoft.graph.participant",
          "info": {
            "@odata.type": "#microsoft.graph.participantInfo",
            "identity": {
              "@odata.type": "#microsoft.graph.identitySet",
              "user": {
                "@odata.type": "#microsoft.graph.identity",
                "displayName": "John",
                "id": "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
              }
            },
            "languageId": "en-US"
          },
          "mediaStreams": [
            {
              "@odata.type": "#microsoft.graph.mediaStream",
              "mediaType": "audio",
              "sourceId": "1",
              "direction": "sendReceive",
              "serverMuted": false
            },
            {
              "@odata.type": "#microsoft.graph.mediaStream",
              "mediaType": "video",
              "sourceId": "2",
              "direction": "receiveOnly",
              "serverMuted": false
            },
            {
              "@odata.type": "#microsoft.graph.mediaStream",
              "mediaType": "videoBasedScreenSharing",
              "sourceId": "8",
              "direction": "receiveOnly",
              "serverMuted": false
            }
          ],
          "isMuted": true,
          "isInLobby": false,
          "id": "0d7664b6-6432-43ed-8d27-d9e7adec188c"
        },
        {
          "@odata.type": "#microsoft.graph.participant",
          "info": {
            "@odata.type": "#microsoft.graph.participantInfo",
            "identity": {
              "@odata.type": "#microsoft.graph.identitySet",
              "application": {
                "@odata.type": "#microsoft.graph.identity",
                "displayName": "Calling Bot",
                "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
              }
            }
          },
          "mediaStreams": [
            {
              "@odata.type": "#microsoft.graph.mediaStream",
              "mediaType": "audio",
              "sourceId": "10",
              "direction": "sendReceive",
              "serverMuted": false
            }
          ],
          "isMuted": false,
          "isInLobby": false,
          "id": "05491616-385f-44a8-9974-18cc5f9933c1"
        }
      ]
    }
  ]
}
```

##### Delta roster enabled

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resource": "/app/calls/421f7700-f4ad-4ea9-a3fc-c1d2195675ad/participants",
      "resourceUrl": "/communications/calls/421f7700-f4ad-4ea9-a3fc-c1d2195675ad/participants",
      "resourceData": [
        {
          "@odata.type": "#microsoft.graph.deltaParticipants",
          "participants": [
            {
              "@odata.type": "#microsoft.graph.participant",
              "info": {
                "@odata.type": "#microsoft.graph.participantInfo",
                "identity": {
                  "@odata.type": "#microsoft.graph.identitySet",
                  "user": {
                    "@odata.type": "#microsoft.graph.identity",
                    "displayName": "John",
                    "id": "112f7296-5fa4-42ca-bae8-6a692b15d4b8"
                  }
                },
                "languageId": "en-US"
              },
              "mediaStreams": [
                {
                  "@odata.type": "#microsoft.graph.mediaStream",
                  "mediaType": "audio",
                  "sourceId": "1",
                  "direction": "sendReceive",
                  "serverMuted": false
                },
                {
                  "@odata.type": "#microsoft.graph.mediaStream",
                  "mediaType": "video",
                  "sourceId": "2",
                  "direction": "receiveOnly",
                  "serverMuted": false
                },
                {
                  "@odata.type": "#microsoft.graph.mediaStream",
                  "mediaType": "videoBasedScreenSharing",
                  "sourceId": "8",
                  "direction": "receiveOnly",
                  "serverMuted": false
                }
              ],
              "isMuted": true,
              "isInLobby": false,
              "id": "0d7664b6-6432-43ed-8d27-d9e7adec188c",
              "rosterSequenceNumber": 1
            },
            {
              "@odata.type": "#microsoft.graph.participant",
              "info": {
                "@odata.type": "#microsoft.graph.participantInfo",
                "identity": {
                  "@odata.type": "#microsoft.graph.identitySet",
                  "application": {
                    "@odata.type": "#microsoft.graph.identity",
                    "displayName": "Calling Bot",
                    "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
                  }
                }
              },
              "mediaStreams": [
                {
                  "@odata.type": "#microsoft.graph.mediaStream",
                  "mediaType": "audio",
                  "sourceId": "10",
                  "direction": "sendReceive",
                  "serverMuted": false
                }
              ],
              "isMuted": false,
              "isInLobby": false,
              "id": "05491616-385f-44a8-9974-18cc5f9933c1",
              "rosterSequenceNumber": 1,
              "removedState": {
                "reason": "Removed from roster"
              }
            }
          ],
          "sequenceNumber": 1
        }
      ]
    }
  ]
}
```

> **Note:** For join meeting scenarios apart from call state notifications, we receive roster notifications.

### Example 6: Join scheduled meeting with application hosted media

Update the media config with the [appHostedMediaConfig](https://learn.microsoft.com/en-us/graph/api/resources/apphostedmediaconfig?view=graph-rest-1.0) as shown in the following example.

#### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig"
  },
  "chatInfo": {
    "@odata.type": "#microsoft.graph.chatInfo",
    "threadId": "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
    "messageId": "0"
  },
  "meetingInfo": {
    "@odata.type": "#microsoft.graph.organizerMeetingInfo",
    "organizer": {
      "@odata.type": "#microsoft.graph.identitySet",
      "user": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
        "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a",
        "displayName": "Bob"
      }
    },
    "allowConversationWithoutHost": true
  },
  "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	Direction = CallDirection.Outgoing,
	CallbackUri = "https://bot.contoso.com/callback",
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new AppHostedMediaConfig
	{
		OdataType = "#microsoft.graph.appHostedMediaConfig",
	},
	ChatInfo = new ChatInfo
	{
		OdataType = "#microsoft.graph.chatInfo",
		ThreadId = "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
		MessageId = "0",
	},
	MeetingInfo = new OrganizerMeetingInfo
	{
		OdataType = "#microsoft.graph.organizerMeetingInfo",
		Organizer = new IdentitySet
		{
			OdataType = "#microsoft.graph.identitySet",
			User = new Identity
			{
				OdataType = "#microsoft.graph.identity",
				Id = "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
				DisplayName = "Bob",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"tenantId" , "aa67bd4c-8475-432d-bd41-39f255720e0a"
					},
				},
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"allowConversationWithoutHost" , true
			},
		},
	},
	TenantId = "aa67bd4c-8475-432d-bd41-39f255720e0a",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
direction := graphmodels.OUTGOING_CALLDIRECTION 
requestBody.SetDirection(&direction) 
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewAppHostedMediaConfig()
requestBody.SetMediaConfig(mediaConfig)
chatInfo := graphmodels.NewChatInfo()
threadId := "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2"
chatInfo.SetThreadId(&threadId) 
messageId := "0"
chatInfo.SetMessageId(&messageId) 
requestBody.SetChatInfo(chatInfo)
meetingInfo := graphmodels.NewOrganizerMeetingInfo()
organizer := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
id := "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96"
user.SetId(&id) 
displayName := "Bob"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"tenantId" : "aa67bd4c-8475-432d-bd41-39f255720e0a", 
}
user.SetAdditionalData(additionalData)
organizer.SetUser(user)
meetingInfo.SetOrganizer(organizer)
additionalData := map[string]interface{}{
	allowConversationWithoutHost := true
meetingInfo.SetAllowConversationWithoutHost(&allowConversationWithoutHost) 
}
meetingInfo.SetAdditionalData(additionalData)
requestBody.SetMeetingInfo(meetingInfo)
tenantId := "aa67bd4c-8475-432d-bd41-39f255720e0a"
requestBody.SetTenantId(&tenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setDirection(CallDirection.Outgoing);
call.setCallbackUri("https://bot.contoso.com/callback");
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
AppHostedMediaConfig mediaConfig = new AppHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.appHostedMediaConfig");
call.setMediaConfig(mediaConfig);
ChatInfo chatInfo = new ChatInfo();
chatInfo.setOdataType("#microsoft.graph.chatInfo");
chatInfo.setThreadId("19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2");
chatInfo.setMessageId("0");
call.setChatInfo(chatInfo);
OrganizerMeetingInfo meetingInfo = new OrganizerMeetingInfo();
meetingInfo.setOdataType("#microsoft.graph.organizerMeetingInfo");
IdentitySet organizer = new IdentitySet();
organizer.setOdataType("#microsoft.graph.identitySet");
Identity user = new Identity();
user.setOdataType("#microsoft.graph.identity");
user.setId("5810cede-f3cc-42eb-b2c1-e9bd5d53ec96");
user.setDisplayName("Bob");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("tenantId", "aa67bd4c-8475-432d-bd41-39f255720e0a");
user.setAdditionalData(additionalData);
organizer.setUser(user);
meetingInfo.setOrganizer(organizer);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("allowConversationWithoutHost", true);
meetingInfo.setAdditionalData(additionalData1);
call.setMeetingInfo(meetingInfo);
call.setTenantId("aa67bd4c-8475-432d-bd41-39f255720e0a");
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  direction: 'outgoing',
  callbackUri: 'https://bot.contoso.com/callback',
  requestedModalities: [
    'audio'
  ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.appHostedMediaConfig'
  },
  chatInfo: {
    '@odata.type': '#microsoft.graph.chatInfo',
    threadId: '19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2',
    messageId: '0'
  },
  meetingInfo: {
    '@odata.type': '#microsoft.graph.organizerMeetingInfo',
    organizer: {
      '@odata.type': '#microsoft.graph.identitySet',
      user: {
        '@odata.type': '#microsoft.graph.identity',
        id: '5810cede-f3cc-42eb-b2c1-e9bd5d53ec96',
        tenantId: 'aa67bd4c-8475-432d-bd41-39f255720e0a',
        displayName: 'Bob'
      }
    },
    allowConversationWithoutHost: true
  },
  tenantId: 'aa67bd4c-8475-432d-bd41-39f255720e0a'
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\CallDirection;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\AppHostedMediaConfig;
use Microsoft\Graph\Generated\Models\ChatInfo;
use Microsoft\Graph\Generated\Models\OrganizerMeetingInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setDirection(new CallDirection('outgoing'));
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$requestBody->setRequestedModalities([new Modality('audio'),	]);
$mediaConfig = new AppHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.appHostedMediaConfig');
$requestBody->setMediaConfig($mediaConfig);
$chatInfo = new ChatInfo();
$chatInfo->setOdataType('#microsoft.graph.chatInfo');
$chatInfo->setThreadId('19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2');
$chatInfo->setMessageId('0');
$requestBody->setChatInfo($chatInfo);
$meetingInfo = new OrganizerMeetingInfo();
$meetingInfo->setOdataType('#microsoft.graph.organizerMeetingInfo');
$meetingInfoOrganizer = new IdentitySet();
$meetingInfoOrganizer->setOdataType('#microsoft.graph.identitySet');
$meetingInfoOrganizerUser = new Identity();
$meetingInfoOrganizerUser->setOdataType('#microsoft.graph.identity');
$meetingInfoOrganizerUser->setId('5810cede-f3cc-42eb-b2c1-e9bd5d53ec96');
$meetingInfoOrganizerUser->setDisplayName('Bob');
$additionalData = [
	'tenantId' => 'aa67bd4c-8475-432d-bd41-39f255720e0a',
];
$meetingInfoOrganizerUser->setAdditionalData($additionalData);
$meetingInfoOrganizer->setUser($meetingInfoOrganizerUser);
$meetingInfo->setOrganizer($meetingInfoOrganizer);
$additionalData = [
	'allowConversationWithoutHost' => true,
];
$meetingInfo->setAdditionalData($additionalData);
$requestBody->setMeetingInfo($meetingInfo);
$requestBody->setTenantId('aa67bd4c-8475-432d-bd41-39f255720e0a');

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	direction = "outgoing"
	callbackUri = "https://bot.contoso.com/callback"
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.appHostedMediaConfig"
}
chatInfo = @{
	"@odata.type" = "#microsoft.graph.chatInfo"
	threadId = "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2"
	messageId = "0"
}
meetingInfo = @{
	"@odata.type" = "#microsoft.graph.organizerMeetingInfo"
	organizer = @{
		"@odata.type" = "#microsoft.graph.identitySet"
		user = @{
			"@odata.type" = "#microsoft.graph.identity"
			id = "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96"
			tenantId = "aa67bd4c-8475-432d-bd41-39f255720e0a"
			displayName = "Bob"
		}
	}
	allowConversationWithoutHost = $true
}
tenantId = "aa67bd4c-8475-432d-bd41-39f255720e0a"
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.call_direction import CallDirection
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.app_hosted_media_config import AppHostedMediaConfig
from msgraph.generated.models.chat_info import ChatInfo
from msgraph.generated.models.organizer_meeting_info import OrganizerMeetingInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	direction = CallDirection.Outgoing,
	callback_uri = "https://bot.contoso.com/callback",
	requested_modalities = [
		Modality.Audio,
	],
	media_config = AppHostedMediaConfig(
		odata_type = "#microsoft.graph.appHostedMediaConfig",
	),
	chat_info = ChatInfo(
		odata_type = "#microsoft.graph.chatInfo",
		thread_id = "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
		message_id = "0",
	),
	meeting_info = OrganizerMeetingInfo(
		odata_type = "#microsoft.graph.organizerMeetingInfo",
		organizer = IdentitySet(
			odata_type = "#microsoft.graph.identitySet",
			user = Identity(
				odata_type = "#microsoft.graph.identity",
				id = "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
				display_name = "Bob",
				additional_data = {
						"tenant_id" : "aa67bd4c-8475-432d-bd41-39f255720e0a",
				}
			),
		),
		additional_data = {
				"allow_conversation_without_host" : True,
		}
	),
	tenant_id = "aa67bd4c-8475-432d-bd41-39f255720e0a",
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "callRoutes": [],
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
      }
    },
    "region": null,
    "languageId": null
  },
  "targets": [],
  "requestedModalities": [
    "audio"
  ],
  "activeModalities": [],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration>",
  },
  "chatInfo": {
    "@odata.type": "#microsoft.graph.chatInfo",
    "threadId": "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNWY2NmNkYTFm@thread.v2",
    "messageId": "0",
    "replyChainMessageId": null
  },
  "meetingInfo": {
    "@odata.type": "#microsoft.graph.organizerMeetingInfo",
    "organizer": {
      "@odata.type": "#microsoft.graph.identitySet",
      "user": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "5810cede-f3cc-42eb-b2c1-e9bd5d53ec96",
        "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a",
        "displayName": "Bob"
      }
    },
    "allowConversationWithoutHost": true
  },
  "transcription": null,
  "routingPolicies": [],
  "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a",
  "myParticipantId": "05491616-385f-44a8-9974-18cc5f9933c1",
  "id": "2f1a1100-b174-40a0-aba7-0b405e01ed92",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
  "terminationReason": null,
  "ringingTimeoutInSeconds": null,
  "mediaState": null,
  "subject": null,
  "resultInfo": null,
  "answeredBy": null,
  "meetingCapability": null,
  "toneInfo": null
}
```

### Example 7: Join a scheduled meeting with joinMeetingId and passcode

The following shows an example that requires a **joinMeetingId** and a **passcode** to join an existing meeting. You can retrieve these properties from the [Get onlineMeeting](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-get?view=graph-rest-1.0) API.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "callbackUri": "https://bot.contoso.com/callback",
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
      {
        "uri": "https://cdn.contoso.com/beep.wav",
        "resourceId": "f8971b04-b53e-418c-9222-c82ce681a582"
      },
      {
        "uri": "https://cdn.contoso.com/cool.wav",
        "resourceId": "86dc814b-c172-4428-9112-60f8ecae1edb"
      }
    ]
  },
  "meetingInfo": {
    "@odata.type": "#microsoft.graph.joinMeetingIdMeetingInfo",
    "joinMeetingId": "1234567",
    "passcode": "psw123"
  },
  "tenantId": "86dc81db-c112-4228-9222-63f3esaa1edb"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	CallbackUri = "https://bot.contoso.com/callback",
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new ServiceHostedMediaConfig
	{
		OdataType = "#microsoft.graph.serviceHostedMediaConfig",
		PreFetchMedia = new List<MediaInfo>
		{
			new MediaInfo
			{
				Uri = "https://cdn.contoso.com/beep.wav",
				ResourceId = "f8971b04-b53e-418c-9222-c82ce681a582",
			},
			new MediaInfo
			{
				Uri = "https://cdn.contoso.com/cool.wav",
				ResourceId = "86dc814b-c172-4428-9112-60f8ecae1edb",
			},
		},
	},
	MeetingInfo = new JoinMeetingIdMeetingInfo
	{
		OdataType = "#microsoft.graph.joinMeetingIdMeetingInfo",
		JoinMeetingId = "1234567",
		Passcode = "psw123",
	},
	TenantId = "86dc81db-c112-4228-9222-63f3esaa1edb",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewServiceHostedMediaConfig()


mediaInfo := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/beep.wav"
mediaInfo.SetUri(&uri) 
resourceId := "f8971b04-b53e-418c-9222-c82ce681a582"
mediaInfo.SetResourceId(&resourceId) 
mediaInfo1 := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/cool.wav"
mediaInfo1.SetUri(&uri) 
resourceId := "86dc814b-c172-4428-9112-60f8ecae1edb"
mediaInfo1.SetResourceId(&resourceId) 

preFetchMedia := []graphmodels.MediaInfoable {
	mediaInfo,
	mediaInfo1,
}
mediaConfig.SetPreFetchMedia(preFetchMedia)
requestBody.SetMediaConfig(mediaConfig)
meetingInfo := graphmodels.NewJoinMeetingIdMeetingInfo()
joinMeetingId := "1234567"
meetingInfo.SetJoinMeetingId(&joinMeetingId) 
passcode := "psw123"
meetingInfo.SetPasscode(&passcode) 
requestBody.SetMeetingInfo(meetingInfo)
tenantId := "86dc81db-c112-4228-9222-63f3esaa1edb"
requestBody.SetTenantId(&tenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setCallbackUri("https://bot.contoso.com/callback");
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
ServiceHostedMediaConfig mediaConfig = new ServiceHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.serviceHostedMediaConfig");
LinkedList<MediaInfo> preFetchMedia = new LinkedList<MediaInfo>();
MediaInfo mediaInfo = new MediaInfo();
mediaInfo.setUri("https://cdn.contoso.com/beep.wav");
mediaInfo.setResourceId("f8971b04-b53e-418c-9222-c82ce681a582");
preFetchMedia.add(mediaInfo);
MediaInfo mediaInfo1 = new MediaInfo();
mediaInfo1.setUri("https://cdn.contoso.com/cool.wav");
mediaInfo1.setResourceId("86dc814b-c172-4428-9112-60f8ecae1edb");
preFetchMedia.add(mediaInfo1);
mediaConfig.setPreFetchMedia(preFetchMedia);
call.setMediaConfig(mediaConfig);
JoinMeetingIdMeetingInfo meetingInfo = new JoinMeetingIdMeetingInfo();
meetingInfo.setOdataType("#microsoft.graph.joinMeetingIdMeetingInfo");
meetingInfo.setJoinMeetingId("1234567");
meetingInfo.setPasscode("psw123");
call.setMeetingInfo(meetingInfo);
call.setTenantId("86dc81db-c112-4228-9222-63f3esaa1edb");
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  callbackUri: 'https://bot.contoso.com/callback',
  requestedModalities: [
    'audio'
  ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.serviceHostedMediaConfig',
    preFetchMedia: [
      {
        uri: 'https://cdn.contoso.com/beep.wav',
        resourceId: 'f8971b04-b53e-418c-9222-c82ce681a582'
      },
      {
        uri: 'https://cdn.contoso.com/cool.wav',
        resourceId: '86dc814b-c172-4428-9112-60f8ecae1edb'
      }
    ]
  },
  meetingInfo: {
    '@odata.type': '#microsoft.graph.joinMeetingIdMeetingInfo',
    joinMeetingId: '1234567',
    passcode: 'psw123'
  },
  tenantId: '86dc81db-c112-4228-9222-63f3esaa1edb'
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\ServiceHostedMediaConfig;
use Microsoft\Graph\Generated\Models\MediaInfo;
use Microsoft\Graph\Generated\Models\JoinMeetingIdMeetingInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$requestBody->setRequestedModalities([new Modality('audio'),	]);
$mediaConfig = new ServiceHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.serviceHostedMediaConfig');
$preFetchMediaMediaInfo1 = new MediaInfo();
$preFetchMediaMediaInfo1->setUri('https://cdn.contoso.com/beep.wav');
$preFetchMediaMediaInfo1->setResourceId('f8971b04-b53e-418c-9222-c82ce681a582');
$preFetchMediaArray []= $preFetchMediaMediaInfo1;
$preFetchMediaMediaInfo2 = new MediaInfo();
$preFetchMediaMediaInfo2->setUri('https://cdn.contoso.com/cool.wav');
$preFetchMediaMediaInfo2->setResourceId('86dc814b-c172-4428-9112-60f8ecae1edb');
$preFetchMediaArray []= $preFetchMediaMediaInfo2;
$mediaConfig->setPreFetchMedia($preFetchMediaArray);

$requestBody->setMediaConfig($mediaConfig);
$meetingInfo = new JoinMeetingIdMeetingInfo();
$meetingInfo->setOdataType('#microsoft.graph.joinMeetingIdMeetingInfo');
$meetingInfo->setJoinMeetingId('1234567');
$meetingInfo->setPasscode('psw123');
$requestBody->setMeetingInfo($meetingInfo);
$requestBody->setTenantId('86dc81db-c112-4228-9222-63f3esaa1edb');

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	callbackUri = "https://bot.contoso.com/callback"
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.serviceHostedMediaConfig"
	preFetchMedia = @(
		@{
			uri = "https://cdn.contoso.com/beep.wav"
			resourceId = "f8971b04-b53e-418c-9222-c82ce681a582"
		}
		@{
			uri = "https://cdn.contoso.com/cool.wav"
			resourceId = "86dc814b-c172-4428-9112-60f8ecae1edb"
		}
	)
}
meetingInfo = @{
	"@odata.type" = "#microsoft.graph.joinMeetingIdMeetingInfo"
	joinMeetingId = "1234567"
	passcode = "psw123"
}
tenantId = "86dc81db-c112-4228-9222-63f3esaa1edb"
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.service_hosted_media_config import ServiceHostedMediaConfig
from msgraph.generated.models.media_info import MediaInfo
from msgraph.generated.models.join_meeting_id_meeting_info import JoinMeetingIdMeetingInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	callback_uri = "https://bot.contoso.com/callback",
	requested_modalities = [
		Modality.Audio,
	],
	media_config = ServiceHostedMediaConfig(
		odata_type = "#microsoft.graph.serviceHostedMediaConfig",
		pre_fetch_media = [
			MediaInfo(
				uri = "https://cdn.contoso.com/beep.wav",
				resource_id = "f8971b04-b53e-418c-9222-c82ce681a582",
			),
			MediaInfo(
				uri = "https://cdn.contoso.com/cool.wav",
				resource_id = "86dc814b-c172-4428-9112-60f8ecae1edb",
			),
		],
	),
	meeting_info = JoinMeetingIdMeetingInfo(
		odata_type = "#microsoft.graph.joinMeetingIdMeetingInfo",
		join_meeting_id = "1234567",
		passcode = "psw123",
	),
	tenant_id = "86dc81db-c112-4228-9222-63f3esaa1edb",
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "callRoutes": [],
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
      }
    },
    "region": null,
    "languageId": null
  },
  "targets": [],
  "requestedModalities": [
    "audio"
  ],
  "activeModalities": [],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
     {
       "uri": "https://cdn.contoso.com/beep.wav",
       "resourceId": "f8971b04-b53e-418c-9222-c82ce681a582"
     },
     {
       "uri": "https://cdn.contoso.com/cool.wav",
       "resourceId": "86dc814b-c172-4428-9112-60f8ecae1edb"
     }
    ],
  },
  "chatInfo": {
    "@odata.type": "#microsoft.graph.chatInfo",
    "threadId": "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNNkYTFm@thread.v2",
    "messageId": "0",
    "replyChainMessageId": null
  },
  "meetingInfo": {
    "@odata.type": "#microsoft.graph.joinMeetingIdMeetingInfo",
    "joinMeetingId": "1234567",
    "passcode": "psw123"
  },
  "transcription": null,
  "routingPolicies": [],
  "tenantId": "86dc81db-c112-4228-9222-63f3esaa1edb",
  "myParticipantId": "05491616-385f-44a8-9974-18cc5f9933c1",
  "id": "2f1a1100-b174-40a0-aba7-0b405e01ed92",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
  "terminationReason": null,
  "ringingTimeoutInSeconds": null,
  "mediaState": null,
  "subject": null,
  "resultInfo": null,
  "answeredBy": null,
  "meetingCapability": null,
  "toneInfo": null
}
```

### Example 8: Join a scheduled meeting with joinMeetingId

The following shows an example that requires a **joinMeetingId** but doesn't require a **passcode** to join an existing meeting. You can retrieve the **joinMeetingId** property from the [Get onlineMeeting](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-get?view=graph-rest-1.0) API.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "callbackUri": "https://bot.contoso.com/callback",
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
      {
        "uri": "https://cdn.contoso.com/beep.wav",
        "resourceId": "f8971b04-b53e-418c-9222-c82ce681a582"
      },
      {
        "uri": "https://cdn.contoso.com/cool.wav",
        "resourceId": "86dc814b-c172-4428-9112-60f8ecae1edb"
      }
    ]
  },
  "meetingInfo": {
    "@odata.type": "#microsoft.graph.joinMeetingIdMeetingInfo",
    "joinMeetingId": "1234567",
    "passcode": null
  },
  "tenantId": "86dc81db-c112-4228-9222-63f3esaa1edb"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	CallbackUri = "https://bot.contoso.com/callback",
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new ServiceHostedMediaConfig
	{
		OdataType = "#microsoft.graph.serviceHostedMediaConfig",
		PreFetchMedia = new List<MediaInfo>
		{
			new MediaInfo
			{
				Uri = "https://cdn.contoso.com/beep.wav",
				ResourceId = "f8971b04-b53e-418c-9222-c82ce681a582",
			},
			new MediaInfo
			{
				Uri = "https://cdn.contoso.com/cool.wav",
				ResourceId = "86dc814b-c172-4428-9112-60f8ecae1edb",
			},
		},
	},
	MeetingInfo = new JoinMeetingIdMeetingInfo
	{
		OdataType = "#microsoft.graph.joinMeetingIdMeetingInfo",
		JoinMeetingId = "1234567",
		Passcode = null,
	},
	TenantId = "86dc81db-c112-4228-9222-63f3esaa1edb",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewServiceHostedMediaConfig()


mediaInfo := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/beep.wav"
mediaInfo.SetUri(&uri) 
resourceId := "f8971b04-b53e-418c-9222-c82ce681a582"
mediaInfo.SetResourceId(&resourceId) 
mediaInfo1 := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/cool.wav"
mediaInfo1.SetUri(&uri) 
resourceId := "86dc814b-c172-4428-9112-60f8ecae1edb"
mediaInfo1.SetResourceId(&resourceId) 

preFetchMedia := []graphmodels.MediaInfoable {
	mediaInfo,
	mediaInfo1,
}
mediaConfig.SetPreFetchMedia(preFetchMedia)
requestBody.SetMediaConfig(mediaConfig)
meetingInfo := graphmodels.NewJoinMeetingIdMeetingInfo()
joinMeetingId := "1234567"
meetingInfo.SetJoinMeetingId(&joinMeetingId) 
passcode := null
meetingInfo.SetPasscode(&passcode) 
requestBody.SetMeetingInfo(meetingInfo)
tenantId := "86dc81db-c112-4228-9222-63f3esaa1edb"
requestBody.SetTenantId(&tenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setCallbackUri("https://bot.contoso.com/callback");
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
ServiceHostedMediaConfig mediaConfig = new ServiceHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.serviceHostedMediaConfig");
LinkedList<MediaInfo> preFetchMedia = new LinkedList<MediaInfo>();
MediaInfo mediaInfo = new MediaInfo();
mediaInfo.setUri("https://cdn.contoso.com/beep.wav");
mediaInfo.setResourceId("f8971b04-b53e-418c-9222-c82ce681a582");
preFetchMedia.add(mediaInfo);
MediaInfo mediaInfo1 = new MediaInfo();
mediaInfo1.setUri("https://cdn.contoso.com/cool.wav");
mediaInfo1.setResourceId("86dc814b-c172-4428-9112-60f8ecae1edb");
preFetchMedia.add(mediaInfo1);
mediaConfig.setPreFetchMedia(preFetchMedia);
call.setMediaConfig(mediaConfig);
JoinMeetingIdMeetingInfo meetingInfo = new JoinMeetingIdMeetingInfo();
meetingInfo.setOdataType("#microsoft.graph.joinMeetingIdMeetingInfo");
meetingInfo.setJoinMeetingId("1234567");
meetingInfo.setPasscode(null);
call.setMeetingInfo(meetingInfo);
call.setTenantId("86dc81db-c112-4228-9222-63f3esaa1edb");
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  callbackUri: 'https://bot.contoso.com/callback',
  requestedModalities: [
    'audio'
  ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.serviceHostedMediaConfig',
    preFetchMedia: [
      {
        uri: 'https://cdn.contoso.com/beep.wav',
        resourceId: 'f8971b04-b53e-418c-9222-c82ce681a582'
      },
      {
        uri: 'https://cdn.contoso.com/cool.wav',
        resourceId: '86dc814b-c172-4428-9112-60f8ecae1edb'
      }
    ]
  },
  meetingInfo: {
    '@odata.type': '#microsoft.graph.joinMeetingIdMeetingInfo',
    joinMeetingId: '1234567',
    passcode: null
  },
  tenantId: '86dc81db-c112-4228-9222-63f3esaa1edb'
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\ServiceHostedMediaConfig;
use Microsoft\Graph\Generated\Models\MediaInfo;
use Microsoft\Graph\Generated\Models\JoinMeetingIdMeetingInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$requestBody->setRequestedModalities([new Modality('audio'),	]);
$mediaConfig = new ServiceHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.serviceHostedMediaConfig');
$preFetchMediaMediaInfo1 = new MediaInfo();
$preFetchMediaMediaInfo1->setUri('https://cdn.contoso.com/beep.wav');
$preFetchMediaMediaInfo1->setResourceId('f8971b04-b53e-418c-9222-c82ce681a582');
$preFetchMediaArray []= $preFetchMediaMediaInfo1;
$preFetchMediaMediaInfo2 = new MediaInfo();
$preFetchMediaMediaInfo2->setUri('https://cdn.contoso.com/cool.wav');
$preFetchMediaMediaInfo2->setResourceId('86dc814b-c172-4428-9112-60f8ecae1edb');
$preFetchMediaArray []= $preFetchMediaMediaInfo2;
$mediaConfig->setPreFetchMedia($preFetchMediaArray);

$requestBody->setMediaConfig($mediaConfig);
$meetingInfo = new JoinMeetingIdMeetingInfo();
$meetingInfo->setOdataType('#microsoft.graph.joinMeetingIdMeetingInfo');
$meetingInfo->setJoinMeetingId('1234567');
$meetingInfo->setPasscode(null);
$requestBody->setMeetingInfo($meetingInfo);
$requestBody->setTenantId('86dc81db-c112-4228-9222-63f3esaa1edb');

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	callbackUri = "https://bot.contoso.com/callback"
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.serviceHostedMediaConfig"
	preFetchMedia = @(
		@{
			uri = "https://cdn.contoso.com/beep.wav"
			resourceId = "f8971b04-b53e-418c-9222-c82ce681a582"
		}
		@{
			uri = "https://cdn.contoso.com/cool.wav"
			resourceId = "86dc814b-c172-4428-9112-60f8ecae1edb"
		}
	)
}
meetingInfo = @{
	"@odata.type" = "#microsoft.graph.joinMeetingIdMeetingInfo"
	joinMeetingId = "1234567"
	passcode = $null
}
tenantId = "86dc81db-c112-4228-9222-63f3esaa1edb"
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.service_hosted_media_config import ServiceHostedMediaConfig
from msgraph.generated.models.media_info import MediaInfo
from msgraph.generated.models.join_meeting_id_meeting_info import JoinMeetingIdMeetingInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	callback_uri = "https://bot.contoso.com/callback",
	requested_modalities = [
		Modality.Audio,
	],
	media_config = ServiceHostedMediaConfig(
		odata_type = "#microsoft.graph.serviceHostedMediaConfig",
		pre_fetch_media = [
			MediaInfo(
				uri = "https://cdn.contoso.com/beep.wav",
				resource_id = "f8971b04-b53e-418c-9222-c82ce681a582",
			),
			MediaInfo(
				uri = "https://cdn.contoso.com/cool.wav",
				resource_id = "86dc814b-c172-4428-9112-60f8ecae1edb",
			),
		],
	),
	meeting_info = JoinMeetingIdMeetingInfo(
		odata_type = "#microsoft.graph.joinMeetingIdMeetingInfo",
		join_meeting_id = "1234567",
		passcode = None,
	),
	tenant_id = "86dc81db-c112-4228-9222-63f3esaa1edb",
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2f1a1100-b174-40a0-aba7-0b405e01ed92
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "callRoutes": [],
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "application": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "2891555a-92ff-42e6-80fa-6e1300c6b5c6"
      }
    },
    "region": null,
    "languageId": null
  },
  "targets": [],
  "requestedModalities": [
    "audio"
  ],
  "activeModalities": [],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
     {
       "uri": "https://cdn.contoso.com/beep.wav",
       "resourceId": "f8971b04-b53e-418c-9222-c82ce681a582"
     },
     {
       "uri": "https://cdn.contoso.com/cool.wav",
       "resourceId": "86dc814b-c172-4428-9112-60f8ecae1edb"
     }
    ],
  },
  "chatInfo": {
    "@odata.type": "#microsoft.graph.chatInfo",
    "threadId": "19:meeting_Win6Ydo4wsMijFjZS00ZGVjLTk5MGUtOTRjNNkYTFm@thread.v2",
    "messageId": "0",
    "replyChainMessageId": null
  },
  "meetingInfo": {
    "@odata.type": "#microsoft.graph.joinMeetingIdMeetingInfo",
    "joinMeetingId": "1234567",
    "passcode": null
  },
  "transcription": null,
  "routingPolicies": [],
  "tenantId": "86dc81db-c112-4228-9222-63f3esaa1edb",
  "myParticipantId": "05491616-385f-44a8-9974-18cc5f9933c1",
  "id": "2f1a1100-b174-40a0-aba7-0b405e01ed92",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
  "terminationReason": null,
  "ringingTimeoutInSeconds": null,
  "mediaState": null,
  "subject": null,
  "resultInfo": null,
  "answeredBy": null,
  "meetingCapability": null,
  "toneInfo": null
}
```

### Example 9: Create peer-to-peer PSTN call with service hosted media

> **Note:** This call requires the Calls.Initiate.All permission.

This call requires an application instance with a PSTN number assigned. For details, see [Assign a phone number to your bot](https://learn.microsoft.com/en-us/graph/cloud-communications-phone-number#assign-a-phone-number-to-your-bot).

#### Request

The following example shows the request to make a peer-to-peer call between the bot and a PSTN number. In this example, the media is hosted by the service. The values of authorization token, callback URL, application instance ID, application instance display name, phone ID and tenant ID must be replaced with actual values to make the example work.

> **Note:** Application instance ID is the object ID of application instance. The application ID that application instance links to should match the one in authorization token. Phone ID is the phone number in E.164 format.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "callbackUri": "https://bot.contoso.com/callback",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "applicationInstance": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "3d913abb-aec0-4964-8fa6-3c6850c4f278"
      },
    },
    "countryCode": null,
    "endpointType": null,
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "phone": {
          "@odata.type": "#microsoft.graph.identity",
          "id": "+12345678901"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig"
  },
  "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	CallbackUri = "https://bot.contoso.com/callback",
	Source = new ParticipantInfo
	{
		OdataType = "#microsoft.graph.participantInfo",
		Identity = new IdentitySet
		{
			OdataType = "#microsoft.graph.identitySet",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"applicationInstance" , new Identity
					{
						OdataType = "#microsoft.graph.identity",
						DisplayName = "Calling Bot",
						Id = "3d913abb-aec0-4964-8fa6-3c6850c4f278",
					}
				},
			},
		},
		CountryCode = null,
		EndpointType = null,
		Region = null,
		LanguageId = null,
	},
	Targets = new List<InvitationParticipantInfo>
	{
		new InvitationParticipantInfo
		{
			OdataType = "#microsoft.graph.invitationParticipantInfo",
			Identity = new IdentitySet
			{
				OdataType = "#microsoft.graph.identitySet",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"phone" , new Identity
						{
							OdataType = "#microsoft.graph.identity",
							Id = "+12345678901",
						}
					},
				},
			},
		},
	},
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new ServiceHostedMediaConfig
	{
		OdataType = "#microsoft.graph.serviceHostedMediaConfig",
	},
	TenantId = "aa67bd4c-8475-432d-bd41-39f255720e0a",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
source := graphmodels.NewParticipantInfo()
identity := graphmodels.NewIdentitySet()
additionalData := map[string]interface{}{
applicationInstance := graphmodels.NewIdentity()
displayName := "Calling Bot"
applicationInstance.SetDisplayName(&displayName) 
id := "3d913abb-aec0-4964-8fa6-3c6850c4f278"
applicationInstance.SetId(&id) 
	identity.SetApplicationInstance(applicationInstance)
}
identity.SetAdditionalData(additionalData)
source.SetIdentity(identity)
countryCode := null
source.SetCountryCode(&countryCode) 
endpointType := null
source.SetEndpointType(&endpointType) 
region := null
source.SetRegion(&region) 
languageId := null
source.SetLanguageId(&languageId) 
requestBody.SetSource(source)


invitationParticipantInfo := graphmodels.NewInvitationParticipantInfo()
identity := graphmodels.NewIdentitySet()
additionalData := map[string]interface{}{
phone := graphmodels.NewIdentity()
id := "+12345678901"
phone.SetId(&id) 
	identity.SetPhone(phone)
}
identity.SetAdditionalData(additionalData)
invitationParticipantInfo.SetIdentity(identity)

targets := []graphmodels.InvitationParticipantInfoable {
	invitationParticipantInfo,
}
requestBody.SetTargets(targets)
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewServiceHostedMediaConfig()
requestBody.SetMediaConfig(mediaConfig)
tenantId := "aa67bd4c-8475-432d-bd41-39f255720e0a"
requestBody.SetTenantId(&tenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setCallbackUri("https://bot.contoso.com/callback");
ParticipantInfo source = new ParticipantInfo();
source.setOdataType("#microsoft.graph.participantInfo");
IdentitySet identity = new IdentitySet();
identity.setOdataType("#microsoft.graph.identitySet");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
Identity applicationInstance = new Identity();
applicationInstance.setOdataType("#microsoft.graph.identity");
applicationInstance.setDisplayName("Calling Bot");
applicationInstance.setId("3d913abb-aec0-4964-8fa6-3c6850c4f278");
additionalData.put("applicationInstance", applicationInstance);
identity.setAdditionalData(additionalData);
source.setIdentity(identity);
source.setCountryCode(null);
source.setEndpointType(null);
source.setRegion(null);
source.setLanguageId(null);
call.setSource(source);
LinkedList<InvitationParticipantInfo> targets = new LinkedList<InvitationParticipantInfo>();
InvitationParticipantInfo invitationParticipantInfo = new InvitationParticipantInfo();
invitationParticipantInfo.setOdataType("#microsoft.graph.invitationParticipantInfo");
IdentitySet identity1 = new IdentitySet();
identity1.setOdataType("#microsoft.graph.identitySet");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
Identity phone = new Identity();
phone.setOdataType("#microsoft.graph.identity");
phone.setId("+12345678901");
additionalData1.put("phone", phone);
identity1.setAdditionalData(additionalData1);
invitationParticipantInfo.setIdentity(identity1);
targets.add(invitationParticipantInfo);
call.setTargets(targets);
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
ServiceHostedMediaConfig mediaConfig = new ServiceHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.serviceHostedMediaConfig");
call.setMediaConfig(mediaConfig);
call.setTenantId("aa67bd4c-8475-432d-bd41-39f255720e0a");
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  callbackUri: 'https://bot.contoso.com/callback',
  source: {
    '@odata.type': '#microsoft.graph.participantInfo',
    identity: {
      '@odata.type': '#microsoft.graph.identitySet',
      applicationInstance: {
        '@odata.type': '#microsoft.graph.identity',
        displayName: 'Calling Bot',
        id: '3d913abb-aec0-4964-8fa6-3c6850c4f278'
      },
    },
    countryCode: null,
    endpointType: null,
    region: null,
    languageId: null
  },
  targets: [
    {
      '@odata.type': '#microsoft.graph.invitationParticipantInfo',
      identity: {
        '@odata.type': '#microsoft.graph.identitySet',
        phone: {
          '@odata.type': '#microsoft.graph.identity',
          id: '+12345678901'
        }
      }
    }
  ],
  requestedModalities: [
    'audio'
  ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.serviceHostedMediaConfig'
  },
  tenantId: 'aa67bd4c-8475-432d-bd41-39f255720e0a'
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\ParticipantInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\InvitationParticipantInfo;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\ServiceHostedMediaConfig;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$source = new ParticipantInfo();
$source->setOdataType('#microsoft.graph.participantInfo');
$sourceIdentity = new IdentitySet();
$sourceIdentity->setOdataType('#microsoft.graph.identitySet');
$additionalData = [
	'applicationInstance' => [
		'@odata.type' => '#microsoft.graph.identity',
		'displayName' => 'Calling Bot',
		'id' => '3d913abb-aec0-4964-8fa6-3c6850c4f278',
	],
];
$sourceIdentity->setAdditionalData($additionalData);
$source->setIdentity($sourceIdentity);
$source->setCountryCode(null);
$source->setEndpointType(null);
$source->setRegion(null);
$source->setLanguageId(null);
$requestBody->setSource($source);
$targetsInvitationParticipantInfo1 = new InvitationParticipantInfo();
$targetsInvitationParticipantInfo1->setOdataType('#microsoft.graph.invitationParticipantInfo');
$targetsInvitationParticipantInfo1Identity = new IdentitySet();
$targetsInvitationParticipantInfo1Identity->setOdataType('#microsoft.graph.identitySet');
$additionalData = [
	'phone' => [
		'@odata.type' => '#microsoft.graph.identity',
		'id' => '+12345678901',
	],
];
$targetsInvitationParticipantInfo1Identity->setAdditionalData($additionalData);
$targetsInvitationParticipantInfo1->setIdentity($targetsInvitationParticipantInfo1Identity);
$targetsArray []= $targetsInvitationParticipantInfo1;
$requestBody->setTargets($targetsArray);

$requestBody->setRequestedModalities([new Modality('audio'),]);
$mediaConfig = new ServiceHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.serviceHostedMediaConfig');
$requestBody->setMediaConfig($mediaConfig);
$requestBody->setTenantId('aa67bd4c-8475-432d-bd41-39f255720e0a');

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	callbackUri = "https://bot.contoso.com/callback"
	source = @{
		"@odata.type" = "#microsoft.graph.participantInfo"
		identity = @{
			"@odata.type" = "#microsoft.graph.identitySet"
			applicationInstance = @{
				"@odata.type" = "#microsoft.graph.identity"
				displayName = "Calling Bot"
				id = "3d913abb-aec0-4964-8fa6-3c6850c4f278"
			}
		}
		countryCode = $null
		endpointType = $null
		region = $null
		languageId = $null
	}
	targets = @(
		@{
			"@odata.type" = "#microsoft.graph.invitationParticipantInfo"
			identity = @{
				"@odata.type" = "#microsoft.graph.identitySet"
				phone = @{
					"@odata.type" = "#microsoft.graph.identity"
					id = "+12345678901"
				}
			}
		}
	)
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.serviceHostedMediaConfig"
}
tenantId = "aa67bd4c-8475-432d-bd41-39f255720e0a"
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.participant_info import ParticipantInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.invitation_participant_info import InvitationParticipantInfo
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.service_hosted_media_config import ServiceHostedMediaConfig
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	callback_uri = "https://bot.contoso.com/callback",
	source = ParticipantInfo(
		odata_type = "#microsoft.graph.participantInfo",
		identity = IdentitySet(
			odata_type = "#microsoft.graph.identitySet",
			additional_data = {
					"application_instance" : {
							"@odata_type" : "#microsoft.graph.identity",
							"display_name" : "Calling Bot",
							"id" : "3d913abb-aec0-4964-8fa6-3c6850c4f278",
					},
			}
		),
		country_code = None,
		endpoint_type = None,
		region = None,
		language_id = None,
	),
	targets = [
		InvitationParticipantInfo(
			odata_type = "#microsoft.graph.invitationParticipantInfo",
			identity = IdentitySet(
				odata_type = "#microsoft.graph.identitySet",
				additional_data = {
						"phone" : {
								"@odata_type" : "#microsoft.graph.identity",
								"id" : "+12345678901",
						},
				}
			),
		),
	],
	requested_modalities = [
		Modality.Audio,
	],
	media_config = ServiceHostedMediaConfig(
		odata_type = "#microsoft.graph.serviceHostedMediaConfig",
	),
	tenant_id = "aa67bd4c-8475-432d-bd41-39f255720e0a",
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2e1a0b00-2db4-4022-9570-243709c565ab
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "callRoutes": [],
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "applicationInstance": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "3d913abb-aec0-4964-8fa6-3c6850c4f278"
      },
    },
    "countryCode": null,
    "endpointType": null,
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "phone": {
          "@odata.type": "#microsoft.graph.identity",
          "id": "+12345678901"
        }
      },
      "endpointType": null,
      "region": null,
      "replacesCallId": null,
      "languageId": null
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "activeModalities": [],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
     {
       "uri": "https://cdn.contoso.com/beep.wav",
       "resourceId": "f8971b04-b53e-418c-9222-c82ce681a582"
     },
     {
       "uri": "https://cdn.contoso.com/cool.wav",
       "resourceId": "86dc814b-c172-4428-9112-60f8ecae1edb"
     }
    ],
  },
  "routingPolicies": [],
  "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a",
  "myParticipantId": "499ff390-7a72-40e8-83a0-8fac6295ae7e",
  "id": "2e1a0b00-2db4-4022-9570-243709c565ab",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
  "subject": null,
  "terminationReason": null,
  "ringingTimeoutInSeconds": null,
  "mediaState": null,
  "resultInfo": null,
  "answeredBy": null,
  "chatInfo": null,
  "meetingInfo": null,
  "transcription": null,
  "meetingCapability": null,
  "toneInfo": null
}
```

### Example 10: Create peer-to-peer PSTN call with application hosted media

> **Note**: This example requires Calls.Initiate.All and Calls.AccessMedia.All permissions.

This call requires an application instance with a PSTN number assigned. For details, see [Assign a phone number to your bot](https://learn.microsoft.com/en-us/graph/cloud-communications-phone-number#assign-a-phone-number-to-your-bot).

#### Request

The following example shows a request to make a peer-to-peer call between the bot and a PSTN number. In this example, the media is hosted locally by the application. The values of authorization token, callback URL, application instance ID, application instance display name, phone ID and tenant ID must be replaced with actual values to make the example work.

> **Note:** Application instance ID is the object ID of application instance. The application ID that application instance links to should match the one in authorization token. Phone ID is the phone number in E.164 format.

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "callbackUri": "https://bot.contoso.com/callback",
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "applicationInstance": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "3d913abb-aec0-4964-8fa6-3c6850c4f278"
      },
    },
    "countryCode": null,
    "endpointType": null,
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "phone": {
          "@odata.type": "#microsoft.graph.identity",
          "id": "+12345678901"
        }
      }
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration>"
  },
  "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Call
{
	OdataType = "#microsoft.graph.call",
	CallbackUri = "https://bot.contoso.com/callback",
	Source = new ParticipantInfo
	{
		OdataType = "#microsoft.graph.participantInfo",
		Identity = new IdentitySet
		{
			OdataType = "#microsoft.graph.identitySet",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"applicationInstance" , new Identity
					{
						OdataType = "#microsoft.graph.identity",
						DisplayName = "Calling Bot",
						Id = "3d913abb-aec0-4964-8fa6-3c6850c4f278",
					}
				},
			},
		},
		CountryCode = null,
		EndpointType = null,
		Region = null,
		LanguageId = null,
	},
	Targets = new List<InvitationParticipantInfo>
	{
		new InvitationParticipantInfo
		{
			OdataType = "#microsoft.graph.invitationParticipantInfo",
			Identity = new IdentitySet
			{
				OdataType = "#microsoft.graph.identitySet",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"phone" , new Identity
						{
							OdataType = "#microsoft.graph.identity",
							Id = "+12345678901",
						}
					},
				},
			},
		},
	},
	RequestedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new AppHostedMediaConfig
	{
		OdataType = "#microsoft.graph.appHostedMediaConfig",
		Blob = "<Media Session Configuration>",
	},
	TenantId = "aa67bd4c-8475-432d-bd41-39f255720e0a",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls.PostAsync(requestBody);
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

requestBody := graphmodels.NewCall()
callbackUri := "https://bot.contoso.com/callback"
requestBody.SetCallbackUri(&callbackUri) 
source := graphmodels.NewParticipantInfo()
identity := graphmodels.NewIdentitySet()
additionalData := map[string]interface{}{
applicationInstance := graphmodels.NewIdentity()
displayName := "Calling Bot"
applicationInstance.SetDisplayName(&displayName) 
id := "3d913abb-aec0-4964-8fa6-3c6850c4f278"
applicationInstance.SetId(&id) 
	identity.SetApplicationInstance(applicationInstance)
}
identity.SetAdditionalData(additionalData)
source.SetIdentity(identity)
countryCode := null
source.SetCountryCode(&countryCode) 
endpointType := null
source.SetEndpointType(&endpointType) 
region := null
source.SetRegion(&region) 
languageId := null
source.SetLanguageId(&languageId) 
requestBody.SetSource(source)


invitationParticipantInfo := graphmodels.NewInvitationParticipantInfo()
identity := graphmodels.NewIdentitySet()
additionalData := map[string]interface{}{
phone := graphmodels.NewIdentity()
id := "+12345678901"
phone.SetId(&id) 
	identity.SetPhone(phone)
}
identity.SetAdditionalData(additionalData)
invitationParticipantInfo.SetIdentity(identity)

targets := []graphmodels.InvitationParticipantInfoable {
	invitationParticipantInfo,
}
requestBody.SetTargets(targets)
requestedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetRequestedModalities(requestedModalities)
mediaConfig := graphmodels.NewAppHostedMediaConfig()
blob := "<Media Session Configuration>"
mediaConfig.SetBlob(&blob) 
requestBody.SetMediaConfig(mediaConfig)
tenantId := "aa67bd4c-8475-432d-bd41-39f255720e0a"
requestBody.SetTenantId(&tenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calls, err := graphClient.Communications().Calls().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Call call = new Call();
call.setOdataType("#microsoft.graph.call");
call.setCallbackUri("https://bot.contoso.com/callback");
ParticipantInfo source = new ParticipantInfo();
source.setOdataType("#microsoft.graph.participantInfo");
IdentitySet identity = new IdentitySet();
identity.setOdataType("#microsoft.graph.identitySet");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
Identity applicationInstance = new Identity();
applicationInstance.setOdataType("#microsoft.graph.identity");
applicationInstance.setDisplayName("Calling Bot");
applicationInstance.setId("3d913abb-aec0-4964-8fa6-3c6850c4f278");
additionalData.put("applicationInstance", applicationInstance);
identity.setAdditionalData(additionalData);
source.setIdentity(identity);
source.setCountryCode(null);
source.setEndpointType(null);
source.setRegion(null);
source.setLanguageId(null);
call.setSource(source);
LinkedList<InvitationParticipantInfo> targets = new LinkedList<InvitationParticipantInfo>();
InvitationParticipantInfo invitationParticipantInfo = new InvitationParticipantInfo();
invitationParticipantInfo.setOdataType("#microsoft.graph.invitationParticipantInfo");
IdentitySet identity1 = new IdentitySet();
identity1.setOdataType("#microsoft.graph.identitySet");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
Identity phone = new Identity();
phone.setOdataType("#microsoft.graph.identity");
phone.setId("+12345678901");
additionalData1.put("phone", phone);
identity1.setAdditionalData(additionalData1);
invitationParticipantInfo.setIdentity(identity1);
targets.add(invitationParticipantInfo);
call.setTargets(targets);
LinkedList<Modality> requestedModalities = new LinkedList<Modality>();
requestedModalities.add(Modality.Audio);
call.setRequestedModalities(requestedModalities);
AppHostedMediaConfig mediaConfig = new AppHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.appHostedMediaConfig");
mediaConfig.setBlob("<Media Session Configuration>");
call.setMediaConfig(mediaConfig);
call.setTenantId("aa67bd4c-8475-432d-bd41-39f255720e0a");
Call result = graphClient.communications().calls().post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const call = {
  '@odata.type': '#microsoft.graph.call',
  callbackUri: 'https://bot.contoso.com/callback',
  source: {
    '@odata.type': '#microsoft.graph.participantInfo',
    identity: {
      '@odata.type': '#microsoft.graph.identitySet',
      applicationInstance: {
        '@odata.type': '#microsoft.graph.identity',
        displayName: 'Calling Bot',
        id: '3d913abb-aec0-4964-8fa6-3c6850c4f278'
      },
    },
    countryCode: null,
    endpointType: null,
    region: null,
    languageId: null
  },
  targets: [
    {
      '@odata.type': '#microsoft.graph.invitationParticipantInfo',
      identity: {
        '@odata.type': '#microsoft.graph.identitySet',
        phone: {
          '@odata.type': '#microsoft.graph.identity',
          id: '+12345678901'
        }
      }
    }
  ],
  requestedModalities: [
    'audio'
  ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.appHostedMediaConfig',
    blob: '<Media Session Configuration>'
  },
  tenantId: 'aa67bd4c-8475-432d-bd41-39f255720e0a'
};

await client.api('/communications/calls')
	.post(call);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Call;
use Microsoft\Graph\Generated\Models\ParticipantInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\InvitationParticipantInfo;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\AppHostedMediaConfig;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Call();
$requestBody->setOdataType('#microsoft.graph.call');
$requestBody->setCallbackUri('https://bot.contoso.com/callback');
$source = new ParticipantInfo();
$source->setOdataType('#microsoft.graph.participantInfo');
$sourceIdentity = new IdentitySet();
$sourceIdentity->setOdataType('#microsoft.graph.identitySet');
$additionalData = [
	'applicationInstance' => [
		'@odata.type' => '#microsoft.graph.identity',
		'displayName' => 'Calling Bot',
		'id' => '3d913abb-aec0-4964-8fa6-3c6850c4f278',
	],
];
$sourceIdentity->setAdditionalData($additionalData);
$source->setIdentity($sourceIdentity);
$source->setCountryCode(null);
$source->setEndpointType(null);
$source->setRegion(null);
$source->setLanguageId(null);
$requestBody->setSource($source);
$targetsInvitationParticipantInfo1 = new InvitationParticipantInfo();
$targetsInvitationParticipantInfo1->setOdataType('#microsoft.graph.invitationParticipantInfo');
$targetsInvitationParticipantInfo1Identity = new IdentitySet();
$targetsInvitationParticipantInfo1Identity->setOdataType('#microsoft.graph.identitySet');
$additionalData = [
	'phone' => [
		'@odata.type' => '#microsoft.graph.identity',
		'id' => '+12345678901',
	],
];
$targetsInvitationParticipantInfo1Identity->setAdditionalData($additionalData);
$targetsInvitationParticipantInfo1->setIdentity($targetsInvitationParticipantInfo1Identity);
$targetsArray []= $targetsInvitationParticipantInfo1;
$requestBody->setTargets($targetsArray);

$requestBody->setRequestedModalities([new Modality('audio'),]);
$mediaConfig = new AppHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.appHostedMediaConfig');
$mediaConfig->setBlob('<Media Session Configuration>');
$requestBody->setMediaConfig($mediaConfig);
$requestBody->setTenantId('aa67bd4c-8475-432d-bd41-39f255720e0a');

$result = $graphServiceClient->communications()->calls()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.call"
	callbackUri = "https://bot.contoso.com/callback"
	source = @{
		"@odata.type" = "#microsoft.graph.participantInfo"
		identity = @{
			"@odata.type" = "#microsoft.graph.identitySet"
			applicationInstance = @{
				"@odata.type" = "#microsoft.graph.identity"
				displayName = "Calling Bot"
				id = "3d913abb-aec0-4964-8fa6-3c6850c4f278"
			}
		}
		countryCode = $null
		endpointType = $null
		region = $null
		languageId = $null
	}
	targets = @(
		@{
			"@odata.type" = "#microsoft.graph.invitationParticipantInfo"
			identity = @{
				"@odata.type" = "#microsoft.graph.identitySet"
				phone = @{
					"@odata.type" = "#microsoft.graph.identity"
					id = "+12345678901"
				}
			}
		}
	)
	requestedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.appHostedMediaConfig"
	blob = "<Media Session Configuration>"
}
tenantId = "aa67bd4c-8475-432d-bd41-39f255720e0a"
}

New-MgCommunicationCall -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.call import Call
from msgraph.generated.models.participant_info import ParticipantInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.invitation_participant_info import InvitationParticipantInfo
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.app_hosted_media_config import AppHostedMediaConfig
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Call(
	odata_type = "#microsoft.graph.call",
	callback_uri = "https://bot.contoso.com/callback",
	source = ParticipantInfo(
		odata_type = "#microsoft.graph.participantInfo",
		identity = IdentitySet(
			odata_type = "#microsoft.graph.identitySet",
			additional_data = {
					"application_instance" : {
							"@odata_type" : "#microsoft.graph.identity",
							"display_name" : "Calling Bot",
							"id" : "3d913abb-aec0-4964-8fa6-3c6850c4f278",
					},
			}
		),
		country_code = None,
		endpoint_type = None,
		region = None,
		language_id = None,
	),
	targets = [
		InvitationParticipantInfo(
			odata_type = "#microsoft.graph.invitationParticipantInfo",
			identity = IdentitySet(
				odata_type = "#microsoft.graph.identitySet",
				additional_data = {
						"phone" : {
								"@odata_type" : "#microsoft.graph.identity",
								"id" : "+12345678901",
						},
				}
			),
		),
	],
	requested_modalities = [
		Modality.Audio,
	],
	media_config = AppHostedMediaConfig(
		odata_type = "#microsoft.graph.appHostedMediaConfig",
		blob = "<Media Session Configuration>",
	),
	tenant_id = "aa67bd4c-8475-432d-bd41-39f255720e0a",
)

result = await graph_client.communications.calls.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/communications/calls/2e1a0b00-2db4-4022-9570-243709c565ab
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.call",
  "state": "establishing",
  "direction": "outgoing",
  "callbackUri": "https://bot.contoso.com/callback",
  "callChainId": "d8217646-3110-40b1-bae6-e9ac6c3a9f74",
  "callRoutes": [],
  "source": {
    "@odata.type": "#microsoft.graph.participantInfo",
    "identity": {
      "@odata.type": "#microsoft.graph.identitySet",
      "applicationInstance": {
        "@odata.type": "#microsoft.graph.identity",
        "displayName": "Calling Bot",
        "id": "3d913abb-aec0-4964-8fa6-3c6850c4f278"
      },
    },
    "countryCode": null,
    "endpointType": null,
    "region": null,
    "languageId": null
  },
  "targets": [
    {
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",
      "identity": {
        "@odata.type": "#microsoft.graph.identitySet",
        "phone": {
          "@odata.type": "#microsoft.graph.identity",
          "id": "+12345678901"
        }
      },
      "endpointType": null,
      "region": null,
      "replacesCallId": null,
      "languageId": null
    }
  ],
  "requestedModalities": [
    "audio"
  ],
  "activeModalities": [],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration>",
  },
  "routingPolicies": [],
  "tenantId": "aa67bd4c-8475-432d-bd41-39f255720e0a",
  "myParticipantId": "499ff390-7a72-40e8-83a0-8fac6295ae7e",
  "id": "2e1a0b00-2db4-4022-9570-243709c565ab",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#app/calls/$entity",
  "subject": null,
  "terminationReason": null,
  "ringingTimeoutInSeconds": null,
  "mediaState": null,
  "resultInfo": null,
  "answeredBy": null,
  "chatInfo": null,
  "meetingInfo": null,
  "transcription": null,
  "meetingCapability": null,
  "toneInfo": null
}
```
