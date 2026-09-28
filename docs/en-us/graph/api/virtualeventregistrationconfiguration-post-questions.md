<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualeventregistrationconfiguration-post-questions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Create virtualEventRegistrationCustomQuestion

Namespace: microsoft.graph

Create a [registration question](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0) for a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0).

You can create either a [predefined registration question](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationpredefinedquestion?view=graph-rest-1.0) or a [custom registration question](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationcustomquestion?view=graph-rest-1.0).

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

To create a question in the registration configuration of a webinar:

```http
POST /solutions/virtualEvents/webinars/{webinarId}/registrationConfiguration/questions
```

To create a question in the registration configuration of a town hall:

```http
POST /solutions/virtualEvents/townhalls/{townhallId}/registrationConfiguration/questions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of etiher a [virtualEventRegistrationCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationcustomquestion?view=graph-rest-1.0) or a [virtualEventRegistrationPredefinedQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationpredefinedquestion?view=graph-rest-1.0) object.

You can specify the following properties when you create a **virtualEventRegistrationCustomQuestion**.

| Property | Type | Description |
| :--- | :--- | :--- |
| answerChoices | String collection | Answer choices when **answerInputType** is `singleChoice` or `multiChoice`. |
| answerInputType | virtualEventRegistrationQuestionAnswerInputType | Input type of the registration question answer. The supported values are `text`, `multilineText`, `singleChoice`, `multiChoice`, `boolean`, and `unknownFutureValue`. |
| displayName | String | Display name of the registration question. |
| isRequired | Boolean | Indicates whether an answer to the question is required. Default value is `false`. |

You can specify the following property when you create a **virtualEventRegistrationPredefinedQuestion**.

| Property | Type | Description |
| :--- | :--- | :--- |
| label | virtualEventRegistrationPredefinedQuestionLabel | Label of the predefined registration question. The following label values accept a single line of text: `street`, `city`, `state`, `postalCode`, `countryOrRegion`, `industry`, `jobTitle`, `organization`, and `unknownFutureValue`. |

## Response

If successful, this method returns a `201 Created` response code and either a [virtualEventRegistrationCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationcustomquestion?view=graph-rest-1.0) or [virtualEventRegistrationPredefinedQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationpredefinedquestion?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Add a custom registration question to a webinar registration

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
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/f4b39f1c-520e-4e75-805a-4b0f2016a0c6@a1a56d21-a8a6-4a6b-97f8-ced53d30f143/registrationConfiguration/questions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.virtualEventRegistrationCustomQuestion",
  "displayName": "What's your job position?",
  "answerInputType": "multiChoice",
  "answerChoices": [
    "Software Engineer",
    "Engineer Manager",
    "Product Manager"
  ],
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventRegistrationCustomQuestion
{
	OdataType = "#microsoft.graph.virtualEventRegistrationCustomQuestion",
	DisplayName = "What's your job position?",
	AnswerInputType = VirtualEventRegistrationQuestionAnswerInputType.MultiChoice,
	AnswerChoices = new List<string>
	{
		"Software Engineer",
		"Engineer Manager",
		"Product Manager",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Webinars["{virtualEventWebinar-id}"].RegistrationConfiguration.Questions.PostAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventRegistrationQuestionBase()
displayName := "What's your job position?"
requestBody.SetDisplayName(&displayName) 
answerInputType := graphmodels.MULTICHOICE_VIRTUALEVENTREGISTRATIONQUESTIONANSWERINPUTTYPE 
requestBody.SetAnswerInputType(&answerInputType) 
answerChoices := []string {
	"Software Engineer",
	"Engineer Manager",
	"Product Manager",
}
requestBody.SetAnswerChoices(answerChoices)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
questions, err := graphClient.Solutions().VirtualEvents().Webinars().ByVirtualEventWebinarId("virtualEventWebinar-id").RegistrationConfiguration().Questions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventRegistrationCustomQuestion virtualEventRegistrationQuestionBase = new VirtualEventRegistrationCustomQuestion();
virtualEventRegistrationQuestionBase.setOdataType("#microsoft.graph.virtualEventRegistrationCustomQuestion");
virtualEventRegistrationQuestionBase.setDisplayName("What's your job position?");
virtualEventRegistrationQuestionBase.setAnswerInputType(VirtualEventRegistrationQuestionAnswerInputType.MultiChoice);
LinkedList<String> answerChoices = new LinkedList<String>();
answerChoices.add("Software Engineer");
answerChoices.add("Engineer Manager");
answerChoices.add("Product Manager");
virtualEventRegistrationQuestionBase.setAnswerChoices(answerChoices);
VirtualEventRegistrationQuestionBase result = graphClient.solutions().virtualEvents().webinars().byVirtualEventWebinarId("{virtualEventWebinar-id}").registrationConfiguration().questions().post(virtualEventRegistrationQuestionBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventRegistrationQuestionBase = {
  '@odata.type': '#microsoft.graph.virtualEventRegistrationCustomQuestion',
  displayName: 'What\'s your job position?',
  answerInputType: 'multiChoice',
  answerChoices: [
    'Software Engineer',
    'Engineer Manager',
    'Product Manager'
  ],
};

await client.api('/solutions/virtualEvents/webinars/f4b39f1c-520e-4e75-805a-4b0f2016a0c6@a1a56d21-a8a6-4a6b-97f8-ced53d30f143/registrationConfiguration/questions')
	.post(virtualEventRegistrationQuestionBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventRegistrationCustomQuestion;
use Microsoft\Graph\Generated\Models\VirtualEventRegistrationQuestionAnswerInputType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventRegistrationCustomQuestion();
$requestBody->setOdataType('#microsoft.graph.virtualEventRegistrationCustomQuestion');
$requestBody->setDisplayName('What\'s your job position?');
$requestBody->setAnswerInputType(new VirtualEventRegistrationQuestionAnswerInputType('multiChoice'));
$requestBody->setAnswerChoices(['Software Engineer', 'Engineer Manager', 'Product Manager', 	]);

$result = $graphServiceClient->solutions()->virtualEvents()->webinars()->byVirtualEventWebinarId('virtualEventWebinar-id')->registrationConfiguration()->questions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	"@odata.type" = "#microsoft.graph.virtualEventRegistrationCustomQuestion"
	displayName = "What's your job position?"
	answerInputType = "multiChoice"
	answerChoices = @(
	"Software Engineer"
"Engineer Manager"
"Product Manager"
)
}

New-MgVirtualEventWebinarRegistrationConfigurationQuestion -VirtualEventWebinarId $virtualEventWebinarId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_registration_custom_question import VirtualEventRegistrationCustomQuestion
from msgraph.generated.models.virtual_event_registration_question_answer_input_type import VirtualEventRegistrationQuestionAnswerInputType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventRegistrationCustomQuestion(
	odata_type = "#microsoft.graph.virtualEventRegistrationCustomQuestion",
	display_name = "What's your job position?",
	answer_input_type = VirtualEventRegistrationQuestionAnswerInputType.MultiChoice,
	answer_choices = [
		"Software Engineer",
		"Engineer Manager",
		"Product Manager",
	],
)

result = await graph_client.solutions.virtual_events.webinars.by_virtual_event_webinar_id('virtualEventWebinar-id').registration_configuration.questions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.virtualEventRegistrationCustomQuestion",
  "id": "f3115d4c-9896-42fc-a649-8ca5e3c3a43f",
  "displayName": "What's your job position?",
  "answerInputType": "multiChoice",
  "answerChoices": [
    "Software Engineer",
    "Engineer Manager",
    "Product Manager"
  ],
  "isRequired": false
}
```

