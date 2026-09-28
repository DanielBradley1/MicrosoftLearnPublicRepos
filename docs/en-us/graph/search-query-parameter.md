<!-- Source: https://learn.microsoft.com/en-us/graph/search-query-parameter -->
<!-- Sitemap-Last-Modified: 2025-07-03 -->

# Use the $search query parameter in Microsoft Graph APIs

The `$search` query parameter is a powerful filtering mechanism in Microsoft Graph that enables you to find specific data by matching search criteria.

Support for this query parameter varies by entity. Some entities, like Microsoft Entra resources that derive from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject), support `$search` only in [advanced queries](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

This article explains how to use the `$search` query parameter effectively with three key resource types: [mail messages](#use-search-on-message-collections), [people](#use-search-on-person-collections), and [Microsoft Entra ID objects \(directory objects\)](#use-search-on-directory-object-collections). You learn the specific syntax requirements, supported properties, and search behaviors for each resource type.

## Use $search on message collections

You can search [messages](https://learn.microsoft.com/en-us/graph/api/resources/message) based on specific message properties. Search results are sorted by the date and time the message was sent. A `$search` request returns up to 1,000 results.

When you search messages without specifying message properties, the search targets these default properties: **from**, **subject**, and **body**.

The following example returns all messages in the signed-in user's Inbox that contains "pizza" in any of the three default search properties:

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/messages?$search="pizza"
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Search = "\"pizza\"";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestSearch := "\"pizza\""

requestParameters := &graphusers.ItemMessagesRequestBuilderGetQueryParameters{
	Search: &requestSearch,
}
configuration := &graphusers.ItemMessagesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Me().Messages().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MessageCollectionResponse result = graphClient.me().messages().get(requestConfiguration -> {
	requestConfiguration.queryParameters.search = "\"pizza\"";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let messages = await client.api('/me/messages')
	.search('pizza')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Messages\MessagesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new MessagesRequestBuilderGetRequestConfiguration();
$queryParameters = MessagesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->search = "\"pizza\"";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->messages()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Mail

# A UPN can also be used as -UserId.
Get-MgUserMessage -UserId $userId -Search '"pizza"' 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.messages.messages_request_builder import MessagesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = MessagesRequestBuilder.MessagesRequestBuilderGetQueryParameters(
		search = "\"pizza\"",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.messages.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Alternatively, you can search messages by specifying message property names that Keyword Query Language \(KQL\) syntax recognizes. These property names correspond to properties defined in the **message** entity of Microsoft Graph. Outlook and other Microsoft 365 applications like SharePoint support KQL syntax, which provides a common discovery domain for their data stores.

| Searchable email property | Description | Example |
| :--- | :--- | :--- |
| **attachment** | Names of files attached to an email message. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22attachment%3Aapi-catalog%2Emd%22&method=GET&version=v1.0) `../me/messages?$search="attachment:api-catalog.md"` |
| **bcc** | The **bcc** field of an email message, specified as an SMTP address, display name, or alias. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22bcc%3Asamanthab%40contoso%2Ecom%22%26$select=subject,bccRecipients&method=GET&version=v1.0) `../me/messages?$search="bcc:samanthab@contoso.com"&$select=subject,bccRecipients` |
| **body** | The body of an email message. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22body%3Aexcitement%22&method=GET&version=v1.0) `../me/messages?$search="body:excitement"` |
| **cc** | The **cc** field of an email message, specified as an SMTP address, display name, or alias. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22cc%3Adanas%22%26$select=subject,ccRecipients&method=GET&version=v1.0) `../me/messages?$search="cc:danas"&$select=subject,ccRecipients` |
| **from** | The sender of an email message, specified as an SMTP address, display name, or alias. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22from%3Arandiw%22%26$select=subject,from&method=GET&version=v1.0) `../me/messages?$search="from:randiw"&$select=subject,from`  <br>  <br>[GET](https://developer.microsoft.com/en-us/graph/graph-explorer?request=me%2Fmessages%3F%24search%3D%22from%3Aadelev%2BOR%2Bfrom%3Aalexw%2BOR%2Bfrom%3A%2BallanD%22%26%24select%3Dsubject%2C%2Bfrom&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) `../me/messages?$search="from:adelev OR from:alexw OR from: allanD"&$select=subject, from` |
| **hasAttachment** | `true` if an email message contains an attachment that isn't an inline attachment; `false` otherwise. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22hasAttachments=true%22&method=GET&version=v1.0) `../me/messages?$search="hasAttachments:true"` |
| **importance** | The importance of an email message that a sender can specify when sending a message. Possible values are `low`, `medium`, or `high`. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22importance%3Ahigh%22%26$select=subject,importance&method=GET&version=v1.0) `../me/messages?$search="importance:high"&$select=subject,importance` |
| **kind** | The type of message. Possible values are `contacts`, `docs`, `email`, `faxes`, `im`, `journals`, `meetings`, `notes`, `posts`, `rssfeeds`, `tasks`, or `voicemail`. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22kind%3Avoicemail%22&method=GET&version=v1.0) `../me/messages?$search="kind:voicemail"` |
| **participants** | The **from**, **to**, **cc**, and **bcc** fields of an email message, specified as an SMTP address, display name, or alias. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22participants%3Adanas%22&method=GET&version=v1.0) `../me/messages?$search="participants:danas"` |
| **received** | The date a recipient received an email message. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22received%3A07/23/2018%22%26$select=subject,receivedDateTime&method=GET&version=v1.0) `../me/messages?$search="received:07/23/2018"&$select=subject,receivedDateTime` |
| **recipients** | The **to**, **cc**, and **bcc** fields of an email message, specified as an SMTP address, display name, or alias. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22recipients%3Arandiw%22%26$select=subject,toRecipients,ccRecipients,bccRecipients&method=GET&version=v1.0) `../me/messages?$search="recipients:randiq"&$select=subject,toRecipients,ccRecipients,bccRecipients` |
| **sent** | The date an email message was sent by the sender. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22sent%3A07/23/2018%22%26$select=subject,sentDateTime&method=GET&version=v1.0) `../me/messages?$search="sent:07/23/2018"&$select=subject,sentDateTime` |
| **size** | The size of an item in bytes. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22size%3A1%2E%2E500000%22&method=GET&version=v1.0) `../me/messages?$search="size:1..500000"` |
| **subject** | The text in the subject line of an email message. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22subject%3Ahas%22%26$select=subject&method=GET&version=v1.0) `../me/messages?$search="subject:has"&$select=subject` |
| **to** | The **to** field of an email message, specified as an SMTP address, display name, or alias. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$search=%22to%3Arandiw%22%26$select=subject,toRecipients&method=GET&version=v1.0)`.../me/messages?$search="to:randiw"&$select=subject,toRecipients` |

