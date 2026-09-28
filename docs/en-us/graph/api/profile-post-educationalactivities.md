<!-- Source: https://learn.microsoft.com/en-us/graph/api/profile-post-educationalactivities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Create educationalActivity

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.ReadWrite | AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | User.ReadWrite | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/profile/educationalActivities
POST /users/{id | userPrincipalName}/profile/educationalActivities
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) object.

The following table shows the properties that are possible to set when creating a new [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) object in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| completionMonthYear | Date | The month and year the user graduated or completed the activity. |
| endMonthYear | Date | The month and year the user completed the educational activity referenced. |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| institution | [institutionData](https://learn.microsoft.com/en-us/graph/api/resources/institutiondata?view=graph-rest-beta) | Contains details of the institution studied at. |
| program | [educationalActivityDetail](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivitydetail?view=graph-rest-beta) | Contains extended information about the program or course. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| startMonthYear | Date | The month and year the user commenced the activity referenced. |

## Response

If successful, this method returns a `201 Created` response code and a new [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/me/profile/educationalActivities
Content-type: application/json

{
  "completionMonthYear": "Date",
  "endMonthYear": "Date",
  "institution": {
    "description": null,
    "displayName": "Colorado State University",
    "location": {
      "type": "business",
      "postOfficeBox": null,
      "street": "12000 E Prospect Rd",
      "city": "Fort Collins",
      "state": "Colorado",
      "countryOrRegion": "USA",
      "postalCode": "80525"
    },
    "webUrl": "https://www.colostate.edu"
  },
  "program": {
    "abbreviation": "MBA",
    "activities": null,
    "awards": null,
    "description": "Master of Business Administration with a major in Entreprenuership and Finance.",
    "displayName": "Master of Business Administration",
    "fieldsOfStudy": null,
    "grade": "3.9",
    "notes": null,
    "webUrl": "https://biz.colostate.edu"
  },
  "startMonthYear": "Date"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new EducationalActivity
{
	CompletionMonthYear = new Date(DateTime.Parse("Date")),
	EndMonthYear = new Date(DateTime.Parse("Date")),
	Institution = new InstitutionData
	{
		Description = null,
		DisplayName = "Colorado State University",
		Location = new PhysicalAddress
		{
			Type = PhysicalAddressType.Business,
			PostOfficeBox = null,
			Street = "12000 E Prospect Rd",
			City = "Fort Collins",
			State = "Colorado",
			CountryOrRegion = "USA",
			PostalCode = "80525",
		},
		WebUrl = "https://www.colostate.edu",
	},
	Program = new EducationalActivityDetail
	{
		Abbreviation = "MBA",
		Activities = null,
		Awards = null,
		Description = "Master of Business Administration with a major in Entreprenuership and Finance.",
		DisplayName = "Master of Business Administration",
		FieldsOfStudy = null,
		Grade = "3.9",
		Notes = null,
		WebUrl = "https://biz.colostate.edu",
	},
	StartMonthYear = new Date(DateTime.Parse("Date")),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Profile.EducationalActivities.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationalActivity()
completionMonthYear := date
requestBody.SetCompletionMonthYear(&completionMonthYear) 
endMonthYear := date
requestBody.SetEndMonthYear(&endMonthYear) 
institution := graphmodels.NewInstitutionData()
description := null
institution.SetDescription(&description) 
displayName := "Colorado State University"
institution.SetDisplayName(&displayName) 
location := graphmodels.NewPhysicalAddress()
type := graphmodels.BUSINESS_PHYSICALADDRESSTYPE 
location.SetType(&type) 
postOfficeBox := null
location.SetPostOfficeBox(&postOfficeBox) 
street := "12000 E Prospect Rd"
location.SetStreet(&street) 
city := "Fort Collins"
location.SetCity(&city) 
state := "Colorado"
location.SetState(&state) 
countryOrRegion := "USA"
location.SetCountryOrRegion(&countryOrRegion) 
postalCode := "80525"
location.SetPostalCode(&postalCode) 
institution.SetLocation(location)
webUrl := "https://www.colostate.edu"
institution.SetWebUrl(&webUrl) 
requestBody.SetInstitution(institution)
program := graphmodels.NewEducationalActivityDetail()
abbreviation := "MBA"
program.SetAbbreviation(&abbreviation) 
activities := null
program.SetActivities(&activities) 
awards := null
program.SetAwards(&awards) 
description := "Master of Business Administration with a major in Entreprenuership and Finance."
program.SetDescription(&description) 
displayName := "Master of Business Administration"
program.SetDisplayName(&displayName) 
fieldsOfStudy := null
program.SetFieldsOfStudy(&fieldsOfStudy) 
grade := "3.9"
program.SetGrade(&grade) 
notes := null
program.SetNotes(&notes) 
webUrl := "https://biz.colostate.edu"
program.SetWebUrl(&webUrl) 
requestBody.SetProgram(program)
startMonthYear := date
requestBody.SetStartMonthYear(&startMonthYear) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
educationalActivities, err := graphClient.Me().Profile().EducationalActivities().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationalActivity educationalActivity = new EducationalActivity();
LocalDate completionMonthYear = LocalDate.parse("Date");
educationalActivity.setCompletionMonthYear(completionMonthYear);
LocalDate endMonthYear = LocalDate.parse("Date");
educationalActivity.setEndMonthYear(endMonthYear);
InstitutionData institution = new InstitutionData();
institution.setDescription(null);
institution.setDisplayName("Colorado State University");
PhysicalAddress location = new PhysicalAddress();
location.setType(PhysicalAddressType.Business);
location.setPostOfficeBox(null);
location.setStreet("12000 E Prospect Rd");
location.setCity("Fort Collins");
location.setState("Colorado");
location.setCountryOrRegion("USA");
location.setPostalCode("80525");
institution.setLocation(location);
institution.setWebUrl("https://www.colostate.edu");
educationalActivity.setInstitution(institution);
EducationalActivityDetail program = new EducationalActivityDetail();
program.setAbbreviation("MBA");
program.setActivities(null);
program.setAwards(null);
program.setDescription("Master of Business Administration with a major in Entreprenuership and Finance.");
program.setDisplayName("Master of Business Administration");
program.setFieldsOfStudy(null);
program.setGrade("3.9");
program.setNotes(null);
program.setWebUrl("https://biz.colostate.edu");
educationalActivity.setProgram(program);
LocalDate startMonthYear = LocalDate.parse("Date");
educationalActivity.setStartMonthYear(startMonthYear);
EducationalActivity result = graphClient.me().profile().educationalActivities().post(educationalActivity);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationalActivity = {
  completionMonthYear: 'Date',
  endMonthYear: 'Date',
  institution: {
    description: null,
    displayName: 'Colorado State University',
    location: {
      type: 'business',
      postOfficeBox: null,
      street: '12000 E Prospect Rd',
      city: 'Fort Collins',
      state: 'Colorado',
      countryOrRegion: 'USA',
      postalCode: '80525'
    },
    webUrl: 'https://www.colostate.edu'
  },
  program: {
    abbreviation: 'MBA',
    activities: null,
    awards: null,
    description: 'Master of Business Administration with a major in Entreprenuership and Finance.',
    displayName: 'Master of Business Administration',
    fieldsOfStudy: null,
    grade: '3.9',
    notes: null,
    webUrl: 'https://biz.colostate.edu'
  },
  startMonthYear: 'Date'
};

await client.api('/me/profile/educationalActivities')
	.version('beta')
	.post(educationalActivity);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\EducationalActivity;
use Microsoft\Kiota\Abstractions\Types\Date;
use Microsoft\Graph\Beta\Generated\Models\InstitutionData;
use Microsoft\Graph\Beta\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Beta\Generated\Models\PhysicalAddressType;
use Microsoft\Graph\Beta\Generated\Models\EducationalActivityDetail;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationalActivity();
$requestBody->setCompletionMonthYear(new Date('Date'));
$requestBody->setEndMonthYear(new Date('Date'));
$institution = new InstitutionData();
$institution->setDescription(null);
$institution->setDisplayName('Colorado State University');
$institutionLocation = new PhysicalAddress();
$institutionLocation->setType(new PhysicalAddressType('business'));
$institutionLocation->setPostOfficeBox(null);
$institutionLocation->setStreet('12000 E Prospect Rd');
$institutionLocation->setCity('Fort Collins');
$institutionLocation->setState('Colorado');
$institutionLocation->setCountryOrRegion('USA');
$institutionLocation->setPostalCode('80525');
$institution->setLocation($institutionLocation);
$institution->setWebUrl('https://www.colostate.edu');
$requestBody->setInstitution($institution);
$program = new EducationalActivityDetail();
$program->setAbbreviation('MBA');
$program->setActivities(null);
$program->setAwards(null);
$program->setDescription('Master of Business Administration with a major in Entreprenuership and Finance.');
$program->setDisplayName('Master of Business Administration');
$program->setFieldsOfStudy(null);
$program->setGrade('3.9');
$program->setNotes(null);
$program->setWebUrl('https://biz.colostate.edu');
$requestBody->setProgram($program);
$requestBody->setStartMonthYear(new Date('Date'));

$result = $graphServiceClient->me()->profile()->educationalActivities()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.People

$params = @{
	completionMonthYear = "Date"
	endMonthYear = "Date"
	institution = @{
		description = $null
		displayName = "Colorado State University"
		location = @{
			type = "business"
			postOfficeBox = $null
			street = "12000 E Prospect Rd"
			city = "Fort Collins"
			state = "Colorado"
			countryOrRegion = "USA"
			postalCode = "80525"
		}
		webUrl = "https://www.colostate.edu"
	}
	program = @{
		abbreviation = "MBA"
		activities = $null
		awards = $null
		description = "Master of Business Administration with a major in Entreprenuership and Finance."
		displayName = "Master of Business Administration"
		fieldsOfStudy = $null
		grade = "3.9"
		notes = $null
		webUrl = "https://biz.colostate.edu"
	}
	startMonthYear = "Date"
}

# A UPN can also be used as -UserId.
New-MgBetaUserProfileEducationalActivity -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.educational_activity import EducationalActivity
from msgraph_beta.generated.models.institution_data import InstitutionData
from msgraph_beta.generated.models.physical_address import PhysicalAddress
from msgraph_beta.generated.models.physical_address_type import PhysicalAddressType
from msgraph_beta.generated.models.educational_activity_detail import EducationalActivityDetail
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationalActivity(
	completion_month_year = "Date",
	end_month_year = "Date",
	institution = InstitutionData(
		description = None,
		display_name = "Colorado State University",
		location = PhysicalAddress(
			type = PhysicalAddressType.Business,
			post_office_box = None,
			street = "12000 E Prospect Rd",
			city = "Fort Collins",
			state = "Colorado",
			country_or_region = "USA",
			postal_code = "80525",
		),
		web_url = "https://www.colostate.edu",
	),
	program = EducationalActivityDetail(
		abbreviation = "MBA",
		activities = None,
		awards = None,
		description = "Master of Business Administration with a major in Entreprenuership and Finance.",
		display_name = "Master of Business Administration",
		fields_of_study = None,
		grade = "3.9",
		notes = None,
		web_url = "https://biz.colostate.edu",
	),
	start_month_year = "Date",
)

result = await graph_client.me.profile.educational_activities.post(request_body)
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
  "id": "0fb4c1e3-c1e3-0fb4-e3c1-b40fe3c1b40f",
  "allowedAudiences": "organization",
  "inference": null,
  "createdDateTime": "2020-07-06T06:34:12.2294868Z",
  "createdBy": {
    "application": null,
    "device": null,
    "user": {
      "displayName": "Innocenty Popov",
      "id": "db789417-4ccb-41d1-a0a9-47b01a09ea49"
    }
  },
  "lastModifiedDateTime": "2020-07-06T06:34:12.2294868Z",
  "lastModifiedBy": {
    "application": null,
    "device": null,
    "user": {
      "displayName": "Innocenty Popov",
      "id": "db789417-4ccb-41d1-a0a9-47b01a09ea49"
    }
  },
  "source": null,
  "completionMonthYear": "Date",
  "endMonthYear": "Date",
  "institution": {
    "description": null,
    "displayName": "Colorado State University",
    "location": {
      "type": "business",
      "postOfficeBox": null,
      "street": "12000 E Prospect Rd",
      "city": "Fort Collins",
      "state": "Colorado",
      "countryOrRegion": "USA",
      "postalCode": "80525"
    },
    "webUrl": "https://www.colostate.edu"
  },
  "program": {
    "abbreviation": "MBA",
    "activities": null,
    "awards": null,
    "description": "Master of Business Administration with a major in Entreprenuership and Finance.",
    "displayName": "Master of Business Administration",
    "fieldsOfStudy": null,
    "grade": "3.9",
    "notes": null,
    "webUrl": "https://biz.colostate.edu"
  },
  "startMonthYear": "Date"
}
```
