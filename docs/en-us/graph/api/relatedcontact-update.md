<!-- Source: https://learn.microsoft.com/en-us/graph/api/relatedcontact-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Update relatedContacts

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the [relatedContact](https://learn.microsoft.com/en-us/graph/api/resources/relatedcontact?view=graph-rest-beta) collection of an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-beta) object.

Note

Updating **relatedContacts** replaces the entire collection. It is not possible to add, remove, or update a single contact.

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
| Application | EduRoster.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /education/users/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [relatedContact](https://learn.microsoft.com/en-us/graph/api/resources/relatedcontact?view=graph-rest-beta) collection.

The following table shows the properties that are required when you update the [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| relatedContacts | [relatedContact](https://learn.microsoft.com/en-us/graph/api/resources/relatedcontact?view=graph-rest-beta) collection | The complete set of related contact for a user |

Important

This update must be a distinct operation. It cannot be combined with updates to other [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-beta) properties. For example, updating both **relatedContacts** and **displayName** requires two distinct requests.

## Response

If successful, this method returns a `200 OK` response code and an updated [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-beta) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/education/users/{educationUserId}
Content-Type: application/json

{
  "relatedContacts": [
    {
      "displayName": "Father Time",
      "emailAddress": "father@time.com",
      "mobilePhone": "4251231234",
      "relationship": "guardian",
      "accessConsent": true
    },
    {
      "displayName": "Mother Nature",
      "emailAddress": "mother@nature.co.uk",
      "mobilePhone": "3251231234",
      "relationship": "parent",
      "accessConsent": true
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new EducationUser
{
	RelatedContacts = new List<RelatedContact>
	{
		new RelatedContact
		{
			DisplayName = "Father Time",
			EmailAddress = "father@time.com",
			MobilePhone = "4251231234",
			Relationship = ContactRelationship.Guardian,
			AccessConsent = true,
		},
		new RelatedContact
		{
			DisplayName = "Mother Nature",
			EmailAddress = "mother@nature.co.uk",
			MobilePhone = "3251231234",
			Relationship = ContactRelationship.Parent,
			AccessConsent = true,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Users["{educationUser-id}"].PatchAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewEducationUser()


relatedContact := graphmodels.NewRelatedContact()
displayName := "Father Time"
relatedContact.SetDisplayName(&displayName) 
emailAddress := "father@time.com"
relatedContact.SetEmailAddress(&emailAddress) 
mobilePhone := "4251231234"
relatedContact.SetMobilePhone(&mobilePhone) 
relationship := graphmodels.GUARDIAN_CONTACTRELATIONSHIP 
relatedContact.SetRelationship(&relationship) 
accessConsent := true
relatedContact.SetAccessConsent(&accessConsent) 
relatedContact1 := graphmodels.NewRelatedContact()
displayName := "Mother Nature"
relatedContact1.SetDisplayName(&displayName) 
emailAddress := "mother@nature.co.uk"
relatedContact1.SetEmailAddress(&emailAddress) 
mobilePhone := "3251231234"
relatedContact1.SetMobilePhone(&mobilePhone) 
relationship := graphmodels.PARENT_CONTACTRELATIONSHIP 
relatedContact1.SetRelationship(&relationship) 
accessConsent := true
relatedContact1.SetAccessConsent(&accessConsent) 

relatedContacts := []graphmodels.RelatedContactable {
	relatedContact,
	relatedContact1,
}
requestBody.SetRelatedContacts(relatedContacts)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Education().Users().ByEducationUserId("educationUser-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationUser educationUser = new EducationUser();
LinkedList<RelatedContact> relatedContacts = new LinkedList<RelatedContact>();
RelatedContact relatedContact = new RelatedContact();
relatedContact.setDisplayName("Father Time");
relatedContact.setEmailAddress("father@time.com");
relatedContact.setMobilePhone("4251231234");
relatedContact.setRelationship(ContactRelationship.Guardian);
relatedContact.setAccessConsent(true);
relatedContacts.add(relatedContact);
RelatedContact relatedContact1 = new RelatedContact();
relatedContact1.setDisplayName("Mother Nature");
relatedContact1.setEmailAddress("mother@nature.co.uk");
relatedContact1.setMobilePhone("3251231234");
relatedContact1.setRelationship(ContactRelationship.Parent);
relatedContact1.setAccessConsent(true);
relatedContacts.add(relatedContact1);
educationUser.setRelatedContacts(relatedContacts);
EducationUser result = graphClient.education().users().byEducationUserId("{educationUser-id}").patch(educationUser);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationUser = {
  relatedContacts: [
    {
      displayName: 'Father Time',
      emailAddress: 'father@time.com',
      mobilePhone: '4251231234',
      relationship: 'guardian',
      accessConsent: true
    },
    {
      displayName: 'Mother Nature',
      emailAddress: 'mother@nature.co.uk',
      mobilePhone: '3251231234',
      relationship: 'parent',
      accessConsent: true
    }
  ]
};

await client.api('/education/users/{educationUserId}')
	.version('beta')
	.update(educationUser);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\EducationUser;
use Microsoft\Graph\Beta\Generated\Models\RelatedContact;
use Microsoft\Graph\Beta\Generated\Models\ContactRelationship;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationUser();
$relatedContactsRelatedContact1 = new RelatedContact();
$relatedContactsRelatedContact1->setDisplayName('Father Time');
$relatedContactsRelatedContact1->setEmailAddress('father@time.com');
$relatedContactsRelatedContact1->setMobilePhone('4251231234');
$relatedContactsRelatedContact1->setRelationship(new ContactRelationship('guardian'));
$relatedContactsRelatedContact1->setAccessConsent(true);
$relatedContactsArray []= $relatedContactsRelatedContact1;
$relatedContactsRelatedContact2 = new RelatedContact();
$relatedContactsRelatedContact2->setDisplayName('Mother Nature');
$relatedContactsRelatedContact2->setEmailAddress('mother@nature.co.uk');
$relatedContactsRelatedContact2->setMobilePhone('3251231234');
$relatedContactsRelatedContact2->setRelationship(new ContactRelationship('parent'));
$relatedContactsRelatedContact2->setAccessConsent(true);
$relatedContactsArray []= $relatedContactsRelatedContact2;
$requestBody->setRelatedContacts($relatedContactsArray);


$result = $graphServiceClient->education()->users()->byEducationUserId('educationUser-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Education

$params = @{
	relatedContacts = @(
		@{
			displayName = "Father Time"
			emailAddress = "father@time.com"
			mobilePhone = "4251231234"
			relationship = "guardian"
			accessConsent = $true
		}
		@{
			displayName = "Mother Nature"
			emailAddress = "mother@nature.co.uk"
			mobilePhone = "3251231234"
			relationship = "parent"
			accessConsent = $true
		}
	)
}

Update-MgBetaEducationUser -EducationUserId $educationUserId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.education_user import EducationUser
from msgraph_beta.generated.models.related_contact import RelatedContact
from msgraph_beta.generated.models.contact_relationship import ContactRelationship
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationUser(
	related_contacts = [
		RelatedContact(
			display_name = "Father Time",
			email_address = "father@time.com",
			mobile_phone = "4251231234",
			relationship = ContactRelationship.Guardian,
			access_consent = True,
		),
		RelatedContact(
			display_name = "Mother Nature",
			email_address = "mother@nature.co.uk",
			mobile_phone = "3251231234",
			relationship = ContactRelationship.Parent,
			access_consent = True,
		),
	],
)

result = await graph_client.education.users.by_education_user_id('educationUser-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "4b712dc5-2dc5-4b71-c52d-714bc52d714b",
  "relatedContacts": [
      {
          "displayName": "Father Time",
          "emailAddress": "father@time.com",
          "mobilePhone": "4251231234",
          "relationship": "guardian",
          "accessConsent": true
      },
      {
          "displayName": "Mother Nature",
          "emailAddress": "mother@nature.co.uk",
          "mobilePhone": "3251231234",
          "relationship": "parent",
          "accessConsent": true
      }
  ]
}
```
