<!-- Source: https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alert-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update alert

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a Microsoft Entra health monitoring [alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) object. For example, change an alert's state from active to resolved.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | HealthMonitoringAlert.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | HealthMonitoringAlert.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Administrator
- Security Operator
- Helpdesk Administrator

## HTTP request

```http
PATCH /reports/healthMonitoring/alerts/{alertId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Prefer: include-unknown-enum-members | Enables evolvable enum values beyond the sentinel value. For more information, see [Best practices for working with Microsoft Graph](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Optional. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| state | microsoft.graph.healthMonitoring.alertState | The current lifecycle state of the alert. The possible values are: `active`, `resolved`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.healthMonitoring.alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) object in the response body.

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
PATCH https://graph.microsoft.com/beta/reports/healthMonitoring/alerts/{alertId}
Content-Type: application/json

{
  "state": "resolved"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.HealthMonitoring;

var requestBody = new Alert
{
	State = AlertState.Resolved,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.HealthMonitoring.Alerts["{alert-id}"].PatchAsync(requestBody);
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
	  graphmodelshealthmonitoring "github.com/microsoftgraph/msgraph-beta-sdk-go/models/healthmonitoring"
	  //other-imports
)

requestBody := graphmodelshealthmonitoring.NewAlert()
state := graphmodels.RESOLVED_ALERTSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts, err := graphClient.Reports().HealthMonitoring().Alerts().ByAlertId("alert-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.healthmonitoring.Alert alert = new com.microsoft.graph.beta.models.healthmonitoring.Alert();
alert.setState(com.microsoft.graph.beta.models.healthmonitoring.AlertState.Resolved);
com.microsoft.graph.models.healthmonitoring.Alert result = graphClient.reports().healthMonitoring().alerts().byAlertId("{alert-id}").patch(alert);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const alert = {
  state: 'resolved'
};

await client.api('/reports/healthMonitoring/alerts/{alertId}')
	.version('beta')
	.update(alert);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\HealthMonitoring\Alert;
use Microsoft\Graph\Beta\Generated\Models\HealthMonitoring\AlertState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Alert();
$requestBody->setState(new AlertState('resolved'));

$result = $graphServiceClient->reports()->healthMonitoring()->alerts()->byAlertId('alert-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

$params = @{
	state = "resolved"
}

Update-MgBetaReportHealthMonitoringAlert -AlertId $alertId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.health_monitoring.alert import Alert
from msgraph_beta.generated.models.alert_state import AlertState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Alert(
	state = AlertState.Resolved,
)

result = await graph_client.reports.health_monitoring.alerts.by_alert_id('alert-id').patch(request_body)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#reports/healthMonitoring/alerts/$entity",
  "id": "0c56dfcb-13db-4128-bda2-fc3e42742467",
  "alertType": "mfaSignInFailure",
  "scenario": "mfa",
  "category": "authentication",
  "createdDateTime": "2024-06-19T11:23:44.1234567Z",
  "state": "resolved",
  "enrichment": {
    "state": "enriched",
    "impacts": [
      {
        "@odata.type": "#microsoft.graph.healthMonitoring.userImpactSummary",
        "resourceType": "user",
        "impactedCount": 143,
        "impactedCountLimitExceeded": false
      },
      {
        "@odata.type": "#microsoft.graph.healthMonitoring.applicationImpactSummary",
        "resourceType": "application",
        "impactedCount": 1,
        "impactedCountLimitExceeded": true
      }
    ],
    "supportingData": {
      "signIns": "https://graph.microsoft.com/beta/auditLogs/signIns?$filter=((status/errorCode eq 500121) and createdDateTime gt 2024-06-08T11:23:44.1234567Z and createdDateTime le 2024-06-19T11:23:44.1234567Z and (signInEventTypes/any(t:t eq 'interactiveUser' or t eq 'noninteractiveUser')))",
      "audits": "https://graph.microsoft.com/beta/auditLogs/directoryaudits?$filter=(activityDateTime ge 2024-06-08T11:23:44.1234567Z and activityDateTime le 2024-06-19T11:23:44.1234567Z)&$top=50&$orderby=activityDateTime desc"
    }
  },
  "signals": {
    "mfaSignInFailure": "https://graph.microsoft.com/beta/reports/serviceActivity/getMetricsForMfaSignInFailure(inclusiveIntervalStartDateTime=2024-06-08T11:23:44.1234567Z, exclusiveIntervalEndDateTime=2024-06-19T11:23:44.1234567Z, aggregationIntervalInMinutes=5)"
  },
  "documentation": {
    "troubleshootingGuide": "https://go.microsoft.com/fwlink/?linkid=2280158"
  }
}
```
