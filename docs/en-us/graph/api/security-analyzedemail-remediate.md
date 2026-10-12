<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-analyzedemail-remediate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# analyzedEmail: remediate

Namespace: microsoft.graph.security

Remove a potential threat from end users' mailboxes.

Remediation means to take prescribed action against a threat. This API can trigger email purge actions like move to junk, move to deleted items, soft delete, hard delete, or move to Inbox. This API enables scenarios and use cases such as SOAR integration, playbooks, and automations. For more information read [email remediation, trigger action and track actions](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365?view=o365-worldwide&preserve-view=true). If there is false positives admins can take move to inbox action.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityAnalyzedMessage.ReadWrite.All | Not available. |

## HTTP request

```http
POST /security/collaboration/analyzedEmails/remediate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the remediation that is used as a reference in the action center. |
| description | String | The description of the remediation. |
| severity | microsoft.graph.security.remediationSeverity | The severity of the remediation. The possible values are: `low`, `medium`, `high`, `unknownFutureValue`. |
| action | microsoft.graph.security.remediationAction | The types of move and delete actions that are supported. The possible values are: `moveToJunk`, `moveToInbox`, `hardDelete`, `softDelete`, `moveToDeletedItems`, `unknownFutureValue`, `moveToQuarantine`. Use the `Prefer: include-unknown-enum-members` request header to get the following members from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `moveToQuarantine`. |
| remediateSendersCopy | Boolean | For internal or outbound email, indicates whether to remediate the sender's copy of an email. |
| analyzedEmails | [microsoft.graph.security.analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0) collection | Contains the **networkMessageId** and **recipientEmailAddress** values of the analyzed emails. |

## Response

If successful, this action returns a `202 Accepted` response code and a `Location` header with a link to the tracking information.

> **Note:** The response to the action can be tracked in [https://security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history). To learn more, see [Use the Action center](https://learn.microsoft.com/en-us/microsoft-365/security/defender/m365d-action-center?view=o365-worldwide&preserve-view=true).

## Examples

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
POST https://graph.microsoft.com/v1.0/security/collaboration/analyzedEmails/remediate
Content-Type: application/json

{
    "displayName": "Clean up Phish email",
    "description": "Delete email",
    "severity": "medium",
    "action": "softDelete",
    "remediateSendersCopy": "false",
    "analyzedEmails": [
      {
        "networkMessageId": "73ca4154-58d8-43d0-a890-08dc18c52e6d",
        "recipientEmailAddress": "hannah.jarvis@contoso.com"
      },
      {
        "networkMessageId": "73ca4154-58d8-43d0-a890-08dc18c52e6d",
        "recipientEmailAddress": "preston.morales@contoso.com"
      }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Collaboration.AnalyzedEmails.MicrosoftGraphSecurityRemediate;
using Microsoft.Graph.Models.Security;

var requestBody = new RemediatePostRequestBody
{
	DisplayName = "Clean up Phish email",
	Description = "Delete email",
	Severity = RemediationSeverity.Medium,
	Action = RemediationAction.SoftDelete,
	RemediateSendersCopy = false,
	AnalyzedEmails = new List<AnalyzedEmail>
	{
		new AnalyzedEmail
		{
			NetworkMessageId = "73ca4154-58d8-43d0-a890-08dc18c52e6d",
			RecipientEmailAddress = "hannah.jarvis@contoso.com",
		},
		new AnalyzedEmail
		{
			NetworkMessageId = "73ca4154-58d8-43d0-a890-08dc18c52e6d",
			RecipientEmailAddress = "preston.morales@contoso.com",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Collaboration.AnalyzedEmails.MicrosoftGraphSecurityRemediate.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewRemediatePostRequestBody()
displayName := "Clean up Phish email"
requestBody.SetDisplayName(&displayName) 
description := "Delete email"
requestBody.SetDescription(&description) 
severity := graphmodels.MEDIUM_REMEDIATIONSEVERITY 
requestBody.SetSeverity(&severity) 
action := graphmodels.SOFTDELETE_REMEDIATIONACTION 
requestBody.SetAction(&action) 
remediateSendersCopy := false
requestBody.SetRemediateSendersCopy(&remediateSendersCopy) 


analyzedEmail := graphmodelssecurity.NewAnalyzedEmail()
networkMessageId := "73ca4154-58d8-43d0-a890-08dc18c52e6d"
analyzedEmail.SetNetworkMessageId(&networkMessageId) 
recipientEmailAddress := "hannah.jarvis@contoso.com"
analyzedEmail.SetRecipientEmailAddress(&recipientEmailAddress) 
analyzedEmail1 := graphmodelssecurity.NewAnalyzedEmail()
networkMessageId := "73ca4154-58d8-43d0-a890-08dc18c52e6d"
analyzedEmail1.SetNetworkMessageId(&networkMessageId) 
recipientEmailAddress := "preston.morales@contoso.com"
analyzedEmail1.SetRecipientEmailAddress(&recipientEmailAddress) 

analyzedEmails := []graphmodelssecurity.AnalyzedEmailable {
	analyzedEmail,
	analyzedEmail1,
}
requestBody.SetAnalyzedEmails(analyzedEmails)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Collaboration().AnalyzedEmails().MicrosoftGraphSecurityRemediate().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.collaboration.analyzedemails.microsoftgraphsecurityremediate.RemediatePostRequestBody remediatePostRequestBody = new com.microsoft.graph.security.collaboration.analyzedemails.microsoftgraphsecurityremediate.RemediatePostRequestBody();
remediatePostRequestBody.setDisplayName("Clean up Phish email");
remediatePostRequestBody.setDescription("Delete email");
remediatePostRequestBody.setSeverity(com.microsoft.graph.models.security.RemediationSeverity.Medium);
remediatePostRequestBody.setAction(com.microsoft.graph.models.security.RemediationAction.SoftDelete);
remediatePostRequestBody.setRemediateSendersCopy(false);
LinkedList<com.microsoft.graph.models.security.AnalyzedEmail> analyzedEmails = new LinkedList<com.microsoft.graph.models.security.AnalyzedEmail>();
com.microsoft.graph.models.security.AnalyzedEmail analyzedEmail = new com.microsoft.graph.models.security.AnalyzedEmail();
analyzedEmail.setNetworkMessageId("73ca4154-58d8-43d0-a890-08dc18c52e6d");
analyzedEmail.setRecipientEmailAddress("hannah.jarvis@contoso.com");
analyzedEmails.add(analyzedEmail);
com.microsoft.graph.models.security.AnalyzedEmail analyzedEmail1 = new com.microsoft.graph.models.security.AnalyzedEmail();
analyzedEmail1.setNetworkMessageId("73ca4154-58d8-43d0-a890-08dc18c52e6d");
analyzedEmail1.setRecipientEmailAddress("preston.morales@contoso.com");
analyzedEmails.add(analyzedEmail1);
remediatePostRequestBody.setAnalyzedEmails(analyzedEmails);
graphClient.security().collaboration().analyzedEmails().microsoftGraphSecurityRemediate().post(remediatePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const remediate = {
    displayName: 'Clean up Phish email',
    description: 'Delete email',
    severity: 'medium',
    action: 'softDelete',
    remediateSendersCopy: 'false',
    analyzedEmails: [
      {
        networkMessageId: '73ca4154-58d8-43d0-a890-08dc18c52e6d',
        recipientEmailAddress: 'hannah.jarvis@contoso.com'
      },
      {
        networkMessageId: '73ca4154-58d8-43d0-a890-08dc18c52e6d',
        recipientEmailAddress: 'preston.morales@contoso.com'
      }
    ]
};

await client.api('/security/collaboration/analyzedEmails/remediate')
	.post(remediate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Collaboration\AnalyzedEmails\MicrosoftGraphSecurityRemediate\RemediatePostRequestBody;
use Microsoft\Graph\Generated\Models\Security\RemediationSeverity;
use Microsoft\Graph\Generated\Models\Security\RemediationAction;
use Microsoft\Graph\Generated\Models\Security\AnalyzedEmail;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemediatePostRequestBody();
$requestBody->setDisplayName('Clean up Phish email');
$requestBody->setDescription('Delete email');
$requestBody->setSeverity(new RemediationSeverity('medium'));
$requestBody->setAction(new RemediationAction('softDelete'));
$requestBody->setRemediateSendersCopy(false);
$analyzedEmailsAnalyzedEmail1 = new AnalyzedEmail();
$analyzedEmailsAnalyzedEmail1->setNetworkMessageId('73ca4154-58d8-43d0-a890-08dc18c52e6d');
$analyzedEmailsAnalyzedEmail1->setRecipientEmailAddress('hannah.jarvis@contoso.com');
$analyzedEmailsArray []= $analyzedEmailsAnalyzedEmail1;
$analyzedEmailsAnalyzedEmail2 = new AnalyzedEmail();
$analyzedEmailsAnalyzedEmail2->setNetworkMessageId('73ca4154-58d8-43d0-a890-08dc18c52e6d');
$analyzedEmailsAnalyzedEmail2->setRecipientEmailAddress('preston.morales@contoso.com');
$analyzedEmailsArray []= $analyzedEmailsAnalyzedEmail2;
$requestBody->setAnalyzedEmails($analyzedEmailsArray);


$graphServiceClient->security()->collaboration()->analyzedEmails()->microsoftGraphSecurityRemediate()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "Clean up Phish email"
	description = "Delete email"
	severity = "medium"
	action = "softDelete"
	remediateSendersCopy = "false"
	analyzedEmails = @(
		@{
			networkMessageId = "73ca4154-58d8-43d0-a890-08dc18c52e6d"
			recipientEmailAddress = "hannah.jarvis@contoso.com"
		}
		@{
			networkMessageId = "73ca4154-58d8-43d0-a890-08dc18c52e6d"
			recipientEmailAddress = "preston.morales@contoso.com"
		}
	)
}

Invoke-MgRemediateSecurityCollaborationAnalyzedEmail -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.collaboration.analyzedemails.microsoft_graph_security_remediate.remediate_post_request_body import RemediatePostRequestBody
from msgraph.generated.models.remediation_severity import RemediationSeverity
from msgraph.generated.models.remediation_action import RemediationAction
from msgraph.generated.models.security.analyzed_email import AnalyzedEmail
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemediatePostRequestBody(
	display_name = "Clean up Phish email",
	description = "Delete email",
	severity = RemediationSeverity.Medium,
	action = RemediationAction.SoftDelete,
	remediate_senders_copy = False,
	analyzed_emails = [
		AnalyzedEmail(
			network_message_id = "73ca4154-58d8-43d0-a890-08dc18c52e6d",
			recipient_email_address = "hannah.jarvis@contoso.com",
		),
		AnalyzedEmail(
			network_message_id = "73ca4154-58d8-43d0-a890-08dc18c52e6d",
			recipient_email_address = "preston.morales@contoso.com",
		),
	],
)

await graph_client.security.collaboration.analyzed_emails.microsoft_graph_security_remediate.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Location: https://security.microsoft.com/action-center/history?filters={"bulkId":["{bulkId}"]}&tid={tid}
Content-Type: application/json;text/plain
Content-Length: 0
```
