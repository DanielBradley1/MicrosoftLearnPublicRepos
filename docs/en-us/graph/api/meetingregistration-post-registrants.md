<!-- Source: https://learn.microsoft.com/en-us/graph/api/meetingregistration-post-registrants?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create meetingRegistrant \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The meeting registrant API is deprecated and will stop returning data on **December 12, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

Enroll a [meeting registrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) in an online meeting that has [meeting registration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) enabled on behalf of the registrant. This operation has two scenarios:

- If the value of the **allowedRegistrant** property of the [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object is `organization`, registrants will be required to sign in before they register for the meeting. The **firstName**, **lastName**, and **email** must match the information stored in Microsoft Entra ID.
- If the value of the **allowedRegistrant** property of the [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object is `everyone`, registrants will not be required to sign in and will be considered anonymous.

In either scenario, the registrant will receive an email notification that contains their registration information.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OnlineMeetings.Read.All | OnlineMeetings.ReadWrite.All |

Tip

- If the value of the **allowedRegistrant** property of the [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object is `organization`, use the registrant's delegated permission to enroll.
- If the value of the **allowedRegistrant** property of the [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object is `everyone`, use the registrant's delegated permission to enroll.

## HTTP request

```http
POST /users/{userId}/onlineMeetings/{id}/registration/registrants
```

> **Note:** `userId` is the **objectID** of the meeting organizer.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the editable properties of a [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) object.

Important

You must supply the **@odata.type** property to specify the registrant type. For more details, see the following [example](#examples).

## Response

If successful, this method returns a `200 OK` response code and a partial [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) object in the response body.

Tip

The response body will contain different information depending on the value of **allowedRegistrant**.

- If the value of the **allowedRegistrant** property is `organization`, only **id** and **joinWebUrl** will be returned in the [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) object. Registrants can use the **id** to cancel their registration or **joinWebUrl** to join the meeting.
- If the value of the **allowedRegistrant** property is `everyone`, an empty [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) object will be returned. Registrants need to use the links in the email they receive to cancel registration or join the meeting.

## Examples

### Example 1: Enroll a signed-in registrant

The following example shows how to enroll a signed-in registrant with the registrant's delegated permission when the meeting has **allowedRegistrant** set to `organization`.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/users/16664f75-11dc-4870-bec6-38c1aaa81431/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/registrants
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.meetingRegistrant",
  "firstName": "Frederick",
  "lastName": "Cormier",
  "email": "frederick.cormier@contoso.com",
  "customQuestionAnswers": [
    {
      "questionId": "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=",
      "value": "No"
    },
    {
      "questionId": "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=",
      "value": "Internet"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new MeetingRegistrant
{
	OdataType = "#microsoft.graph.meetingRegistrant",
	FirstName = "Frederick",
	LastName = "Cormier",
	Email = "frederick.cormier@contoso.com",
	CustomQuestionAnswers = new List<CustomQuestionAnswer>
	{
		new CustomQuestionAnswer
		{
			QuestionId = "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=",
			Value = "No",
		},
		new CustomQuestionAnswer
		{
			QuestionId = "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=",
			Value = "Internet",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].OnlineMeetings["{onlineMeeting-id}"].Registration.Registrants.PostAsync(requestBody);
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

requestBody := graphmodels.NewMeetingRegistrantBase()
firstName := "Frederick"
requestBody.SetFirstName(&firstName) 
lastName := "Cormier"
requestBody.SetLastName(&lastName) 
email := "frederick.cormier@contoso.com"
requestBody.SetEmail(&email) 


customQuestionAnswer := graphmodels.NewCustomQuestionAnswer()
questionId := "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU="
customQuestionAnswer.SetQuestionId(&questionId) 
value := "No"
customQuestionAnswer.SetValue(&value) 
customQuestionAnswer1 := graphmodels.NewCustomQuestionAnswer()
questionId := "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8="
customQuestionAnswer1.SetQuestionId(&questionId) 
value := "Internet"
customQuestionAnswer1.SetValue(&value) 

customQuestionAnswers := []graphmodels.CustomQuestionAnswerable {
	customQuestionAnswer,
	customQuestionAnswer1,
}
requestBody.SetCustomQuestionAnswers(customQuestionAnswers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
registrants, err := graphClient.Users().ByUserId("user-id").OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Registration().Registrants().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MeetingRegistrant meetingRegistrantBase = new MeetingRegistrant();
meetingRegistrantBase.setOdataType("#microsoft.graph.meetingRegistrant");
meetingRegistrantBase.setFirstName("Frederick");
meetingRegistrantBase.setLastName("Cormier");
meetingRegistrantBase.setEmail("frederick.cormier@contoso.com");
LinkedList<CustomQuestionAnswer> customQuestionAnswers = new LinkedList<CustomQuestionAnswer>();
CustomQuestionAnswer customQuestionAnswer = new CustomQuestionAnswer();
customQuestionAnswer.setQuestionId("MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=");
customQuestionAnswer.setValue("No");
customQuestionAnswers.add(customQuestionAnswer);
CustomQuestionAnswer customQuestionAnswer1 = new CustomQuestionAnswer();
customQuestionAnswer1.setQuestionId("MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=");
customQuestionAnswer1.setValue("Internet");
customQuestionAnswers.add(customQuestionAnswer1);
meetingRegistrantBase.setCustomQuestionAnswers(customQuestionAnswers);
MeetingRegistrantBase result = graphClient.users().byUserId("{user-id}").onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").registration().registrants().post(meetingRegistrantBase);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const meetingRegistrantBase = {
  '@odata.type': '#microsoft.graph.meetingRegistrant',
  firstName: 'Frederick',
  lastName: 'Cormier',
  email: 'frederick.cormier@contoso.com',
  customQuestionAnswers: [
    {
      questionId: 'MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=',
      value: 'No'
    },
    {
      questionId: 'MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=',
      value: 'Internet'
    }
  ]
};

await client.api('/users/16664f75-11dc-4870-bec6-38c1aaa81431/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/registrants')
	.version('beta')
	.post(meetingRegistrantBase);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\MeetingRegistrant;
use Microsoft\Graph\Beta\Generated\Models\CustomQuestionAnswer;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MeetingRegistrant();
$requestBody->setOdataType('#microsoft.graph.meetingRegistrant');
$requestBody->setFirstName('Frederick');
$requestBody->setLastName('Cormier');
$requestBody->setEmail('frederick.cormier@contoso.com');
$customQuestionAnswersCustomQuestionAnswer1 = new CustomQuestionAnswer();
$customQuestionAnswersCustomQuestionAnswer1->setQuestionId('MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=');
$customQuestionAnswersCustomQuestionAnswer1->setValue('No');
$customQuestionAnswersArray []= $customQuestionAnswersCustomQuestionAnswer1;
$customQuestionAnswersCustomQuestionAnswer2 = new CustomQuestionAnswer();
$customQuestionAnswersCustomQuestionAnswer2->setQuestionId('MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=');
$customQuestionAnswersCustomQuestionAnswer2->setValue('Internet');
$customQuestionAnswersArray []= $customQuestionAnswersCustomQuestionAnswer2;
$requestBody->setCustomQuestionAnswers($customQuestionAnswersArray);


$result = $graphServiceClient->users()->byUserId('user-id')->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->registration()->registrants()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.meetingRegistrant"
	firstName = "Frederick"
	lastName = "Cormier"
	email = "frederick.cormier@contoso.com"
	customQuestionAnswers = @(
		@{
			questionId = "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU="
			value = "No"
		}
		@{
			questionId = "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8="
			value = "Internet"
		}
	)
}

New-MgBetaUserOnlineMeetingRegistrationRegistrant -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.meeting_registrant import MeetingRegistrant
from msgraph_beta.generated.models.custom_question_answer import CustomQuestionAnswer
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MeetingRegistrant(
	odata_type = "#microsoft.graph.meetingRegistrant",
	first_name = "Frederick",
	last_name = "Cormier",
	email = "frederick.cormier@contoso.com",
	custom_question_answers = [
		CustomQuestionAnswer(
			question_id = "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=",
			value = "No",
		),
		CustomQuestionAnswer(
			question_id = "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=",
			value = "Internet",
		),
	],
)

result = await graph_client.users.by_user_id('user-id').online_meetings.by_online_meeting_id('onlineMeeting-id').registration.registrants.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('16664f75-11dc-4870-bec6-38c1aaa81431')/onlineMeetings('MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ')/registration/registrants/$entity",
  "@odata.type": "#microsoft.graph.meetingRegistrant",
  "id": "gWWckDBR6UOI8_yzWCzeNw,6pAAiSU1bkGqzLnbHG_muA,bzLh6uR-5EGYsCvtvIvs6Q,E4jbleVFdE6BDf6ei3YBOA,KvXQzK4zfU-5LQj_ZLWgow,A7_SArco00S-Qr707l0vBA,UFakyZrk1K9vBacExW1muA",
  "registrationDateTime": null,
  "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MmE4Mzg1OTItYjg2Ni00ZmNmLWI5NjMtODNkZDJiMWNlNTVi%40thread.v2/0?context=%7b%22Tid%22%3a%22909c6581-5131-43e9-88f3-fcb3582cde37%22%2c%22Oid%22%3a%22dc17674c-81d9-4adb-bfb2-8f6a442e4622%22%2c%22prid%22%3a%22gWWckDBR6UOI8_yzWCzeNw%2c6pAAiSa1bkGqzLnbHG_muA%2cbzLh6uR-5EGdsCvtvIvs6Q%2cE4jbleVFdE6BDf6ei3YBOA%2cKvXQzK4zfU-5LQj_ZLWgow%2cA7_SArco00S-Qr707l0vBA%2cUFaiyZrk1K9vBacExW1muA%22%2c%22isPublic%22%3afalse%7d",
  "firstName": null,
  "lastName": null,
  "email": null,
  "status": null,
  "customQuestionAnswers": []
}
```

### Example 2: Enroll an anonymous registrant

The following example shows how to enroll an anonymous registrant with application permission when the meeting has **allowedRegistrant** set to `everyone`.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/users/dc17674c-81d9-4adb-bfb2-8f6a442e4622/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/registrants
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.meetingRegistrant",
  "firstName": "Lisa",
  "lastName": "Adkins",
  "email": "lisa.adkins@contoso.com",
  "customQuestionAnswers": [
    {
      "questionId": "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=",
      "value": "No"
    },
    {
      "questionId": "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=",
      "value": "Internet"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new MeetingRegistrant
{
	OdataType = "#microsoft.graph.meetingRegistrant",
	FirstName = "Lisa",
	LastName = "Adkins",
	Email = "lisa.adkins@contoso.com",
	CustomQuestionAnswers = new List<CustomQuestionAnswer>
	{
		new CustomQuestionAnswer
		{
			QuestionId = "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=",
			Value = "No",
		},
		new CustomQuestionAnswer
		{
			QuestionId = "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=",
			Value = "Internet",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].OnlineMeetings["{onlineMeeting-id}"].Registration.Registrants.PostAsync(requestBody);
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

requestBody := graphmodels.NewMeetingRegistrantBase()
firstName := "Lisa"
requestBody.SetFirstName(&firstName) 
lastName := "Adkins"
requestBody.SetLastName(&lastName) 
email := "lisa.adkins@contoso.com"
requestBody.SetEmail(&email) 


customQuestionAnswer := graphmodels.NewCustomQuestionAnswer()
questionId := "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU="
customQuestionAnswer.SetQuestionId(&questionId) 
value := "No"
customQuestionAnswer.SetValue(&value) 
customQuestionAnswer1 := graphmodels.NewCustomQuestionAnswer()
questionId := "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8="
customQuestionAnswer1.SetQuestionId(&questionId) 
value := "Internet"
customQuestionAnswer1.SetValue(&value) 

customQuestionAnswers := []graphmodels.CustomQuestionAnswerable {
	customQuestionAnswer,
	customQuestionAnswer1,
}
requestBody.SetCustomQuestionAnswers(customQuestionAnswers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
registrants, err := graphClient.Users().ByUserId("user-id").OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Registration().Registrants().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MeetingRegistrant meetingRegistrantBase = new MeetingRegistrant();
meetingRegistrantBase.setOdataType("#microsoft.graph.meetingRegistrant");
meetingRegistrantBase.setFirstName("Lisa");
meetingRegistrantBase.setLastName("Adkins");
meetingRegistrantBase.setEmail("lisa.adkins@contoso.com");
LinkedList<CustomQuestionAnswer> customQuestionAnswers = new LinkedList<CustomQuestionAnswer>();
CustomQuestionAnswer customQuestionAnswer = new CustomQuestionAnswer();
customQuestionAnswer.setQuestionId("MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=");
customQuestionAnswer.setValue("No");
customQuestionAnswers.add(customQuestionAnswer);
CustomQuestionAnswer customQuestionAnswer1 = new CustomQuestionAnswer();
customQuestionAnswer1.setQuestionId("MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=");
customQuestionAnswer1.setValue("Internet");
customQuestionAnswers.add(customQuestionAnswer1);
meetingRegistrantBase.setCustomQuestionAnswers(customQuestionAnswers);
MeetingRegistrantBase result = graphClient.users().byUserId("{user-id}").onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").registration().registrants().post(meetingRegistrantBase);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const meetingRegistrantBase = {
  '@odata.type': '#microsoft.graph.meetingRegistrant',
  firstName: 'Lisa',
  lastName: 'Adkins',
  email: 'lisa.adkins@contoso.com',
  customQuestionAnswers: [
    {
      questionId: 'MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=',
      value: 'No'
    },
    {
      questionId: 'MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=',
      value: 'Internet'
    }
  ]
};

await client.api('/users/dc17674c-81d9-4adb-bfb2-8f6a442e4622/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/registrants')
	.version('beta')
	.post(meetingRegistrantBase);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\MeetingRegistrant;
use Microsoft\Graph\Beta\Generated\Models\CustomQuestionAnswer;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MeetingRegistrant();
$requestBody->setOdataType('#microsoft.graph.meetingRegistrant');
$requestBody->setFirstName('Lisa');
$requestBody->setLastName('Adkins');
$requestBody->setEmail('lisa.adkins@contoso.com');
$customQuestionAnswersCustomQuestionAnswer1 = new CustomQuestionAnswer();
$customQuestionAnswersCustomQuestionAnswer1->setQuestionId('MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=');
$customQuestionAnswersCustomQuestionAnswer1->setValue('No');
$customQuestionAnswersArray []= $customQuestionAnswersCustomQuestionAnswer1;
$customQuestionAnswersCustomQuestionAnswer2 = new CustomQuestionAnswer();
$customQuestionAnswersCustomQuestionAnswer2->setQuestionId('MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=');
$customQuestionAnswersCustomQuestionAnswer2->setValue('Internet');
$customQuestionAnswersArray []= $customQuestionAnswersCustomQuestionAnswer2;
$requestBody->setCustomQuestionAnswers($customQuestionAnswersArray);


$result = $graphServiceClient->users()->byUserId('user-id')->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->registration()->registrants()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.meetingRegistrant"
	firstName = "Lisa"
	lastName = "Adkins"
	email = "lisa.adkins@contoso.com"
	customQuestionAnswers = @(
		@{
			questionId = "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU="
			value = "No"
		}
		@{
			questionId = "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8="
			value = "Internet"
		}
	)
}

New-MgBetaUserOnlineMeetingRegistrationRegistrant -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.meeting_registrant import MeetingRegistrant
from msgraph_beta.generated.models.custom_question_answer import CustomQuestionAnswer
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MeetingRegistrant(
	odata_type = "#microsoft.graph.meetingRegistrant",
	first_name = "Lisa",
	last_name = "Adkins",
	email = "lisa.adkins@contoso.com",
	custom_question_answers = [
		CustomQuestionAnswer(
			question_id = "MSM5YjlmM2Q4ZS03ZmVkLTRmN3gwMDIw94MDAyMF9hX3gwMDIwX2RldmU=",
			value = "No",
		),
		CustomQuestionAnswer(
			question_id = "MSM5M2E2OWQ1Ni1jZTc4LTQDAwMjBfZGlkX3gwMDIwX3lvdV94MDAyMF8=",
			value = "Internet",
		),
	],
)

result = await graph_client.users.by_user_id('user-id').online_meetings.by_online_meeting_id('onlineMeeting-id').registration.registrants.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('16664f75-11dc-4870-bec6-38c1aaa81431')/onlineMeetings('MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ')/registration/registrants/$entity",
    "@odata.type": "#microsoft.graph.meetingRegistrant",
    "id": "",
    "registrationDateTime": null,
    "joinWebUrl": "",
    "firstName": null,
    "lastName": null,
    "email": null,
    "status": null,
    "customQuestionAnswers": []
}
```
