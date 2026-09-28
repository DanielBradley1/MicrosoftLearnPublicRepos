<!-- Source: https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-payloads?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-24 -->

# List payloads

Namespace: microsoft.graph

Get a list of payloads for attack simulation campaigns. This operation expects the mandatory parameter **source** to filter and query the respective data source.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AttackSimulation.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AttackSimulation.Read.All | Not available. |

## HTTP request

```http
GET /security/attackSimulation/payloads?$filter=source eq 'tenant'
```

## Optional query parameters

This method supports the `$count`, `$filter`, `$orderby`, `$skipToken`, `$top`, and `$select` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. You can use the `$filter` and `$orderby` query parameters on the **technique**, **simulationAttackType**, **completionDateTime**, **displayName**, **isAutomated**, **launchDateTime**, and **status** properties.

If the result set spans multiple pages, the response body contains an `@odata.nextLink` that you can use to page through the result set.

The following list shows examples of their use:

```http
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&$count=true
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&{property} eq '{property-value}'
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&{property} eq '{property-value}' &$top=5
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&$filter={property} eq '{property-value}'
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&$filter={property} eq '{property-value}'&$top=5
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&$orderby={property}
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&$skipToken={skipToken}
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&$top=1
GET /security/attackSimulation/payloads?$filter=source eq 'Tenant'&$select={property}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [payload](https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/security/attackSimulation/payloads?$filter=source eq 'Tenant'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AttackSimulation.Payloads.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "source eq 'Tenant'";
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


requestFilter := "source eq 'Tenant'"

requestParameters := &graphsecurity.AttackSimulationPayloadsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphsecurity.AttackSimulationPayloadsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
payloads, err := graphClient.Security().AttackSimulation().Payloads().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PayloadCollectionResponse result = graphClient.security().attackSimulation().payloads().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "source eq 'Tenant'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\AttackSimulation\Payloads\PayloadsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new PayloadsRequestBuilderGetRequestConfiguration();
$queryParameters = PayloadsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "source eq 'Tenant'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->attackSimulation()->payloads()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityAttackSimulationPayload -Filter "source eq 'Tenant'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.attack_simulation.payloads.payloads_request_builder import PayloadsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = PayloadsRequestBuilder.PayloadsRequestBuilderGetQueryParameters(
		filter = "source eq 'Tenant'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.attack_simulation.payloads.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/attackSimulation/payloads?$filter=source eq 'Tenant'",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/security/attackSimulation/payloads?$filter=source+eq+%27Tenant%27&$skiptoken=MyZRVkZCUVVGQlFVRXZMeTh2THk4dkx5OHZPSGxCUVVGQk4yZDZMMFZwZFRjcmF6WjJURk14TWtKVk9WYzNaejA5",
  "value": [
    {
      "id": "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
      "name": "AttackSimTest Payload",
      "description": "AttackSim Test Payload",
      "simulationAttackType": "social",
      "platform": "email",
      "isAutomated": null,
      "status": "draft",
      "source": "tenant",
      "language": "en",
      "predictedCompromiseRate": 20.0,
      "complexity": "medium",
      "technique": "credentialHarvesting",
      "createdBy": {
        "email": "faiza@contoso.com",
        "id": "121212",
        "displayName": "Faiza"
      },
      "createdDateTime": "2022-01-12T03:15:01.5906699Z",
      "lastModifiedBy": {
        "email": "faiza@contoso.com",
        "id": "121212",
        "displayName": "Faiza"
      },
      "lastModifiedDateTime": "2021-10-07T12:23:18.8157586Z",
      "theme": "personalizedOffer",
      "Brand": "microsoft",
      "payloadIndustry": "IT",
      "isCurrentEvent": false,
      "isControversial": false,
      "payloadTags": [],
      "detail": null
    }
  ]
}
```
