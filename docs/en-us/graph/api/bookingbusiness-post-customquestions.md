<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customquestions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create bookingCustomQuestion

Namespace: microsoft.graph

Create a new [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BookingsAppointment.ReadWrite.All | Bookings.Manage.All, Bookings.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Bookings.ReadWrite.All | Bookings.Manage.All |

## HTTP request

```http
POST /solutions/bookingBusinesses/{bookingBusinessesId}/customQuestions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) object.

You can specify the following properties when creating a **bookingCustomQuestion**.

| Property | Type | Description |
| :--- | :--- | :--- |
| answerInputType | answerInputType | The expected answer type. The possible values are: `text`, `radioButton`, `unknownFutureValue`. Optional. |
| answerOptions | String collection | List of possible answer values. Optional. |
| displayName | String | The question. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/customQuestions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.bookingCustomQuestion",
  "displayName": "What is your age?",
  "answerInputType": "text",
  "answerOptions" : []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BookingCustomQuestion
{
	OdataType = "#microsoft.graph.bookingCustomQuestion",
	DisplayName = "What is your age?",
	AnswerInputType = AnswerInputType.Text,
	AnswerOptions = new List<string>
	{
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].CustomQuestions.PostAsync(requestBody);
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

requestBody := graphmodels.NewBookingCustomQuestion()
displayName := "What is your age?"
requestBody.SetDisplayName(&displayName) 
answerInputType := graphmodels.TEXT_ANSWERINPUTTYPE 
requestBody.SetAnswerInputType(&answerInputType) 
answerOptions := []string {

}
requestBody.SetAnswerOptions(answerOptions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customQuestions, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").CustomQuestions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingCustomQuestion bookingCustomQuestion = new BookingCustomQuestion();
bookingCustomQuestion.setOdataType("#microsoft.graph.bookingCustomQuestion");
bookingCustomQuestion.setDisplayName("What is your age?");
bookingCustomQuestion.setAnswerInputType(AnswerInputType.Text);
LinkedList<String> answerOptions = new LinkedList<String>();
bookingCustomQuestion.setAnswerOptions(answerOptions);
BookingCustomQuestion result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").customQuestions().post(bookingCustomQuestion);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingCustomQuestion = {
  '@odata.type': '#microsoft.graph.bookingCustomQuestion',
  displayName: 'What is your age?',
  answerInputType: 'text',
  answerOptions: []
};

await client.api('/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/customQuestions')
	.post(bookingCustomQuestion);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingCustomQuestion;
use Microsoft\Graph\Generated\Models\AnswerInputType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingCustomQuestion();
$requestBody->setOdataType('#microsoft.graph.bookingCustomQuestion');
$requestBody->setDisplayName('What is your age?');
$requestBody->setAnswerInputType(new AnswerInputType('text'));
$requestBody->setAnswerOptions([	]);

$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->customQuestions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	"@odata.type" = "#microsoft.graph.bookingCustomQuestion"
	displayName = "What is your age?"
	answerInputType = "text"
	answerOptions = @(
	)
}

New-MgBookingBusinessCustomQuestion -BookingBusinessId $bookingBusinessId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_custom_question import BookingCustomQuestion
from msgraph.generated.models.answer_input_type import AnswerInputType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingCustomQuestion(
	odata_type = "#microsoft.graph.bookingCustomQuestion",
	display_name = "What is your age?",
	answer_input_type = AnswerInputType.Text,
	answer_options = [
	],
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').custom_questions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.bookingCustomQuestion",
  "id": "3bc6fde0-4ad3-445d-ab17-0fc15dba0774",
  "displayName": "What is your age?",
  "answerInputType": "text",
  "answerOptions": [],
}
```
