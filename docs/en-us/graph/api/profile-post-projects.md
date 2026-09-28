<!-- Source: https://learn.microsoft.com/en-us/graph/api/profile-post-projects?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Create projectParticipation

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Use this API to create a new [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) object in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

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
POST /me/profile/projects
POST /users/{id | userPrincipalName}/profile/projects
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) object.

The following table shows the properties that are possible to set when you create a new [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) object in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| categories | String collection | Contains categories a user has associated with the project \(for example, digital transformation, oil rig\). |
| client | [companyDetail](https://learn.microsoft.com/en-us/graph/api/resources/companydetail?view=graph-rest-beta) | Contains detailed information about the client the project was for. |
| collaborationTags | String collection | Contains experience scenario tags a user has associated with the interest. Allowed values in the collection are: `askMeAbout`, `ableToMentor`, `wantsToLearn`, `wantsToImprove`. |
| colleagues | [relatedPerson](https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta) collection | Lists people that also worked on the project. |
| detail | [positionDetail](https://learn.microsoft.com/en-us/graph/api/resources/positiondetail?view=graph-rest-beta) | Contains detail about the user's role on the project. |
| displayName | String | Contains a friendly name for the project. |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| sponsors | [relatedPerson](https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta) collection | The Person or people who sponsored the project. |

## Relationships

## Response

If successful, this method returns `201, Created` response code and a new [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/me/profile/projects
Content-type: application/json

{
  "categories": [
    "Branding"
  ],
  "client": {
    "displayName": "Contoso Ltd.",
    "department": "Corporate Marketing",
    "webUrl": "https://www.contoso.com"
  },
  "displayName": "Contoso Re-branding Project",
  "detail": {
    "company": {
      "displayName": "Adventureworks Inc.",
      "department": "Consulting",
      "webUrl": "https://adventureworks.com"
    },
    "description": "Rebranding of Contoso Ltd.",
    "jobTitle": "Lead PM Rebranding",
    "role": "project management",
    "summary": "A 6 month project to help Contoso rebrand after they were divested from a parent organization."
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ProjectParticipation
{
	Categories = new List<string>
	{
		"Branding",
	},
	Client = new CompanyDetail
	{
		DisplayName = "Contoso Ltd.",
		Department = "Corporate Marketing",
		WebUrl = "https://www.contoso.com",
	},
	DisplayName = "Contoso Re-branding Project",
	Detail = new PositionDetail
	{
		Company = new CompanyDetail
		{
			DisplayName = "Adventureworks Inc.",
			Department = "Consulting",
			WebUrl = "https://adventureworks.com",
		},
		Description = "Rebranding of Contoso Ltd.",
		JobTitle = "Lead PM Rebranding",
		Role = "project management",
		Summary = "A 6 month project to help Contoso rebrand after they were divested from a parent organization.",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Profile.Projects.PostAsync(requestBody);
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

requestBody := graphmodels.NewProjectParticipation()
categories := []string {
	"Branding",
}
requestBody.SetCategories(categories)
client := graphmodels.NewCompanyDetail()
displayName := "Contoso Ltd."
client.SetDisplayName(&displayName) 
department := "Corporate Marketing"
client.SetDepartment(&department) 
webUrl := "https://www.contoso.com"
client.SetWebUrl(&webUrl) 
requestBody.SetClient(client)
displayName := "Contoso Re-branding Project"
requestBody.SetDisplayName(&displayName) 
detail := graphmodels.NewPositionDetail()
company := graphmodels.NewCompanyDetail()
displayName := "Adventureworks Inc."
company.SetDisplayName(&displayName) 
department := "Consulting"
company.SetDepartment(&department) 
webUrl := "https://adventureworks.com"
company.SetWebUrl(&webUrl) 
detail.SetCompany(company)
description := "Rebranding of Contoso Ltd."
detail.SetDescription(&description) 
jobTitle := "Lead PM Rebranding"
detail.SetJobTitle(&jobTitle) 
role := "project management"
detail.SetRole(&role) 
summary := "A 6 month project to help Contoso rebrand after they were divested from a parent organization."
detail.SetSummary(&summary) 
requestBody.SetDetail(detail)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
projects, err := graphClient.Me().Profile().Projects().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ProjectParticipation projectParticipation = new ProjectParticipation();
LinkedList<String> categories = new LinkedList<String>();
categories.add("Branding");
projectParticipation.setCategories(categories);
CompanyDetail client = new CompanyDetail();
client.setDisplayName("Contoso Ltd.");
client.setDepartment("Corporate Marketing");
client.setWebUrl("https://www.contoso.com");
projectParticipation.setClient(client);
projectParticipation.setDisplayName("Contoso Re-branding Project");
PositionDetail detail = new PositionDetail();
CompanyDetail company = new CompanyDetail();
company.setDisplayName("Adventureworks Inc.");
company.setDepartment("Consulting");
company.setWebUrl("https://adventureworks.com");
detail.setCompany(company);
detail.setDescription("Rebranding of Contoso Ltd.");
detail.setJobTitle("Lead PM Rebranding");
detail.setRole("project management");
detail.setSummary("A 6 month project to help Contoso rebrand after they were divested from a parent organization.");
projectParticipation.setDetail(detail);
ProjectParticipation result = graphClient.me().profile().projects().post(projectParticipation);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const projectParticipation = {
  categories: [
    'Branding'
  ],
  client: {
    displayName: 'Contoso Ltd.',
    department: 'Corporate Marketing',
    webUrl: 'https://www.contoso.com'
  },
  displayName: 'Contoso Re-branding Project',
  detail: {
    company: {
      displayName: 'Adventureworks Inc.',
      department: 'Consulting',
      webUrl: 'https://adventureworks.com'
    },
    description: 'Rebranding of Contoso Ltd.',
    jobTitle: 'Lead PM Rebranding',
    role: 'project management',
    summary: 'A 6 month project to help Contoso rebrand after they were divested from a parent organization.'
  }
};

await client.api('/me/profile/projects')
	.version('beta')
	.post(projectParticipation);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ProjectParticipation;
use Microsoft\Graph\Beta\Generated\Models\CompanyDetail;
use Microsoft\Graph\Beta\Generated\Models\PositionDetail;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ProjectParticipation();
$requestBody->setCategories(['Branding', 	]);
$client = new CompanyDetail();
$client->setDisplayName('Contoso Ltd.');
$client->setDepartment('Corporate Marketing');
$client->setWebUrl('https://www.contoso.com');
$requestBody->setClient($client);
$requestBody->setDisplayName('Contoso Re-branding Project');
$detail = new PositionDetail();
$detailCompany = new CompanyDetail();
$detailCompany->setDisplayName('Adventureworks Inc.');
$detailCompany->setDepartment('Consulting');
$detailCompany->setWebUrl('https://adventureworks.com');
$detail->setCompany($detailCompany);
$detail->setDescription('Rebranding of Contoso Ltd.');
$detail->setJobTitle('Lead PM Rebranding');
$detail->setRole('project management');
$detail->setSummary('A 6 month project to help Contoso rebrand after they were divested from a parent organization.');
$requestBody->setDetail($detail);

$result = $graphServiceClient->me()->profile()->projects()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.People

$params = @{
	categories = @(
	"Branding"
)
client = @{
	displayName = "Contoso Ltd."
	department = "Corporate Marketing"
	webUrl = "https://www.contoso.com"
}
displayName = "Contoso Re-branding Project"
detail = @{
	company = @{
		displayName = "Adventureworks Inc."
		department = "Consulting"
		webUrl = "https://adventureworks.com"
	}
	description = "Rebranding of Contoso Ltd."
	jobTitle = "Lead PM Rebranding"
	role = "project management"
	summary = "A 6 month project to help Contoso rebrand after they were divested from a parent organization."
}
}

# A UPN can also be used as -UserId.
New-MgBetaUserProfileProject -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.project_participation import ProjectParticipation
from msgraph_beta.generated.models.company_detail import CompanyDetail
from msgraph_beta.generated.models.position_detail import PositionDetail
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ProjectParticipation(
	categories = [
		"Branding",
	],
	client = CompanyDetail(
		display_name = "Contoso Ltd.",
		department = "Corporate Marketing",
		web_url = "https://www.contoso.com",
	),
	display_name = "Contoso Re-branding Project",
	detail = PositionDetail(
		company = CompanyDetail(
			display_name = "Adventureworks Inc.",
			department = "Consulting",
			web_url = "https://adventureworks.com",
		),
		description = "Rebranding of Contoso Ltd.",
		job_title = "Lead PM Rebranding",
		role = "project management",
		summary = "A 6 month project to help Contoso rebrand after they were divested from a parent organization.",
	),
)

result = await graph_client.me.profile.projects.post(request_body)
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
  "categories": [
    "Branding"
  ],
  "client": {
    "displayName": "Contoso Ltd.",
    "pronunciation": null,
    "department": "Corporate Marketing",
    "officeLocation": null,
    "address": null,
    "webUrl": "https://www.contoso.com"
  },
  "displayName": "Contoso Re-branding Project",
  "detail": {
    "company": {
      "displayName": "Adventureworks Inc.",
      "pronunciation": null,
      "department": "Consulting",
      "companyCode": "C-100",
      "officeLocation": null,
      "address": null,
      "webUrl": "https://adventureworks.com"
    },
    "description": "Rebranding of Contoso Ltd.",
    "endMonthYear": "datetime-value",
    "jobTitle": "Lead PM Rebranding",
    "role": "project management",
    "startMonthYear": "datetime-value",
    "summary": "A 6 month project to help Contoso rebrand after they were divested from a parent organization."
  },
  "colleagues": null,
  "sponsors": null
}
```
