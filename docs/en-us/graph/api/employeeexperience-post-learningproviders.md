<!-- Source: https://learn.microsoft.com/en-us/graph/api/employeeexperience-post-learningproviders?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create learningProvider

Namespace: microsoft.graph

Create a new [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) object and register it with Viva Learning using the specified display name and logos for different themes.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LearningProvider.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

> **Note:** The following are required for the user:
> 
> - Viva Suite or Viva Learning license.
> - A supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json), where Knowledge Administrator is the least privileged supported role.

## HTTP request

```http
POST /employeeExperience/learningProviders
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) object.

You can specify the following properties when you create a **learningProvider**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name that appears in Viva Learning. Required. |
| isCourseActivitySyncEnabled | Boolean | Indicates whether a provider can ingest [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) records. The default value is `false`. Set to `true` to make learningCourseActivities available for this provider. |
| loginWebUrl | String | Authentication URL to access the courses for the provider. Optional. |
| longLogoWebUrlForDarkTheme | String | The long logo URL for the dark mode that needs to be a publicly accessible image. This image would be saved to the blob storage of Viva Learning for rendering within the Viva Learning app. Required. |
| longLogoWebUrlForLightTheme | String | The long logo URL for the light mode that needs to be a publicly accessible image. This image would be saved to the blob storage of Viva Learning for rendering within the Viva Learning app. Required. |
| squareLogoWebUrlForDarkTheme | String | The square logo URL for the dark mode that needs to be a publicly accessible image. This image would be saved to the blob storage of Viva Learning for rendering within the Viva Learning app. Required. |
| squareLogoWebUrlForLightTheme | String | The square logo URL for the light mode that needs to be a publicly accessible image. This image would be saved to the blob storage of Viva Learning for rendering within the Viva Learning app. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/employeeExperience/learningProviders
Content-Type: application/json

{
    "displayName": "Microsoft",
    "squareLogoWebUrlForDarkTheme": "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
    "longLogoWebUrlForDarkTheme": "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
    "squareLogoWebUrlForLightTheme": "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
    "longLogoWebUrlForLightTheme": "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
    "loginWebUrl": "https://www.linkedin.com/learning-login/teams",
    "isCourseActivitySyncEnabled": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new LearningProvider
{
	DisplayName = "Microsoft",
	SquareLogoWebUrlForDarkTheme = "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
	LongLogoWebUrlForDarkTheme = "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
	SquareLogoWebUrlForLightTheme = "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
	LongLogoWebUrlForLightTheme = "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
	LoginWebUrl = "https://www.linkedin.com/learning-login/teams",
	IsCourseActivitySyncEnabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.LearningProviders.PostAsync(requestBody);
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

requestBody := graphmodels.NewLearningProvider()
displayName := "Microsoft"
requestBody.SetDisplayName(&displayName) 
squareLogoWebUrlForDarkTheme := "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png"
requestBody.SetSquareLogoWebUrlForDarkTheme(&squareLogoWebUrlForDarkTheme) 
longLogoWebUrlForDarkTheme := "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png"
requestBody.SetLongLogoWebUrlForDarkTheme(&longLogoWebUrlForDarkTheme) 
squareLogoWebUrlForLightTheme := "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png"
requestBody.SetSquareLogoWebUrlForLightTheme(&squareLogoWebUrlForLightTheme) 
longLogoWebUrlForLightTheme := "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png"
requestBody.SetLongLogoWebUrlForLightTheme(&longLogoWebUrlForLightTheme) 
loginWebUrl := "https://www.linkedin.com/learning-login/teams"
requestBody.SetLoginWebUrl(&loginWebUrl) 
isCourseActivitySyncEnabled := true
requestBody.SetIsCourseActivitySyncEnabled(&isCourseActivitySyncEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
learningProviders, err := graphClient.EmployeeExperience().LearningProviders().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningProvider learningProvider = new LearningProvider();
learningProvider.setDisplayName("Microsoft");
learningProvider.setSquareLogoWebUrlForDarkTheme("https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png");
learningProvider.setLongLogoWebUrlForDarkTheme("https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png");
learningProvider.setSquareLogoWebUrlForLightTheme("https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png");
learningProvider.setLongLogoWebUrlForLightTheme("https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png");
learningProvider.setLoginWebUrl("https://www.linkedin.com/learning-login/teams");
learningProvider.setIsCourseActivitySyncEnabled(true);
LearningProvider result = graphClient.employeeExperience().learningProviders().post(learningProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const learningProvider = {
    displayName: 'Microsoft',
    squareLogoWebUrlForDarkTheme: 'https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png',
    longLogoWebUrlForDarkTheme: 'https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png',
    squareLogoWebUrlForLightTheme: 'https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png',
    longLogoWebUrlForLightTheme: 'https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png',
    loginWebUrl: 'https://www.linkedin.com/learning-login/teams',
    isCourseActivitySyncEnabled: true
};

await client.api('/employeeExperience/learningProviders')
	.post(learningProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\LearningProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LearningProvider();
$requestBody->setDisplayName('Microsoft');
$requestBody->setSquareLogoWebUrlForDarkTheme('https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png');
$requestBody->setLongLogoWebUrlForDarkTheme('https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png');
$requestBody->setSquareLogoWebUrlForLightTheme('https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png');
$requestBody->setLongLogoWebUrlForLightTheme('https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png');
$requestBody->setLoginWebUrl('https://www.linkedin.com/learning-login/teams');
$requestBody->setIsCourseActivitySyncEnabled(true);

$result = $graphServiceClient->employeeExperience()->learningProviders()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.learning_provider import LearningProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LearningProvider(
	display_name = "Microsoft",
	square_logo_web_url_for_dark_theme = "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
	long_logo_web_url_for_dark_theme = "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
	square_logo_web_url_for_light_theme = "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
	long_logo_web_url_for_light_theme = "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
	login_web_url = "https://www.linkedin.com/learning-login/teams",
	is_course_activity_sync_enabled = True,
)

result = await graph_client.employee_experience.learning_providers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders/$entity",
    "id": "ba9790ef-21d5-4c17-808c-acda55230253",
    "displayName": "Microsoft",
    "squareLogoWebUrlForDarkTheme": "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
    "longLogoWebUrlForDarkTheme": "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
    "squareLogoWebUrlForLightTheme": "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
    "longLogoWebUrlForLightTheme": "https://support.content.office.net/en-us/media/4c531d12-4c13-4782-a6e4-4b8f991801a3.png",
    "loginWebUrl": "https://www.linkedin.com/learning-login/teams",
    "isCourseActivitySyncEnabled": true
}
```
