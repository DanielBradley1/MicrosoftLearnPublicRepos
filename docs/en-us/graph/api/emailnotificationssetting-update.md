<!-- Source: https://learn.microsoft.com/en-us/graph/api/emailnotificationssetting-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Update emailNotificationsSetting

Namespace: microsoft.graph

Update the properties of an [emailNotificationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/emailnotificationssetting?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Control.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /solutions/backupRestore/emailNotificationsSetting
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalEvents | notificationEventsType | Indicates whether to opt in to additional policy and restore updates. Possible values: `none`, `restoreAndPolicyUpdates`, `unknownFutureValue`. |
| isEnabled | Boolean | Indicates whether notifications are enabled. |
| recipients | [notificationRecipients](https://learn.microsoft.com/en-us/graph/api/resources/notificationrecipients?view=graph-rest-1.0) | Specifies the recipients who receive the notifications. |

## Response

If successful, this method returns a `200 OK` response code and an updated [emailNotificationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/emailnotificationssetting?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/solutions/backupRestore/emailNotificationsSetting
Content-Type: application/json

{
  "isEnabled": true,
  "additionalEvents": "restoreAndPolicyUpdates",
  "recipients": {
    "role": "custom",
    "customRecipients": [
      {
        "email": "amala@contoso.com"
      },
      {
        "email": "conrad@contoso.com"
      },
      {
        "email": "lothar@contoso.com"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EmailNotificationsSetting
{
	IsEnabled = true,
	AdditionalEvents = NotificationEventsType.RestoreAndPolicyUpdates,
	Recipients = new NotificationRecipients
	{
		Role = NotificationRecipientsType.Custom,
		CustomRecipients = new List<EmailIdentity>
		{
			new EmailIdentity
			{
				Email = "amala@contoso.com",
			},
			new EmailIdentity
			{
				Email = "conrad@contoso.com",
			},
			new EmailIdentity
			{
				Email = "lothar@contoso.com",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.EmailNotificationsSetting.PatchAsync(requestBody);
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

requestBody := graphmodels.NewEmailNotificationsSetting()
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
additionalEvents := graphmodels.RESTOREANDPOLICYUPDATES_NOTIFICATIONEVENTSTYPE 
requestBody.SetAdditionalEvents(&additionalEvents) 
recipients := graphmodels.NewNotificationRecipients()
role := graphmodels.CUSTOM_NOTIFICATIONRECIPIENTSTYPE 
recipients.SetRole(&role) 


emailIdentity := graphmodels.NewEmailIdentity()
email := "amala@contoso.com"
emailIdentity.SetEmail(&email) 
emailIdentity1 := graphmodels.NewEmailIdentity()
email := "conrad@contoso.com"
emailIdentity1.SetEmail(&email) 
emailIdentity2 := graphmodels.NewEmailIdentity()
email := "lothar@contoso.com"
emailIdentity2.SetEmail(&email) 

customRecipients := []graphmodels.EmailIdentityable {
	emailIdentity,
	emailIdentity1,
	emailIdentity2,
}
recipients.SetCustomRecipients(customRecipients)
requestBody.SetRecipients(recipients)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
emailNotificationsSetting, err := graphClient.Solutions().BackupRestore().EmailNotificationsSetting().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EmailNotificationsSetting emailNotificationsSetting = new EmailNotificationsSetting();
emailNotificationsSetting.setIsEnabled(true);
emailNotificationsSetting.setAdditionalEvents(EnumSet.of(NotificationEventsType.RestoreAndPolicyUpdates));
NotificationRecipients recipients = new NotificationRecipients();
recipients.setRole(EnumSet.of(NotificationRecipientsType.Custom));
LinkedList<EmailIdentity> customRecipients = new LinkedList<EmailIdentity>();
EmailIdentity emailIdentity = new EmailIdentity();
emailIdentity.setEmail("amala@contoso.com");
customRecipients.add(emailIdentity);
EmailIdentity emailIdentity1 = new EmailIdentity();
emailIdentity1.setEmail("conrad@contoso.com");
customRecipients.add(emailIdentity1);
EmailIdentity emailIdentity2 = new EmailIdentity();
emailIdentity2.setEmail("lothar@contoso.com");
customRecipients.add(emailIdentity2);
recipients.setCustomRecipients(customRecipients);
emailNotificationsSetting.setRecipients(recipients);
EmailNotificationsSetting result = graphClient.solutions().backupRestore().emailNotificationsSetting().patch(emailNotificationsSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const emailNotificationsSetting = {
  isEnabled: true,
  additionalEvents: 'restoreAndPolicyUpdates',
  recipients: {
    role: 'custom',
    customRecipients: [
      {
        email: 'amala@contoso.com'
      },
      {
        email: 'conrad@contoso.com'
      },
      {
        email: 'lothar@contoso.com'
      }
    ]
  }
};

await client.api('/solutions/backupRestore/emailNotificationsSetting')
	.update(emailNotificationsSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EmailNotificationsSetting;
use Microsoft\Graph\Generated\Models\NotificationEventsType;
use Microsoft\Graph\Generated\Models\NotificationRecipients;
use Microsoft\Graph\Generated\Models\NotificationRecipientsType;
use Microsoft\Graph\Generated\Models\EmailIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EmailNotificationsSetting();
$requestBody->setIsEnabled(true);
$requestBody->setAdditionalEvents(new NotificationEventsType('restoreAndPolicyUpdates'));
$recipients = new NotificationRecipients();
$recipients->setRole(new NotificationRecipientsType('custom'));
$customRecipientsEmailIdentity1 = new EmailIdentity();
$customRecipientsEmailIdentity1->setEmail('amala@contoso.com');
$customRecipientsArray []= $customRecipientsEmailIdentity1;
$customRecipientsEmailIdentity2 = new EmailIdentity();
$customRecipientsEmailIdentity2->setEmail('conrad@contoso.com');
$customRecipientsArray []= $customRecipientsEmailIdentity2;
$customRecipientsEmailIdentity3 = new EmailIdentity();
$customRecipientsEmailIdentity3->setEmail('lothar@contoso.com');
$customRecipientsArray []= $customRecipientsEmailIdentity3;
$recipients->setCustomRecipients($customRecipientsArray);

$requestBody->setRecipients($recipients);

$result = $graphServiceClient->solutions()->backupRestore()->emailNotificationsSetting()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	isEnabled = $true
	additionalEvents = "restoreAndPolicyUpdates"
	recipients = @{
		role = "custom"
		customRecipients = @(
			@{
				email = "amala@contoso.com"
			}
			@{
				email = "conrad@contoso.com"
			}
			@{
				email = "lothar@contoso.com"
			}
		)
	}
}

Update-MgSolutionBackupRestoreEmailNotificationSetting -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.email_notifications_setting import EmailNotificationsSetting
from msgraph.generated.models.notification_events_type import NotificationEventsType
from msgraph.generated.models.notification_recipients import NotificationRecipients
from msgraph.generated.models.notification_recipients_type import NotificationRecipientsType
from msgraph.generated.models.email_identity import EmailIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EmailNotificationsSetting(
	is_enabled = True,
	additional_events = NotificationEventsType.RestoreAndPolicyUpdates,
	recipients = NotificationRecipients(
		role = NotificationRecipientsType.Custom,
		custom_recipients = [
			EmailIdentity(
				email = "amala@contoso.com",
			),
			EmailIdentity(
				email = "conrad@contoso.com",
			),
			EmailIdentity(
				email = "lothar@contoso.com",
			),
		],
	),
)

result = await graph_client.solutions.backup_restore.email_notifications_setting.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "isEnabled": true,
  "additionalEvents": "restoreAndPolicyUpdates",
  "recipients": {
    "role": "custom",
    "customRecipients": [
      {
        "email": "amala@contoso.com"
      },
      {
        "email": "conrad@contoso.com"
      },
      {
        "email": "lothar@contoso.com"
      }
    ]
  }
}
```
