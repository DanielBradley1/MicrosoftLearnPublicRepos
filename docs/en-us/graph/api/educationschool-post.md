<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationschool-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Create educationSchool

Namespace: microsoft.graph

Create a new [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object.

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

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the school. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). |
| description | String | Description of the school. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). |
| externalSource | educationExternalSource | Source where this organization was created from. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). The possible values are: `sis`, `manual. |
| externalSourceDetail | String | The name of the external source this resources was generated from. |
| principalEmail | String | Email address of the principal. |
| principalName | String | Name of the principal. |
| externalPrincipalId | String | ID of principal in syncing system. |
| highestGrade | String | Highest grade taught. |
| lowestGrade | String | Lowest grade taught. |
| schoolNumber | String | School Number. |
| externalId | String | ID of school in syncing system. |
| phone | String | Phone number of school. |
| fax | String | Fax number of school. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Entity who created the school. |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | Address of the school. |

## Response

If successful, this method returns a `201 Created` response code and an [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/education/schools
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.educationSchool",
  "displayName": "String",
  "description": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "principalEmail": "String",
  "principalName": "String",
  "externalPrincipalId": "String",
  "lowestGrade": "String",
  "highestGrade": "String",
  "schoolNumber": "String",
  "externalId": "String",
  "phone": "String",
  "fax": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "address": {
    "@odata.type": "microsoft.graph.physicalAddress"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationSchool
{
	OdataType = "#microsoft.graph.educationSchool",
	DisplayName = "String",
	Description = "String",
	ExternalSource = EducationExternalSource.Sis,
	ExternalSourceDetail = "String",
	PrincipalEmail = "String",
	PrincipalName = "String",
	ExternalPrincipalId = "String",
	LowestGrade = "String",
	HighestGrade = "String",
	SchoolNumber = "String",
	ExternalId = "String",
	Phone = "String",
	Fax = "String",
	CreatedBy = new IdentitySet
	{
		OdataType = "microsoft.graph.identitySet",
	},
	Address = new PhysicalAddress
	{
		OdataType = "microsoft.graph.physicalAddress",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Schools.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewEducationSchool()
displayName := "String"
requestBody.SetDisplayName(&displayName) 
description := "String"
requestBody.SetDescription(&description) 
externalSource := graphmodels.STRING_EDUCATIONEXTERNALSOURCE 
requestBody.SetExternalSource(&externalSource) 
externalSourceDetail := "String"
requestBody.SetExternalSourceDetail(&externalSourceDetail) 
principalEmail := "String"
requestBody.SetPrincipalEmail(&principalEmail) 
principalName := "String"
requestBody.SetPrincipalName(&principalName) 
externalPrincipalId := "String"
requestBody.SetExternalPrincipalId(&externalPrincipalId) 
lowestGrade := "String"
requestBody.SetLowestGrade(&lowestGrade) 
highestGrade := "String"
requestBody.SetHighestGrade(&highestGrade) 
schoolNumber := "String"
requestBody.SetSchoolNumber(&schoolNumber) 
externalId := "String"
requestBody.SetExternalId(&externalId) 
phone := "String"
requestBody.SetPhone(&phone) 
fax := "String"
requestBody.SetFax(&fax) 
createdBy := graphmodels.NewIdentitySet()
requestBody.SetCreatedBy(createdBy)
address := graphmodels.NewPhysicalAddress()
requestBody.SetAddress(address)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
schools, err := graphClient.Education().Schools().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationSchool educationSchool = new EducationSchool();
educationSchool.setOdataType("#microsoft.graph.educationSchool");
educationSchool.setDisplayName("String");
educationSchool.setDescription("String");
educationSchool.setExternalSource(EducationExternalSource.Sis);
educationSchool.setExternalSourceDetail("String");
educationSchool.setPrincipalEmail("String");
educationSchool.setPrincipalName("String");
educationSchool.setExternalPrincipalId("String");
educationSchool.setLowestGrade("String");
educationSchool.setHighestGrade("String");
educationSchool.setSchoolNumber("String");
educationSchool.setExternalId("String");
educationSchool.setPhone("String");
educationSchool.setFax("String");
IdentitySet createdBy = new IdentitySet();
createdBy.setOdataType("microsoft.graph.identitySet");
educationSchool.setCreatedBy(createdBy);
PhysicalAddress address = new PhysicalAddress();
address.setOdataType("microsoft.graph.physicalAddress");
educationSchool.setAddress(address);
EducationSchool result = graphClient.education().schools().post(educationSchool);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationSchool = {
  '@odata.type': '#microsoft.graph.educationSchool',
  displayName: 'String',
  description: 'String',
  externalSource: 'String',
  externalSourceDetail: 'String',
  principalEmail: 'String',
  principalName: 'String',
  externalPrincipalId: 'String',
  lowestGrade: 'String',
  highestGrade: 'String',
  schoolNumber: 'String',
  externalId: 'String',
  phone: 'String',
  fax: 'String',
  createdBy: {
    '@odata.type': 'microsoft.graph.identitySet'
  },
  address: {
    '@odata.type': 'microsoft.graph.physicalAddress'
  }
};

await client.api('/education/schools')
	.post(educationSchool);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationSchool;
use Microsoft\Graph\Generated\Models\EducationExternalSource;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\PhysicalAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationSchool();
$requestBody->setOdataType('#microsoft.graph.educationSchool');
$requestBody->setDisplayName('String');
$requestBody->setDescription('String');
$requestBody->setExternalSource(new EducationExternalSource('string'));
$requestBody->setExternalSourceDetail('String');
$requestBody->setPrincipalEmail('String');
$requestBody->setPrincipalName('String');
$requestBody->setExternalPrincipalId('String');
$requestBody->setLowestGrade('String');
$requestBody->setHighestGrade('String');
$requestBody->setSchoolNumber('String');
$requestBody->setExternalId('String');
$requestBody->setPhone('String');
$requestBody->setFax('String');
$createdBy = new IdentitySet();
$createdBy->setOdataType('microsoft.graph.identitySet');
$requestBody->setCreatedBy($createdBy);
$address = new PhysicalAddress();
$address->setOdataType('microsoft.graph.physicalAddress');
$requestBody->setAddress($address);

$result = $graphServiceClient->education()->schools()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	"@odata.type" = "#microsoft.graph.educationSchool"
	displayName = "String"
	description = "String"
	externalSource = "String"
	externalSourceDetail = "String"
	principalEmail = "String"
	principalName = "String"
	externalPrincipalId = "String"
	lowestGrade = "String"
	highestGrade = "String"
	schoolNumber = "String"
	externalId = "String"
	phone = "String"
	fax = "String"
	createdBy = @{
		"@odata.type" = "microsoft.graph.identitySet"
	}
	address = @{
		"@odata.type" = "microsoft.graph.physicalAddress"
	}
}

New-MgEducationSchool -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_school import EducationSchool
from msgraph.generated.models.education_external_source import EducationExternalSource
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.physical_address import PhysicalAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationSchool(
	odata_type = "#microsoft.graph.educationSchool",
	display_name = "String",
	description = "String",
	external_source = EducationExternalSource.Sis,
	external_source_detail = "String",
	principal_email = "String",
	principal_name = "String",
	external_principal_id = "String",
	lowest_grade = "String",
	highest_grade = "String",
	school_number = "String",
	external_id = "String",
	phone = "String",
	fax = "String",
	created_by = IdentitySet(
		odata_type = "microsoft.graph.identitySet",
	),
	address = PhysicalAddress(
		odata_type = "microsoft.graph.physicalAddress",
	),
)

result = await graph_client.education.schools.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.educationSchool",
  "id": "1c23c12e-c12e-1c23-2ec1-231c2ec1231c",
  "displayName": "String",
  "description": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "principalEmail": "String",
  "principalName": "String",
  "externalPrincipalId": "String",
  "lowestGrade": "String",
  "highestGrade": "String",
  "schoolNumber": "String",
  "externalId": "String",
  "phone": "String",
  "fax": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "address": {
    "@odata.type": "microsoft.graph.physicalAddress"
  }
}
```
