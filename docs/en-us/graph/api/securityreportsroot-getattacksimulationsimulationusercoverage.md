<!-- Source: https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationsimulationusercoverage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# securityReportsRoot: getAttackSimulationSimulationUserCoverage

Namespace: microsoft.graph

List [training coverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationtrainingusercoverage?view=graph-rest-1.0) for each tenant user in attack simulation and training campaigns.

This function supports `@odata.nextLink` for pagination.

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
GET /reports/security/getAttackSimulationSimulationUserCoverage
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and an [attackSimulationSimulationUserCoverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationsimulationusercoverage?view=graph-rest-1.0) collection in the response body.

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
GET https://graph.microsoft.com/v1.0/reports/security/getAttackSimulationSimulationUserCoverage
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.Security.GetAttackSimulationSimulationUserCoverage.GetAsGetAttackSimulationSimulationUserCoverageGetResponseAsync();
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
getAttackSimulationSimulationUserCoverage, err := graphClient.Reports().Security().GetAttackSimulationSimulationUserCoverage().GetAsGetAttackSimulationSimulationUserCoverageGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.reports().security().getAttackSimulationSimulationUserCoverage().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAttackSimulationSimulationUserCoverage = await client.api('/reports/security/getAttackSimulationSimulationUserCoverage')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->reports()->security()->getAttackSimulationSimulationUserCoverage()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Reports

Get-MgReportSecurityAttackSimulationUserCoverage
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.reports.security.get_attack_simulation_simulation_user_coverage.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.attackSimulationSimulationUserCoverage)",
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/reports/security/getAttackSimulationSimulationUserCoverage?$skiptoken=rZDNasMwEIRfxei%2bRLFWtgRxwZKsYCil0J9rcCORGlI7yHLbvH3j0pQefCqew7LMsOzHbEL%2fkbRuVzvfxTaeC6ItMpVxBKpKBkh5CcIKhLVUSLUtdaYFSbr3%2fe4%2b9Ccf4vmuefMFuW2GaH3cv3pXO5K0v3HdOf9ZEEqmP1fzuTmOfju27hKgYJbmFSjGNGCuLKRZJYEKIxApo6WQZHWzWYz0sXk5%2bmmdp%2fx78I35EEPbHQryNPgwzJKgqGiKUoK%2boACmQoFMDQdmM56uc2O4qZbt7EcwM65alPS%2fnW1DP56m0r4A",
    "value": [
        {
            "simulationCount": 1063,
            "latestSimulationDateTime": "2022-02-10T10:45:50Z",
            "clickCount": 0,
            "compromisedCount": 0,
            "attackSimulationUser": {
                "userId": "9a00ce98-2c83-41be-89f7-6fdff7950aa9",
                "displayName": "Reed Flores",
                "email": "reed@contoso.com"
            }
        },
        {
            "simulationCount": null,
            "latestSimulationDateTime": null,
            "clickCount": null,
            "compromisedCount": null,
            "attackSimulationUser": {
                "userId": "e911a813-d360-4b1a-b3df-375dde934f2b",
                "displayName": "no role",
                "email": ""
            }
        }
    ]
}
```
