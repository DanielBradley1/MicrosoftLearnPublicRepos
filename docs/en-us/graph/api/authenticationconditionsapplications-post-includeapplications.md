<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationconditionsapplications-post-includeapplications?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Add includeApplication \(to a user flow\)

Namespace: microsoft.graph

Add or link an application to a user flow, or [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0). This enables the authentication experience defined by the user flow to be enabled for the application. An application can only be linked to one user flow. The app must have an associated service principal in the tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EventListener.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EventListener.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External ID User Flow Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identity/authenticationEventsFlows/{authenticationEventsFlow-id}/conditions/applications/includeApplications
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON representation of the **appId** of the service principal to associate with the user flow.

## Response

If successful, this method returns a `201 Created` response code and a new [authenticationConditionApplication](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditionapplication?view=graph-rest-1.0) object in the response body. If unsuccessful, a `4xx` error is returned with specific details.

## Examples

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
POST https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows/0313cc37-d421-421d-857b-87804d61e33e/conditions/applications/includeApplications
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.authenticationConditionApplication",
    "appId": "63856651-13d9-4784-9abf-20758d509e19"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AuthenticationConditionApplication
{
	OdataType = "#microsoft.graph.authenticationConditionApplication",
	AppId = "63856651-13d9-4784-9abf-20758d509e19",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows["{authenticationEventsFlow-id}"].Conditions.Applications.IncludeApplications.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationConditionApplication()
appId := "63856651-13d9-4784-9abf-20758d509e19"
requestBody.SetAppId(&appId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
includeApplications, err := graphClient.Identity().AuthenticationEventsFlows().ByAuthenticationEventsFlowId("authenticationEventsFlow-id").Conditions().Applications().IncludeApplications().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationConditionApplication authenticationConditionApplication = new AuthenticationConditionApplication();
authenticationConditionApplication.setOdataType("#microsoft.graph.authenticationConditionApplication");
authenticationConditionApplication.setAppId("63856651-13d9-4784-9abf-20758d509e19");
AuthenticationConditionApplication result = graphClient.identity().authenticationEventsFlows().byAuthenticationEventsFlowId("{authenticationEventsFlow-id}").conditions().applications().includeApplications().post(authenticationConditionApplication);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationConditionApplication = {
    '@odata.type': '#microsoft.graph.authenticationConditionApplication',
    appId: '63856651-13d9-4784-9abf-20758d509e19'
};

await client.api('/identity/authenticationEventsFlows/0313cc37-d421-421d-857b-87804d61e33e/conditions/applications/includeApplications')
	.post(authenticationConditionApplication);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AuthenticationConditionApplication;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AuthenticationConditionApplication();
$requestBody->setOdataType('#microsoft.graph.authenticationConditionApplication');
$requestBody->setAppId('63856651-13d9-4784-9abf-20758d509e19');

$result = $graphServiceClient->identity()->authenticationEventsFlows()->byAuthenticationEventsFlowId('authenticationEventsFlow-id')->conditions()->applications()->includeApplications()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.authenticationConditionApplication"
	appId = "63856651-13d9-4784-9abf-20758d509e19"
}

New-MgIdentityAuthenticationEventFlowIncludeApplication -AuthenticationEventsFlowId $authenticationEventsFlowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.authentication_condition_application import AuthenticationConditionApplication
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AuthenticationConditionApplication(
	odata_type = "#microsoft.graph.authenticationConditionApplication",
	app_id = "63856651-13d9-4784-9abf-20758d509e19",
)

result = await graph_client.identity.authentication_events_flows.by_authentication_events_flow_id('authenticationEventsFlow-id').conditions.applications.include_applications.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows('0313cc37-d421-421d-857b-87804d61e33e')/conditions/applications/includeApplications/$entity",
    "appId": "63856651-13d9-4784-9abf-20758d509e19"
}
```
