<!-- Source: https://learn.microsoft.com/en-us/graph/api/reportroot-getrelyingpartydetailedsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# reportRoot: getRelyingPartyDetailedSummary

Namespace: microsoft.graph

Get a summary of AD FS relying parties information.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Reports.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Reports.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Reports Reader
- Security Reader
- Security Administrator

## HTTP request

```http
GET /reports/getRelyingPartyDetailedSummary(period='parameterValue')
```

## Function parameters

In the request URL, provide the following query parameters with values.

## Optional query parameters

This method supports the `$filter` and `$orderby` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Parameter | Type | Description |
| :--- | :--- | :--- |
| period | String | Specifies the length of time over which the report is aggregated. The supported values are: D1, D7, D30. These values follow the format `Dn` where n represents the number of days over which the report is aggregated. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [relyingPartyDetailedSummary](https://learn.microsoft.com/en-us/graph/api/resources/relyingpartydetailedsummary?view=graph-rest-1.0) collection in the response body.

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
GET https://graph.microsoft.com/v1.0/reports/getRelyingPartyDetailedSummary(period='D7')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.GetRelyingPartyDetailedSummaryWithPeriod("{period}").GetAsGetRelyingPartyDetailedSummaryWithPeriodGetResponseAsync();
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
period := "{period}"
getRelyingPartyDetailedSummary, err := graphClient.Reports().GetRelyingPartyDetailedSummaryWithPeriod(&period).GetAsGetRelyingPartyDetailedSummaryWithPeriodGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.reports().getRelyingPartyDetailedSummaryWithPeriod("{period}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getRelyingPartyDetailedSummary = await client.api('/reports/getRelyingPartyDetailedSummary(period='D7')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->reports()->getRelyingPartyDetailedSummaryWithPeriod('{period}', )->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Reports

Get-MgReportRelyingPartyDetailedSummary -Period $periodId 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.reports.get_relying_party_detailed_summary_with_period("{period}").get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
        {
            "@odata.type": "#microsoft.graph.relyingPartyDetailedSummary",
            "id": "31b45f83-0f5c-40be-80af-02e918f3b55b",
            "relyingPartyId": "https://customer.contoso.com/mgmt",
            "serviceId": "4cce6fff-4ccc-41fe-8521-bce16ea521e9",
            "relyingPartyName": "Contoso",
            "successfulSignInCount": 0,
            "failedSignInCount": 225,
            "totalSignInCount": 225,
            "signInSuccessRate": 0,
            "uniqueUserCount": 1,
            "migrationStatus": "ready",
            "replyUrls": [
                "https://adfshelp.microsoft.com/Contoso/tokenresponse"
            ],
            "migrationValidationDetails": [
                {
                    "name": "AdditionalWSFedEndpointCheckResult",
                    "value": "{\"result\": 0, \"message\": \"No additional WS-Federation endpoints were found.\"}"
                },
                {
                    "name": "AllowedAuthenticationClassReferencesCheckResult",
                    "value": "{\"result\": 0, \"message\": \"AllowedAuthenticationClassReferences is not set up.\"}"
                }
            ]
        }
    ]
}
```
