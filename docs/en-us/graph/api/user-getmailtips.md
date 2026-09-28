<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-getmailtips?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# user: getMailTips

Namespace: microsoft.graph

Get the MailTips of one or more recipients as available to the signed-in [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0).

Note that by making a `POST` call to the `getMailTips` action, you can request specific types of MailTips to be returned for more than one recipient at one time. The requested MailTips are returned in a [mailTips](https://learn.microsoft.com/en-us/graph/api/resources/mailtips?view=graph-rest-1.0) collection.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.Read | Mail.Read.Shared, MailTips.ReadBasic.Shared |
| Delegated \(personal Microsoft account\) | Mail.Read | MailTips.ReadBasic.Shared |
| Application | Mail.Read | Not available. |

## HTTP request

```http
POST /me/getMailTips
POST /users/{id|userPrincipalName}/getMailTips
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, provide a JSON object with the following parameters.

| Property | Type | Description |
| :--- | :--- | :--- |
| EmailAddresses | String collection | A collection of SMTP addresses of recipients to get MailTips for. |
| MailTipsOptions | String | A enumeration of flags that represents the requested mailtips. The possible values are: `automaticReplies`, `customMailTip`, `deliveryRestriction`, `externalMemberCount`, `mailboxFullStatus`, `maxMessageSize`, `moderationStatus`, `recipientScope`, `recipientSuggestions`, and `totalMemberCount`. |

## Response

If successful, this method returns a `200 OK` response code and a collection of [mailTips](https://learn.microsoft.com/en-us/graph/api/resources/mailtips?view=graph-rest-1.0) objects in the response body.

## Example

### Request

The following example gets MailTips for the specified recipients, for any automatic reply settings and the mailbox full status.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/getMailTips
Content-Type: application/json

{
    "EmailAddresses": [
        "danas@contoso.com",
        "fannyd@contoso.com"
    ],
    "MailTipsOptions": "automaticReplies, mailboxFullStatus"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.GetMailTips;
using Microsoft.Graph.Models;

var requestBody = new GetMailTipsPostRequestBody
{
	EmailAddresses = new List<string>
	{
		"danas@contoso.com",
		"fannyd@contoso.com",
	},
	MailTipsOptions = MailTipsType.AutomaticReplies | MailTipsType.MailboxFullStatus,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.GetMailTips.PostAsGetMailTipsPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemGetMailTipsPostRequestBody()
emailAddresses := []string {
	"danas@contoso.com",
	"fannyd@contoso.com",
}
requestBody.SetEmailAddresses(emailAddresses)
mailTipsOptions := graphmodels.AUTOMATICREPLIES, MAILBOXFULLSTATUS_MAILTIPSTYPE 
requestBody.SetMailTipsOptions(&mailTipsOptions) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getMailTips, err := graphClient.Me().GetMailTips().PostAsGetMailTipsPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.getmailtips.GetMailTipsPostRequestBody getMailTipsPostRequestBody = new com.microsoft.graph.users.item.getmailtips.GetMailTipsPostRequestBody();
LinkedList<String> emailAddresses = new LinkedList<String>();
emailAddresses.add("danas@contoso.com");
emailAddresses.add("fannyd@contoso.com");
getMailTipsPostRequestBody.setEmailAddresses(emailAddresses);
getMailTipsPostRequestBody.setMailTipsOptions(EnumSet.of(MailTipsType.AutomaticReplies, MailTipsType.MailboxFullStatus));
var result = graphClient.me().getMailTips().post(getMailTipsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mailTips = {
    EmailAddresses: [
        'danas@contoso.com',
        'fannyd@contoso.com'
    ],
    MailTipsOptions: 'automaticReplies, mailboxFullStatus'
};

await client.api('/me/getMailTips')
	.post(mailTips);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\GetMailTips\GetMailTipsPostRequestBody;
use Microsoft\Graph\Generated\Models\MailTipsType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetMailTipsPostRequestBody();
$requestBody->setEmailAddresses(['danas@contoso.com', 'fannyd@contoso.com', 	]);
$requestBody->setMailTipsOptions(new MailTipsType('automaticReplies, mailboxFullStatus'));

$result = $graphServiceClient->me()->getMailTips()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users.Actions

$params = @{
	EmailAddresses = @(
	"danas@contoso.com"
"fannyd@contoso.com"
)
MailTipsOptions = "automaticReplies, mailboxFullStatus"
}

# A UPN can also be used as -UserId.
Get-MgUserMailTip -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.get_mail_tips.get_mail_tips_post_request_body import GetMailTipsPostRequestBody
from msgraph.generated.models.mail_tips_type import MailTipsType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetMailTipsPostRequestBody(
	email_addresses = [
		"danas@contoso.com",
		"fannyd@contoso.com",
	],
	mail_tips_options = MailTipsType.AutomaticReplies | MailTipsType.MailboxFullStatus,
)

result = await graph_client.me.get_mail_tips.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.mailTips)",
    "value":[
        {
            "emailAddress":{
                "name":"",
                "address":"danas@contoso.com"
            },
            "automaticReplies":{
                "message":"<style type=\"text/css\" style=\"\">\r\n<!--\r\np\r\n\t{margin-top:0;\r\n\tmargin-bottom:0}\r\n-->\r\n</style>\r\n<div dir=\"ltr\">\r\n<div id=\"x_divtagdefaultwrapper\" style=\"font-size:12pt; color:#000000; background-color:#FFFFFF; font-family:Calibri,Arial,Helvetica,sans-serif\">\r\n<p>Hi, I am on vacation right now. I'll get back to you after I return.<br>\r\n</p>\r\n</div>\r\n</div>",
                "messageLanguage":{
                    "locale":"en-US",
                    "displayName":"English (United States)"
                },
                "scheduledStartTime": {
                    "dateTime": "2018-08-07T02:00:00.0000000",
                    "timeZone": "UTC"
                },
                "scheduledEndTime": {
                    "dateTime": "2018-08-09T02:00:00.0000000",
                    "timeZone": "UTC"
                }
            },
            "mailboxFull":false
        },
        {
            "emailAddress":{
                "name":"",
                "address":"fannyd@contoso.com"
            },
            "automaticReplies":{
                "message":""
            },
            "mailboxFull":false
        }
    ]
}
```
