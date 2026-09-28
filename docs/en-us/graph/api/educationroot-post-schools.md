<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationroot-post-schools?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create educationSchool

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a school.

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
POST /education/schools
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of an [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-beta) object.

## Response

If successful, this method returns a `201 Created` response code and an [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/education/schools
Content-type: application/json

{
  "displayName": "Fabrikam High School",
  "description": "Magnate school for the arts. Los Angeles School District",
  "externalSource": "String",
  "principalEmail": "AmyR@fabrikam.com",
  "principalName": "Amy Roebuck",
  "externalPrincipalId": "14007",
  "highestGrade": "12",
  "lowestGrade": "9",
  "schoolNumber": "10002",
  "address": {
    "city": "Los Angeles",
    "countryOrRegion": "United States",
    "postalCode": "98055",
    "state": "CA",
    "street": "12345 Main St."
  },
  "externalId": "10002",
  "phone": "+1 (253) 555-0102",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new EducationSchool
{
	DisplayName = "Fabrikam High School",
	Description = "Magnate school for the arts. Los Angeles School District",
	ExternalSource = EducationExternalSource.Sis,
	PrincipalEmail = "AmyR@fabrikam.com",
	PrincipalName = "Amy Roebuck",
	ExternalPrincipalId = "14007",
	HighestGrade = "12",
	LowestGrade = "9",
	SchoolNumber = "10002",
	Address = new PhysicalAddress
	{
		City = "Los Angeles",
		CountryOrRegion = "United States",
		PostalCode = "98055",
		State = "CA",
		Street = "12345 Main St.",
	},
	ExternalId = "10002",
	Phone = "+1 (253) 555-0102",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Schools.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationSchool()
displayName := "Fabrikam High School"
requestBody.SetDisplayName(&displayName) 
description := "Magnate school for the arts. Los Angeles School District"
requestBody.SetDescription(&description) 
externalSource := graphmodels.STRING_EDUCATIONEXTERNALSOURCE 
requestBody.SetExternalSource(&externalSource) 
principalEmail := "AmyR@fabrikam.com"
requestBody.SetPrincipalEmail(&principalEmail) 
principalName := "Amy Roebuck"
requestBody.SetPrincipalName(&principalName) 
externalPrincipalId := "14007"
requestBody.SetExternalPrincipalId(&externalPrincipalId) 
highestGrade := "12"
requestBody.SetHighestGrade(&highestGrade) 
lowestGrade := "9"
requestBody.SetLowestGrade(&lowestGrade) 
schoolNumber := "10002"
requestBody.SetSchoolNumber(&schoolNumber) 
address := graphmodels.NewPhysicalAddress()
city := "Los Angeles"
address.SetCity(&city) 
countryOrRegion := "United States"
address.SetCountryOrRegion(&countryOrRegion) 
postalCode := "98055"
address.SetPostalCode(&postalCode) 
state := "CA"
address.SetState(&state) 
street := "12345 Main St."
address.SetStreet(&street) 
requestBody.SetAddress(address)
externalId := "10002"
requestBody.SetExternalId(&externalId) 
phone := "+1 (253) 555-0102"
requestBody.SetPhone(&phone) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
schools, err := graphClient.Education().Schools().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationSchool educationSchool = new EducationSchool();
educationSchool.setDisplayName("Fabrikam High School");
educationSchool.setDescription("Magnate school for the arts. Los Angeles School District");
educationSchool.setExternalSource(EducationExternalSource.Sis);
educationSchool.setPrincipalEmail("AmyR@fabrikam.com");
educationSchool.setPrincipalName("Amy Roebuck");
educationSchool.setExternalPrincipalId("14007");
educationSchool.setHighestGrade("12");
educationSchool.setLowestGrade("9");
educationSchool.setSchoolNumber("10002");
PhysicalAddress address = new PhysicalAddress();
address.setCity("Los Angeles");
address.setCountryOrRegion("United States");
address.setPostalCode("98055");
address.setState("CA");
address.setStreet("12345 Main St.");
educationSchool.setAddress(address);
educationSchool.setExternalId("10002");
educationSchool.setPhone("+1 (253) 555-0102");
EducationSchool result = graphClient.education().schools().post(educationSchool);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationSchool = {
  displayName: 'Fabrikam High School',
  description: 'Magnate school for the arts. Los Angeles School District',
  externalSource: 'String',
  principalEmail: 'AmyR@fabrikam.com',
  principalName: 'Amy Roebuck',
  externalPrincipalId: '14007',
  highestGrade: '12',
  lowestGrade: '9',
  schoolNumber: '10002',
  address: {
    city: 'Los Angeles',
    countryOrRegion: 'United States',
    postalCode: '98055',
    state: 'CA',
    street: '12345 Main St.'
  },
  externalId: '10002',
  phone: '+1 (253) 555-0102',
};

await client.api('/education/schools')
	.version('beta')
	.post(educationSchool);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\EducationSchool;
use Microsoft\Graph\Beta\Generated\Models\EducationExternalSource;
use Microsoft\Graph\Beta\Generated\Models\PhysicalAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationSchool();
$requestBody->setDisplayName('Fabrikam High School');
$requestBody->setDescription('Magnate school for the arts. Los Angeles School District');
$requestBody->setExternalSource(new EducationExternalSource('string'));
$requestBody->setPrincipalEmail('AmyR@fabrikam.com');
$requestBody->setPrincipalName('Amy Roebuck');
$requestBody->setExternalPrincipalId('14007');
$requestBody->setHighestGrade('12');
$requestBody->setLowestGrade('9');
$requestBody->setSchoolNumber('10002');
$address = new PhysicalAddress();
$address->setCity('Los Angeles');
$address->setCountryOrRegion('United States');
$address->setPostalCode('98055');
$address->setState('CA');
$address->setStreet('12345 Main St.');
$requestBody->setAddress($address);
$requestBody->setExternalId('10002');
$requestBody->setPhone('+1 (253) 555-0102');

$result = $graphServiceClient->education()->schools()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Education

$params = @{
	displayName = "Fabrikam High School"
	description = "Magnate school for the arts. Los Angeles School District"
	externalSource = "String"
	principalEmail = "AmyR@fabrikam.com"
	principalName = "Amy Roebuck"
	externalPrincipalId = "14007"
	highestGrade = "12"
	lowestGrade = "9"
	schoolNumber = "10002"
	address = @{
		city = "Los Angeles"
		countryOrRegion = "United States"
		postalCode = "98055"
		state = "CA"
		street = "12345 Main St."
	}
	externalId = "10002"
	phone = "+1 (253) 555-0102"
}

New-MgBetaEducationSchool -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.education_school import EducationSchool
from msgraph_beta.generated.models.education_external_source import EducationExternalSource
from msgraph_beta.generated.models.physical_address import PhysicalAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationSchool(
	display_name = "Fabrikam High School",
	description = "Magnate school for the arts. Los Angeles School District",
	external_source = EducationExternalSource.Sis,
	principal_email = "AmyR@fabrikam.com",
	principal_name = "Amy Roebuck",
	external_principal_id = "14007",
	highest_grade = "12",
	lowest_grade = "9",
	school_number = "10002",
	address = PhysicalAddress(
		city = "Los Angeles",
		country_or_region = "United States",
		postal_code = "98055",
		state = "CA",
		street = "12345 Main St.",
	),
	external_id = "10002",
	phone = "+1 (253) 555-0102",
)

result = await graph_client.education.schools.post(request_body)
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
  "id": "10002",
  "displayName": "Fabrikam High School",
  "description": "Magnate school for the arts. Los Angeles School District",
  "externalSource": "String",
  "principalEmail": "AmyR@fabrikam.com",
  "principalName": "Amy Roebuck",
  "externalPrincipalId": "14007",
  "highestGrade": "12",
  "lowestGrade": "9",
  "schoolNumber": "10002",
  "address": {
    "city": "Los Angeles",
    "countryOrRegion": "United States",
    "postalCode": "98055",
    "state": "CA",
    "street": "12345 Main St."
  },
  "createdBy": {
    "user": {
      "displayName": "Susana Rocha",
      "id": "14012",
    }
  },
  "externalId": "10002",
  "phone": "+1 (253) 555-0102",
}
```
