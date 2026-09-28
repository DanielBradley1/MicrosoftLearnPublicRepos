<!-- Source: https://learn.microsoft.com/en-us/graph/api/opentypeextension-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-14 -->

# Update open extension

Namespace: microsoft.graph

Update an open extension \([openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) object\) on a supported resource type.

- If a property in the request body matches the name of an existing property in the extension, the data in the extension is updated.
- Otherwise, that property and its data are added to the extension.

The data in an extension can be primitive types or arrays of primitive types.

See the table in the [Permissions](#permissions) section for the list of resources that support open extensions.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Depending on the resource that the extension was created in and the permission type \(delegated or application\) requested, the permission specified in the following table is the least privileged required to call this API. To learn more, including [taking caution](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#best-practices-for-requesting-permissions) before choosing more privileged permissions, search for the following permissions in [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

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

In the request, identify the resource instance, use the **extensions** navigation property of that instance to identify the extension, and do a `PATCH` on that extension instance.

```http
PATCH /devices/{Id}/extensions/{extensionId}
PATCH /users/{id|userPrincipalName}/events/{id}/extensions/{extensionId}
PATCH /groups/{id}/extensions/{extensionId}
PATCH /groups/{id}/events/{id}/extensions/{extensionId}
PATCH /groups/{id}/threads/{id}/posts/{id}/extensions/{extensionId}
PATCH /users/{id|userPrincipalName}/messages/{id}/extensions/{extensionId}
PATCH /users/{id|userPrincipalName}/notes/{id}/extensions/{extensionId}
PATCH /organization/{Id}/extensions/{extensionId}
PATCH /users/{id|userPrincipalName}/contacts/{id}/extensions/{extensionId}
PATCH /users/{id|userPrincipalName}/extensions/{extensionId}
PATCH /users/{id|userPrincipalName}/todo/lists/{todoTaskListId}/tasks/{taskId}/extensions/{extensionId}
PATCH /users/{id|userPrincipalName}/todo/lists/{todoTaskListId}/extensions/{extensionId}
```

> **Note:** The above syntax shows some common ways to identify a resource instance, in order to update an extension in it. All other syntax that allows you to identify these resource instances supports updating open extensions in them in a similar way.

See the [Request body](#request-body) section about including in the request body any custom data to change or add to that extension.

## Request headers

| Name | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

Provide a JSON body of an [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) object, with the following required name-value pairs, and any custom data to change or add to that extension.

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | Must be `#microsoft.graph.openTypeExtension`. Required. |
| extensionName | String | Required if **id** isn't supplied. Updatable. |
| id | String | Required if **id** isn't supplied. Read-only. |

For resources that are directory \(Microsoft Entra ID\) objects:

- To update any property in the open extension object, you must specify *all* properties in the request body; otherwise, Microsoft Graph deletes the unspecified properties.
- To delete data from a property in the open extension object but keep the property, set its value to `null`.
- To delete a property from the open extension object, don't pass it in the PATCH request body, and Microsoft Graph deletes it.
- To delete data from all properties in the open extension object but keep the open extension object, update the values of all the properties to `null`.

For Microsoft 365 resources like messages:

- You can specify a subset of the properties in the request body to update them. The omitted properties and their values are retained.
- `null` values aren't allowed.

## Response

If successful, this method returns a `204 No Content` response code for directory objects or a `200 OK` response code and an updated [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) object for other resources.

## Example

#### Request 1

The first example shows how to update an extension in a message. The extension is initially represented by the following JSON payload:

```http
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "extensionName": "Com.Contoso.Referral",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "companyName": "Wingtip Toys",
    "dealValue": 500050,
    "expirationDate": "2015-12-03T10:00:00Z"
}
```

You can reference the extension by its name:

```http
PATCH https://graph.microsoft.com/v1.0/me/messages/AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===/extensions/Com.Contoso.Referral
```

Or you can reference the extension by its fully qualified name:

```http
PATCH https://graph.microsoft.com/v1.0/me/messages/AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===/extensions/Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral
```

You can use either example request and the following request body to update the above extension by:

- Changing `companyName` from `Wingtip Toys` to `Wingtip Toys (USA)`
- Changing `dealValue` from `500050` to `500100`
- Adding new data as the custom property `updated`

```http
{
    "@odata.type": "microsoft.graph.openTypeExtension",
    "extensionName": "Com.Contoso.Referral",
    "companyName": "Wingtip Toys (USA)",
    "dealValue": "500100",
    "expirationDate": "2015-12-03T10:00:00.000Z",
    "updated": "2015-10-29T11:00:00.000Z"
} 
```

#### Response 1

Here is the response which is the same regardless of the way used to reference the extension.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "extensionName": "Com.Contoso.Referral",
    "companyName": "Wingtip Toys (USA)",
    "dealValue": 500100,
    "expirationDate": "2015-12-03T10:00:00Z",
    "updated": "2015-10-29T11:00:00.000Z"
}
```

---

#### Request 2

The second example shows how to update an extension in a group post. The extension is initially represented by the following JSON payload, with an `expirationDate` value of `2015-07-03T13:04:00Z`:

```http
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA%3D%3D')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate",
    "extensionName": "Com.Contoso.Estimate",
    "companyName": "Contoso",
    "expirationDate": "2015-07-03T13:04:00Z",
    "DealValue": 1010100,
    "Strings@odata.type": "#Collection(String)",
    "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
    ]
}
```

The following is the request and request body to change the `expirationDate` to `2016-07-30T11:00:00Z`:

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/groups/37df2ff0-0de0-4c33-8aee-75289364aef6/threads/AAQkADJizZJpEWwqDHsEpV_KA==/posts/AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA=/extensions/Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate
Content-type: application/json

{
   "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
   "extensionName": "Com.Contoso.Estimate",
   "companyName": "Contoso",
   "expirationDate": "2016-07-30T11:00:00.000Z",
   "DealValue": 1010100,
   "topPicks": [
       "Employees only",
       "Add spouse or guest",
       "Add family"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Extension
{
	OdataType = "Microsoft.OutlookServices.OpenTypeExtension",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"extensionName" , "Com.Contoso.Estimate"
		},
		{
			"companyName" , "Contoso"
		},
		{
			"expirationDate" , "2016-07-30T11:00:00.000Z"
		},
		{
			"DealValue" , 1010100
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
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Threads["{conversationThread-id}"].Posts["{post-id}"].Extensions["{extension-id}"].PatchAsync(requestBody);
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
additionalData := map[string]interface{}{
	"extensionName" : "Com.Contoso.Estimate", 
	"companyName" : "Contoso", 
	"expirationDate" : "2016-07-30T11:00:00.000Z", 
	"dealValue" : int32(1010100) , 
	topPicks := []string {
		"Employees only",
		"Add spouse or guest",
		"Add family",
	}
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extensions, err := graphClient.Groups().ByGroupId("group-id").Threads().ByConversationThreadId("conversationThread-id").Posts().ByPostId("post-id").Extensions().ByExtensionId("extension-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Extension extension = new Extension();
extension.setOdataType("Microsoft.OutlookServices.OpenTypeExtension");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("extensionName", "Com.Contoso.Estimate");
additionalData.put("companyName", "Contoso");
additionalData.put("expirationDate", "2016-07-30T11:00:00.000Z");
additionalData.put("DealValue", 1010100);
LinkedList<String> topPicks = new LinkedList<String>();
topPicks.add("Employees only");
topPicks.add("Add spouse or guest");
topPicks.add("Add family");
additionalData.put("topPicks", topPicks);
extension.setAdditionalData(additionalData);
Extension result = graphClient.groups().byGroupId("{group-id}").threads().byConversationThreadId("{conversationThread-id}").posts().byPostId("{post-id}").extensions().byExtensionId("{extension-id}").patch(extension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const extension = {
   '@odata.type': 'Microsoft.OutlookServices.OpenTypeExtension',
   extensionName: 'Com.Contoso.Estimate',
   companyName: 'Contoso',
   expirationDate: '2016-07-30T11:00:00.000Z',
   DealValue: 1010100,
   topPicks: [
       'Employees only',
       'Add spouse or guest',
       'Add family'
    ]
};

await client.api('/groups/37df2ff0-0de0-4c33-8aee-75289364aef6/threads/AAQkADJizZJpEWwqDHsEpV_KA==/posts/AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA=/extensions/Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate')
	.update(extension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Extension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Extension();
$requestBody->setOdataType('Microsoft.OutlookServices.OpenTypeExtension');
$additionalData = [
	'extensionName' => 'Com.Contoso.Estimate',
	'companyName' => 'Contoso',
	'expirationDate' => '2016-07-30T11:00:00.000Z',
	'DealValue' => 1010100,
	'topPicks' => [
'Employees only', 'Add spouse or guest', 'Add family', ],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->byGroupId('group-id')->threads()->byConversationThreadId('conversationThread-id')->posts()->byPostId('post-id')->extensions()->byExtensionId('extension-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	"@odata.type" = "Microsoft.OutlookServices.OpenTypeExtension"
	extensionName = "Com.Contoso.Estimate"
	companyName = "Contoso"
	expirationDate = "2016-07-30T11:00:00.000Z"
	DealValue = 
	topPicks = @(
	"Employees only"
"Add spouse or guest"
"Add family"
)
}

Update-MgGroupThreadPostExtension -GroupId $groupId -ConversationThreadId $conversationThreadId -PostId $postId -ExtensionId $extensionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.extension import Extension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Extension(
	odata_type = "Microsoft.OutlookServices.OpenTypeExtension",
	additional_data = {
			"extension_name" : "Com.Contoso.Estimate",
			"company_name" : "Contoso",
			"expiration_date" : "2016-07-30T11:00:00.000Z",
			"deal_value" : 1010100,
			"top_picks" : [
				"Employees only",
				"Add spouse or guest",
				"Add family",
			],
	}
)

result = await graph_client.groups.by_group_id('group-id').threads.by_conversation_thread_id('conversationThread-id').posts.by_post_id('post-id').extensions.by_extension_id('extension-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response 2

Here is the response of the second example which shows the updated `expirationDate` in the extension.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA%3D%3D')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate",
    "extensionName": "Com.Contoso.Estimate",
    "companyName": "Contoso",
    "expirationDate": "2016-07-30T11:00:00Z",
    "DealValue": 1010100,
    "Strings@odata.type": "#Collection(String)",
    "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
    ]
}
```
