<!-- Source: https://learn.microsoft.com/en-us/graph/api/externalmeetingregistrant-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create externalMeetingRegistrant \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The external meeting registrant API is deprecated and will stop returning data on **December 12, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

Enroll an [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) in an online meeting which has [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) enabled. The meeting organizer enrolls someone by providing a unique **id** in the external registration system and gets the unique **joinWebUrl** of this registrant.

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
| Application | Not supported. | Not supported. |

To use application permission for this API, tenant administrators must create an [application access policy](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy) and grant it to a user to authorize the app configured in the policy to fetch online meetings and/or online meeting artifacts on behalf of that user \(with user ID specified in the request path\).

## HTTP request

To create an external meeting registrant with delegated \(`/me`\) and app \(`/users/{userId}/`\) permission:

```http
POST /me/onlineMeetings/{meetingId}/registration/registrants
POST /users/{userId}/onlineMeetings/{meetingId}/registration/registrants
```

Tip

- `userId` is the **objectId** of the meeting organizer.
- `meetingId` is the **id** of the [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-beta) object.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

- If the value of the **allowedRegistrant** property of the [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) object is `organization`, supply the **id** from the external registration system, the registrant's **tenantId** and **userId** in Microsoft Entra ID.
- If the value of the **allowedRegistrant** property of the [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) object is `everyone`, only supply the **id** from the external registration system.

Important

