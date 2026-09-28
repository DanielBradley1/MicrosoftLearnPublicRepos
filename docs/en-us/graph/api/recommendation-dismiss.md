<!-- Source: https://learn.microsoft.com/en-us/graph/api/recommendation-dismiss?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# recommendation: dismiss

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Dismiss a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) object that you consider to be inapplicable to your tenant and update its **status** to `dismissed` .

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DirectoryRecommendations.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DirectoryRecommendations.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Administrator
- Security Operator
- Application Administrator
- Cloud Application Administrator

## HTTP request

```http
POST /directory/recommendations/{recommendationId}/dismiss
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that are required with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| dismissReason | String | Explanation for why this recommendation is not applicable to your tenant. |

## Response

If successful, this action returns a `200 OK` response code and a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) in the response body.

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
POST https://graph.microsoft.com/beta/directory/recommendations/0cb31920-84b9-471f-a6fb-468c1a847088_Microsoft.Identity.IAM.Insights.TurnOffPerUserMFA/dismiss
Content-Type: application/json

{
  "dismissReason": "Recommendations is not relevant for my organization because..."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DirectoryNamespace.Recommendations.Item.Dismiss;

var requestBody = new DismissPostRequestBody
{
	DismissReason = "Recommendations is not relevant for my organization because...",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.Recommendations["{recommendation-id}"].Dismiss.PostAsync(requestBody);
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
	  graphdirectory "github.com/microsoftgraph/msgraph-beta-sdk-go/directory"
	  //other-imports
)

requestBody := graphdirectory.NewDismissPostRequestBody()
dismissReason := "Recommendations is not relevant for my organization because..."
requestBody.SetDismissReason(&dismissReason) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
dismiss, err := graphClient.Directory().Recommendations().ByRecommendationId("recommendation-id").Dismiss().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.directory.recommendations.item.dismiss.DismissPostRequestBody dismissPostRequestBody = new com.microsoft.graph.beta.directory.recommendations.item.dismiss.DismissPostRequestBody();
dismissPostRequestBody.setDismissReason("Recommendations is not relevant for my organization because...");
var result = graphClient.directory().recommendations().byRecommendationId("{recommendation-id}").dismiss().post(dismissPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const recommendation = {
  dismissReason: 'Recommendations is not relevant for my organization because...'
};

await client.api('/directory/recommendations/0cb31920-84b9-471f-a6fb-468c1a847088_Microsoft.Identity.IAM.Insights.TurnOffPerUserMFA/dismiss')
	.version('beta')
	.post(recommendation);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Directory\Recommendations\Item\Dismiss\DismissPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DismissPostRequestBody();
$requestBody->setDismissReason('Recommendations is not relevant for my organization because...');

$result = $graphServiceClient->directory()->recommendations()->byRecommendationId('recommendation-id')->dismiss()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	dismissReason = "Recommendations is not relevant for my organization because..."
}

Invoke-MgBetaDismissDirectoryRecommendation -RecommendationId $recommendationId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.directory.recommendations.item.dismiss.dismiss_post_request_body import DismissPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DismissPostRequestBody(
	dismiss_reason = "Recommendations is not relevant for my organization because...",
)

result = await graph_client.directory.recommendations.by_recommendation_id('recommendation-id').dismiss.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#recommendation",
    "@odata.type": "#microsoft.graph.recommendation",
    "id": "0cb31920-84b9-471f-a6fb-468c1a847088_Microsoft.Identity.IAM.Insights.TurnOffPerUserMFA",
    "recommendationType": "turnOffPerUserMFA",
    "createdDateTime": "2022-02-28T02:53:00Z",
    "impactStartDateTime": "2022-02-28T02:53:00Z",
    "postponeUntilDateTime": null,
    "lastModifiedDateTime": "2023-01-20T02:08:33.4580541Z",
    "lastModifiedBy": "b5fa65db-0d2b-4233-8788-ab0213567669",
    "currentScore": 0.0,
    "maxScore": 5.0,
    "displayName": "Convert from per-user MFA to Conditional Access MFA",
    "featureAreas": [
        "conditionalAccess"
    ],
    "insights": "13 users are currently configured for per-user Multi-Factor Authentication (MFA). However, there are 6 users configured for Conditional Access (CA) MFA. The per-user MFA configuration supersedes the MFA settings applied via CA policies, potentially creating unnecessary MFA prompts.",
    "benefits": "Improve user productivity and minimize sign-in time with fewer MFA prompts. Ensure that your most sensitive resources can have the tighest controls, while your least sensitive resources can be more freely accessible.",
    "category": "identityBestPractice",
    "status": "completedByUser",
    "priority": "medium",
    "impactType": "users",
    "remediationImpact": "",
    "actionSteps": [
        {
            "stepNumber": 1,
            "text": "1. To get started, confirm that there is an existing CA policy with an MFA requirement. Ensure that you are covering all resources and users you would like to secure with MFA.",
            "actionUrl": {
                "displayName": "Click here to view your CA policies",
                "url": "https://portal.azure.com/#blade/Microsoft_AAD_IAM/PoliciesTemplateBlade"
            }
        },
        {
            "stepNumber": 2,
            "text": "2. To require MFA via a CA policy, follow the steps in this tutorial.",
            "actionUrl": {
                "displayName": "Secure user sign-in events with Azure AD Multi-Factor Authentication",
                "url": "https://docs.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-azure-mfa?toc=/azure/active-directory/conditional-access/toc.json&bc=/azure/active-directory/conditional-access/breadcrumb/toc.json"
            }
        },
        {
            "stepNumber": 3,
            "text": "3. Ensure that the per-user MFA configuration is turned off",
            "actionUrl": {
                "displayName": "Navigate to MFA settings.",
                "url": "https://account.activedirectory.windowsazure.com/UserManagement/MfaSettings.aspx"
            }
        }
    ]
}
```
