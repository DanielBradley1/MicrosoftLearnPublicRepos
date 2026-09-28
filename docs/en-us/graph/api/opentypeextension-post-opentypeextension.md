<!-- Source: https://learn.microsoft.com/en-us/graph/api/opentypeextension-post-opentypeextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-10 -->

# Create open extension

Namespace: microsoft.graph

Create an open extension \([openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) object\) and add custom properties in a new or existing instance of a resource. You can [create an open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-post-opentypeextension) in a resource instance and store custom data to it all in the same operation, except for specific resources.

The table in the [Permissions](#permissions) section lists the resources that support open extensions.

> **Note:** If you're creating open extensions on Outlook resources, see **Outlook-specific considerations** in [openTypeExtension resource type](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0#outlook-specific-considerations).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Depending on the resource you're creating, the extension and the permission type \(delegated or application\) requested, the permission specified in the following table is the least privileged required to call this API. To learn more, including [taking caution](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#best-practices-for-requesting-permissions) before choosing more privileged permissions, search for the following permissions in [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | Directory.AccessAsUser.All | Not supported | Device.ReadWrite.All |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.ReadWrite | Calendars.ReadWrite | Calendars.ReadWrite |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported | Group.ReadWrite.All |
| [group event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported | Not supported |
| [group post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported | Group.ReadWrite.All |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.ReadWrite | Mail.ReadWrite | Mail.ReadWrite |
| [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) | ShortNotes.ReadWrite | ShortNotes.ReadWrite | ShortNotes.ReadWrite.All |
| [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0) | Organization.ReadWrite.All | Not supported | Organization.ReadWrite.All |
| [personal contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Contacts.ReadWrite | Contacts.ReadWrite | Contacts.ReadWrite |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Tasks.ReadWrite | Tasks.ReadWrite | Tasks.ReadWrite.All |
| [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) | Tasks.ReadWrite | Tasks.ReadWrite | Tasks.ReadWrite.All |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.ReadWrite | Not supported | User.ReadWrite.All |

## HTTP request

### Create an extension in a new resource instance

Use the same REST request that you use to create the instance.

```http
POST /users/{id|userPrincipalName}/events
POST /users/{id|userPrincipalName}/messages
POST /users/{id|userPrincipalName}/notes
POST /groups/{id}/events
POST /groups/{id}/threads/{id}/posts/{id}/reply
POST /users/{id|userPrincipalName}/contacts
POST /users/{id|userPrincipalName}/todo/lists/{id}/tasks
POST /users/{id|userPrincipalName}/todo/lists
```

> **Note:** This syntax shows some common ways to create the supported resource instances. All other POST syntaxes that allows you to create these resource instances supports creating open extensions in them in a similar way.

See the [Request body](#request-body) section about including the properties of the new resource instance *and the extension* in the request body.

### Create an extension in an existing resource instance

Identify the resource instance in the request and do a `POST` to the **extensions** navigation property.

```http
POST /devices/{id}/extensions
POST /users/{id|userPrincipalName}/events/{id}/extensions
POST /groups/{id}/extensions
POST /groups/{id}/events/{id}/extensions
POST /groups/{id}/threads/{id}/posts/{id}/extensions
POST /users/{id|userPrincipalName}/messages/{id}/extensions
POST /users/{id|userPrincipalName}/notes/{id}/extensions
POST /organization/{id}/extensions
POST /users/{id|userPrincipalName}/contacts/{id}/extensions
POST /users/{id|userPrincipalName}/extensions
POST /users/{id|userPrincipalName}/todo/lists/{id}/tasks/{id}/extensions
POST /users/{id|userPrincipalName}/todo/lists/{id}/extensions
```

> **Note:** This syntax shows some common ways to identify a resource instance, in order to create an extension in it. All other syntaxes that allows you to identify these resource instances supports creating open extensions in them in a similar way.

See the [Request body](#request-body) section about including *the extension* in the request body.

## Path parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| id | string | A unique identifier for an object in the corresponding collection. Required. |

## Request headers

| Name | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

Provide a JSON body of an [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0), with the following required name-value pairs, and any other custom data. The data in the JSON payload can be primitive types, or arrays of primitive types.

| Name | Value |
| :--- | :--- |
| @odata.type | microsoft.graph.openTypeExtension |
| extensionName | %unique\_string% |

When creating an extension in a *new* resource instance, in addition to the new **openTypeExtension** object, provide a JSON representation of the relevant properties to create such a resource instance.

## Response

### Response code

Depending on the operation, the response code can be `201 Created` or `202 Accepted`.

When you create an extension using the same operation that you use to create a resource instance, the operation returns the same response code that it returns when you use the operation to create the resource instance without the extension. Refer to the corresponding articles for creating the instance, as listed [above](#create-an-extension-in-a-new-resource-instance).

### Response body

| Scenario | Resource | Response body |
| :--- | :--- | :--- |
| Creating an extension while explicitly creating a *new* resource instance | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Includes the new instance expanded with the [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) object. |
| Creating an extension while implicitly creating a resource instance | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | The response includes only a response code but not a response body. |
| Creating an extension in an *existing* resource instance | All supported resources | Includes the **openTypeExtension** object. |

## Examples

### Example 1: Create a message and extension in the same call

#### Request

The following example creates a message and an extension in the same call. The request body includes the following:

- The **subject**, **body**, and **toRecipients** properties typical of a new message.
- And for the extension:

  - The type `microsoft.graph.openTypeExtension`.
  - The extension name "Com.Contoso.Referral".
  - Additional data to be stored as three custom properties in the JSON payload: `companyName`, `expirationDate`, and `dealValue`.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/messages

{
  "subject": "Annual review",
  "body": {
    "contentType": "HTML",
    "content": "You should be proud!"
  },
  "toRecipients": [
    {
      "emailAddress": {
        "address": "rufus@contoso.com"
      }
    }
  ],
  "extensions": [
    {
      "@odata.type": "microsoft.graph.openTypeExtension",
      "extensionName": "Com.Contoso.Referral",
      "companyName": "Wingtip Toys",
      "expirationDate": "2015-12-30T11:00:00.000Z",
      "dealValue": 10000
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Message
{
	Subject = "Annual review",
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "You should be proud!",
	},
	ToRecipients = new List<Recipient>
	{
		new Recipient
		{
			EmailAddress = new EmailAddress
			{
				Address = "rufus@contoso.com",
			},
		},
	},
	Extensions = new List<Extension>
	{
		new OpenTypeExtension
		{
			OdataType = "microsoft.graph.openTypeExtension",
			ExtensionName = "Com.Contoso.Referral",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"companyName" , "Wingtip Toys"
				},
				{
					"expirationDate" , "2015-12-30T11:00:00.000Z"
				},
				{
					"dealValue" , 10000
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages.PostAsync(requestBody);
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

requestBody := graphmodels.NewMessage()
subject := "Annual review"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "You should be proud!"
body.SetContent(&content) 
requestBody.SetBody(body)


recipient := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
address := "rufus@contoso.com"
emailAddress.SetAddress(&address) 
recipient.SetEmailAddress(emailAddress)

toRecipients := []graphmodels.Recipientable {
	recipient,
}
requestBody.SetToRecipients(toRecipients)


extension := graphmodels.NewOpenTypeExtension()
extensionName := "Com.Contoso.Referral"
extension.SetExtensionName(&extensionName) 
additionalData := map[string]interface{}{
	"companyName" : "Wingtip Toys", 
	"expirationDate" : "2015-12-30T11:00:00.000Z", 
	"dealValue" : int32(10000) , 
}
extension.SetAdditionalData(additionalData)

extensions := []graphmodels.Extensionable {
	extension,
}
requestBody.SetExtensions(extensions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Me().Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Message message = new Message();
message.setSubject("Annual review");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("You should be proud!");
message.setBody(body);
LinkedList<Recipient> toRecipients = new LinkedList<Recipient>();
Recipient recipient = new Recipient();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setAddress("rufus@contoso.com");
recipient.setEmailAddress(emailAddress);
toRecipients.add(recipient);
message.setToRecipients(toRecipients);
LinkedList<Extension> extensions = new LinkedList<Extension>();
OpenTypeExtension extension = new OpenTypeExtension();
extension.setOdataType("microsoft.graph.openTypeExtension");
extension.setExtensionName("Com.Contoso.Referral");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("companyName", "Wingtip Toys");
additionalData.put("expirationDate", "2015-12-30T11:00:00.000Z");
additionalData.put("dealValue", 10000);
extension.setAdditionalData(additionalData);
extensions.add(extension);
message.setExtensions(extensions);
Message result = graphClient.me().messages().post(message);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const message = {
  subject: 'Annual review',
  body: {
    contentType: 'HTML',
    content: 'You should be proud!'
  },
  toRecipients: [
    {
      emailAddress: {
        address: 'rufus@contoso.com'
      }
    }
  ],
  extensions: [
    {
      '@odata.type': 'microsoft.graph.openTypeExtension',
      extensionName: 'Com.Contoso.Referral',
      companyName: 'Wingtip Toys',
      expirationDate: '2015-12-30T11:00:00.000Z',
      dealValue: 10000
    }
  ]
};

await client.api('/me/messages')
	.post(message);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Message;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Recipient;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\Extension;
use Microsoft\Graph\Generated\Models\OpenTypeExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Message();
$requestBody->setSubject('Annual review');
$body = new ItemBody();
$body->setContentType(new BodyType('hTML'));
$body->setContent('You should be proud!');
$requestBody->setBody($body);
$toRecipientsRecipient1 = new Recipient();
$toRecipientsRecipient1EmailAddress = new EmailAddress();
$toRecipientsRecipient1EmailAddress->setAddress('rufus@contoso.com');
$toRecipientsRecipient1->setEmailAddress($toRecipientsRecipient1EmailAddress);
$toRecipientsArray []= $toRecipientsRecipient1;
$requestBody->setToRecipients($toRecipientsArray);

$extensionsExtension1 = new OpenTypeExtension();
$extensionsExtension1->setOdataType('microsoft.graph.openTypeExtension');
$extensionsExtension1->setExtensionName('Com.Contoso.Referral');
$additionalData = [
'companyName' => 'Wingtip Toys',
'expirationDate' => '2015-12-30T11:00:00.000Z',
'dealValue' => 10000,
];
$extensionsExtension1->setAdditionalData($additionalData);
$extensionsArray []= $extensionsExtension1;
$requestBody->setExtensions($extensionsArray);


$result = $graphServiceClient->me()->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	subject = "Annual review"
	body = @{
		contentType = "HTML"
		content = "You should be proud!"
	}
	toRecipients = @(
		@{
			emailAddress = @{
				address = "rufus@contoso.com"
			}
		}
	)
	extensions = @(
		@{
			"@odata.type" = "microsoft.graph.openTypeExtension"
			extensionName = "Com.Contoso.Referral"
			companyName = "Wingtip Toys"
			expirationDate = "2015-12-30T11:00:00.000Z"
			dealValue = 
		}
	)
}

# A UPN can also be used as -UserId.
New-MgUserMessage -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.message import Message
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.recipient import Recipient
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.extension import Extension
from msgraph.generated.models.open_type_extension import OpenTypeExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Message(
	subject = "Annual review",
	body = ItemBody(
		content_type = BodyType.Html,
		content = "You should be proud!",
	),
	to_recipients = [
		Recipient(
			email_address = EmailAddress(
				address = "rufus@contoso.com",
			),
		),
	],
	extensions = [
		OpenTypeExtension(
			odata_type = "microsoft.graph.openTypeExtension",
			extension_name = "Com.Contoso.Referral",
			additional_data = {
					"company_name" : "Wingtip Toys",
					"expiration_date" : "2015-12-30T11:00:00.000Z",
					"deal_value" : 10000,
			}
		),
	],
)

result = await graph_client.me.messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response for the first example. The response body includes properties of the new message, and the following for the new extension:

- The **id** property with the fully qualified name of `microsoft.graph.openTypeExtension.Com.Contoso.Referral`.
- The default property **extensionName** specified in the request.
- The custom data specified in the request stored as three custom properties.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages/$entity",
  "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/messages
('AAMkAGEbs88AAB84uLuAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj\"",
  "id": "AAMkAGEbs88AAB84uLuAAA=",
  "createdDateTime": "2015-10-30T03:03:43Z",
  "lastModifiedDateTime": "2015-10-30T03:03:43Z",
  "changeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj",
  "categories": [ ],
  "receivedDateTime": "2015-10-30T03:03:43Z",
  "sentDateTime": "2015-10-30T03:03:43Z",
  "hasAttachments": false,
  "subject": "Annual review",
  "body": {
    "contentType": "HTML",
    "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r
\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nYou should be proud!\r\n</body>\r
\n</html>\r\n"
  },
  "bodyPreview": "You should be proud!",
  "importance": "Normal",
  "parentFolderId": "AQMkAGEwAAAIBDwAAAA==",
  "sender": null,
  "from": null,
  "toRecipients": [
    {
      "emailAddress": {
        "address": "rufus@contoso.com",
        "name": "John Doe"
      }
    }
  ],
  "ccRecipients": [ ],
  "bccRecipients": [ ],
  "replyTo": [ ],
  "conversationId": "AAQkAGEFGugh3SVdMzzc=",
  "isDeliveryReceiptRequested": false,
  "isReadReceiptRequested": false,
  "isRead": true,
  "isDraft": true,
  "webLink": "https://outlook.office.com/owa/?
ItemID=AAMkAGEbs88AAB84uLuAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "inferenceClassification": "Focused",
  "extensions": [
    {
      "@odata.type": "#microsoft.graph.openTypeExtension",
      "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/messages
('AAMkAGEbs88AAB84uLuAAA=')/extensions('microsoft.graph.openTypeExtension.Com.Contoso.Referral')",
      "id": "microsoft.graph.openTypeExtension.Com.Contoso.Referral",
      "extensionName": "Com.Contoso.Referral",
      "companyName": "Wingtip Toys",
      "expirationDate": "2015-12-30T11:00:00.000Z",
      "dealValue": 10000
    }
  ]
}
```

---

### Example 2: Create an extension in the specified message

#### Request

The following example creates an extension in the specified message. The request body includes the following for the extension:

- The type `microsoft.graph.openTypeExtension`.
- The extension name "Com.Contoso.Referral".
- Additional data to be stored as three custom properties in the JSON payload: `companyName`, `dealValue`, and `expirationDate`.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/messages/AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===/extensions

{
  "@odata.type" : "microsoft.graph.openTypeExtension",
  "extensionName" : "Com.Contoso.Referral",
  "companyName" : "Wingtip Toys",
  "dealValue" : 500050,
  "expirationDate" : "2015-12-03T10:00:00.000Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OpenTypeExtension
{
	OdataType = "microsoft.graph.openTypeExtension",
	ExtensionName = "Com.Contoso.Referral",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"companyName" , "Wingtip Toys"
		},
		{
			"dealValue" , 500050
		},
		{
			"expirationDate" , "2015-12-03T10:00:00.000Z"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages["{message-id}"].Extensions.PostAsync(requestBody);
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

requestBody := graphmodels.NewExtension()
extensionName := "Com.Contoso.Referral"
requestBody.SetExtensionName(&extensionName) 
additionalData := map[string]interface{}{
	"companyName" : "Wingtip Toys", 
	"dealValue" : int32(500050) , 
	"expirationDate" : "2015-12-03T10:00:00.000Z", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extensions, err := graphClient.Me().Messages().ByMessageId("message-id").Extensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OpenTypeExtension extension = new OpenTypeExtension();
extension.setOdataType("microsoft.graph.openTypeExtension");
extension.setExtensionName("Com.Contoso.Referral");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("companyName", "Wingtip Toys");
additionalData.put("dealValue", 500050);
additionalData.put("expirationDate", "2015-12-03T10:00:00.000Z");
extension.setAdditionalData(additionalData);
Extension result = graphClient.me().messages().byMessageId("{message-id}").extensions().post(extension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const extension = {
  '@odata.type': 'microsoft.graph.openTypeExtension',
  extensionName: 'Com.Contoso.Referral',
  companyName: 'Wingtip Toys',
  dealValue: 500050,
  expirationDate: '2015-12-03T10:00:00.000Z'
};

await client.api('/me/messages/AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===/extensions')
	.post(extension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OpenTypeExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OpenTypeExtension();
$requestBody->setOdataType('microsoft.graph.openTypeExtension');
$requestBody->setExtensionName('Com.Contoso.Referral');
$additionalData = [
	'companyName' => 'Wingtip Toys',
	'dealValue' => 500050,
	'expirationDate' => '2015-12-03T10:00:00.000Z',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->me()->messages()->byMessageId('message-id')->extensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	"@odata.type" = "microsoft.graph.openTypeExtension"
	extensionName = "Com.Contoso.Referral"
	companyName = "Wingtip Toys"
	dealValue = 
	expirationDate = "2015-12-03T10:00:00.000Z"
}

# A UPN can also be used as -UserId.
New-MgUserMessageExtension -UserId $userId -MessageId $messageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.open_type_extension import OpenTypeExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OpenTypeExtension(
	odata_type = "microsoft.graph.openTypeExtension",
	extension_name = "Com.Contoso.Referral",
	additional_data = {
			"company_name" : "Wingtip Toys",
			"deal_value" : 500050,
			"expiration_date" : "2015-12-03T10:00:00.000Z",
	}
)

result = await graph_client.me.messages.by_message_id('message-id').extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response for the second example. The response body includes the following for the new extension:

- The default property **extensionName**.
- The **id** property with the fully qualified name of `microsoft.graph.openTypeExtension.Com.Contoso.Referral`.
- The custom data to be stored.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('microsoft.graph.openTypeExtension.Com.Contoso.Referral')",
    "extensionName": "Com.Contoso.Referral",
    "id": "microsoft.graph.openTypeExtension.Com.Contoso.Referral",
    "companyName": "Wingtip Toys",
    "dealValue": 500050,
    "expirationDate": "2015-12-03T10:00:00.000Z"
}
```

### Example 3: Create an extension in the specified group event

#### Request

The following example creates an extension in the specified group event. The request body includes the following for the extension:

- The type `microsoft.graph.openTypeExtension`.
- The extension name "Com.Contoso.Deal".
- Additional data to be stored as three custom properties in the JSON payload: `companyName`, `dealValue`, and `expirationDate`.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/groups/f5480dfd-7d77-4d0b-ba2e-3391953cc74a/events/AAMkADVl17IsAAA=/extensions

{
  "@odata.type" : "microsoft.graph.openTypeExtension",
  "extensionName" : "Com.Contoso.Deal",
  "companyName" : "Alpine Skis",
  "dealValue" : 1010100,
  "expirationDate" : "2015-07-03T13:04:00.000Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OpenTypeExtension
{
	OdataType = "microsoft.graph.openTypeExtension",
	ExtensionName = "Com.Contoso.Deal",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"companyName" , "Alpine Skis"
		},
		{
			"dealValue" , 1010100
		},
		{
			"expirationDate" , "2015-07-03T13:04:00.000Z"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Events["{event-id}"].Extensions.PostAsync(requestBody);
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

requestBody := graphmodels.NewExtension()
extensionName := "Com.Contoso.Deal"
requestBody.SetExtensionName(&extensionName) 
additionalData := map[string]interface{}{
	"companyName" : "Alpine Skis", 
	"dealValue" : int32(1010100) , 
	"expirationDate" : "2015-07-03T13:04:00.000Z", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extensions, err := graphClient.Groups().ByGroupId("group-id").Events().ByEventId("event-id").Extensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OpenTypeExtension extension = new OpenTypeExtension();
extension.setOdataType("microsoft.graph.openTypeExtension");
extension.setExtensionName("Com.Contoso.Deal");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("companyName", "Alpine Skis");
additionalData.put("dealValue", 1010100);
additionalData.put("expirationDate", "2015-07-03T13:04:00.000Z");
extension.setAdditionalData(additionalData);
Extension result = graphClient.groups().byGroupId("{group-id}").events().byEventId("{event-id}").extensions().post(extension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const extension = {
  '@odata.type': 'microsoft.graph.openTypeExtension',
  extensionName: 'Com.Contoso.Deal',
  companyName: 'Alpine Skis',
  dealValue: 1010100,
  expirationDate: '2015-07-03T13:04:00.000Z'
};

await client.api('/groups/f5480dfd-7d77-4d0b-ba2e-3391953cc74a/events/AAMkADVl17IsAAA=/extensions')
	.post(extension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OpenTypeExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OpenTypeExtension();
$requestBody->setOdataType('microsoft.graph.openTypeExtension');
$requestBody->setExtensionName('Com.Contoso.Deal');
$additionalData = [
	'companyName' => 'Alpine Skis',
	'dealValue' => 1010100,
	'expirationDate' => '2015-07-03T13:04:00.000Z',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->byGroupId('group-id')->events()->byEventId('event-id')->extensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.openTypeExtension"
	extensionName = "Com.Contoso.Deal"
	companyName = "Alpine Skis"
	dealValue = 
	expirationDate = "2015-07-03T13:04:00.000Z"
}

New-MgGroupEventExtension -GroupId $groupId -EventId $eventId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.open_type_extension import OpenTypeExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OpenTypeExtension(
	odata_type = "microsoft.graph.openTypeExtension",
	extension_name = "Com.Contoso.Deal",
	additional_data = {
			"company_name" : "Alpine Skis",
			"deal_value" : 1010100,
			"expiration_date" : "2015-07-03T13:04:00.000Z",
	}
)

result = await graph_client.groups.by_group_id('group-id').events.by_event_id('event-id').extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl7IsAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "microsoft.graph.openTypeExtension.Com.Contoso.Deal",
    "extensionName": "Com.Contoso.Deal",
    "companyName": "Alpine Skis",
    "dealValue": 1010100,
    "expirationDate": "2015-07-03T13:04:00Z"
}
```

### Example 4: Create an extension in a new group post

#### Request

The following example creates an extension in a new group post, using the same **reply** action call to an existing group post. The **reply** action creates a new post, and a new extension embedded in the post. The request body includes a **post** property, which in turn contains the **body** of the new post, and the following data for the new extension:

- The type `microsoft.graph.openTypeExtension`.
- The extension name "Com.Contoso.HR".
- Additional data to be stored as three custom properties in the JSON payload: `companyName`, `expirationDate`, and the array of strings `topPicks`.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/groups/37df2ff0-0de0-4c33-8aee-75289364aef6/threads/AAQkADJizZJpEWwqDHsEpV_KA==/posts/AAMkADJiUg96QZUkA-ICwMubAAC1heiSAAA=/reply

{
  "post": {
    "body": {
      "contentType": "html",
      "content": "<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>"
    },
  "extensions": [
    {
      "@odata.type": "microsoft.graph.openTypeExtension",
      "extensionName": "Com.Contoso.HR",
      "companyName": "Contoso",
      "expirationDate": "2015-07-03T13:04:00.000Z",
      "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
      ]
    }
  ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Groups.Item.Threads.Item.Posts.Item.Reply;
using Microsoft.Graph.Models;

var requestBody = new ReplyPostRequestBody
{
	Post = new Post
	{
		Body = new ItemBody
		{
			ContentType = BodyType.Html,
			Content = "<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>",
		},
		Extensions = new List<Extension>
		{
			new OpenTypeExtension
			{
				OdataType = "microsoft.graph.openTypeExtension",
				ExtensionName = "Com.Contoso.HR",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"companyName" , "Contoso"
					},
					{
						"expirationDate" , "2015-07-03T13:04:00.000Z"
					},
					{
						"topPicks" , new List<string>
						{
							"Employees only",
							"Add spouse or guest",
							"Add family",
						}
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Groups["{group-id}"].Threads["{conversationThread-id}"].Posts["{post-id}"].Reply.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-sdk-go/groups"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphgroups.NewReplyPostRequestBody()
post := graphmodels.NewPost()
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>"
body.SetContent(&content) 
post.SetBody(body)


extension := graphmodels.NewOpenTypeExtension()
extensionName := "Com.Contoso.HR"
extension.SetExtensionName(&extensionName) 
additionalData := map[string]interface{}{
	"companyName" : "Contoso", 
	"expirationDate" : "2015-07-03T13:04:00.000Z", 
	topPicks := []string {
		"Employees only",
		"Add spouse or guest",
		"Add family",
	}
}
extension.SetAdditionalData(additionalData)

extensions := []graphmodels.Extensionable {
	extension,
}
post.SetExtensions(extensions)
requestBody.SetPost(post)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Groups().ByGroupId("group-id").Threads().ByConversationThreadId("conversationThread-id").Posts().ByPostId("post-id").Reply().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.groups.item.threads.item.posts.item.reply.ReplyPostRequestBody replyPostRequestBody = new com.microsoft.graph.groups.item.threads.item.posts.item.reply.ReplyPostRequestBody();
Post post = new Post();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>");
post.setBody(body);
LinkedList<Extension> extensions = new LinkedList<Extension>();
OpenTypeExtension extension = new OpenTypeExtension();
extension.setOdataType("microsoft.graph.openTypeExtension");
extension.setExtensionName("Com.Contoso.HR");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("companyName", "Contoso");
additionalData.put("expirationDate", "2015-07-03T13:04:00.000Z");
LinkedList<String> topPicks = new LinkedList<String>();
topPicks.add("Employees only");
topPicks.add("Add spouse or guest");
topPicks.add("Add family");
additionalData.put("topPicks", topPicks);
extension.setAdditionalData(additionalData);
extensions.add(extension);
post.setExtensions(extensions);
replyPostRequestBody.setPost(post);
graphClient.groups().byGroupId("{group-id}").threads().byConversationThreadId("{conversationThread-id}").posts().byPostId("{post-id}").reply().post(replyPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const reply = {
  post: {
    body: {
      contentType: 'html',
      content: '<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>'
    },
  extensions: [
    {
      '@odata.type': 'microsoft.graph.openTypeExtension',
      extensionName: 'Com.Contoso.HR',
      companyName: 'Contoso',
      expirationDate: '2015-07-03T13:04:00.000Z',
      topPicks: [
        'Employees only',
        'Add spouse or guest',
        'Add family'
      ]
    }
  ]
  }
};

await client.api('/groups/37df2ff0-0de0-4c33-8aee-75289364aef6/threads/AAQkADJizZJpEWwqDHsEpV_KA==/posts/AAMkADJiUg96QZUkA-ICwMubAAC1heiSAAA=/reply')
	.post(reply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\Item\Threads\Item\Posts\Item\Reply\ReplyPostRequestBody;
use Microsoft\Graph\Generated\Models\Post;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Extension;
use Microsoft\Graph\Generated\Models\OpenTypeExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReplyPostRequestBody();
$post = new Post();
$postBody = new ItemBody();
$postBody->setContentType(new BodyType('html'));
$postBody->setContent('<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>');
$post->setBody($postBody);
$extensionsExtension1 = new OpenTypeExtension();
$extensionsExtension1->setOdataType('microsoft.graph.openTypeExtension');
$extensionsExtension1->setExtensionName('Com.Contoso.HR');
$additionalData = [
	'companyName' => 'Contoso',
	'expirationDate' => '2015-07-03T13:04:00.000Z',
	'topPicks' => [
'Employees only', 'Add spouse or guest', 'Add family', ],
];
$extensionsExtension1->setAdditionalData($additionalData);
$extensionsArray []= $extensionsExtension1;
$post->setExtensions($extensionsArray);

$requestBody->setPost($post);

$graphServiceClient->groups()->byGroupId('group-id')->threads()->byConversationThreadId('conversationThread-id')->posts()->byPostId('post-id')->reply()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	post = @{
		body = @{
			contentType = "html"
			content = "<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>"
		}
		extensions = @(
			@{
				"@odata.type" = "microsoft.graph.openTypeExtension"
				extensionName = "Com.Contoso.HR"
				companyName = "Contoso"
				expirationDate = "2015-07-03T13:04:00.000Z"
				topPicks = @(
				"Employees only"
			"Add spouse or guest"
		"Add family"
	)
}
)
}
}

Invoke-MgReplyGroupThreadPost -GroupId $groupId -ConversationThreadId $conversationThreadId -PostId $postId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.item.threads.item.posts.item.reply.reply_post_request_body import ReplyPostRequestBody
from msgraph.generated.models.post import Post
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.extension import Extension
from msgraph.generated.models.open_type_extension import OpenTypeExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReplyPostRequestBody(
	post = Post(
		body = ItemBody(
			content_type = BodyType.Html,
			content = "<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>",
		),
		extensions = [
			OpenTypeExtension(
				odata_type = "microsoft.graph.openTypeExtension",
				extension_name = "Com.Contoso.HR",
				additional_data = {
						"company_name" : "Contoso",
						"expiration_date" : "2015-07-03T13:04:00.000Z",
						"top_picks" : [
							"Employees only",
							"Add spouse or guest",
							"Add family",
						],
				}
			),
		],
	),
)

await graph_client.groups.by_group_id('group-id').threads.by_conversation_thread_id('conversationThread-id').posts.by_post_id('post-id').reply.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. Successfully creating an extension in a new group post results in only the HTTP 202 response code.

```http
HTTP/1.1 202 Accepted
Content-type: text/plain
Content-Length: 0
```

### Example 5: Create an extension in a new group post using POST operation

#### Request

The following example creates an extension in a new group post using the same POST operation to create a conversation. The POST operation creates a new conversation, thread and post, and a new extension embedded in the post. The request body includes the **Topic** and **Threads** properties, and a child **post** object for the new conversation. The **post** object in turn contains the **body** of the new post, and the following data for the extension:

- The type `microsoft.graph.openTypeExtension`.
- The extension name "Com.Contoso.HR".
- Additional data to be stored as three custom properties in the JSON payload: `companyName`, `expirationDate`, and the array of strings `topPicks`.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/groups/37df2ff0-0de0-4c33-8aee-75289364aef6/conversations

{
  "Topic": "Does anyone have a second?",
  "Threads": [
    {
      "Posts": [
        {
          "Body": {
            "ContentType": "HTML",
            "Content": "This is urgent!"
          },
          "Extensions": [
            {
              "@odata.type": "microsoft.graph.openTypeExtension",
              "extensionName": "Com.Contoso.Benefits",
              "companyName": "Contoso",
              "expirationDate": "2016-08-03T11:00:00.000Z",
              "topPicks": [
                "Employees only",
                "Add spouse or guest",
                "Add family"
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Conversation
{
	Topic = "Does anyone have a second?",
	Threads = new List<ConversationThread>
	{
		new ConversationThread
		{
			Posts = new List<Post>
			{
				new Post
				{
					Body = new ItemBody
					{
						ContentType = BodyType.Html,
						Content = "This is urgent!",
					},
					Extensions = new List<Extension>
					{
						new OpenTypeExtension
						{
							OdataType = "microsoft.graph.openTypeExtension",
							ExtensionName = "Com.Contoso.Benefits",
							AdditionalData = new Dictionary<string, object>
							{
								{
									"companyName" , "Contoso"
								},
								{
									"expirationDate" , "2016-08-03T11:00:00.000Z"
								},
								{
									"topPicks" , new List<string>
									{
										"Employees only",
										"Add spouse or guest",
										"Add family",
									}
								},
							},
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Conversations.PostAsync(requestBody);
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

requestBody := graphmodels.NewConversation()
topic := "Does anyone have a second?"
requestBody.SetTopic(&topic) 


conversationThread := graphmodels.NewConversationThread()


post := graphmodels.NewPost()
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "This is urgent!"
body.SetContent(&content) 
post.SetBody(body)


extension := graphmodels.NewOpenTypeExtension()
extensionName := "Com.Contoso.Benefits"
extension.SetExtensionName(&extensionName) 
additionalData := map[string]interface{}{
	"companyName" : "Contoso", 
	"expirationDate" : "2016-08-03T11:00:00.000Z", 
	topPicks := []string {
		"Employees only",
		"Add spouse or guest",
		"Add family",
	}
}
extension.SetAdditionalData(additionalData)

extensions := []graphmodels.Extensionable {
	extension,
}
post.SetExtensions(extensions)

posts := []graphmodels.Postable {
	post,
}
conversationThread.SetPosts(posts)

threads := []graphmodels.ConversationThreadable {
	conversationThread,
}
requestBody.SetThreads(threads)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
conversations, err := graphClient.Groups().ByGroupId("group-id").Conversations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Conversation conversation = new Conversation();
conversation.setTopic("Does anyone have a second?");
LinkedList<ConversationThread> threads = new LinkedList<ConversationThread>();
ConversationThread conversationThread = new ConversationThread();
LinkedList<Post> posts = new LinkedList<Post>();
Post post = new Post();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("This is urgent!");
post.setBody(body);
LinkedList<Extension> extensions = new LinkedList<Extension>();
OpenTypeExtension extension = new OpenTypeExtension();
extension.setOdataType("microsoft.graph.openTypeExtension");
extension.setExtensionName("Com.Contoso.Benefits");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("companyName", "Contoso");
additionalData.put("expirationDate", "2016-08-03T11:00:00.000Z");
LinkedList<String> topPicks = new LinkedList<String>();
topPicks.add("Employees only");
topPicks.add("Add spouse or guest");
topPicks.add("Add family");
additionalData.put("topPicks", topPicks);
extension.setAdditionalData(additionalData);
extensions.add(extension);
post.setExtensions(extensions);
posts.add(post);
conversationThread.setPosts(posts);
threads.add(conversationThread);
conversation.setThreads(threads);
Conversation result = graphClient.groups().byGroupId("{group-id}").conversations().post(conversation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conversation = {
  Topic: 'Does anyone have a second?',
  Threads: [
    {
      Posts: [
        {
          Body: {
            ContentType: 'HTML',
            Content: 'This is urgent!'
          },
          Extensions: [
            {
              '@odata.type': 'microsoft.graph.openTypeExtension',
              extensionName: 'Com.Contoso.Benefits',
              companyName: 'Contoso',
              expirationDate: '2016-08-03T11:00:00.000Z',
              topPicks: [
                'Employees only',
                'Add spouse or guest',
                'Add family'
              ]
            }
          ]
        }
      ]
    }
  ]
};

await client.api('/groups/37df2ff0-0de0-4c33-8aee-75289364aef6/conversations')
	.post(conversation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Conversation;
use Microsoft\Graph\Generated\Models\ConversationThread;
use Microsoft\Graph\Generated\Models\Post;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Extension;
use Microsoft\Graph\Generated\Models\OpenTypeExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Conversation();
$requestBody->setTopic('Does anyone have a second?');
$threadsConversationThread1 = new ConversationThread();
$postsPost1 = new Post();
$postsPost1Body = new ItemBody();
$postsPost1Body->setContentType(new BodyType('hTML'));
$postsPost1Body->setContent('This is urgent!');
$postsPost1->setBody($postsPost1Body);
$extensionsExtension1 = new OpenTypeExtension();
$extensionsExtension1->setOdataType('microsoft.graph.openTypeExtension');
$extensionsExtension1->setExtensionName('Com.Contoso.Benefits');
$additionalData = [
	'companyName' => 'Contoso',
	'expirationDate' => '2016-08-03T11:00:00.000Z',
	'topPicks' => [
'Employees only', 'Add spouse or guest', 'Add family', ],
];
$extensionsExtension1->setAdditionalData($additionalData);
$extensionsArray []= $extensionsExtension1;
$postsPost1->setExtensions($extensionsArray);

$postsArray []= $postsPost1;
$threadsConversationThread1->setPosts($postsArray);

$threadsArray []= $threadsConversationThread1;
$requestBody->setThreads($threadsArray);


$result = $graphServiceClient->groups()->byGroupId('group-id')->conversations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	Topic = "Does anyone have a second?"
	Threads = @(
		@{
			Posts = @(
				@{
					Body = @{
						ContentType = "HTML"
						Content = "This is urgent!"
					}
					Extensions = @(
						@{
							"@odata.type" = "microsoft.graph.openTypeExtension"
							extensionName = "Com.Contoso.Benefits"
							companyName = "Contoso"
							expirationDate = "2016-08-03T11:00:00.000Z"
							topPicks = @(
							"Employees only"
						"Add spouse or guest"
					"Add family"
				)
			}
		)
	}
)
}
)
}

New-MgGroupConversation -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.conversation import Conversation
from msgraph.generated.models.conversation_thread import ConversationThread
from msgraph.generated.models.post import Post
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.extension import Extension
from msgraph.generated.models.open_type_extension import OpenTypeExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Conversation(
	topic = "Does anyone have a second?",
	threads = [
		ConversationThread(
			posts = [
				Post(
					body = ItemBody(
						content_type = BodyType.Html,
						content = "This is urgent!",
					),
					extensions = [
						OpenTypeExtension(
							odata_type = "microsoft.graph.openTypeExtension",
							extension_name = "Com.Contoso.Benefits",
							additional_data = {
									"company_name" : "Contoso",
									"expiration_date" : "2016-08-03T11:00:00.000Z",
									"top_picks" : [
										"Employees only",
										"Add spouse or guest",
										"Add family",
									],
							}
						),
					],
				),
			],
		),
	],
)

result = await graph_client.groups.by_group_id('group-id').conversations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response 5

The following example shows the response, which contains the new conversation and a thread ID. This new thread contains an automatically created post, which in turn contains the new extension.

Note: The response object shown here might be shortened for readability.

To get the new extension, first [get all the posts](https://learn.microsoft.com/en-us/graph/api/conversationthread-list-posts?view=graph-rest-1.0) in this thread, and initially there should be only one. Then apply the post ID and the extension name `Com.Contoso.Benefits` to [get the extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-get?view=graph-rest-1.0).

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations/$entity",
    "id": "AAQkADJToRlbJ5Mg7TFM7H-j3Y=",
    "threads": [
        {
            "id": "AAQkADJDtMUzsf_PdhAAswJOhGVsnkyDtMUzsf_Pdg=="
        }
    ]
}
```
