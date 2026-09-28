<!-- Source: https://learn.microsoft.com/en-us/graph/api/contactfolder-post-contacts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create contact

Namespace: microsoft.graph

Add a contact to the root Contacts folder or to the `contacts` endpoint of another contact folder.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Contacts.ReadWrite |
| Delegated \(personal Microsoft account\) | Contacts.ReadWrite |
| Application | Contacts.ReadWrite |

## HTTP request

```http
POST /me/contacts
POST /users/{id | userPrincipalName}/contacts

POST /me/contactFolders/{id}/contacts
POST /users/{id | userPrincipalName}/contactFolders/{id}/contacts
```

  


## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [Contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) object.

## Response

If successful, this method returns `201 Created` response code and the [Contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/me/contactFolders/{id}/contacts
Content-type: application/json

{
  "parentFolderId": "parentFolderId-value",
  "birthday": "datetime-value",
  "fileAs": "fileAs-value",
  "displayName": "displayName-value",
  "givenName": "givenName-value",
  "initials": "initials-value"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Contact
{
	ParentFolderId = "parentFolderId-value",
	Birthday = DateTimeOffset.Parse("datetime-value"),
	FileAs = "fileAs-value",
	DisplayName = "displayName-value",
	GivenName = "givenName-value",
	Initials = "initials-value",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.ContactFolders["{contactFolder-id}"].Contacts.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewContact()
parentFolderId := "parentFolderId-value"
requestBody.SetParentFolderId(&parentFolderId) 
birthday , err := time.Parse(time.RFC3339, "datetime-value")
requestBody.SetBirthday(&birthday) 
fileAs := "fileAs-value"
requestBody.SetFileAs(&fileAs) 
displayName := "displayName-value"
requestBody.SetDisplayName(&displayName) 
givenName := "givenName-value"
requestBody.SetGivenName(&givenName) 
initials := "initials-value"
requestBody.SetInitials(&initials) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
contacts, err := graphClient.Me().ContactFolders().ByContactFolderId("contactFolder-id").Contacts().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Contact contact = new Contact();
contact.setParentFolderId("parentFolderId-value");
OffsetDateTime birthday = OffsetDateTime.parse("datetime-value");
contact.setBirthday(birthday);
contact.setFileAs("fileAs-value");
contact.setDisplayName("displayName-value");
contact.setGivenName("givenName-value");
contact.setInitials("initials-value");
Contact result = graphClient.me().contactFolders().byContactFolderId("{contactFolder-id}").contacts().post(contact);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const contact = {
  parentFolderId: 'parentFolderId-value',
  birthday: 'datetime-value',
  fileAs: 'fileAs-value',
  displayName: 'displayName-value',
  givenName: 'givenName-value',
  initials: 'initials-value'
};

await client.api('/me/contactFolders/{id}/contacts')
	.post(contact);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Contact;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Contact();
$requestBody->setParentFolderId('parentFolderId-value');
$requestBody->setBirthday(new \DateTime('datetime-value'));
$requestBody->setFileAs('fileAs-value');
$requestBody->setDisplayName('displayName-value');
$requestBody->setGivenName('givenName-value');
$requestBody->setInitials('initials-value');

$result = $graphServiceClient->me()->contactFolders()->byContactFolderId('contactFolder-id')->contacts()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.PersonalContacts

$params = @{
	parentFolderId = "parentFolderId-value"
	birthday = [System.DateTime]::Parse("datetime-value")
	fileAs = "fileAs-value"
	displayName = "displayName-value"
	givenName = "givenName-value"
	initials = "initials-value"
}

# A UPN can also be used as -UserId.
New-MgUserContactFolderContact -UserId $userId -ContactFolderId $contactFolderId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.contact import Contact
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Contact(
	parent_folder_id = "parentFolderId-value",
	birthday = "datetime-value",
	file_as = "fileAs-value",
	display_name = "displayName-value",
	given_name = "givenName-value",
	initials = "initials-value",
)

result = await graph_client.me.contact_folders.by_contact_folder_id('contactFolder-id').contacts.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

  


In the request body, supply a JSON representation of the [Contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) object.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "parentFolderId": "parentFolderId-value",
  "birthday": "datetime-value",
  "fileAs": "fileAs-value",
  "displayName": "displayName-value",
  "givenName": "givenName-value",
  "initials": "initials-value"
}
```
