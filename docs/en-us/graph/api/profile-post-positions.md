<!-- Source: https://learn.microsoft.com/en-us/graph/api/profile-post-positions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-15 -->

# Create workPosition

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Use this API to create a new [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

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
POST /me/profile/positions
POST /users/{id | userPrincipalName}/profile/positions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) object.

The following table shows the properties that are possible to set when you create a new [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) object in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| categories | String collection | Categories that the user has associated with this position. |
| colleagues | [relatedPerson](https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta) collection | Colleagues that are associated with this position. |
| detail | [positionDetail](https://learn.microsoft.com/en-us/graph/api/resources/positiondetail?view=graph-rest-beta) | Contains detailed information about the position. |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| isCurrent | Boolean | Denotes whether or not the position is current. |
| manager | [relatedPerson](https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta) | Contains detail of the user's manager in this position. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |

## Response

If successful, this method returns `201, Created` response code and a new [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/me/profile/positions
Content-type: application/json

{
  "detail": {
    "company": {
      "displayName": "Adventureworks Ltd.",
      "department": "Consulting",
      "officeLocation": "AW23/344",
      "address": {
        "type": "business",
        "street": "123 Patriachy Ponds",
        "city": "Moscow",
        "countryOrRegion": "Russian Federation",
        "postalCode": "RU-34621"
      },
      "webUrl": "https://www.adventureworks.com"
    },
    "jobTitle": "Senior Product Branding Manager II",
    "role": "consulting"
  },
  "isCurrent": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new WorkPosition
{
	Detail = new PositionDetail
	{
		Company = new CompanyDetail
		{
			DisplayName = "Adventureworks Ltd.",
			Department = "Consulting",
			OfficeLocation = "AW23/344",
			Address = new PhysicalAddress
			{
				Type = PhysicalAddressType.Business,
				Street = "123 Patriachy Ponds",
				City = "Moscow",
				CountryOrRegion = "Russian Federation",
				PostalCode = "RU-34621",
			},
			WebUrl = "https://www.adventureworks.com",
		},
		JobTitle = "Senior Product Branding Manager II",
		Role = "consulting",
	},
	IsCurrent = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Profile.Positions.PostAsync(requestBody);
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

requestBody := graphmodels.NewWorkPosition()
detail := graphmodels.NewPositionDetail()
company := graphmodels.NewCompanyDetail()
displayName := "Adventureworks Ltd."
company.SetDisplayName(&displayName) 
department := "Consulting"
company.SetDepartment(&department) 
officeLocation := "AW23/344"
company.SetOfficeLocation(&officeLocation) 
address := graphmodels.NewPhysicalAddress()
type := graphmodels.BUSINESS_PHYSICALADDRESSTYPE 
address.SetType(&type) 
street := "123 Patriachy Ponds"
address.SetStreet(&street) 
city := "Moscow"
address.SetCity(&city) 
countryOrRegion := "Russian Federation"
address.SetCountryOrRegion(&countryOrRegion) 
postalCode := "RU-34621"
address.SetPostalCode(&postalCode) 
company.SetAddress(address)
webUrl := "https://www.adventureworks.com"
company.SetWebUrl(&webUrl) 
detail.SetCompany(company)
jobTitle := "Senior Product Branding Manager II"
detail.SetJobTitle(&jobTitle) 
role := "consulting"
detail.SetRole(&role) 
requestBody.SetDetail(detail)
isCurrent := true
requestBody.SetIsCurrent(&isCurrent) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
positions, err := graphClient.Me().Profile().Positions().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WorkPosition workPosition = new WorkPosition();
PositionDetail detail = new PositionDetail();
CompanyDetail company = new CompanyDetail();
company.setDisplayName("Adventureworks Ltd.");
company.setDepartment("Consulting");
company.setOfficeLocation("AW23/344");
PhysicalAddress address = new PhysicalAddress();
address.setType(PhysicalAddressType.Business);
address.setStreet("123 Patriachy Ponds");
address.setCity("Moscow");
address.setCountryOrRegion("Russian Federation");
address.setPostalCode("RU-34621");
company.setAddress(address);
company.setWebUrl("https://www.adventureworks.com");
detail.setCompany(company);
detail.setJobTitle("Senior Product Branding Manager II");
detail.setRole("consulting");
workPosition.setDetail(detail);
workPosition.setIsCurrent(true);
WorkPosition result = graphClient.me().profile().positions().post(workPosition);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workPosition = {
  detail: {
    company: {
      displayName: 'Adventureworks Ltd.',
      department: 'Consulting',
      officeLocation: 'AW23/344',
      address: {
        type: 'business',
        street: '123 Patriachy Ponds',
        city: 'Moscow',
        countryOrRegion: 'Russian Federation',
        postalCode: 'RU-34621'
      },
      webUrl: 'https://www.adventureworks.com'
    },
    jobTitle: 'Senior Product Branding Manager II',
    role: 'consulting'
  },
  isCurrent: true
};

await client.api('/me/profile/positions')
	.version('beta')
	.post(workPosition);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WorkPosition;
use Microsoft\Graph\Beta\Generated\Models\PositionDetail;
use Microsoft\Graph\Beta\Generated\Models\CompanyDetail;
use Microsoft\Graph\Beta\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Beta\Generated\Models\PhysicalAddressType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WorkPosition();
$detail = new PositionDetail();
$detailCompany = new CompanyDetail();
$detailCompany->setDisplayName('Adventureworks Ltd.');
$detailCompany->setDepartment('Consulting');
$detailCompany->setOfficeLocation('AW23/344');
$detailCompanyAddress = new PhysicalAddress();
$detailCompanyAddress->setType(new PhysicalAddressType('business'));
$detailCompanyAddress->setStreet('123 Patriachy Ponds');
$detailCompanyAddress->setCity('Moscow');
$detailCompanyAddress->setCountryOrRegion('Russian Federation');
$detailCompanyAddress->setPostalCode('RU-34621');
$detailCompany->setAddress($detailCompanyAddress);
$detailCompany->setWebUrl('https://www.adventureworks.com');
$detail->setCompany($detailCompany);
$detail->setJobTitle('Senior Product Branding Manager II');
$detail->setRole('consulting');
$requestBody->setDetail($detail);
$requestBody->setIsCurrent(true);

$result = $graphServiceClient->me()->profile()->positions()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.People

$params = @{
	detail = @{
		company = @{
			displayName = "Adventureworks Ltd."
			department = "Consulting"
			officeLocation = "AW23/344"
			address = @{
				type = "business"
				street = "123 Patriachy Ponds"
				city = "Moscow"
				countryOrRegion = "Russian Federation"
				postalCode = "RU-34621"
			}
			webUrl = "https://www.adventureworks.com"
		}
		jobTitle = "Senior Product Branding Manager II"
		role = "consulting"
	}
	isCurrent = $true
}

# A UPN can also be used as -UserId.
New-MgBetaUserProfilePosition -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.work_position import WorkPosition
from msgraph_beta.generated.models.position_detail import PositionDetail
from msgraph_beta.generated.models.company_detail import CompanyDetail
from msgraph_beta.generated.models.physical_address import PhysicalAddress
from msgraph_beta.generated.models.physical_address_type import PhysicalAddressType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WorkPosition(
	detail = PositionDetail(
		company = CompanyDetail(
			display_name = "Adventureworks Ltd.",
			department = "Consulting",
			office_location = "AW23/344",
			address = PhysicalAddress(
				type = PhysicalAddressType.Business,
				street = "123 Patriachy Ponds",
				city = "Moscow",
				country_or_region = "Russian Federation",
				postal_code = "RU-34621",
			),
			web_url = "https://www.adventureworks.com",
		),
		job_title = "Senior Product Branding Manager II",
		role = "consulting",
	),
	is_current = True,
)

result = await graph_client.me.profile.positions.post(request_body)
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
  "categories": null,
  "detail": {
    "company": {
      "displayName": "Adventureworks Ltd.",
      "pronunciation": null,
      "department": "Consulting",
      "companyCode": null,
      "officeLocation": "AW23/344",
      "address": {
        "type": "business",
        "postOfficeBox": null,
        "street": "123 Patriachy Ponds",
        "city": "Moscow",
        "state": null,
        "countryOrRegion": "Russian Federation",
        "postalCode": "RU-34621"
      },
      "webUrl": "https://www.adventureworks.com"
    },
    "description": null,
    "endMonthYear": null,
    "jobTitle": "Senior Product Branding Manager II",
    "role": "consulting",
    "startMonthYear": "datetime-value",
    "summary": null
  },
  "manager": null,
  "colleagues": null,
  "isCurrent": true
}
```
