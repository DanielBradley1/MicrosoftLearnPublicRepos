<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualeventwebinar-post-registrations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Create virtualEventRegistration

Namespace: microsoft.graph

Create a [registration record](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) for a registrant of a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). This method registers the person for the webinar or town hall.

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
| Application | VirtualEventRegistration-Anon.ReadWrite.Chat | VirtualEventRegistration-Anon.ReadWrite.All |

Note

The `VirtualEventRegistration-Anon.ReadWrite.Chat` permission uses [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

## HTTP request

To create a registration of a webinar:

```http
POST /solutions/virtualEvents/webinars/{webinarId}/registrations
```

To create a registration of a town hall:

```http
POST /solutions/virtualEvents/townhalls/{townhallId}/registrations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of a [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) object.

You can specify the following properties when you create a **virtualEventRegistration** with delegated permission.

| Property | Type | Description |
| :--- | :--- | :--- |
| externalRegistrationInformation | [virtualEventExternalRegistrationInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalregistrationinformation?view=graph-rest-1.0) | The external information for a virtual event registration. Optional. |
| preferredTimezone | String | The registrant's time zone details. Required. |
| preferredLanguage | String | The registrant's preferred language. Required. |
| registrationQuestionAnswers | [virtualEventRegistrationQuestionAnswer](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionanswer?view=graph-rest-1.0) collection | The registrant's answer to the registration questions. Optional. |

You can specify the following properties when you create a **virtualEventRegistration** with application permission.

| Property | Type | Description |
| :--- | :--- | :--- |
| firstName | String | The registrant's first name. Required. |
| lastName | String | The registrant's last name. Required. |
| email | String | The registrant's email address. Required. |
| externalRegistrationInformation | [virtualEventExternalRegistrationInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalregistrationinformation?view=graph-rest-1.0) | The external information for a virtual event registration. Optional. |
| preferredTimezone | String | The registrant's time zone details. Required. |
| preferredLanguage | String | The registrant's preferred language. Required. |
| registrationQuestionAnswers | [virtualEventRegistrationQuestionAnswer](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionanswer?view=graph-rest-1.0) collection | The registrant's answer to the registration questions. Optional. |

## Response

If successful, this method returns one of the following results:

- A `201 Created` response code and a [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) object for delegated permissions.
- A `204 No Content` response code for application permissions.

## Examples

### Example 1: Creating registration record with delegated permission

Use delegated permission to create a registration record for a person who has a [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/whatis) as a way to register a Microsoft Entra user to a webinar.

#### Request

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
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/f4b39f1c-520e-4e75-805a-4b0f2016a0c6@a1a56d21-a8a6-4a6b-97f8-ced53d30f143/registrations
Content-Type: application/json

{
  "externalRegistrationInformation": {
    "referrer": "Fabrikam",
    "registrationId": "myExternalRegistrationId"
  },
  "preferredTimezone":"Pacific Standard Time",
  "preferredLanguage":"en-us",
  "registrationQuestionAnswers": [
    {
      "questionId": "95320781-96b3-4b8f-8cf8-e6561d23447a",
      "value": null,
      "booleanValue": null,
      "multiChoiceValues": [
        "Seattle"
      ]
    },
    {
      "questionId": "4577afdb-8bee-4219-b482-04b52c6b855c",
      "value": null,
      "booleanValue": true,
      "multiChoiceValues": []
    },
    {
      "questionId": "80fefcf1-caf7-4cd3-b8d7-159e17c47f20",
      "value": null,
      "booleanValue": null,
      "multiChoiceValues": [
        "Cancun",
        "Hoboken",
        "Beijing"
      ]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventRegistration
{
	ExternalRegistrationInformation = new VirtualEventExternalRegistrationInformation
	{
		Referrer = "Fabrikam",
		RegistrationId = "myExternalRegistrationId",
	},
	PreferredTimezone = "Pacific Standard Time",
	PreferredLanguage = "en-us",
	RegistrationQuestionAnswers = new List<VirtualEventRegistrationQuestionAnswer>
	{
		new VirtualEventRegistrationQuestionAnswer
		{
			QuestionId = "95320781-96b3-4b8f-8cf8-e6561d23447a",
			Value = null,
			BooleanValue = null,
			MultiChoiceValues = new List<string>
			{
				"Seattle",
			},
		},
		new VirtualEventRegistrationQuestionAnswer
		{
			QuestionId = "4577afdb-8bee-4219-b482-04b52c6b855c",
			Value = null,
			BooleanValue = true,
			MultiChoiceValues = new List<string>
			{
			},
		},
		new VirtualEventRegistrationQuestionAnswer
		{
			QuestionId = "80fefcf1-caf7-4cd3-b8d7-159e17c47f20",
			Value = null,
			BooleanValue = null,
			MultiChoiceValues = new List<string>
			{
				"Cancun",
				"Hoboken",
				"Beijing",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Webinars["{virtualEventWebinar-id}"].Registrations.PostAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventRegistration()
externalRegistrationInformation := graphmodels.NewVirtualEventExternalRegistrationInformation()
referrer := "Fabrikam"
externalRegistrationInformation.SetReferrer(&referrer) 
registrationId := "myExternalRegistrationId"
externalRegistrationInformation.SetRegistrationId(&registrationId) 
requestBody.SetExternalRegistrationInformation(externalRegistrationInformation)
preferredTimezone := "Pacific Standard Time"
requestBody.SetPreferredTimezone(&preferredTimezone) 
preferredLanguage := "en-us"
requestBody.SetPreferredLanguage(&preferredLanguage) 


virtualEventRegistrationQuestionAnswer := graphmodels.NewVirtualEventRegistrationQuestionAnswer()
questionId := "95320781-96b3-4b8f-8cf8-e6561d23447a"
virtualEventRegistrationQuestionAnswer.SetQuestionId(&questionId) 
value := null
virtualEventRegistrationQuestionAnswer.SetValue(&value) 
booleanValue := null
virtualEventRegistrationQuestionAnswer.SetBooleanValue(&booleanValue) 
multiChoiceValues := []string {
	"Seattle",
}
virtualEventRegistrationQuestionAnswer.SetMultiChoiceValues(multiChoiceValues)
virtualEventRegistrationQuestionAnswer1 := graphmodels.NewVirtualEventRegistrationQuestionAnswer()
questionId := "4577afdb-8bee-4219-b482-04b52c6b855c"
virtualEventRegistrationQuestionAnswer1.SetQuestionId(&questionId) 
value := null
virtualEventRegistrationQuestionAnswer1.SetValue(&value) 
booleanValue := true
virtualEventRegistrationQuestionAnswer1.SetBooleanValue(&booleanValue) 
multiChoiceValues := []string {

}
virtualEventRegistrationQuestionAnswer1.SetMultiChoiceValues(multiChoiceValues)
virtualEventRegistrationQuestionAnswer2 := graphmodels.NewVirtualEventRegistrationQuestionAnswer()
questionId := "80fefcf1-caf7-4cd3-b8d7-159e17c47f20"
virtualEventRegistrationQuestionAnswer2.SetQuestionId(&questionId) 
value := null
virtualEventRegistrationQuestionAnswer2.SetValue(&value) 
booleanValue := null
virtualEventRegistrationQuestionAnswer2.SetBooleanValue(&booleanValue) 
multiChoiceValues := []string {
	"Cancun",
	"Hoboken",
	"Beijing",
}
virtualEventRegistrationQuestionAnswer2.SetMultiChoiceValues(multiChoiceValues)

registrationQuestionAnswers := []graphmodels.VirtualEventRegistrationQuestionAnswerable {
	virtualEventRegistrationQuestionAnswer,
	virtualEventRegistrationQuestionAnswer1,
	virtualEventRegistrationQuestionAnswer2,
}
requestBody.SetRegistrationQuestionAnswers(registrationQuestionAnswers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
registrations, err := graphClient.Solutions().VirtualEvents().Webinars().ByVirtualEventWebinarId("virtualEventWebinar-id").Registrations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventRegistration virtualEventRegistration = new VirtualEventRegistration();
VirtualEventExternalRegistrationInformation externalRegistrationInformation = new VirtualEventExternalRegistrationInformation();
externalRegistrationInformation.setReferrer("Fabrikam");
externalRegistrationInformation.setRegistrationId("myExternalRegistrationId");
virtualEventRegistration.setExternalRegistrationInformation(externalRegistrationInformation);
virtualEventRegistration.setPreferredTimezone("Pacific Standard Time");
virtualEventRegistration.setPreferredLanguage("en-us");
LinkedList<VirtualEventRegistrationQuestionAnswer> registrationQuestionAnswers = new LinkedList<VirtualEventRegistrationQuestionAnswer>();
VirtualEventRegistrationQuestionAnswer virtualEventRegistrationQuestionAnswer = new VirtualEventRegistrationQuestionAnswer();
virtualEventRegistrationQuestionAnswer.setQuestionId("95320781-96b3-4b8f-8cf8-e6561d23447a");
virtualEventRegistrationQuestionAnswer.setValue(null);
virtualEventRegistrationQuestionAnswer.setBooleanValue(null);
LinkedList<String> multiChoiceValues = new LinkedList<String>();
multiChoiceValues.add("Seattle");
virtualEventRegistrationQuestionAnswer.setMultiChoiceValues(multiChoiceValues);
registrationQuestionAnswers.add(virtualEventRegistrationQuestionAnswer);
VirtualEventRegistrationQuestionAnswer virtualEventRegistrationQuestionAnswer1 = new VirtualEventRegistrationQuestionAnswer();
virtualEventRegistrationQuestionAnswer1.setQuestionId("4577afdb-8bee-4219-b482-04b52c6b855c");
virtualEventRegistrationQuestionAnswer1.setValue(null);
virtualEventRegistrationQuestionAnswer1.setBooleanValue(true);
LinkedList<String> multiChoiceValues1 = new LinkedList<String>();
virtualEventRegistrationQuestionAnswer1.setMultiChoiceValues(multiChoiceValues1);
registrationQuestionAnswers.add(virtualEventRegistrationQuestionAnswer1);
VirtualEventRegistrationQuestionAnswer virtualEventRegistrationQuestionAnswer2 = new VirtualEventRegistrationQuestionAnswer();
virtualEventRegistrationQuestionAnswer2.setQuestionId("80fefcf1-caf7-4cd3-b8d7-159e17c47f20");
virtualEventRegistrationQuestionAnswer2.setValue(null);
virtualEventRegistrationQuestionAnswer2.setBooleanValue(null);
LinkedList<String> multiChoiceValues2 = new LinkedList<String>();
multiChoiceValues2.add("Cancun");
multiChoiceValues2.add("Hoboken");
multiChoiceValues2.add("Beijing");
virtualEventRegistrationQuestionAnswer2.setMultiChoiceValues(multiChoiceValues2);
registrationQuestionAnswers.add(virtualEventRegistrationQuestionAnswer2);
virtualEventRegistration.setRegistrationQuestionAnswers(registrationQuestionAnswers);
VirtualEventRegistration result = graphClient.solutions().virtualEvents().webinars().byVirtualEventWebinarId("{virtualEventWebinar-id}").registrations().post(virtualEventRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventRegistration = {
  externalRegistrationInformation: {
    referrer: 'Fabrikam',
    registrationId: 'myExternalRegistrationId'
  },
  preferredTimezone: 'Pacific Standard Time',
  preferredLanguage: 'en-us',
  registrationQuestionAnswers: [
    {
      questionId: '95320781-96b3-4b8f-8cf8-e6561d23447a',
      value: null,
      booleanValue: null,
      multiChoiceValues: [
        'Seattle'
      ]
    },
    {
      questionId: '4577afdb-8bee-4219-b482-04b52c6b855c',
      value: null,
      booleanValue: true,
      multiChoiceValues: []
    },
    {
      questionId: '80fefcf1-caf7-4cd3-b8d7-159e17c47f20',
      value: null,
      booleanValue: null,
      multiChoiceValues: [
        'Cancun',
        'Hoboken',
        'Beijing'
      ]
    }
  ]
};

await client.api('/solutions/virtualEvents/webinars/f4b39f1c-520e-4e75-805a-4b0f2016a0c6@a1a56d21-a8a6-4a6b-97f8-ced53d30f143/registrations')
	.post(virtualEventRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventRegistration;
use Microsoft\Graph\Generated\Models\VirtualEventExternalRegistrationInformation;
use Microsoft\Graph\Generated\Models\VirtualEventRegistrationQuestionAnswer;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventRegistration();
$externalRegistrationInformation = new VirtualEventExternalRegistrationInformation();
$externalRegistrationInformation->setReferrer('Fabrikam');
$externalRegistrationInformation->setRegistrationId('myExternalRegistrationId');
$requestBody->setExternalRegistrationInformation($externalRegistrationInformation);
$requestBody->setPreferredTimezone('Pacific Standard Time');
$requestBody->setPreferredLanguage('en-us');
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1 = new VirtualEventRegistrationQuestionAnswer();
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1->setQuestionId('95320781-96b3-4b8f-8cf8-e6561d23447a');
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1->setValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1->setBooleanValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1->setMultiChoiceValues(['Seattle', 	]);
$registrationQuestionAnswersArray []= $registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1;
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2 = new VirtualEventRegistrationQuestionAnswer();
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2->setQuestionId('4577afdb-8bee-4219-b482-04b52c6b855c');
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2->setValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2->setBooleanValue(true);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2->setMultiChoiceValues([	]);
$registrationQuestionAnswersArray []= $registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2;
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3 = new VirtualEventRegistrationQuestionAnswer();
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3->setQuestionId('80fefcf1-caf7-4cd3-b8d7-159e17c47f20');
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3->setValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3->setBooleanValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3->setMultiChoiceValues(['Cancun', 'Hoboken', 'Beijing', 	]);
$registrationQuestionAnswersArray []= $registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3;
$requestBody->setRegistrationQuestionAnswers($registrationQuestionAnswersArray);


$result = $graphServiceClient->solutions()->virtualEvents()->webinars()->byVirtualEventWebinarId('virtualEventWebinar-id')->registrations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	externalRegistrationInformation = @{
		referrer = "Fabrikam"
		registrationId = "myExternalRegistrationId"
	}
	preferredTimezone = "Pacific Standard Time"
	preferredLanguage = "en-us"
	registrationQuestionAnswers = @(
		@{
			questionId = "95320781-96b3-4b8f-8cf8-e6561d23447a"
			value = $null
			booleanValue = $null
			multiChoiceValues = @(
			"Seattle"
		)
	}
	@{
		questionId = "4577afdb-8bee-4219-b482-04b52c6b855c"
		value = $null
		booleanValue = $true
		multiChoiceValues = @(
		)
	}
	@{
		questionId = "80fefcf1-caf7-4cd3-b8d7-159e17c47f20"
		value = $null
		booleanValue = $null
		multiChoiceValues = @(
		"Cancun"
	"Hoboken"
"Beijing"
)
}
)
}

New-MgVirtualEventWebinarRegistration -VirtualEventWebinarId $virtualEventWebinarId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_registration import VirtualEventRegistration
from msgraph.generated.models.virtual_event_external_registration_information import VirtualEventExternalRegistrationInformation
from msgraph.generated.models.virtual_event_registration_question_answer import VirtualEventRegistrationQuestionAnswer
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventRegistration(
	external_registration_information = VirtualEventExternalRegistrationInformation(
		referrer = "Fabrikam",
		registration_id = "myExternalRegistrationId",
	),
	preferred_timezone = "Pacific Standard Time",
	preferred_language = "en-us",
	registration_question_answers = [
		VirtualEventRegistrationQuestionAnswer(
			question_id = "95320781-96b3-4b8f-8cf8-e6561d23447a",
			value = None,
			boolean_value = None,
			multi_choice_values = [
				"Seattle",
			],
		),
		VirtualEventRegistrationQuestionAnswer(
			question_id = "4577afdb-8bee-4219-b482-04b52c6b855c",
			value = None,
			boolean_value = True,
			multi_choice_values = [
			],
		),
		VirtualEventRegistrationQuestionAnswer(
			question_id = "80fefcf1-caf7-4cd3-b8d7-159e17c47f20",
			value = None,
			boolean_value = None,
			multi_choice_values = [
				"Cancun",
				"Hoboken",
				"Beijing",
			],
		),
	],
)

result = await graph_client.solutions.virtual_events.webinars.by_virtual_event_webinar_id('virtualEventWebinar-id').registrations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.virtualEventRegistration",
  "id": "127962bb-84e1-7b62-fd98-1c9d39def7b6",
  "userId": "String",
  "firstName": "Emilee",
  "lastName": "Pham",
  "email": "EmileeMPham@contoso.com",
  "externalRegistrationInformation": {
    "referrer": "Fabrikam",
    "registrationId": "myExternalRegistrationId"
  },
  "status": "registered",
  "registrationDateTime": "2023-03-07T22:04:17",
  "cancelationDateTime": null,
  "preferredTimezone":"Pacific Standard Time",
  "preferredLanguage":"en-us",
  "registrationQuestionAnswers": [
    {
      "questionId": "95320781-96b3-4b8f-8cf8-e6561d23447a",
      "displayName": "Which city do you currently work in?",
      "value": null,
      "booleanValue": null,
      "multiChoiceValues": [
        "Seattle"
      ]
    },
    {
      "questionId": "4577afdb-8bee-4219-b482-04b52c6b855c",
      "displayName": "Do you live in the same city where you work?",
      "value": null,
      "booleanValue": true,
      "multiChoiceValues": []
    },
    {
      "questionId": "80fefcf1-caf7-4cd3-b8d7-159e17c47f20",
      "displayName": "Which cities have you worked in?",
      "value": null,
      "booleanValue": null,
      "multiChoiceValues": [
        "Cancun",
        "Hoboken",
        "Beijing"
      ]
    }
  ]
}
```

### Example 2: Creating registration record with application permission

Use application permission to create a registration record for a person who doesn't have a [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/whatis) as a way to register an anonymous user for a webinar.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/f4b39f1c-520e-4e75-805a-4b0f2016a0c6@a1a56d21-a8a6-4a6b-97f8-ced53d30f143/registrations
Content-Type: application/json

{
  "firstName" : "Diane",
  "lastName" : "Demoss",
  "email" : "DianeDemoss@contoso.com",
  "externalRegistrationInformation": {
    "referrer": "Fabrikam",
    "registrationId": "myExternalRegistrationId"
  },
  "preferredTimezone":"Pacific Standard Time",
  "preferredLanguage":"en-us",
  "registrationQuestionAnswers": [
    {
      "questionId": "95320781-96b3-4b8f-8cf8-e6561d23447a",
      "value": null,
      "booleanValue": null,
      "multiChoiceValues": [
        "Seattle"
      ]
    },
    {
      "questionId": "4577afdb-8bee-4219-b482-04b52c6b855c",
      "value": null,
      "booleanValue": true,
      "multiChoiceValues": []
    },
    {
      "questionId": "80fefcf1-caf7-4cd3-b8d7-159e17c47f20",
      "value": null,
      "booleanValue": null,
      "multiChoiceValues": [
        "London",
        "New York City"
      ]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventRegistration
{
	FirstName = "Diane",
	LastName = "Demoss",
	Email = "DianeDemoss@contoso.com",
	ExternalRegistrationInformation = new VirtualEventExternalRegistrationInformation
	{
		Referrer = "Fabrikam",
		RegistrationId = "myExternalRegistrationId",
	},
	PreferredTimezone = "Pacific Standard Time",
	PreferredLanguage = "en-us",
	RegistrationQuestionAnswers = new List<VirtualEventRegistrationQuestionAnswer>
	{
		new VirtualEventRegistrationQuestionAnswer
		{
			QuestionId = "95320781-96b3-4b8f-8cf8-e6561d23447a",
			Value = null,
			BooleanValue = null,
			MultiChoiceValues = new List<string>
			{
				"Seattle",
			},
		},
		new VirtualEventRegistrationQuestionAnswer
		{
			QuestionId = "4577afdb-8bee-4219-b482-04b52c6b855c",
			Value = null,
			BooleanValue = true,
			MultiChoiceValues = new List<string>
			{
			},
		},
		new VirtualEventRegistrationQuestionAnswer
		{
			QuestionId = "80fefcf1-caf7-4cd3-b8d7-159e17c47f20",
			Value = null,
			BooleanValue = null,
			MultiChoiceValues = new List<string>
			{
				"London",
				"New York City",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Webinars["{virtualEventWebinar-id}"].Registrations.PostAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventRegistration()
firstName := "Diane"
requestBody.SetFirstName(&firstName) 
lastName := "Demoss"
requestBody.SetLastName(&lastName) 
email := "DianeDemoss@contoso.com"
requestBody.SetEmail(&email) 
externalRegistrationInformation := graphmodels.NewVirtualEventExternalRegistrationInformation()
referrer := "Fabrikam"
externalRegistrationInformation.SetReferrer(&referrer) 
registrationId := "myExternalRegistrationId"
externalRegistrationInformation.SetRegistrationId(&registrationId) 
requestBody.SetExternalRegistrationInformation(externalRegistrationInformation)
preferredTimezone := "Pacific Standard Time"
requestBody.SetPreferredTimezone(&preferredTimezone) 
preferredLanguage := "en-us"
requestBody.SetPreferredLanguage(&preferredLanguage) 


virtualEventRegistrationQuestionAnswer := graphmodels.NewVirtualEventRegistrationQuestionAnswer()
questionId := "95320781-96b3-4b8f-8cf8-e6561d23447a"
virtualEventRegistrationQuestionAnswer.SetQuestionId(&questionId) 
value := null
virtualEventRegistrationQuestionAnswer.SetValue(&value) 
booleanValue := null
virtualEventRegistrationQuestionAnswer.SetBooleanValue(&booleanValue) 
multiChoiceValues := []string {
	"Seattle",
}
virtualEventRegistrationQuestionAnswer.SetMultiChoiceValues(multiChoiceValues)
virtualEventRegistrationQuestionAnswer1 := graphmodels.NewVirtualEventRegistrationQuestionAnswer()
questionId := "4577afdb-8bee-4219-b482-04b52c6b855c"
virtualEventRegistrationQuestionAnswer1.SetQuestionId(&questionId) 
value := null
virtualEventRegistrationQuestionAnswer1.SetValue(&value) 
booleanValue := true
virtualEventRegistrationQuestionAnswer1.SetBooleanValue(&booleanValue) 
multiChoiceValues := []string {

}
virtualEventRegistrationQuestionAnswer1.SetMultiChoiceValues(multiChoiceValues)
virtualEventRegistrationQuestionAnswer2 := graphmodels.NewVirtualEventRegistrationQuestionAnswer()
questionId := "80fefcf1-caf7-4cd3-b8d7-159e17c47f20"
virtualEventRegistrationQuestionAnswer2.SetQuestionId(&questionId) 
value := null
virtualEventRegistrationQuestionAnswer2.SetValue(&value) 
booleanValue := null
virtualEventRegistrationQuestionAnswer2.SetBooleanValue(&booleanValue) 
multiChoiceValues := []string {
	"London",
	"New York City",
}
virtualEventRegistrationQuestionAnswer2.SetMultiChoiceValues(multiChoiceValues)

registrationQuestionAnswers := []graphmodels.VirtualEventRegistrationQuestionAnswerable {
	virtualEventRegistrationQuestionAnswer,
	virtualEventRegistrationQuestionAnswer1,
	virtualEventRegistrationQuestionAnswer2,
}
requestBody.SetRegistrationQuestionAnswers(registrationQuestionAnswers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
registrations, err := graphClient.Solutions().VirtualEvents().Webinars().ByVirtualEventWebinarId("virtualEventWebinar-id").Registrations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventRegistration virtualEventRegistration = new VirtualEventRegistration();
virtualEventRegistration.setFirstName("Diane");
virtualEventRegistration.setLastName("Demoss");
virtualEventRegistration.setEmail("DianeDemoss@contoso.com");
VirtualEventExternalRegistrationInformation externalRegistrationInformation = new VirtualEventExternalRegistrationInformation();
externalRegistrationInformation.setReferrer("Fabrikam");
externalRegistrationInformation.setRegistrationId("myExternalRegistrationId");
virtualEventRegistration.setExternalRegistrationInformation(externalRegistrationInformation);
virtualEventRegistration.setPreferredTimezone("Pacific Standard Time");
virtualEventRegistration.setPreferredLanguage("en-us");
LinkedList<VirtualEventRegistrationQuestionAnswer> registrationQuestionAnswers = new LinkedList<VirtualEventRegistrationQuestionAnswer>();
VirtualEventRegistrationQuestionAnswer virtualEventRegistrationQuestionAnswer = new VirtualEventRegistrationQuestionAnswer();
virtualEventRegistrationQuestionAnswer.setQuestionId("95320781-96b3-4b8f-8cf8-e6561d23447a");
virtualEventRegistrationQuestionAnswer.setValue(null);
virtualEventRegistrationQuestionAnswer.setBooleanValue(null);
LinkedList<String> multiChoiceValues = new LinkedList<String>();
multiChoiceValues.add("Seattle");
virtualEventRegistrationQuestionAnswer.setMultiChoiceValues(multiChoiceValues);
registrationQuestionAnswers.add(virtualEventRegistrationQuestionAnswer);
VirtualEventRegistrationQuestionAnswer virtualEventRegistrationQuestionAnswer1 = new VirtualEventRegistrationQuestionAnswer();
virtualEventRegistrationQuestionAnswer1.setQuestionId("4577afdb-8bee-4219-b482-04b52c6b855c");
virtualEventRegistrationQuestionAnswer1.setValue(null);
virtualEventRegistrationQuestionAnswer1.setBooleanValue(true);
LinkedList<String> multiChoiceValues1 = new LinkedList<String>();
virtualEventRegistrationQuestionAnswer1.setMultiChoiceValues(multiChoiceValues1);
registrationQuestionAnswers.add(virtualEventRegistrationQuestionAnswer1);
VirtualEventRegistrationQuestionAnswer virtualEventRegistrationQuestionAnswer2 = new VirtualEventRegistrationQuestionAnswer();
virtualEventRegistrationQuestionAnswer2.setQuestionId("80fefcf1-caf7-4cd3-b8d7-159e17c47f20");
virtualEventRegistrationQuestionAnswer2.setValue(null);
virtualEventRegistrationQuestionAnswer2.setBooleanValue(null);
LinkedList<String> multiChoiceValues2 = new LinkedList<String>();
multiChoiceValues2.add("London");
multiChoiceValues2.add("New York City");
virtualEventRegistrationQuestionAnswer2.setMultiChoiceValues(multiChoiceValues2);
registrationQuestionAnswers.add(virtualEventRegistrationQuestionAnswer2);
virtualEventRegistration.setRegistrationQuestionAnswers(registrationQuestionAnswers);
VirtualEventRegistration result = graphClient.solutions().virtualEvents().webinars().byVirtualEventWebinarId("{virtualEventWebinar-id}").registrations().post(virtualEventRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventRegistration = {
  firstName: 'Diane',
  lastName: 'Demoss',
  email: 'DianeDemoss@contoso.com',
  externalRegistrationInformation: {
    referrer: 'Fabrikam',
    registrationId: 'myExternalRegistrationId'
  },
  preferredTimezone: 'Pacific Standard Time',
  preferredLanguage: 'en-us',
  registrationQuestionAnswers: [
    {
      questionId: '95320781-96b3-4b8f-8cf8-e6561d23447a',
      value: null,
      booleanValue: null,
      multiChoiceValues: [
        'Seattle'
      ]
    },
    {
      questionId: '4577afdb-8bee-4219-b482-04b52c6b855c',
      value: null,
      booleanValue: true,
      multiChoiceValues: []
    },
    {
      questionId: '80fefcf1-caf7-4cd3-b8d7-159e17c47f20',
      value: null,
      booleanValue: null,
      multiChoiceValues: [
        'London',
        'New York City'
      ]
    }
  ]
};

await client.api('/solutions/virtualEvents/webinars/f4b39f1c-520e-4e75-805a-4b0f2016a0c6@a1a56d21-a8a6-4a6b-97f8-ced53d30f143/registrations')
	.post(virtualEventRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventRegistration;
use Microsoft\Graph\Generated\Models\VirtualEventExternalRegistrationInformation;
use Microsoft\Graph\Generated\Models\VirtualEventRegistrationQuestionAnswer;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventRegistration();
$requestBody->setFirstName('Diane');
$requestBody->setLastName('Demoss');
$requestBody->setEmail('DianeDemoss@contoso.com');
$externalRegistrationInformation = new VirtualEventExternalRegistrationInformation();
$externalRegistrationInformation->setReferrer('Fabrikam');
$externalRegistrationInformation->setRegistrationId('myExternalRegistrationId');
$requestBody->setExternalRegistrationInformation($externalRegistrationInformation);
$requestBody->setPreferredTimezone('Pacific Standard Time');
$requestBody->setPreferredLanguage('en-us');
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1 = new VirtualEventRegistrationQuestionAnswer();
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1->setQuestionId('95320781-96b3-4b8f-8cf8-e6561d23447a');
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1->setValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1->setBooleanValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1->setMultiChoiceValues(['Seattle', 	]);
$registrationQuestionAnswersArray []= $registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer1;
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2 = new VirtualEventRegistrationQuestionAnswer();
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2->setQuestionId('4577afdb-8bee-4219-b482-04b52c6b855c');
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2->setValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2->setBooleanValue(true);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2->setMultiChoiceValues([	]);
$registrationQuestionAnswersArray []= $registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer2;
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3 = new VirtualEventRegistrationQuestionAnswer();
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3->setQuestionId('80fefcf1-caf7-4cd3-b8d7-159e17c47f20');
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3->setValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3->setBooleanValue(null);
$registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3->setMultiChoiceValues(['London', 'New York City', 	]);
$registrationQuestionAnswersArray []= $registrationQuestionAnswersVirtualEventRegistrationQuestionAnswer3;
$requestBody->setRegistrationQuestionAnswers($registrationQuestionAnswersArray);


$result = $graphServiceClient->solutions()->virtualEvents()->webinars()->byVirtualEventWebinarId('virtualEventWebinar-id')->registrations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	firstName = "Diane"
	lastName = "Demoss"
	email = "DianeDemoss@contoso.com"
	externalRegistrationInformation = @{
		referrer = "Fabrikam"
		registrationId = "myExternalRegistrationId"
	}
	preferredTimezone = "Pacific Standard Time"
	preferredLanguage = "en-us"
	registrationQuestionAnswers = @(
		@{
			questionId = "95320781-96b3-4b8f-8cf8-e6561d23447a"
			value = $null
			booleanValue = $null
			multiChoiceValues = @(
			"Seattle"
		)
	}
	@{
		questionId = "4577afdb-8bee-4219-b482-04b52c6b855c"
		value = $null
		booleanValue = $true
		multiChoiceValues = @(
		)
	}
	@{
		questionId = "80fefcf1-caf7-4cd3-b8d7-159e17c47f20"
		value = $null
		booleanValue = $null
		multiChoiceValues = @(
		"London"
	"New York City"
)
}
)
}

New-MgVirtualEventWebinarRegistration -VirtualEventWebinarId $virtualEventWebinarId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_registration import VirtualEventRegistration
from msgraph.generated.models.virtual_event_external_registration_information import VirtualEventExternalRegistrationInformation
from msgraph.generated.models.virtual_event_registration_question_answer import VirtualEventRegistrationQuestionAnswer
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventRegistration(
	first_name = "Diane",
	last_name = "Demoss",
	email = "DianeDemoss@contoso.com",
	external_registration_information = VirtualEventExternalRegistrationInformation(
		referrer = "Fabrikam",
		registration_id = "myExternalRegistrationId",
	),
	preferred_timezone = "Pacific Standard Time",
	preferred_language = "en-us",
	registration_question_answers = [
		VirtualEventRegistrationQuestionAnswer(
			question_id = "95320781-96b3-4b8f-8cf8-e6561d23447a",
			value = None,
			boolean_value = None,
			multi_choice_values = [
				"Seattle",
			],
		),
		VirtualEventRegistrationQuestionAnswer(
			question_id = "4577afdb-8bee-4219-b482-04b52c6b855c",
			value = None,
			boolean_value = True,
			multi_choice_values = [
			],
		),
		VirtualEventRegistrationQuestionAnswer(
			question_id = "80fefcf1-caf7-4cd3-b8d7-159e17c47f20",
			value = None,
			boolean_value = None,
			multi_choice_values = [
				"London",
				"New York City",
			],
		),
	],
)

result = await graph_client.solutions.virtual_events.webinars.by_virtual_event_webinar_id('virtualEventWebinar-id').registrations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
