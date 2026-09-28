<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-alert-movealerts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# alert: moveAlerts

Namespace: microsoft.graph.security

Move one or more [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) resources to a new or existing [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0).

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
POST /security/alerts_v2/moveAlerts
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
| alertIds | String collection | Required. The IDs of the [alerts](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) to move. |
| incidentId | String | Optional. The ID of the target [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0). A request with `null` creates a new incident. |
| alertComment | String | Optional. A comment to add when moving the alerts. |
| newCorrelationReasons | [microsoft.graph.security.correlationReason](https://learn.microsoft.com/en-us/graph/api/resources/security-correlationreason?view=graph-rest-1.0) | Optional. The correlation reasons to associate with the move operation. This object is a flags enum that allows multiple values to be specified. |

## Response

If successful, this action returns a `200 OK` response code and a [microsoft.graph.security.mergeResponse](https://learn.microsoft.com/en-us/graph/api/resources/security-mergeresponse?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Move alerts to an incident

#### Request

The following example moves two alerts to an existing incident.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/security/alerts_v2/moveAlerts
Content-Type: application/json

{
  "alertIds": [
    "da637551227677560813_-961444813",
    "da637551227677560813_-961444814"
  ],
  "incidentId": "2972395",
  "alertComment": "Moving alerts for investigation consolidation",
  "newCorrelationReasons": "sameAsset, temporalProximity"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Alerts_v2.MicrosoftGraphSecurityMoveAlerts;
using Microsoft.Graph.Models.Security;

var requestBody = new MoveAlertsPostRequestBody
{
	AlertIds = new List<string>
	{
		"da637551227677560813_-961444813",
		"da637551227677560813_-961444814",
	},
	IncidentId = "2972395",
	AlertComment = "Moving alerts for investigation consolidation",
	NewCorrelationReasons = CorrelationReason.SameAsset | CorrelationReason.TemporalProximity,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Alerts_v2.MicrosoftGraphSecurityMoveAlerts.PostAsync(requestBody);
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

requestBody := graphsecurity.NewMoveAlertsPostRequestBody()
alertIds := []string {
	"da637551227677560813_-961444813",
	"da637551227677560813_-961444814",
}
requestBody.SetAlertIds(alertIds)
incidentId := "2972395"
requestBody.SetIncidentId(&incidentId) 
alertComment := "Moving alerts for investigation consolidation"
requestBody.SetAlertComment(&alertComment) 
newCorrelationReasons := graphmodels.SAMEASSET, TEMPORALPROXIMITY_CORRELATIONREASON 
requestBody.SetNewCorrelationReasons(&newCorrelationReasons) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityMoveAlerts, err := graphClient.Security().Alerts_v2().MicrosoftGraphSecurityMoveAlerts().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.alerts_v2.microsoftgraphsecuritymovealerts.MoveAlertsPostRequestBody moveAlertsPostRequestBody = new com.microsoft.graph.security.alerts_v2.microsoftgraphsecuritymovealerts.MoveAlertsPostRequestBody();
LinkedList<String> alertIds = new LinkedList<String>();
alertIds.add("da637551227677560813_-961444813");
alertIds.add("da637551227677560813_-961444814");
moveAlertsPostRequestBody.setAlertIds(alertIds);
moveAlertsPostRequestBody.setIncidentId("2972395");
moveAlertsPostRequestBody.setAlertComment("Moving alerts for investigation consolidation");
moveAlertsPostRequestBody.setNewCorrelationReasons(EnumSet.of(com.microsoft.graph.models.security.CorrelationReason.SameAsset, com.microsoft.graph.models.security.CorrelationReason.TemporalProximity));
var result = graphClient.security().alertsV2().microsoftGraphSecurityMoveAlerts().post(moveAlertsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mergeResponse = {
  alertIds: [
    'da637551227677560813_-961444813',
    'da637551227677560813_-961444814'
  ],
  incidentId: '2972395',
  alertComment: 'Moving alerts for investigation consolidation',
  newCorrelationReasons: 'sameAsset, temporalProximity'
};

await client.api('/security/alerts_v2/moveAlerts')
	.post(mergeResponse);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Alerts_v2\MicrosoftGraphSecurityMoveAlerts\MoveAlertsPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\CorrelationReason;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MoveAlertsPostRequestBody();
$requestBody->setAlertIds(['da637551227677560813_-961444813', 'da637551227677560813_-961444814', 	]);
$requestBody->setIncidentId('2972395');
$requestBody->setAlertComment('Moving alerts for investigation consolidation');
$requestBody->setNewCorrelationReasons(new CorrelationReason('sameAsset, temporalProximity'));

$result = $graphServiceClient->security()->alerts_v2()->microsoftGraphSecurityMoveAlerts()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	alertIds = @(
	"da637551227677560813_-961444813"
"da637551227677560813_-961444814"
)
incidentId = "2972395"
alertComment = "Moving alerts for investigation consolidation"
newCorrelationReasons = "sameAsset, temporalProximity"
}

Move-MgSecurityAlert -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.alerts_v2.microsoft_graph_security_move_alerts.move_alerts_post_request_body import MoveAlertsPostRequestBody
from msgraph.generated.models.correlation_reason import CorrelationReason
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MoveAlertsPostRequestBody(
	alert_ids = [
		"da637551227677560813_-961444813",
		"da637551227677560813_-961444814",
	],
	incident_id = "2972395",
	alert_comment = "Moving alerts for investigation consolidation",
	new_correlation_reasons = CorrelationReason.SameAsset | CorrelationReason.TemporalProximity,
)

result = await graph_client.security.alerts_v2.microsoft_graph_security_move_alerts.post(request_body)
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
