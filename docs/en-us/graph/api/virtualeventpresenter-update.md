<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualeventpresenter-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Update virtualEventPresenter

Namespace: microsoft.graph

Update the properties of a [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object.

Currently the supported virtual event types are:

- [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | VirtualEvent.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /solutions/virtualEvents/webinars/{webinarId}/presenters/{presenterId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| presenterDetails | [virtualEventPresenterDetails](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenterdetails?view=graph-rest-1.0) | Other details about the presenter. |

## Response

If successful, this method returns a `200 OK` response code and an updated [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows how to update a presenter on a **virtualEventWebinar**.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/88b245ac-b0b2-f1aa-e34a-c81c27abdac2@f9448ec4-804b-46af-b810-62085248da33/presenters/831affc2-4c8a-9929-50e7-02964563b6e4
Content-Type: application/json

{
  "presenterDetails": {
    "bio": {
      "content": "Lead Product Manager of Contoso Sales department",
      "contentType": "text"
    },
    "company": "Contoso",
    "jobTitle": "Product Manager",
    "linkedInProfileWebUrl": "https://linkedin.com/in/DianeDemoss",
    "personalSiteWebUrl": "https://DianeDemoss.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventPresenter
{
	PresenterDetails = new VirtualEventPresenterDetails
	{
		Bio = new ItemBody
		{
			Content = "Lead Product Manager of Contoso Sales department",
			ContentType = BodyType.Text,
		},
		Company = "Contoso",
		JobTitle = "Product Manager",
		LinkedInProfileWebUrl = "https://linkedin.com/in/DianeDemoss",
		PersonalSiteWebUrl = "https://DianeDemoss.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Webinars["{virtualEventWebinar-id}"].Presenters["{virtualEventPresenter-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventPresenter()
presenterDetails := graphmodels.NewVirtualEventPresenterDetails()
bio := graphmodels.NewItemBody()
content := "Lead Product Manager of Contoso Sales department"
bio.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
bio.SetContentType(&contentType) 
presenterDetails.SetBio(bio)
company := "Contoso"
presenterDetails.SetCompany(&company) 
jobTitle := "Product Manager"
presenterDetails.SetJobTitle(&jobTitle) 
linkedInProfileWebUrl := "https://linkedin.com/in/DianeDemoss"
presenterDetails.SetLinkedInProfileWebUrl(&linkedInProfileWebUrl) 
personalSiteWebUrl := "https://DianeDemoss.com"
presenterDetails.SetPersonalSiteWebUrl(&personalSiteWebUrl) 
requestBody.SetPresenterDetails(presenterDetails)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
presenters, err := graphClient.Solutions().VirtualEvents().Webinars().ByVirtualEventWebinarId("virtualEventWebinar-id").Presenters().ByVirtualEventPresenterId("virtualEventPresenter-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventPresenter virtualEventPresenter = new VirtualEventPresenter();
VirtualEventPresenterDetails presenterDetails = new VirtualEventPresenterDetails();
ItemBody bio = new ItemBody();
bio.setContent("Lead Product Manager of Contoso Sales department");
bio.setContentType(BodyType.Text);
presenterDetails.setBio(bio);
presenterDetails.setCompany("Contoso");
presenterDetails.setJobTitle("Product Manager");
presenterDetails.setLinkedInProfileWebUrl("https://linkedin.com/in/DianeDemoss");
presenterDetails.setPersonalSiteWebUrl("https://DianeDemoss.com");
virtualEventPresenter.setPresenterDetails(presenterDetails);
VirtualEventPresenter result = graphClient.solutions().virtualEvents().webinars().byVirtualEventWebinarId("{virtualEventWebinar-id}").presenters().byVirtualEventPresenterId("{virtualEventPresenter-id}").patch(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventPresenter = {
  presenterDetails: {
    bio: {
      content: 'Lead Product Manager of Contoso Sales department',
      contentType: 'text'
    },
    company: 'Contoso',
    jobTitle: 'Product Manager',
    linkedInProfileWebUrl: 'https://linkedin.com/in/DianeDemoss',
    personalSiteWebUrl: 'https://DianeDemoss.com'
  }
};

await client.api('/solutions/virtualEvents/webinars/88b245ac-b0b2-f1aa-e34a-c81c27abdac2@f9448ec4-804b-46af-b810-62085248da33/presenters/831affc2-4c8a-9929-50e7-02964563b6e4')
	.update(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventPresenter;
use Microsoft\Graph\Generated\Models\VirtualEventPresenterDetails;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventPresenter();
$presenterDetails = new VirtualEventPresenterDetails();
$presenterDetailsBio = new ItemBody();
$presenterDetailsBio->setContent('Lead Product Manager of Contoso Sales department');
$presenterDetailsBio->setContentType(new BodyType('text'));
$presenterDetails->setBio($presenterDetailsBio);
$presenterDetails->setCompany('Contoso');
$presenterDetails->setJobTitle('Product Manager');
$presenterDetails->setLinkedInProfileWebUrl('https://linkedin.com/in/DianeDemoss');
$presenterDetails->setPersonalSiteWebUrl('https://DianeDemoss.com');
$requestBody->setPresenterDetails($presenterDetails);

$result = $graphServiceClient->solutions()->virtualEvents()->webinars()->byVirtualEventWebinarId('virtualEventWebinar-id')->presenters()->byVirtualEventPresenterId('virtualEventPresenter-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	presenterDetails = @{
		bio = @{
			content = "Lead Product Manager of Contoso Sales department"
			contentType = "text"
		}
		company = "Contoso"
		jobTitle = "Product Manager"
		linkedInProfileWebUrl = "https://linkedin.com/in/DianeDemoss"
		personalSiteWebUrl = "https://DianeDemoss.com"
	}
}

Update-MgVirtualEventWebinarPresenter -VirtualEventWebinarId $virtualEventWebinarId -VirtualEventPresenterId $virtualEventPresenterId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_presenter import VirtualEventPresenter
from msgraph.generated.models.virtual_event_presenter_details import VirtualEventPresenterDetails
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventPresenter(
	presenter_details = VirtualEventPresenterDetails(
		bio = ItemBody(
			content = "Lead Product Manager of Contoso Sales department",
			content_type = BodyType.Text,
		),
		company = "Contoso",
		job_title = "Product Manager",
		linked_in_profile_web_url = "https://linkedin.com/in/DianeDemoss",
		personal_site_web_url = "https://DianeDemoss.com",
	),
)

result = await graph_client.solutions.virtual_events.webinars.by_virtual_event_webinar_id('virtualEventWebinar-id').presenters.by_virtual_event_presenter_id('virtualEventPresenter-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.virtualEventPresenter",
  "id": "831affc2-4c8a-9929-50e7-02964563b6e4",
  "identity": {
    "@odata.type": "microsoft.graph.communicationsUserIdentity",
    "displayName": "Diane Demoss",
    "id": "831affc2-4c8a-9929-50e7-02964563b6e4",
    "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
  },
  "email": "DianeDemoss@contoso.com",
  "presenterDetails": {
    "company": "Contoso",
    "jobTitle": "Product Manager",
    "personalSiteWebUrl": "https://DianeDemoss.com",
    "linkedInProfileWebUrl": "https://linkedin.com/in/DianeDemoss",
    "twitterProfileWebUrl": null,
    "bio": {
      "content": "Lead Product Manager of Contoso Sales department",
      "contentType": "text"
    }
  }
}
```
