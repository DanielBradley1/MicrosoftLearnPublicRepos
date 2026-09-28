<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-collaborationroot-list-analyzedemails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# List analyzedEmails

Namespace: microsoft.graph.security

Get a list of [analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0) objects and their properties.

This API allows Security Operations teams to have direct access to hunt \(query\) for threats, IOCs, attack vectors, and evidences for a tenant. It is a powerful, near real-time tool to help Security Operations teams investigate and respond to threats. It consists of email metadata, verdict information, related underlying entities \(attachments/URL\), filters, and more.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityAnalyzedMessage.Read.All | SecurityAnalyzedMessage.ReadWrite.All |

## HTTP request

```http
GET /security/collaboration/analyzedEmails
```

## Query parameters

In the request URL, you can optionally provide the following query parameters with values to narrow the search window.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startTime | DateTime | Optional. The start time of the email search. |
| endTime | DateTime | Optional. The end time of the email search. |

### OData query parameters

This method supports the following OData query parameters to help customize the response: `$count`, `$filter`, `$skiptoken`, `$top`. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The following example shows how to use the `$filter` parameter to customize the response.

```http
GET /security/collaboration/analyzedEmails?startTime=2024-02-18&endTime=2024-02-20&$filter=networkMessageId eq 'bde1f764-bbf4-5673-fbba-0asdhsgfhf1'
GET /security/collaboration/analyzedEmails?startTime=2024-02-18&endTime=2024-02-20&$filter=networkMessageId eq 'bde1f764-bbf4-5673-fbba-0asdhsgfhf1' and recipientEmailAddress eq 'tomas.richardson@contoso.com'
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/security/collaboration/analyzedEmails?startTime=2024-02-18&endTime=2024-02-20
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Collaboration.AnalyzedEmails.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.StartTime = "2024-02-18";
	requestConfiguration.QueryParameters.EndTime = "2024-02-20";
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


requestStartTime := "2024-02-18"
requestEndTime := "2024-02-20"

requestParameters := &graphsecurity.CollaborationAnalyzedEmailsRequestBuilderGetQueryParameters{
	StartTime: &requestStartTime,
	EndTime: &requestEndTime,
}
configuration := &graphsecurity.CollaborationAnalyzedEmailsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
analyzedEmails, err := graphClient.Security().Collaboration().AnalyzedEmails().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.AnalyzedEmailCollectionResponse result = graphClient.security().collaboration().analyzedEmails().get(requestConfiguration -> {
	requestConfiguration.queryParameters.startTime = "2024-02-18";
	requestConfiguration.queryParameters.endTime = "2024-02-20";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let analyzedEmails = await client.api('/security/collaboration/analyzedEmails?startTime=2024-02-18&endTime=2024-02-20')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Collaboration\AnalyzedEmails\AnalyzedEmailsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AnalyzedEmailsRequestBuilderGetRequestConfiguration();
$queryParameters = AnalyzedEmailsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->startTime = "2024-02-18";
$queryParameters->endTime = "2024-02-20";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->collaboration()->analyzedEmails()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityCollaborationAnalyzedEmail -Starttime "2024-02-18" -Endtime "2024-02-20" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.collaboration.analyzed_emails.analyzed_emails_request_builder import AnalyzedEmailsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AnalyzedEmailsRequestBuilder.AnalyzedEmailsRequestBuilderGetQueryParameters(
		start_time = "2024-02-18",
		end_time = "2024-02-20",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.collaboration.analyzed_emails.get(request_configuration = request_configuration)
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
      "@odata.type": "#microsoft.graph.security.analyzedEmail",
      "id": "String",
      "loggedDateTime": "Datetime",
      "networkMessageId": "String",
      "internetMessageId": "String",
      "senderDetail": {
        "@odata.type": "microsoft.graph.security.analyzedEmailSenderDetail"
      },
      "recipientEmailAddress": "String",
      "distributionList": "String",
      "subject": "String",
      "returnPath": "String",
      "directionality": "microsoft.graph.security.antispamDirectionality",
      "originalDelivery": {
        "@odata.type": "microsoft.graph.security.analyzedEmailDeliveryDetail"
      },
      "latestDelivery": {
        "@odata.type": "microsoft.graph.security.analyzedEmailDeliveryDetail"
      },
      "attachments": [
        {
          "@odata.type": "microsoft.graph.security.analyzedEmailAttachment"
        }
      ],
      "urls": [
        {
          "@odata.type": "microsoft.graph.security.analyzedEmailUrl"
        }
      ],
      "language": "String",
      "sizeInBytes": "Integer",
      "alertIds": [
        "String"
      ],
      "exchangeTransportRules": [
        {
          "@odata.type": "microsoft.graph.security.analyzedEmailExchangeTransportRuleInfo"
        }
      ],
      "overrideSources": [
        "String"
      ],
      "threatTypes": [
        "microsoft.graph.security.threatType"
      ],
      "detectionMethods": [
        "String"
      ],
      "contexts": [
        "String"
      ],
      "authenticationDetails": {
        "@odata.type": "microsoft.graph.security.analyzedEmailAuthenticationDetail"
      },
      "phishConfidenceLevel": "String",
      "spamConfidenceLevel": "String",
      "bulkComplaintLevel": "String",
      "emailClusterId": "String",
      "policyAction": "String",
      "policy": "String",
      "timelineEvents": [
        {
          "@odata.type": "microsoft.graph.security.timelineEvent"
        }
      ],
      "threatDetectionDetails": [
        {
          "@odata.type": "microsoft.graph.security.threatDetectionDetail"
        }
      ],
      "primaryOverrideSource": "String",
      "inboundConnectorFormattedName": "String",
      "policyType": "String",
      "clientType": "String",
      "dlpRules": [
        {
          "@odata.type": "microsoft.graph.security.analyzedEmailDlpRuleInfo"
        }
      ],
      "forwardingDetail": "String",
      "recipientDetail": {
        "@odata.type": "microsoft.graph.security.analyzedEmailRecipientDetail"
      }
    }
  ]
}
```
