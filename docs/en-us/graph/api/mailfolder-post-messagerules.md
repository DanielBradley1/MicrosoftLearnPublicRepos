<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailfolder-post-messagerules?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create rule

Namespace: microsoft.graph

Create a [messageRule](https://learn.microsoft.com/en-us/graph/api/resources/messagerule?view=graph-rest-1.0) object by specifying a set of conditions and actions.

Outlook carries out those actions if an incoming message in the user's Inbox meets the specified conditions.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxSettings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | MailboxSettings.ReadWrite | Not available. |
| Application | MailboxSettings.ReadWrite | Not available. |

## HTTP request

```http
POST /me/mailFolders/inbox/messageRules
POST /users/{id | userPrincipalName}/mailFolders/inbox/messageRules
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply the parameters that are applicable to your rule. The following are body parameters that are typically used when creating rules. You can specify any other writable **messageRule** properties as appropriate in the request body.

| Name | Type | Description |
| :--- | :--- | :--- |
| actions | [messageRuleActions](https://learn.microsoft.com/en-us/graph/api/resources/messageruleactions?view=graph-rest-1.0) | Actions to be taken on a message when the corresponding conditions, if any, are fulfilled. Required. |
| conditions | [messageRulePredicates](https://learn.microsoft.com/en-us/graph/api/resources/messagerulepredicates?view=graph-rest-1.0) | Conditions that when fulfilled, will trigger the corresponding actions for that rule. Optional. |
| displayName | String | The display name of the rule. Required. |
| exceptions | [messageRulePredicates](https://learn.microsoft.com/en-us/graph/api/resources/messagerulepredicates?view=graph-rest-1.0) | Represents exception conditions for the rule. Optional. |
| isEnabled | Boolean | Indicates whether the rule is enabled to be applied to messages. Optional. |
| sequence | Int32 | Indicates the order in which the rule is executed, among other rules. Required. |

## Response

If successful, this method returns `201 Created` response code and a **messageRule** object in the response body.

## Example

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
POST https://graph.microsoft.com/v1.0/me/mailFolders/inbox/messageRules
Content-type: application/json

{
    "displayName": "From partner",
    "sequence": 2,
    "isEnabled": true,
    "conditions": {
        "senderContains": [
          "adele"
        ]
     },
     "actions": {
        "forwardTo": [
          {
             "emailAddress": {
                "name": "Alex Wilbur",
                "address": "AlexW@contoso.com"
              }
           }
        ],
        "stopProcessingRules": true
     }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MessageRule
{
	DisplayName = "From partner",
	Sequence = 2,
	IsEnabled = true,
	Conditions = new MessageRulePredicates
	{
		SenderContains = new List<string>
		{
			"adele",
		},
	},
	Actions = new MessageRuleActions
	{
		ForwardTo = new List<Recipient>
		{
			new Recipient
			{
				EmailAddress = new EmailAddress
				{
					Name = "Alex Wilbur",
					Address = "AlexW@contoso.com",
				},
			},
		},
		StopProcessingRules = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.MailFolders["{mailFolder-id}"].MessageRules.PostAsync(requestBody);
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

requestBody := graphmodels.NewMessageRule()
displayName := "From partner"
requestBody.SetDisplayName(&displayName) 
sequence := int32(2)
requestBody.SetSequence(&sequence) 
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
conditions := graphmodels.NewMessageRulePredicates()
senderContains := []string {
	"adele",
}
conditions.SetSenderContains(senderContains)
requestBody.SetConditions(conditions)
actions := graphmodels.NewMessageRuleActions()


recipient := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
name := "Alex Wilbur"
emailAddress.SetName(&name) 
address := "AlexW@contoso.com"
emailAddress.SetAddress(&address) 
recipient.SetEmailAddress(emailAddress)

forwardTo := []graphmodels.Recipientable {
	recipient,
}
actions.SetForwardTo(forwardTo)
stopProcessingRules := true
actions.SetStopProcessingRules(&stopProcessingRules) 
requestBody.SetActions(actions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messageRules, err := graphClient.Me().MailFolders().ByMailFolderId("mailFolder-id").MessageRules().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MessageRule messageRule = new MessageRule();
messageRule.setDisplayName("From partner");
messageRule.setSequence(2);
messageRule.setIsEnabled(true);
MessageRulePredicates conditions = new MessageRulePredicates();
LinkedList<String> senderContains = new LinkedList<String>();
senderContains.add("adele");
conditions.setSenderContains(senderContains);
messageRule.setConditions(conditions);
MessageRuleActions actions = new MessageRuleActions();
LinkedList<Recipient> forwardTo = new LinkedList<Recipient>();
Recipient recipient = new Recipient();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setName("Alex Wilbur");
emailAddress.setAddress("AlexW@contoso.com");
recipient.setEmailAddress(emailAddress);
forwardTo.add(recipient);
actions.setForwardTo(forwardTo);
actions.setStopProcessingRules(true);
messageRule.setActions(actions);
MessageRule result = graphClient.me().mailFolders().byMailFolderId("{mailFolder-id}").messageRules().post(messageRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const messageRule = {
    displayName: 'From partner',
    sequence: 2,
    isEnabled: true,
    conditions: {
        senderContains: [
          'adele'
        ]
     },
     actions: {
        forwardTo: [
          {
             emailAddress: {
                name: 'Alex Wilbur',
                address: 'AlexW@contoso.com'
              }
           }
        ],
        stopProcessingRules: true
     }
};

await client.api('/me/mailFolders/inbox/messageRules')
	.post(messageRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MessageRule;
use Microsoft\Graph\Generated\Models\MessageRulePredicates;
use Microsoft\Graph\Generated\Models\MessageRuleActions;
use Microsoft\Graph\Generated\Models\Recipient;
use Microsoft\Graph\Generated\Models\EmailAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MessageRule();
$requestBody->setDisplayName('From partner');
$requestBody->setSequence(2);
$requestBody->setIsEnabled(true);
$conditions = new MessageRulePredicates();
$conditions->setSenderContains(['adele', 	]);
$requestBody->setConditions($conditions);
$actions = new MessageRuleActions();
$forwardToRecipient1 = new Recipient();
$forwardToRecipient1EmailAddress = new EmailAddress();
$forwardToRecipient1EmailAddress->setName('Alex Wilbur');
$forwardToRecipient1EmailAddress->setAddress('AlexW@contoso.com');
$forwardToRecipient1->setEmailAddress($forwardToRecipient1EmailAddress);
$forwardToArray []= $forwardToRecipient1;
$actions->setForwardTo($forwardToArray);

$actions->setStopProcessingRules(true);
$requestBody->setActions($actions);

$result = $graphServiceClient->me()->mailFolders()->byMailFolderId('mailFolder-id')->messageRules()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	displayName = "From partner"
	sequence = 2
	isEnabled = $true
	conditions = @{
		senderContains = @(
		"adele"
	)
}
actions = @{
	forwardTo = @(
		@{
			emailAddress = @{
				name = "Alex Wilbur"
				address = "AlexW@contoso.com"
			}
		}
	)
	stopProcessingRules = $true
}
}

# A UPN can also be used as -UserId.
New-MgUserMailFolderMessageRule -UserId $userId -MailFolderId $mailFolderId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.message_rule import MessageRule
from msgraph.generated.models.message_rule_predicates import MessageRulePredicates
from msgraph.generated.models.message_rule_actions import MessageRuleActions
from msgraph.generated.models.recipient import Recipient
from msgraph.generated.models.email_address import EmailAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MessageRule(
	display_name = "From partner",
	sequence = 2,
	is_enabled = True,
	conditions = MessageRulePredicates(
		sender_contains = [
			"adele",
		],
	),
	actions = MessageRuleActions(
		forward_to = [
			Recipient(
				email_address = EmailAddress(
					name = "Alex Wilbur",
					address = "AlexW@contoso.com",
				),
			),
		],
		stop_processing_rules = True,
	),
)

result = await graph_client.me.mail_folders.by_mail_folder_id('mailFolder-id').message_rules.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id":"AQAAAJ5dZqA=",
  "displayName":"From partner",
  "sequence":2,
  "isEnabled":true,
  "hasError":false,
  "isReadOnly":false,
  "conditions":{
    "senderContains":[
      "ADELE"
    ]
  },
  "actions":{
      "stopProcessingRules":true,
      "forwardTo":[
        {
          "emailAddress":{
            "name":"Alex Wilbur",
            "address":"AlexW@contoso.com"
          }
        }
      ]
  }
}
```