### Example 2: Add a predefined registration question to a webinar registration

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
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/f4b39f1c-520e-4e75-805a-4b0f2016a0c6@a1a56d21-a8a6-4a6b-97f8-ced53d30f143/registrationConfiguration/questions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Webinars["{virtualEventWebinar-id}"].RegistrationConfiguration.Questions.PostAsync(null);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
questions, err := graphClient.Solutions().VirtualEvents().Webinars().ByVirtualEventWebinarId("virtualEventWebinar-id").RegistrationConfiguration().Questions().Post(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventRegistrationQuestionBase result = graphClient.solutions().virtualEvents().webinars().byVirtualEventWebinarId("{virtualEventWebinar-id}").registrationConfiguration().questions().post(null);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/virtualEvents/webinars/f4b39f1c-520e-4e75-805a-4b0f2016a0c6@a1a56d21-a8a6-4a6b-97f8-ced53d30f143/registrationConfiguration/questions')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->virtualEvents()->webinars()->byVirtualEventWebinarId('virtualEventWebinar-id')->registrationConfiguration()->questions()->post()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

New-MgVirtualEventWebinarRegistrationConfigurationQuestion -VirtualEventWebinarId $virtualEventWebinarId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.virtual_events.webinars.by_virtual_event_webinar_id('virtualEventWebinar-id').registration_configuration.questions.post(None)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```http
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.virtualEventRegistrationPredefinedQuestion",
  "label": "street"
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.virtualEventRegistrationPredefinedQuestion",
  "id": "7a852983-013a-4062-9e97-f784c6a57ec8",
  "label": "street",
  "displayName": "Address",
  "isRequired": false
}
```
