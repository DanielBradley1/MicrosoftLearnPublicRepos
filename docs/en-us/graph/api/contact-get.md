<!-- Source: https://learn.microsoft.com/en-us/graph/api/contact-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# Get contact

Namespace: microsoft.graph

Retrieve the properties and relationships of a contact object.

There are two scenarios where an app can get a contact in another user's contact folder:

- If the app has application permissions, or,
- If the app has the appropriate delegated [permissions](#permissions) from one user, and another user has shared a contact folder with that user, or, has given delegated access to that user. See [details and an example](https://learn.microsoft.com/en-us/graph/outlook-get-shared-contacts-folders).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Contacts.Read | Contacts.ReadWrite |
| Delegated \(personal Microsoft account\) | Contacts.Read | Contacts.ReadWrite |
| Application | Contacts.Read | Contacts.ReadWrite |

## HTTP request

A [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) in the user's mailbox.

```http
GET /me/contacts/{id}
GET /users/{id | userPrincipalName}/contacts/{id}
```

A [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) from a user's top level [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0).

```http
GET /me/contactfolders/{Id}/contacts/{id}
GET /users/{id | userPrincipalName}/contactfolders/{id}/contacts/{id}
```

A [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) contained in a child folder of a [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0). The example below shows one level of nesting, but a contact can be located in a child of a child and so on.

```http
GET /me/contactFolders/{id}/childFolders/{id}/.../contacts/{id}
GET /users/{id | userPrincipalName}/contactFolders/{id}/childFolders/{id}/contacts/{id}
```

## Optional query parameters

| Name | Value | Description |
| :--- | :--- | :--- |
| $expand | string | Comma-separated list of relationships to expand and include in the response. See the relationships table of the [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) object for supported names. |
| $select | string | Comma-separated list of properties to include in the response. |

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) object in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/me/contacts/AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAEOAAAiIsqMbYjsT5e-T7KzowPTAAAYbuK-AAA=
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Contacts["{contact-id}"].GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
contacts, err := graphClient.Me().Contacts().ByContactId("contact-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Contact result = graphClient.me().contacts().byContactId("{contact-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let contact = await client.api('/me/contacts/AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAEOAAAiIsqMbYjsT5e-T7KzowPTAAAYbuK-AAA=')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->contacts()->byContactId('contact-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.PersonalContacts

# A UPN can also be used as -UserId.
Get-MgUserContact -UserId $userId -ContactId $contactId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.contacts.by_contact_id('contact-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('48d31887-5fad-4d73-a9f5-3c356e68a038')/contacts/$entity",
    "@odata.etag": "W/\"EQAAABYAAAAiIsqMbYjsT5e/T7KzowPTAAAYc8Bf\"",
    "id": "AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAEOAAAiIsqMbYjsT5e-T7KzowPTAAAYbuK-AAA=",
    "createdDateTime": "2017-09-04T15:54:01Z",
    "lastModifiedDateTime": "2017-09-04T15:54:02Z",
    "changeKey": "EQAAABYAAAAiIsqMbYjsT5e/T7KzowPTAAAYc8Bf",
    "categories": [],
    "parentFolderId": "AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OAAuAAAAAAAiQ8W967B7TKBjgx9rVEURAQAiIsqMbYjsT5e-T7KzowPTAAAAAAEOAAA=",
    "birthday": null,
    "fileAs": "",
    "displayName": "Alex Wilber",
    "givenName": "Alex",
    "initials": null,
    "middleName": null,
    "nickName": null,
    "surname": "Wilber",
    "title": null,
    "yomiGivenName": null,
    "yomiSurname": null,
    "yomiCompanyName": null,
    "generation": null,
    "emailAddresses": [
      {
        "name": "Alex Wilber",
        "address": "alexw@contoso.com",
        "type": "unknown"
      },
      {
        "name": "Alex Wilber",
        "address": "alex.wilber@outlook.com",
        "type": "personal"
      }
    ],
    "primaryEmailAddress": {
      "name": "Alex Wilber",
      "address": "alexw@contoso.com"
    },
    "secondaryEmailAddress": {
      "name": "Alex Wilber",
      "address": "alex.wilber@outlook.com"
    },
    "tertiaryEmailAddress": null,
    "imAddresses": [
      "sip:alexw@contoso.com"
    ],
    "jobTitle": "Web Marketing Manager",
    "companyName": null,
    "department": null,
    "officeLocation": null,
    "profession": null,
    "businessHomePage": null,
    "assistantName": null,
    "manager": null,
    "homePhones": [],
    "mobilePhone": null,
    "businessPhones": [],
    "spouseName": null,
    "personalNotes": "",
    "children": [],
    "homeAddress": {},
    "businessAddress": {},
    "otherAddress": {}
}
```
