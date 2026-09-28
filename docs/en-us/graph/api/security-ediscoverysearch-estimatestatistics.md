<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-estimatestatistics?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# ediscoverySearch: estimateStatistics

Namespace: microsoft.graph.security

Run an estimate of the number of emails and documents in the eDiscovery search. To learn more about searches in eDiscovery, see [Collect data for a case in eDiscovery \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/compliance/collecting-data-for-ediscovery).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to create and manage eDiscovery cases they create, including creating custodians, holds, searches, and other case management tasks. However, eDiscovery Managers can only create and manage the cases they create. **This is the least privileged option for managing their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to access and manage all eDiscovery cases in the organization, configure eDiscovery settings, and manage any case after adding themselves as a member.

Additional roles that provide write access to eDiscovery features:

- **Compliance Administrator**. Includes Case Management, Compliance Search, and Hold permissions.
- **Organization Management**. Includes Case Management, Compliance Search, Hold, and Search And Purge permissions.

The eDiscovery Manager and eDiscovery Administrator roles are part of the Microsoft Purview role groups and provide access to eDiscovery features through [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/purview/edisc-permissions#rbac-roles-related-to-ediscovery).

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/searches/{ediscoverySearchId}/estimateStatistics
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| statisticsOptions | [microsoft.graph.security.statisticsOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryestimateoperation?view=graph-rest-1.0#statisticsoptions-values) | Bitwise options that specify the statistics to generate. The possible values are: `includeRefiners`, `includeQueryStats`, `includeUnindexedStats`, `advancedIndexing`, `locationsWithoutHits`, `unknownFutureValue`. The `advancedIndexing` and `locationsWithoutHits` values are only considered if `includeUnindexedStats` is set. |

## Response

If the estimate is started successfully, this action returns a `202 Accepted` response code. The response contains a `Location` header, which contains the location of the [microsoft.graph.security.estimateStatisticsOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryestimateoperation?view=graph-rest-1.0) that was created to handle the estimate. Check the status of the estimate operation by making a GET request to the value of the `Location` header.

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/searches/c61a5860-d634-4d14-aea7-d82b6f4eb7af/estimatestatistics
Content-Type: application/json

{
  "statisticsOptions": "includeRefiners, includeQueryStats, includeUnindexedStats, advancedIndexing, locationsWithoutHits"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.Searches.Item.MicrosoftGraphSecurityEstimateStatistics;

var requestBody = new EstimateStatisticsPostRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"statisticsOptions" , "includeRefiners, includeQueryStats, includeUnindexedStats, advancedIndexing, locationsWithoutHits"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Searches["{ediscoverySearch-id}"].MicrosoftGraphSecurityEstimateStatistics.PostAsync(requestBody);
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

requestBody := graphsecurity.NewEstimateStatisticsPostRequestBody()
additionalData := map[string]interface{}{
	"statisticsOptions" : "includeRefiners, includeQueryStats, includeUnindexedStats, advancedIndexing, locationsWithoutHits", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Searches().ByEdiscoverySearchId("ediscoverySearch-id").MicrosoftGraphSecurityEstimateStatistics().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityestimatestatistics.EstimateStatisticsPostRequestBody estimateStatisticsPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.searches.item.microsoftgraphsecurityestimatestatistics.EstimateStatisticsPostRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("statisticsOptions", "includeRefiners, includeQueryStats, includeUnindexedStats, advancedIndexing, locationsWithoutHits");
estimateStatisticsPostRequestBody.setAdditionalData(additionalData);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").searches().byEdiscoverySearchId("{ediscoverySearch-id}").microsoftGraphSecurityEstimateStatistics().post(estimateStatisticsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const estimatestatistics = {
  statisticsOptions: 'includeRefiners, includeQueryStats, includeUnindexedStats, advancedIndexing, locationsWithoutHits'
};

await client.api('/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/searches/c61a5860-d634-4d14-aea7-d82b6f4eb7af/estimatestatistics')
	.post(estimatestatistics);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\Searches\Item\MicrosoftGraphSecurityEstimateStatistics\EstimateStatisticsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EstimateStatisticsPostRequestBody();
$additionalData = [
	'statisticsOptions' => 'includeRefiners, includeQueryStats, includeUnindexedStats, advancedIndexing, locationsWithoutHits',
];
$requestBody->setAdditionalData($additionalData);

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->searches()->byEdiscoverySearchId('ediscoverySearch-id')->microsoftGraphSecurityEstimateStatistics()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	statisticsOptions = "includeRefiners, includeQueryStats, includeUnindexedStats, advancedIndexing, locationsWithoutHits"
}

Invoke-MgEstimateSecurityCaseEdiscoveryCaseSearchStatistics -EdiscoveryCaseId $ediscoveryCaseId -EdiscoverySearchId $ediscoverySearchId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.searches.item.microsoft_graph_security_estimate_statistics.estimate_statistics_post_request_body import EstimateStatisticsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EstimateStatisticsPostRequestBody(
	additional_data = {
			"statistics_options" : "includeRefiners, includeQueryStats, includeUnindexedStats, advancedIndexing, locationsWithoutHits",
	}
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').searches.by_ediscovery_search_id('ediscoverySearch-id').microsoft_graph_security_estimate_statistics.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/security/cases/ediscoverycases('4c551bc5-f6f8-435c-8391-d1a08f1ffd5b')/operations('698514cc118f4c8b8cdf1bf0797bf478')
```
