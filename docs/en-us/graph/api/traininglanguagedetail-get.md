<!-- Source: https://learn.microsoft.com/en-us/graph/api/traininglanguagedetail-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# Get trainingLanguageDetail

Namespace: microsoft.graph

Get the [language details](https://learn.microsoft.com/en-us/graph/api/resources/traininglanguagedetail?view=graph-rest-1.0) about an attack simulation training for a tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AttackSimulation.Read.All | AttackSimulation.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AttackSimulation.Read.All | AttackSimulation.ReadWrite.All |

## HTTP request

```http
GET /security/attackSimulation/trainings/{trainingId}/languageDetails/{trainingLanguageDetailId}?$filter=locale eq 'locale'
```

## Optional query parameters

This method doesn't currently support the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [trainingLanguageDetail](https://learn.microsoft.com/en-us/graph/api/resources/traininglanguagedetail?view=graph-rest-1.0) object in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/security/attackSimulation/trainings/3f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc/languageDetails/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc?$filter=locale eq 'en'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AttackSimulation.Trainings["{training-id}"].LanguageDetails["{trainingLanguageDetail-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "locale eq 'en'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)


requestFilter := "locale eq 'en'"

requestParameters := &graphsecurity.AttackSimulationTrainingsItemLanguageDetailsItemRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphsecurity.AttackSimulationTrainingsItemLanguageDetailsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
languageDetails, err := graphClient.Security().AttackSimulation().Trainings().ByTrainingId("training-id").LanguageDetails().ByTrainingLanguageDetailId("trainingLanguageDetail-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TrainingLanguageDetail result = graphClient.security().attackSimulation().trainings().byTrainingId("{training-id}").languageDetails().byTrainingLanguageDetailId("{trainingLanguageDetail-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "locale eq 'en'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let trainingLanguageDetail = await client.api('/security/attackSimulation/trainings/3f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc/languageDetails/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc')
	.filter('locale eq \'en\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\AttackSimulation\Trainings\Item\LanguageDetails\Item\TrainingLanguageDetailItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TrainingLanguageDetailItemRequestBuilderGetRequestConfiguration();
$queryParameters = TrainingLanguageDetailItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "locale eq 'en'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->attackSimulation()->trainings()->byTrainingId('training-id')->languageDetails()->byTrainingLanguageDetailId('trainingLanguageDetail-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityAttackSimulationTrainingLanguageDetail -TrainingId $trainingId -TrainingLanguageDetailId $trainingLanguageDetailId -Filter "locale eq 'en'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.attack_simulation.trainings.item.language_details.item.training_language_detail_item_request_builder import TrainingLanguageDetailItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TrainingLanguageDetailItemRequestBuilder.TrainingLanguageDetailItemRequestBuilderGetQueryParameters(
		filter = "locale eq 'en'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.attack_simulation.trainings.by_training_id('training-id').language_details.by_training_language_detail_id('trainingLanguageDetail-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "1cdfcb49-1065-46a6-b1c3-672071e20a6b",
  "displayName": "Email phish prevention training",
  "description": "Email phish prevention training",
  "locale": "en-us",
  "createdBy": {
    "email": "alexwaber@contoso.com",
    "id": "1rdfcb49-1065-46a6-b1c3-672071e20a6b",
    "displayName": "Alex Waber"
  },
  "createdDateTime": "2022-01-12T03:15:01.5906699Z",
  "lastModifiedBy": {
    "email": "alexwaber@contoso.com",
    "id": "1rdfcb49-1065-46a6-b1c3-672071e20a6b",
    "displayName": "Alex Waber"
  },
  "lastModifiedDateTime": "2021-10-07T12:23:18.8157586Z",
  "isDefaultLangauge": true
}
```
