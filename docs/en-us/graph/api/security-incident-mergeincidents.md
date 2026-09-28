<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-incident-mergeincidents?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# incident: mergeIncidents

Namespace: microsoft.graph.security

Merge multiple [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) resources into a single incident.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityData.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityData.Manage.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- *Security Operator*. Can manage alerts and view, investigate, and respond to security alerts in the Microsoft 365 Defender portal. **This is the least privileged role for this operation.**
- *Security Administrator*. Has permissions to manage security-related features in the Microsoft 365 Defender portal, including managing security threats and alerts.

## HTTP request

```http
POST /security/incidents/mergeIncidents
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| incidentIds | String collection | Required. The IDs of the [incidents](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) to merge. |
| incidentComment | String | Optional. A comment to add to the merged incident. |
| mergeReasons | [microsoft.graph.security.correlationReason](https://learn.microsoft.com/en-us/graph/api/resources/security-correlationreason?view=graph-rest-1.0) | Optional. The correlation reasons for merging the incidents. This object is a flags enum that allows multiple values to be specified. |

## Response

If successful, this action returns a `200 OK` response code and a [microsoft.graph.security.mergeResponse](https://learn.microsoft.com/en-us/graph/api/resources/security-mergeresponse?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Merge incidents

#### Request

The following example merges two incidents.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/security/incidents/mergeIncidents
Content-Type: application/json

{
  "incidentIds": [
    "2972395",
    "2972396"
  ],
  "incidentComment": "Merging related incidents from the same campaign",
  "mergeReasons": "sameCampaign, sameActor"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Incidents.MicrosoftGraphSecurityMergeIncidents;
using Microsoft.Graph.Models.Security;

var requestBody = new MergeIncidentsPostRequestBody
{
	IncidentIds = new List<string>
	{
		"2972395",
		"2972396",
	},
	IncidentComment = "Merging related incidents from the same campaign",
	MergeReasons = CorrelationReason.SameCampaign | CorrelationReason.SameActor,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Incidents.MicrosoftGraphSecurityMergeIncidents.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewMergeIncidentsPostRequestBody()
incidentIds := []string {
	"2972395",
	"2972396",
}
requestBody.SetIncidentIds(incidentIds)
incidentComment := "Merging related incidents from the same campaign"
requestBody.SetIncidentComment(&incidentComment) 
mergeReasons := graphmodels.SAMECAMPAIGN, SAMEACTOR_CORRELATIONREASON 
requestBody.SetMergeReasons(&mergeReasons) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityMergeIncidents, err := graphClient.Security().Incidents().MicrosoftGraphSecurityMergeIncidents().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.incidents.microsoftgraphsecuritymergeincidents.MergeIncidentsPostRequestBody mergeIncidentsPostRequestBody = new com.microsoft.graph.security.incidents.microsoftgraphsecuritymergeincidents.MergeIncidentsPostRequestBody();
LinkedList<String> incidentIds = new LinkedList<String>();
incidentIds.add("2972395");
incidentIds.add("2972396");
mergeIncidentsPostRequestBody.setIncidentIds(incidentIds);
mergeIncidentsPostRequestBody.setIncidentComment("Merging related incidents from the same campaign");
mergeIncidentsPostRequestBody.setMergeReasons(EnumSet.of(com.microsoft.graph.models.security.CorrelationReason.SameCampaign, com.microsoft.graph.models.security.CorrelationReason.SameActor));
var result = graphClient.security().incidents().microsoftGraphSecurityMergeIncidents().post(mergeIncidentsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mergeResponse = {
  incidentIds: [
    '2972395',
    '2972396'
  ],
  incidentComment: 'Merging related incidents from the same campaign',
  mergeReasons: 'sameCampaign, sameActor'
};

await client.api('/security/incidents/mergeIncidents')
	.post(mergeResponse);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Incidents\MicrosoftGraphSecurityMergeIncidents\MergeIncidentsPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\CorrelationReason;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MergeIncidentsPostRequestBody();
$requestBody->setIncidentIds(['2972395', '2972396', 	]);
$requestBody->setIncidentComment('Merging related incidents from the same campaign');
$requestBody->setMergeReasons(new CorrelationReason('sameCampaign, sameActor'));

$result = $graphServiceClient->security()->incidents()->microsoftGraphSecurityMergeIncidents()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	incidentIds = @(
	"2972395"
"2972396"
)
incidentComment = "Merging related incidents from the same campaign"
mergeReasons = "sameCampaign, sameActor"
}

Merge-MgSecurityIncident -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.incidents.microsoft_graph_security_merge_incidents.merge_incidents_post_request_body import MergeIncidentsPostRequestBody
from msgraph.generated.models.correlation_reason import CorrelationReason
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MergeIncidentsPostRequestBody(
	incident_ids = [
		"2972395",
		"2972396",
	],
	incident_comment = "Merging related incidents from the same campaign",
	merge_reasons = CorrelationReason.SameCampaign | CorrelationReason.SameActor,
)

result = await graph_client.security.incidents.microsoft_graph_security_merge_incidents.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "targetIncidentId": "2972395"
}
```