For more information about searchable email properties, KQL syntax, supported operators, and search tips, see these articles:

- [Searchable properties in Exchange](https://learn.microsoft.com/en-us/Exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange)
- [Keyword Query Language \(KQL\) syntax reference](https://learn.microsoft.com/en-us/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)
- [Message properties and search operators for In-Place eDiscovery in Exchange 2016](https://learn.microsoft.com/en-us/Exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators)

## Use $search on person collections

You can apply `$search` to the **displayName** and **emailAddresses** properties of the [person](https://learn.microsoft.com/en-us/graph/api/resources/person) resource. Requests return up to 250 results by default.

The following request searches for "Irene McGowan" in the **person** objects collection for the signed-in user. Microsoft Graph searches the **displayName** and **emailAddresses** properties.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/people/?$search="Irene McGowen"
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.People.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Search = "\"Irene McGowen\"";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestSearch := "\"Irene McGowen\""

requestParameters := &graphusers.ItemPeopleRequestBuilderGetQueryParameters{
	Search: &requestSearch,
}
configuration := &graphusers.ItemPeopleRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
people, err := graphClient.Me().People().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PersonCollectionResponse result = graphClient.me().people().get(requestConfiguration -> {
	requestConfiguration.queryParameters.search = "\"Irene McGowen\"";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let people = await client.api('/me/people/')
	.search('Irene McGowen')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\People\PeopleRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new PeopleRequestBuilderGetRequestConfiguration();
$queryParameters = PeopleRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->search = "\"Irene McGowen\"";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->people()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.People

# A UPN can also be used as -UserId.
Get-MgUserPerson -UserId $userId -Search '"Irene McGowen"' 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.people.people_request_builder import PeopleRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = PeopleRequestBuilder.PeopleRequestBuilderGetQueryParameters(
		search = "\"Irene McGowen\"",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.people.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
       {
           "id": "C0BD1BA1-A84E-4796-9C65-F8A0293741D1",
           "displayName": "Irene McGowan",
           "givenName": "Irene",
           "surname": "McGowan",
           "birthday": "",
           "personNotes": "",
           "isFavorite": false,
           "jobTitle": "Auditor",
           "companyName": null,
           "yomiCompany": "",
           "department": "Finance",
           "officeLocation": "12/1110",
           "profession": "",
           "userPrincipalName": "irenem@contoso.com",
           "imAddress": "sip:irenem@contoso.com",
           "scoredEmailAddresses": [
               {
                   "address": "irenem@contoso.com",
                   "relevanceScore": -16.446060612802224
               }
           ],
           "phones": [
               {
                   "type": "Business",
                   "number": "+1 412 555 0109"
               }
           ],
           "postalAddresses": [],
           "websites": [],
           "personType": {
               "class": "Person",
               "subclass": "OrganizationUser"
           }
       }
   ]
}
```

To learn more about the People API, see [Get information about relevant people](https://learn.microsoft.com/en-us/graph/people-insights-overview#search-people).

## Use $search on directory object collections

Microsoft Entra ID resources and their relationships that derive from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject) support the `$search` query parameter only in [advanced queries](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

Note

- The `$search` query parameter is currently not available in Azure AD B2C tenants.
- There's a [known issue](https://learn.microsoft.com/en-us/graph/known-issues#search-for-directory-objects-fails-for-encoded-ampersand-character) with `$search` on directory objects for values that contain an ampersand \(&\) symbol.

The search implementation doesn't support "contains" logic. Instead, it uses a tokenization approach that extracts words from property values and search strings using spaces, numbers, different casing, and symbols as shown in these examples:

- **Spaces**: `hello world` => `hello`, `world`
- **Different casing**⁽<sup>1</sup>⁾: `HelloWorld` or `helloWORLD` => `hello`, `world`
- **Symbols**⁽<sup>2</sup>⁾: `hello.world` => `hello`, `.`, `world`, `helloworld`
- **Numbers**: `hello123world` => `hello`, `123`, `world`

⁽<sup>1</sup>⁾ For different casing, tokenization currently only works when casing changes from lowercase to uppercase. For example, `HELLOworld` is a single token: `helloworld`, and `HelloWORld` is two tokens: `hello`, `world`.

⁽<sup>2</sup>⁾ Tokenization logic also combines words that are separated only by symbols. For example, searching for `helloworld` finds `hello-world` and `hello.world`.

After tokenization, tokens are matched regardless of original casing and in any order. For example, displayName `李四(David Li)` matches search strings like `李四(David Li)`, `李四`, `David`, `Li`, `David)`, `(李四`, `Li 李`. A change in alphabet \(such as from Latin to Cyrillic or Chinese\) doesn't create a new token. For example, displayName `蓝色group` matches the `蓝色group` and `蓝色` search strings, but not `group`. DisplayName `group蓝色` matches the `group蓝色` and `group` search strings, but not `蓝色` or `蓝`.

Tokenized search works only on the **displayName** and **description** fields. Any string type field can be used in `$search`, but fields other than **displayName** and **description** default to `$filter` `startswith` behavior.

For example:

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/groups/?$search="displayName:OneVideo" OR "mail:onevideo"
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Search = "\"displayName:OneVideo\" OR \"mail:onevideo\"";
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-sdk-go/groups"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestSearch := "\"displayName:OneVideo\" OR \"mail:onevideo\""

requestParameters := &graphgroups.GroupsRequestBuilderGetQueryParameters{
	Search: &requestSearch,
}
configuration := &graphgroups.GroupsRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupCollectionResponse result = graphClient.groups().get(requestConfiguration -> {
	requestConfiguration.queryParameters.search = "\"displayName:OneVideo\" OR \"mail:onevideo\"";
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\GroupsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GroupsRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = GroupsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->search = "\"displayName:OneVideo\" OR \"mail:onevideo\"";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->groups()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

Get-MgGroup -Search '"displayName:OneVideo" OR "mail:onevideo"'  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.groups_request_builder import GroupsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GroupsRequestBuilder.GroupsRequestBuilderGetQueryParameters(
		search = "\"displayName:OneVideo\" OR \"mail:onevideo\"",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.groups.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

This searches for all groups with display names that have `one` and `video` tokens, or mail starting with `onevideo`.

You can use `$search` together with `$filter`:

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/groups/?$filter=mailEnabled eq true&$search="displayName:OneVideo"
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "mailEnabled eq true";
	requestConfiguration.QueryParameters.Search = "\"displayName:OneVideo\"";
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-sdk-go/groups"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestFilter := "mailEnabled eq true"
requestSearch := "\"displayName:OneVideo\""

requestParameters := &graphgroups.GroupsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Search: &requestSearch,
}
configuration := &graphgroups.GroupsRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupCollectionResponse result = graphClient.groups().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "mailEnabled eq true";
	requestConfiguration.queryParameters.search = "\"displayName:OneVideo\"";
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let groups = await client.api('/groups/')
	.header('ConsistencyLevel','eventual')
	.filter('mailEnabled eq true')
	.search('displayName:OneVideo')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\GroupsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GroupsRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = GroupsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "mailEnabled eq true";
$queryParameters->search = "\"displayName:OneVideo\"";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->groups()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

Get-MgGroup -Filter "mailEnabled eq true" -Search '"displayName:OneVideo"'  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.groups_request_builder import GroupsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GroupsRequestBuilder.GroupsRequestBuilderGetQueryParameters(
		filter = "mailEnabled eq true",
		search = "\"displayName:OneVideo\"",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.groups.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

This searches for all mail-enabled groups with display names that look like "OneVideo". Results are filtered based on a logical conjunction \(AND\) of the `$filter` and the entire query in the `$search`.

The search syntax follows these rules:

- **General format**: $search="clause1" \[AND \| OR\] "clauseX"
- **Number of clauses**: Any number of clauses is supported. Parentheses for precedence are also supported.
- **Clause syntax**: "<property>:<text to search>"

  - You must specify the property name in the clause.
  - The whole clause must be enclosed in double quotes. If it contains double quotes or backslash, escape it with a backslash. All other special characters must be URL encoded.

- **Logical operators**: `AND` and `OR` operators must be outside double quotes and in uppercase.
- **Search behavior**: True search is only supported for **displayName** and **description** properties. Any property that can be used in `$filter` can also be used inside `$search`. Properties other than **displayName** and **description** default to `$filter` with "startsWith" behavior if search isn't supported.
- **Tokenization**: Both the string inputs you provide in `$search` and the searchable properties are split into parts by spaces, different casing, and character types \(numbers and special characters\).

The following table shows some examples:

| Object class | Description | Example |
| --- | --- | --- |
| User | Address book display name of the user. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24search%3D%22displayName%3AGuthr%22&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `../users?$search="displayName:Guthr"` |
| User | Address book display name or mail of the user. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24search%3D%22displayName%3AGuthr%22%20OR%20%22mail%3AGuthr%22&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `../users?$search="displayName:Guthr" OR "mail:Guthr"` |
| Group | Address book display name or description of the group. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=groups%3F%24search%3D%22description%3AOne%22%20AND%20\(%22displayName%3AVideo%22%20OR%20%22displayName%3ADrive%22\)&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `../groups?$search="description:One" AND ("displayName:Video" OR "displayName:Drive")` |
| Group | Address book display name on a mail-enabled group. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=groups%3F%24filter%3DmailEnabled%20eq%20true%26%24search%3D%22displayName%3AOneVideo%22&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `../groups?$filter=mailEnabled eq true&$search="displayName:OneVideo"` |

## Related content

- [Use query parameters to customize responses](https://learn.microsoft.com/en-us/graph/query-parameters)
- [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries)
- [Query parameter limitations](https://developer.microsoft.com/graph/known-issues/?filterBy=Query%20parameters&search=)