- The **id** from the external registration system can be any form of string.
- You must supply the **@odata.type** property to specify the registrant type. For more details, see the following [examples](#examples).

## Response

If successful, this method returns a `200 OK` response code and an [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Enroll a registrant when the meeting registration has allowedRegistrant set to 'everyone'

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
POST https://graph.microsoft.com/beta/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/registrants
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalMeetingRegistrant",
  "id": "9d96988d-a66a-46ce-aad7-0b245615b297"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ExternalMeetingRegistrant
{
	OdataType = "#microsoft.graph.externalMeetingRegistrant",
	Id = "9d96988d-a66a-46ce-aad7-0b245615b297",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].Registration.Registrants.PostAsync(requestBody);
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
id := "9d96988d-a66a-46ce-aad7-0b245615b297"
requestBody.SetId(&id) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
registrants, err := graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Registration().Registrants().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalMeetingRegistrant meetingRegistrantBase = new ExternalMeetingRegistrant();
meetingRegistrantBase.setOdataType("#microsoft.graph.externalMeetingRegistrant");
meetingRegistrantBase.setId("9d96988d-a66a-46ce-aad7-0b245615b297");
MeetingRegistrantBase result = graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").registration().registrants().post(meetingRegistrantBase);
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
  '@odata.type': '#microsoft.graph.externalMeetingRegistrant',
  id: '9d96988d-a66a-46ce-aad7-0b245615b297'
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/registrants')
	.version('beta')
	.post(meetingRegistrantBase);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ExternalMeetingRegistrant;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalMeetingRegistrant();
$requestBody->setOdataType('#microsoft.graph.externalMeetingRegistrant');
$requestBody->setId('9d96988d-a66a-46ce-aad7-0b245615b297');

$result = $graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->registration()->registrants()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.externalMeetingRegistrant"
	id = "9d96988d-a66a-46ce-aad7-0b245615b297"
}

# A UPN can also be used as -UserId.
New-MgBetaUserOnlineMeetingRegistrationRegistrant -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.external_meeting_registrant import ExternalMeetingRegistrant
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalMeetingRegistrant(
	odata_type = "#microsoft.graph.externalMeetingRegistrant",
	id = "9d96988d-a66a-46ce-aad7-0b245615b297",
)

result = await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').registration.registrants.post(request_body)
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
  "@odata.type": "#microsoft.graph.externalMeetingRegistrant",
  "id": "30494ab7-7338-4592-bfec-a4333be2a0a6",
  "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_NjliNTYxNjktNzAwNi00OTlhLWFmMWEtMGZhY2JjZGM5NmEy%40thread.v2/0?context=%7b%22Tid%22%3a%22909c6581-5130-43e9-88f3-fcb3582cde37%22%2c%22Oid%22%3a%2216664f75-11dc-4870-bec6-38c1aaa81431%22%2c%22prid%22%3a%229d96988d-a66a-46ce-aad7-0b245615b297%22%2c%22isPublic%22%3atrue%7d",
  "userId": null,
  "tenantId": null
}
```

### Example 2: Enroll a registrant when the meeting registration has allowedRegistrant set to 'organization'

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
POST https://graph.microsoft.com/beta/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/registrants
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalMeetingRegistrant",
  "id": "30494ab7-7338-4592-bfec-a4333be2a0a6",
  "tenantId": "909c6581-5130-43e9-88f3-fcb3582cde37",
  "userId": "cc515404-b55c-466e-b896-992c918ecc01"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ExternalMeetingRegistrant
{
	OdataType = "#microsoft.graph.externalMeetingRegistrant",
	Id = "30494ab7-7338-4592-bfec-a4333be2a0a6",
	TenantId = "909c6581-5130-43e9-88f3-fcb3582cde37",
	UserId = "cc515404-b55c-466e-b896-992c918ecc01",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].Registration.Registrants.PostAsync(requestBody);
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
id := "30494ab7-7338-4592-bfec-a4333be2a0a6"
requestBody.SetId(&id) 
tenantId := "909c6581-5130-43e9-88f3-fcb3582cde37"
requestBody.SetTenantId(&tenantId) 
userId := "cc515404-b55c-466e-b896-992c918ecc01"
requestBody.SetUserId(&userId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
registrants, err := graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Registration().Registrants().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalMeetingRegistrant meetingRegistrantBase = new ExternalMeetingRegistrant();
meetingRegistrantBase.setOdataType("#microsoft.graph.externalMeetingRegistrant");
meetingRegistrantBase.setId("30494ab7-7338-4592-bfec-a4333be2a0a6");
meetingRegistrantBase.setTenantId("909c6581-5130-43e9-88f3-fcb3582cde37");
meetingRegistrantBase.setUserId("cc515404-b55c-466e-b896-992c918ecc01");
MeetingRegistrantBase result = graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").registration().registrants().post(meetingRegistrantBase);
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
  '@odata.type': '#microsoft.graph.externalMeetingRegistrant',
  id: '30494ab7-7338-4592-bfec-a4333be2a0a6',
  tenantId: '909c6581-5130-43e9-88f3-fcb3582cde37',
  userId: 'cc515404-b55c-466e-b896-992c918ecc01'
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/registrants')
	.version('beta')
	.post(meetingRegistrantBase);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ExternalMeetingRegistrant;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalMeetingRegistrant();
$requestBody->setOdataType('#microsoft.graph.externalMeetingRegistrant');
$requestBody->setId('30494ab7-7338-4592-bfec-a4333be2a0a6');
$requestBody->setTenantId('909c6581-5130-43e9-88f3-fcb3582cde37');
$requestBody->setUserId('cc515404-b55c-466e-b896-992c918ecc01');

$result = $graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->registration()->registrants()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.CloudCommunications

$params = @{
	"@odata.type" = "#microsoft.graph.externalMeetingRegistrant"
	id = "30494ab7-7338-4592-bfec-a4333be2a0a6"
	tenantId = "909c6581-5130-43e9-88f3-fcb3582cde37"
	userId = "cc515404-b55c-466e-b896-992c918ecc01"
}

# A UPN can also be used as -UserId.
New-MgBetaUserOnlineMeetingRegistrationRegistrant -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.external_meeting_registrant import ExternalMeetingRegistrant
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalMeetingRegistrant(
	odata_type = "#microsoft.graph.externalMeetingRegistrant",
	id = "30494ab7-7338-4592-bfec-a4333be2a0a6",
	tenant_id = "909c6581-5130-43e9-88f3-fcb3582cde37",
	user_id = "cc515404-b55c-466e-b896-992c918ecc01",
)

result = await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').registration.registrants.post(request_body)
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
  "@odata.type": "#microsoft.graph.externalMeetingRegistrant",
  "id": "30494ab7-7338-4592-bfec-a4333be2a0a6",
  "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_NjliNTYxNjktNzAwNi00OTlhLWFmMWEtMGZhY2JjZGM5NmEy%40thread.v2/0?context=%7b%22Tid%22%3a%22909c6581-5130-43e9-88f3-fcb3582cde37%22%2c%22Oid%22%3a%2216664f75-11dc-4870-bec6-38c1aaa81431%22%2c%22prid%22%3a%2230494ab7-7338-4592-bfec-a4333be2a0a6%22%2c%22isPublic%22%3afalse%7d",
  "userId": "909c6581-5130-43e9-88f3-fcb3582cde37",
  "tenantId": "cc515404-b55c-466e-b896-992c918ecc01"
}
```
