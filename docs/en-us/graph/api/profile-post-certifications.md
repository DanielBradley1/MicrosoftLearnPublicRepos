<!-- Source: https://learn.microsoft.com/en-us/graph/api/profile-post-certifications?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# Create personCertification

Namespace: microsoft.graph

Create a new [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) object in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

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
POST /me/profile/certifications
POST /users/{id | userPrincipalName}/profile/certifications
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) object.

The following table shows the properties that are possible to set when creating a new [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) object in a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| certificationId | String | The referenceable identifier for the certification. |
| description | String | Description of the certification. |
| displayName | String | Title of the certification. |
| endDate | Date | The date that the certification expires. |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| issuedDate | Date | The date that the certification was issued. |
| issuingAuthority | String | Authority which granted the certification. |
| issuingCompany | String | Authority which granted the certification. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| startDate | Date | The date that the certification became valid. |
| thumbnailUrl | String | URL referencing a thumbnail of the certification. |
| webUrl | String | URL referencing the certification. |

## Response

If successful, this method returns a `201 Created` response code and an [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) object in the response body.

## Examples

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/me/profile/certifications
Content-Type: application/json

{
  "certificationId": "KB-1235466333663322",
  "description": "Blackbelt in Marketing - Brand Management",
  "displayName": "Marketing Blackbelt - Brand Management",
  "thumbnailUrl": "https://iame.io/dfhdfdfd334.jpg",
  "webUrl": "https://www.iame.io/blackbelt"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PersonCertification
{
	CertificationId = "KB-1235466333663322",
	Description = "Blackbelt in Marketing - Brand Management",
	DisplayName = "Marketing Blackbelt - Brand Management",
	ThumbnailUrl = "https://iame.io/dfhdfdfd334.jpg",
	WebUrl = "https://www.iame.io/blackbelt",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Profile.Certifications.PostAsync(requestBody);
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

requestBody := graphmodels.NewPersonCertification()
certificationId := "KB-1235466333663322"
requestBody.SetCertificationId(&certificationId) 
description := "Blackbelt in Marketing - Brand Management"
requestBody.SetDescription(&description) 
displayName := "Marketing Blackbelt - Brand Management"
requestBody.SetDisplayName(&displayName) 
thumbnailUrl := "https://iame.io/dfhdfdfd334.jpg"
requestBody.SetThumbnailUrl(&thumbnailUrl) 
webUrl := "https://www.iame.io/blackbelt"
requestBody.SetWebUrl(&webUrl) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
certifications, err := graphClient.Me().Profile().Certifications().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PersonCertification personCertification = new PersonCertification();
personCertification.setCertificationId("KB-1235466333663322");
personCertification.setDescription("Blackbelt in Marketing - Brand Management");
personCertification.setDisplayName("Marketing Blackbelt - Brand Management");
personCertification.setThumbnailUrl("https://iame.io/dfhdfdfd334.jpg");
personCertification.setWebUrl("https://www.iame.io/blackbelt");
PersonCertification result = graphClient.me().profile().certifications().post(personCertification);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const personCertification = {
  certificationId: 'KB-1235466333663322',
  description: 'Blackbelt in Marketing - Brand Management',
  displayName: 'Marketing Blackbelt - Brand Management',
  thumbnailUrl: 'https://iame.io/dfhdfdfd334.jpg',
  webUrl: 'https://www.iame.io/blackbelt'
};

await client.api('/me/profile/certifications')
	.version('beta')
	.post(personCertification);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\PersonCertification;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PersonCertification();
$requestBody->setCertificationId('KB-1235466333663322');
$requestBody->setDescription('Blackbelt in Marketing - Brand Management');
$requestBody->setDisplayName('Marketing Blackbelt - Brand Management');
$requestBody->setThumbnailUrl('https://iame.io/dfhdfdfd334.jpg');
$requestBody->setWebUrl('https://www.iame.io/blackbelt');

$result = $graphServiceClient->me()->profile()->certifications()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.People

$params = @{
	certificationId = "KB-1235466333663322"
	description = "Blackbelt in Marketing - Brand Management"
	displayName = "Marketing Blackbelt - Brand Management"
	thumbnailUrl = "https://iame.io/dfhdfdfd334.jpg"
	webUrl = "https://www.iame.io/blackbelt"
}

# A UPN can also be used as -UserId.
New-MgBetaUserProfileCertification -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.person_certification import PersonCertification
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PersonCertification(
	certification_id = "KB-1235466333663322",
	description = "Blackbelt in Marketing - Brand Management",
	display_name = "Marketing Blackbelt - Brand Management",
	thumbnail_url = "https://iame.io/dfhdfdfd334.jpg",
	web_url = "https://www.iame.io/blackbelt",
)

result = await graph_client.me.profile.certifications.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

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
  "certificationId": "KB-1235466333663322",
  "description": "Blackbelt in Marketing - Brand Management",
  "displayName": "Marketing Blackbelt - Brand Management",
  "endDate": "Date",
  "issuedDate": "Date",
  "issuingAuthority": null,
  "issuingCompany": null,
  "startDate": "Date",
  "thumbnailUrl": "https://iame.io/dfhdfdfd334.jpg",
  "webUrl": "https://www.iame.io/blackbelt"
}
```
