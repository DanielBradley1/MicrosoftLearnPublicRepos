<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationroot-post-users?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create educationUser

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new user.

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
POST /education/users
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-beta) object.

## Response

If successful, this method returns a `201 Created` response code and an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/education/users
Content-type: application/json

{
  "displayName": "Dion Matheson",
  "givenName": "Dion",
  "middleName": null,
  "surname": "Matheson",
  "mail": "DionM@contoso.com",
  "mobilePhone": "+1 (253) 555-0101",
  "createdBy": {
    "user": {
      "displayName": "Susana Rocha",
      "id": "14012"
    }
  },
  "externalSource": "sis",
  "mailingAddress": {
    "city": "Los Angeles",
    "countryOrRegion": "United States",
    "postalCode": "98055",
    "state": "CA",
    "street": "12345 Main St."
  },
  "primaryRole": "student",
  "residenceAddress": {
    "city": "Los Angeles",
    "countryOrRegion": "United States",
    "postalCode": "98055",
    "state": "CA",
    "street": "12345 Main St."
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new EducationUser
{
	DisplayName = "Dion Matheson",
	GivenName = "Dion",
	MiddleName = null,
	Surname = "Matheson",
	Mail = "DionM@contoso.com",
	MobilePhone = "+1 (253) 555-0101",
	CreatedBy = new IdentitySet
	{
		User = new Identity
		{
			DisplayName = "Susana Rocha",
			Id = "14012",
		},
	},
	ExternalSource = EducationExternalSource.Sis,
	MailingAddress = new PhysicalAddress
	{
		City = "Los Angeles",
		CountryOrRegion = "United States",
		PostalCode = "98055",
		State = "CA",
		Street = "12345 Main St.",
	},
	PrimaryRole = EducationUserRole.Student,
	ResidenceAddress = new PhysicalAddress
	{
		City = "Los Angeles",
		CountryOrRegion = "United States",
		PostalCode = "98055",
		State = "CA",
		Street = "12345 Main St.",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Users.PostAsync(requestBody);
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
displayName := "Dion Matheson"
requestBody.SetDisplayName(&displayName) 
givenName := "Dion"
requestBody.SetGivenName(&givenName) 
middleName := null
requestBody.SetMiddleName(&middleName) 
surname := "Matheson"
requestBody.SetSurname(&surname) 
mail := "DionM@contoso.com"
requestBody.SetMail(&mail) 
mobilePhone := "+1 (253) 555-0101"
requestBody.SetMobilePhone(&mobilePhone) 
createdBy := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
displayName := "Susana Rocha"
user.SetDisplayName(&displayName) 
id := "14012"
user.SetId(&id) 
createdBy.SetUser(user)
requestBody.SetCreatedBy(createdBy)
externalSource := graphmodels.SIS_EDUCATIONEXTERNALSOURCE 
requestBody.SetExternalSource(&externalSource) 
mailingAddress := graphmodels.NewPhysicalAddress()
city := "Los Angeles"
mailingAddress.SetCity(&city) 
countryOrRegion := "United States"
mailingAddress.SetCountryOrRegion(&countryOrRegion) 
postalCode := "98055"
mailingAddress.SetPostalCode(&postalCode) 
state := "CA"
mailingAddress.SetState(&state) 
street := "12345 Main St."
mailingAddress.SetStreet(&street) 
requestBody.SetMailingAddress(mailingAddress)
primaryRole := graphmodels.STUDENT_EDUCATIONUSERROLE 
requestBody.SetPrimaryRole(&primaryRole) 
residenceAddress := graphmodels.NewPhysicalAddress()
city := "Los Angeles"
residenceAddress.SetCity(&city) 
countryOrRegion := "United States"
residenceAddress.SetCountryOrRegion(&countryOrRegion) 
postalCode := "98055"
residenceAddress.SetPostalCode(&postalCode) 
state := "CA"
residenceAddress.SetState(&state) 
street := "12345 Main St."
residenceAddress.SetStreet(&street) 
requestBody.SetResidenceAddress(residenceAddress)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Education().Users().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationUser educationUser = new EducationUser();
educationUser.setDisplayName("Dion Matheson");
educationUser.setGivenName("Dion");
educationUser.setMiddleName(null);
educationUser.setSurname("Matheson");
educationUser.setMail("DionM@contoso.com");
educationUser.setMobilePhone("+1 (253) 555-0101");
IdentitySet createdBy = new IdentitySet();
Identity user = new Identity();
user.setDisplayName("Susana Rocha");
user.setId("14012");
createdBy.setUser(user);
educationUser.setCreatedBy(createdBy);
educationUser.setExternalSource(EducationExternalSource.Sis);
PhysicalAddress mailingAddress = new PhysicalAddress();
mailingAddress.setCity("Los Angeles");
mailingAddress.setCountryOrRegion("United States");
mailingAddress.setPostalCode("98055");
mailingAddress.setState("CA");
mailingAddress.setStreet("12345 Main St.");
educationUser.setMailingAddress(mailingAddress);
educationUser.setPrimaryRole(EducationUserRole.Student);
PhysicalAddress residenceAddress = new PhysicalAddress();
residenceAddress.setCity("Los Angeles");
residenceAddress.setCountryOrRegion("United States");
residenceAddress.setPostalCode("98055");
residenceAddress.setState("CA");
residenceAddress.setStreet("12345 Main St.");
educationUser.setResidenceAddress(residenceAddress);
EducationUser result = graphClient.education().users().post(educationUser);
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
  displayName: 'Dion Matheson',
  givenName: 'Dion',
  middleName: null,
  surname: 'Matheson',
  mail: 'DionM@contoso.com',
  mobilePhone: '+1 (253) 555-0101',
  createdBy: {
    user: {
      displayName: 'Susana Rocha',
      id: '14012'
    }
  },
  externalSource: 'sis',
  mailingAddress: {
    city: 'Los Angeles',
    countryOrRegion: 'United States',
    postalCode: '98055',
    state: 'CA',
    street: '12345 Main St.'
  },
  primaryRole: 'student',
  residenceAddress: {
    city: 'Los Angeles',
    countryOrRegion: 'United States',
    postalCode: '98055',
    state: 'CA',
    street: '12345 Main St.'
  }
};

await client.api('/education/users')
	.version('beta')
	.post(educationUser);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\EducationUser;
use Microsoft\Graph\Beta\Generated\Models\IdentitySet;
use Microsoft\Graph\Beta\Generated\Models\Identity;
use Microsoft\Graph\Beta\Generated\Models\EducationExternalSource;
use Microsoft\Graph\Beta\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Beta\Generated\Models\EducationUserRole;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationUser();
$requestBody->setDisplayName('Dion Matheson');
$requestBody->setGivenName('Dion');
$requestBody->setMiddleName(null);
$requestBody->setSurname('Matheson');
$requestBody->setMail('DionM@contoso.com');
$requestBody->setMobilePhone('+1 (253) 555-0101');
$createdBy = new IdentitySet();
$createdByUser = new Identity();
$createdByUser->setDisplayName('Susana Rocha');
$createdByUser->setId('14012');
$createdBy->setUser($createdByUser);
$requestBody->setCreatedBy($createdBy);
$requestBody->setExternalSource(new EducationExternalSource('sis'));
$mailingAddress = new PhysicalAddress();
$mailingAddress->setCity('Los Angeles');
$mailingAddress->setCountryOrRegion('United States');
$mailingAddress->setPostalCode('98055');
$mailingAddress->setState('CA');
$mailingAddress->setStreet('12345 Main St.');
$requestBody->setMailingAddress($mailingAddress);
$requestBody->setPrimaryRole(new EducationUserRole('student'));
$residenceAddress = new PhysicalAddress();
$residenceAddress->setCity('Los Angeles');
$residenceAddress->setCountryOrRegion('United States');
$residenceAddress->setPostalCode('98055');
$residenceAddress->setState('CA');
$residenceAddress->setStreet('12345 Main St.');
$requestBody->setResidenceAddress($residenceAddress);

$result = $graphServiceClient->education()->users()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Education

$params = @{
	displayName = "Dion Matheson"
	givenName = "Dion"
	middleName = $null
	surname = "Matheson"
	mail = "DionM@contoso.com"
	mobilePhone = "+1 (253) 555-0101"
	createdBy = @{
		user = @{
			displayName = "Susana Rocha"
			id = "14012"
		}
	}
	externalSource = "sis"
	mailingAddress = @{
		city = "Los Angeles"
		countryOrRegion = "United States"
		postalCode = "98055"
		state = "CA"
		street = "12345 Main St."
	}
	primaryRole = "student"
	residenceAddress = @{
		city = "Los Angeles"
		countryOrRegion = "United States"
		postalCode = "98055"
		state = "CA"
		street = "12345 Main St."
	}
}

New-MgBetaEducationUser -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.education_user import EducationUser
from msgraph_beta.generated.models.identity_set import IdentitySet
from msgraph_beta.generated.models.identity import Identity
from msgraph_beta.generated.models.education_external_source import EducationExternalSource
from msgraph_beta.generated.models.physical_address import PhysicalAddress
from msgraph_beta.generated.models.education_user_role import EducationUserRole
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationUser(
	display_name = "Dion Matheson",
	given_name = "Dion",
	middle_name = None,
	surname = "Matheson",
	mail = "DionM@contoso.com",
	mobile_phone = "+1 (253) 555-0101",
	created_by = IdentitySet(
		user = Identity(
			display_name = "Susana Rocha",
			id = "14012",
		),
	),
	external_source = EducationExternalSource.Sis,
	mailing_address = PhysicalAddress(
		city = "Los Angeles",
		country_or_region = "United States",
		postal_code = "98055",
		state = "CA",
		street = "12345 Main St.",
	),
	primary_role = EducationUserRole.Student,
	residence_address = PhysicalAddress(
		city = "Los Angeles",
		country_or_region = "United States",
		postal_code = "98055",
		state = "CA",
		street = "12345 Main St.",
	),
)

result = await graph_client.education.users.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "13012",
  "displayName": "Dion Matheson",
  "givenName": "Dion",
  "middleName": " ",
  "surname": "Matheson",
  "mail": "DionM@contoso.com",
  "mobilePhone": "+1 (253) 555-0101",
  "createdBy": {
    "user": {
      "displayName": "Susana Rocha",
      "id": "14012",
    }
  },
  "externalSource": "sis",
  "mailingAddress": {
    "city": "Los Angeles",
    "countryOrRegion": "United States",
    "postalCode": "98055",
    "state": "CA",
    "street": "12345 Main St."
  },
  "primaryRole": "student",
  "residenceAddress": {
    "city": "Los Angeles",
    "countryOrRegion": "United States",
    "postalCode": "98055",
    "state": "CA",
    "street": "12345 Main St."
  }
}
```
