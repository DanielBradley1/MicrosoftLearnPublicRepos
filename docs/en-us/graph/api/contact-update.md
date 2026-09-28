<!-- Source: https://learn.microsoft.com/en-us/graph/api/contact-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# Update contact

Namespace: microsoft.graph

Update the properties of a contact object.

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

A [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) from a user's default [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0).

```http
PATCH /me/contacts/{id}
PATCH /users/{id | userPrincipalName}/contacts/{id}
```

A [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) from a user's top level [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0).

```http
PATCH /me/contactFolders/{id}/contacts/{id}
PATCH /users/{id | userPrincipalName}/contactFolders/{id}/contacts/{id}
```

A [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) contained in a child folder of a [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0). The example below shows one level of nesting, but a contact can be located in a child of a child and so on.

```http
PATCH /me/contactFolders/{id}/childFolders/{id}/.../contacts/{id}
PATCH /users/{id | userPrincipalName}/contactFolders/{id}/childFolders/{id}/contacts/{id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

When you update structured properties such as **homeAddress**, you must pass the full property set.

| Property | Type | Description |
| :--- | :--- | :--- |
| assistantName | String | The name of the contact's assistant. |
| birthday | DateTimeOffset | The contact's birthday. |
| businessAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The contact's business address. |
| businessHomePage | String | The business home page of the contact. |
| businessPhones | String | The contact's business phone numbers. |
| categories | String | The categories associated with the contact. |
| children | String | The names of the contact's children. |
| companyName | String | The name of the contact's company. |
| department | String | The contact's department. |
| displayName | String | The contact's display name. Note that later updates to other properties may cause an automatically generated value to overwrite the displayName value you have specified. To preserve a pre-existing value, always include it as displayName in an update operation. |
| emailAddresses | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) collection | The contact's email addresses. |
| fileAs | String | The name the contact is filed under. |
| generation | String | The contact's generation. |
| givenName | String | The contact's given name. |
| homeAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The contact's home address. |
| homePhones | String collection | The contact's home phone numbers. |
| imAddresses | String | The contact's instant messaging \(IM\) addresses. |
| initials | String | The contact's initials. |
| jobTitle | String | The contact’s job title. |
| manager | String | The name of the contact's manager. |
| middleName | String | The contact's middle name. |
| mobilePhone | String | The contact's mobile phone number. |
| nickName | String | The contact's nickname. |
| officeLocation | String | The location of the contact's office. |
| otherAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | Other addresses for the contact. |
| parentFolderId | String | The ID of the contact's parent folder. |
| personalNotes | String | The user's notes about the contact. |
| primaryEmailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The contact's primary email address. Optional. |
| profession | String | The contact's profession. |
| secondaryEmailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The contact's secondary email address. Optional. |
| spouseName | String | The name of the contact's spouse/partner. |
| surname | String | The contact's surname. |
| tertiaryEmailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The contact's tertiary email address. Optional. |
| title | String | The contact's title. |
| yomiCompanyName | String | The phonetic Japanese company name of the contact. Optional. |
| yomiGivenName | String | The phonetic Japanese given name \(first name\) of the contact. Optional. |
| yomiSurname | String | The phonetic Japanese surname \(last name\) of the contact. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/me/contacts/{id}
Content-type: application/json

{
  "homeAddress": {
    "street": "123 Some street",
    "city": "Seattle",
    "state": "WA",
    "postalCode": "98121"
  },
  "birthday": "1974-07-22"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Contact
{
	HomeAddress = new PhysicalAddress
	{
		Street = "123 Some street",
		City = "Seattle",
		State = "WA",
		PostalCode = "98121",
	},
	Birthday = DateTimeOffset.Parse("1974-07-22"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Contacts["{contact-id}"].PatchAsync(requestBody);
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
homeAddress := graphmodels.NewPhysicalAddress()
street := "123 Some street"
homeAddress.SetStreet(&street) 
city := "Seattle"
homeAddress.SetCity(&city) 
state := "WA"
homeAddress.SetState(&state) 
postalCode := "98121"
homeAddress.SetPostalCode(&postalCode) 
requestBody.SetHomeAddress(homeAddress)
birthday , err := time.Parse(time.RFC3339, "1974-07-22")
requestBody.SetBirthday(&birthday) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
contacts, err := graphClient.Me().Contacts().ByContactId("contact-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Contact contact = new Contact();
PhysicalAddress homeAddress = new PhysicalAddress();
homeAddress.setStreet("123 Some street");
homeAddress.setCity("Seattle");
homeAddress.setState("WA");
homeAddress.setPostalCode("98121");
contact.setHomeAddress(homeAddress);
OffsetDateTime birthday = OffsetDateTime.parse("1974-07-22");
contact.setBirthday(birthday);
Contact result = graphClient.me().contacts().byContactId("{contact-id}").patch(contact);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const contact = {
  homeAddress: {
    street: '123 Some street',
    city: 'Seattle',
    state: 'WA',
    postalCode: '98121'
  },
  birthday: '1974-07-22'
};

await client.api('/me/contacts/{id}')
	.update(contact);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Contact;
use Microsoft\Graph\Generated\Models\PhysicalAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Contact();
$homeAddress = new PhysicalAddress();
$homeAddress->setStreet('123 Some street');
$homeAddress->setCity('Seattle');
$homeAddress->setState('WA');
$homeAddress->setPostalCode('98121');
$requestBody->setHomeAddress($homeAddress);
$requestBody->setBirthday(new \DateTime('1974-07-22'));

$result = $graphServiceClient->me()->contacts()->byContactId('contact-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.PersonalContacts

$params = @{
	homeAddress = @{
		street = "123 Some street"
		city = "Seattle"
		state = "WA"
		postalCode = "98121"
	}
	birthday = [System.DateTime]::Parse("1974-07-22")
}

# A UPN can also be used as -UserId.
Update-MgUserContact -UserId $userId -ContactId $contactId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.contact import Contact
from msgraph.generated.models.physical_address import PhysicalAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Contact(
	home_address = PhysicalAddress(
		street = "123 Some street",
		city = "Seattle",
		state = "WA",
		postal_code = "98121",
	),
	birthday = "1974-07-22",
)

result = await graph_client.me.contacts.by_contact_id('contact-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "AAMkAGI2THk0AAA=",
  "createdDateTime": "2014-10-19T23:08:24Z",
  "lastModifiedDateTime": "2014-10-19T23:08:24Z",
  "changeKey": "EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa4",
  "categories": [],
  "parentFolderId": "AAMkAGI2AAEOAAA=",
  "birthday": "1974-07-22",
  "fileAs": "Fort, Garth",
  "displayName": "Garth Fort",
  "givenName": "Garth",
  "initials": "G.F.",
  "middleName": null,
  "nickName": "Garth",
  "surname": "Fort",
  "title": null,
  "yomiGivenName": null,
  "yomiSurname": null,
  "yomiCompanyName": null,
  "generation": null,
  "emailAddresses": [
    {
      "name": "Garth",
      "address": "garth@contoso.com"
    }
  ],
  "primaryEmailAddress": {
    "name": "Garth",
    "address": "garth@contoso.com"
  },
  "secondaryEmailAddress": null,
  "tertiaryEmailAddress": null,
  "imAddresses": [
    "sip:garthf@contoso.com"
  ],
  "jobTitle": "Web Marketing Manager",
  "companyName": "Contoso, Inc.",
  "department": "Sales & Marketing",
  "officeLocation": "20/1101",
  "profession": null,
  "businessHomePage": "https://www.contoso.com",
  "assistantName": null,
  "manager": null,
  "homePhones": [],
  "mobilePhone": null,
  "businessPhones": [
    "+1 918 555 0101"
  ],
  "homeAddress": {
    "street": "123 Some street",
    "city": "Seattle",
    "state": "WA",
    "postalCode": "98121"
  },
  "businessAddress": {
      "street": "10 Contoso Way",
      "city": "Redmond",
      "state": "WA",
      "countryOrRegion": "USA",
      "postalCode": "98075"
  },
  "otherAddress": {},
  "spouseName": null,
  "personalNotes": null,
  "children": []
}
```
