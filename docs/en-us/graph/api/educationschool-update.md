<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationschool-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-26 -->

# Update educationSchool

Namespace: microsoft.graph

Update the properties of an [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object.

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
PATCH /education/schools/{id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of the [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object.

The following table shows the properties that are required when you update the [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the school. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). |
| description | String | Description of the school. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). |
| externalSource | educationExternalSource | Source where this organization was created from. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). The possible values are: `sis`, `manual`. |
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

If successful, this method returns a `200 OK` response code and an updated [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/education/schools/{school-id}
Content-type: application/json

{
  "displayName": "Fabrikam Arts High School",
  "description": "Magnate school for the arts. Los Angeles School District"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationSchool
{
	DisplayName = "Fabrikam Arts High School",
	Description = "Magnate school for the arts. Los Angeles School District",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Schools["{educationSchool-id}"].PatchAsync(requestBody);
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
displayName := "Fabrikam Arts High School"
requestBody.SetDisplayName(&displayName) 
description := "Magnate school for the arts. Los Angeles School District"
requestBody.SetDescription(&description) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
schools, err := graphClient.Education().Schools().ByEducationSchoolId("educationSchool-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationSchool educationSchool = new EducationSchool();
educationSchool.setDisplayName("Fabrikam Arts High School");
educationSchool.setDescription("Magnate school for the arts. Los Angeles School District");
EducationSchool result = graphClient.education().schools().byEducationSchoolId("{educationSchool-id}").patch(educationSchool);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationSchool = {
  displayName: 'Fabrikam Arts High School',
  description: 'Magnate school for the arts. Los Angeles School District'
};

await client.api('/education/schools/{school-id}')
	.update(educationSchool);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationSchool;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationSchool();
$requestBody->setDisplayName('Fabrikam Arts High School');
$requestBody->setDescription('Magnate school for the arts. Los Angeles School District');

$result = $graphServiceClient->education()->schools()->byEducationSchoolId('educationSchool-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	displayName = "Fabrikam Arts High School"
	description = "Magnate school for the arts. Los Angeles School District"
}

Update-MgEducationSchool -EducationSchoolId $educationSchoolId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_school import EducationSchool
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationSchool(
	display_name = "Fabrikam Arts High School",
	description = "Magnate school for the arts. Los Angeles School District",
)

result = await graph_client.education.schools.by_education_school_id('educationSchool-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "10002",
  "displayName": "Fabrikam Arts High School",
  "description": "Magnate school for the arts. Los Angeles School District",
  "status": "String",
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
  "phone": "+1 (253) 555-0102"
}
```
