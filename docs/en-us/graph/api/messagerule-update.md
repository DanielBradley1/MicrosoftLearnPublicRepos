<!-- Source: https://learn.microsoft.com/en-us/graph/api/messagerule-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update rule

Namespace: microsoft.graph

Change writable properties on a [messageRule](https://learn.microsoft.com/en-us/graph/api/resources/messagerule?view=graph-rest-1.0) object and save the changes.

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
PATCH /me/mailFolders/inbox/messageRules/{id}
PATCH /users/{id | userPrincipalName}/mailFolders/inbox/messageRules/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| actions | [messageRuleActions](https://learn.microsoft.com/en-us/graph/api/resources/messageruleactions?view=graph-rest-1.0) | Actions to be taken on a message when the corresponding conditions are fulfilled. |
| conditions | [messageRulePredicates](https://learn.microsoft.com/en-us/graph/api/resources/messagerulepredicates?view=graph-rest-1.0) | Conditions that when fulfilled, will trigger the corresponding actions for that rule. |
| displayName | String | The display name of the rule. |
| exceptions | [messageRulePredicates](https://learn.microsoft.com/en-us/graph/api/resources/messagerulepredicates?view=graph-rest-1.0) | Exception conditions for the rule. |
| isEnabled | Boolean | Indicates whether the rule is enabled to be applied to messages. |
| isReadOnly | Boolean | Indicates if the rule is read-only and cannot be modified or deleted by the rules REST API. |
| sequence | Int32 | Indicates the order in which the rule is executed, among other rules. |

## Response

If successful, this method returns a `200 OK` response code and updated [messageRule](https://learn.microsoft.com/en-us/graph/api/resources/messagerule?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example changes the name of the rule, and the actions to be taken for that rule in the [example](https://learn.microsoft.com/en-us/graph/api/messagerule-get?view=graph-rest-1.0#example) in [Get rule](https://learn.microsoft.com/en-us/graph/api/messagerule-get?view=graph-rest-1.0), from forwarding to an address to marking its importance as high.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/mailFolders/inbox/messageRules/AQAAAJ5dZqA=
Content-type: application/json

{
    "displayName": "Important from partner",
    "actions": {
        "markImportance": "high"
     }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MessageRule
{
	DisplayName = "Important from partner",
	Actions = new MessageRuleActions
	{
		MarkImportance = Importance.High,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.MailFolders["{mailFolder-id}"].MessageRules["{messageRule-id}"].PatchAsync(requestBody);
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
displayName := "Important from partner"
requestBody.SetDisplayName(&displayName) 
actions := graphmodels.NewMessageRuleActions()
markImportance := graphmodels.HIGH_IMPORTANCE 
actions.SetMarkImportance(&markImportance) 
requestBody.SetActions(actions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messageRules, err := graphClient.Me().MailFolders().ByMailFolderId("mailFolder-id").MessageRules().ByMessageRuleId("messageRule-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MessageRule messageRule = new MessageRule();
messageRule.setDisplayName("Important from partner");
MessageRuleActions actions = new MessageRuleActions();
actions.setMarkImportance(Importance.High);
messageRule.setActions(actions);
MessageRule result = graphClient.me().mailFolders().byMailFolderId("{mailFolder-id}").messageRules().byMessageRuleId("{messageRule-id}").patch(messageRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const messageRule = {
    displayName: 'Important from partner',
    actions: {
        markImportance: 'high'
     }
};

await client.api('/me/mailFolders/inbox/messageRules/AQAAAJ5dZqA=')
	.update(messageRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MessageRule;
use Microsoft\Graph\Generated\Models\MessageRuleActions;
use Microsoft\Graph\Generated\Models\Importance;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MessageRule();
$requestBody->setDisplayName('Important from partner');
$actions = new MessageRuleActions();
$actions->setMarkImportance(new Importance('high'));
$requestBody->setActions($actions);

$result = $graphServiceClient->me()->mailFolders()->byMailFolderId('mailFolder-id')->messageRules()->byMessageRuleId('messageRule-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	displayName = "Important from partner"
	actions = @{
		markImportance = "high"
	}
}

# A UPN can also be used as -UserId.
Update-MgUserMailFolderMessageRule -UserId $userId -MailFolderId $mailFolderId -MessageRuleId $messageRuleId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.message_rule import MessageRule
from msgraph.generated.models.message_rule_actions import MessageRuleActions
from msgraph.generated.models.importance import Importance
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MessageRule(
	display_name = "Important from partner",
	actions = MessageRuleActions(
		mark_importance = Importance.High,
	),
)

result = await graph_client.me.mail_folders.by_mail_folder_id('mailFolder-id').message_rules.by_message_rule_id('messageRule-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#Me/mailFolders('inbox')/messageRules/$entity",
  "id":"AQAAAJ5dZqA=",
  "displayName":"Important from partner",
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
    "markImportance": "high"
  }
}
```
