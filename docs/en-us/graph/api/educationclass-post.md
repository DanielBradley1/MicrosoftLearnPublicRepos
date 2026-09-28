<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationclass-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Create educationClass

Namespace: microsoft.graph

Create a new [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) object.

Note

This will also create a universal group. When you use this API to create a class, it will add special properties to the group, which will add features such as assignments and special handling within Microsoft Teams when teams are created using the group. Please note that this API only creates the universal group and doesn't create a team. Microsoft Teams provides a user interface for teachers to create teams for their own classes using the groups created by this API.

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
POST /education/classes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Object identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| displayName | String | Name of the class. |
| mailNickname | String | Mail name for sending email to all members, if this is enabled. |
| description | String | Description of the class. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Entity who created the class |
| classCode | String | Class code used by the school to identify the class. |
| externalName | String | Name of the class in the syncing system. |
| externalId | String | ID of the class from the syncing system. |
| externalSource | educationExternalSource | How this class was created. The possible values are: `sis`, `manual` |
| externalSourceDetail | String | The name of the external source this resources was generated from. |
| grade | String | Grade level of the class. |
| term | [educationTerm](https://learn.microsoft.com/en-us/graph/api/resources/educationterm?view=graph-rest-1.0) | Term for this class. |

## Response

If successful, this method returns a `201 Created` response code and an [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/education/classes
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.educationClass",
  "displayName": "String",
  "mailNickname": "String",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "classCode": "String",
  "externalName": "String",
  "externalId": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "grade": "String",
  "term": {
    "@odata.type": "microsoft.graph.educationTerm"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationClass
{
	OdataType = "#microsoft.graph.educationClass",
	DisplayName = "String",
	MailNickname = "String",
	Description = "String",
	CreatedBy = new IdentitySet
	{
		OdataType = "microsoft.graph.identitySet",
	},
	ClassCode = "String",
	ExternalName = "String",
	ExternalId = "String",
	ExternalSource = EducationExternalSource.Sis,
	ExternalSourceDetail = "String",
	Grade = "String",
	Term = new EducationTerm
	{
		OdataType = "microsoft.graph.educationTerm",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationClass()
displayName := "String"
requestBody.SetDisplayName(&displayName) 
mailNickname := "String"
requestBody.SetMailNickname(&mailNickname) 
description := "String"
requestBody.SetDescription(&description) 
createdBy := graphmodels.NewIdentitySet()
requestBody.SetCreatedBy(createdBy)
classCode := "String"
requestBody.SetClassCode(&classCode) 
externalName := "String"
requestBody.SetExternalName(&externalName) 
externalId := "String"
requestBody.SetExternalId(&externalId) 
externalSource := graphmodels.STRING_EDUCATIONEXTERNALSOURCE 
requestBody.SetExternalSource(&externalSource) 
externalSourceDetail := "String"
requestBody.SetExternalSourceDetail(&externalSourceDetail) 
grade := "String"
requestBody.SetGrade(&grade) 
term := graphmodels.NewEducationTerm()
requestBody.SetTerm(term)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
classes, err := graphClient.Education().Classes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationClass educationClass = new EducationClass();
educationClass.setOdataType("#microsoft.graph.educationClass");
educationClass.setDisplayName("String");
educationClass.setMailNickname("String");
educationClass.setDescription("String");
IdentitySet createdBy = new IdentitySet();
createdBy.setOdataType("microsoft.graph.identitySet");
educationClass.setCreatedBy(createdBy);
educationClass.setClassCode("String");
educationClass.setExternalName("String");
educationClass.setExternalId("String");
educationClass.setExternalSource(EducationExternalSource.Sis);
educationClass.setExternalSourceDetail("String");
educationClass.setGrade("String");
EducationTerm term = new EducationTerm();
term.setOdataType("microsoft.graph.educationTerm");
educationClass.setTerm(term);
EducationClass result = graphClient.education().classes().post(educationClass);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationClass = {
  '@odata.type': '#microsoft.graph.educationClass',
  displayName: 'String',
  mailNickname: 'String',
  description: 'String',
  createdBy: {
    '@odata.type': 'microsoft.graph.identitySet'
  },
  classCode: 'String',
  externalName: 'String',
  externalId: 'String',
  externalSource: 'String',
  externalSourceDetail: 'String',
  grade: 'String',
  term: {
    '@odata.type': 'microsoft.graph.educationTerm'
  }
};

await client.api('/education/classes')
	.post(educationClass);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationClass;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\EducationExternalSource;
use Microsoft\Graph\Generated\Models\EducationTerm;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationClass();
$requestBody->setOdataType('#microsoft.graph.educationClass');
$requestBody->setDisplayName('String');
$requestBody->setMailNickname('String');
$requestBody->setDescription('String');
$createdBy = new IdentitySet();
$createdBy->setOdataType('microsoft.graph.identitySet');
$requestBody->setCreatedBy($createdBy);
$requestBody->setClassCode('String');
$requestBody->setExternalName('String');
$requestBody->setExternalId('String');
$requestBody->setExternalSource(new EducationExternalSource('string'));
$requestBody->setExternalSourceDetail('String');
$requestBody->setGrade('String');
$term = new EducationTerm();
$term->setOdataType('microsoft.graph.educationTerm');
$requestBody->setTerm($term);

$result = $graphServiceClient->education()->classes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	"@odata.type" = "#microsoft.graph.educationClass"
	displayName = "String"
	mailNickname = "String"
	description = "String"
	createdBy = @{
		"@odata.type" = "microsoft.graph.identitySet"
	}
	classCode = "String"
	externalName = "String"
	externalId = "String"
	externalSource = "String"
	externalSourceDetail = "String"
	grade = "String"
	term = @{
		"@odata.type" = "microsoft.graph.educationTerm"
	}
}

New-MgEducationClass -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_class import EducationClass
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.education_external_source import EducationExternalSource
from msgraph.generated.models.education_term import EducationTerm
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationClass(
	odata_type = "#microsoft.graph.educationClass",
	display_name = "String",
	mail_nickname = "String",
	description = "String",
	created_by = IdentitySet(
		odata_type = "microsoft.graph.identitySet",
	),
	class_code = "String",
	external_name = "String",
	external_id = "String",
	external_source = EducationExternalSource.Sis,
	external_source_detail = "String",
	grade = "String",
	term = EducationTerm(
		odata_type = "microsoft.graph.educationTerm",
	),
)

result = await graph_client.education.classes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.educationClass",
  "id": "64ef8ce5-8ce5-64ef-e58c-ef64e58cef64",
  "displayName": "String",
  "mailNickname": "String",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "classCode": "String",
  "externalName": "String",
  "externalId": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "grade": "String",
  "term": {
    "@odata.type": "microsoft.graph.educationTerm"
  }
}
```
