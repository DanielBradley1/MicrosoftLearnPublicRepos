<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-incident-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Update incident

Namespace: microsoft.graph.security

Update the properties of an [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityIncident.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityIncident.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Operator
- Security Administrator

## HTTP request

```http
PATCH /security/incidents/{incidentId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | Owner of the incident, or `null` if no owner is assigned. Free editable text. |
| classification | microsoft.graph.security.alertClassification | The specification for the incident. The possible values are: `unknown`, `falsePositive`, `truePositive`, `informationalExpectedActivity`, `unknownFutureValue`. |
| customTags | String collection | Array of custom tags associated with an incident. |
| description | String | Description of the incident. |
| determination | microsoft.graph.security.alertDetermination | Specifies the determination of the incident. The possible values are: `unknown`, `apt`, `malware`, `securityPersonnel`, `securityTesting`, `unwantedSoftware`, `other`, `multiStagedAttack`, `compromisedAccount`, `phishing`, `maliciousUserActivity`, `notMalicious`, `notEnoughDataToValidate`, `confirmedActivity`, `lineOfBusinessApplication`, `unknownFutureValue`. |
| displayName | String | The incident name. |
| severity | microsoft.graph.security.alertSeverity | Indicates the possible impact on assets. The higher the severity, the bigger the impact. Typically, higher severity items require the most immediate attention. The possible values are: `unknown`, `informational`, `low`, `medium`, `high`, `unknownFutureValue`. |
| resolvingComment | string | User input that explains the resolution of the incident and the classification choice. It contains free editable text. |
| status | microsoft.graph.security.incidentStatus | The status of the incident. The possible values are: `active`, `resolved`, `redirected`, `unknownFutureValue`. |
| summary | String | The overview of an attack. When applicable, the summary contains details of what occurred, impacted assets, and the type of attack. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.security.incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/security/incidents/29
Content-Type: application/json

{
    "classification": "TruePositive",
    "determination": "MultiStagedAttack",
    "customTags": [
      "Demo"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new Incident
{
	Classification = AlertClassification.TruePositive,
	Determination = AlertDetermination.MultiStagedAttack,
	CustomTags = new List<string>
	{
		"Demo",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Incidents["{incident-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewIncident()
classification := graphmodels.TRUEPOSITIVE_ALERTCLASSIFICATION 
requestBody.SetClassification(&classification) 
determination := graphmodels.MULTISTAGEDATTACK_ALERTDETERMINATION 
requestBody.SetDetermination(&determination) 
customTags := []string {
	"Demo",
}
requestBody.SetCustomTags(customTags)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
incidents, err := graphClient.Security().Incidents().ByIncidentId("incident-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.Incident incident = new com.microsoft.graph.models.security.Incident();
incident.setClassification(com.microsoft.graph.models.security.AlertClassification.TruePositive);
incident.setDetermination(com.microsoft.graph.models.security.AlertDetermination.MultiStagedAttack);
LinkedList<String> customTags = new LinkedList<String>();
customTags.add("Demo");
incident.setCustomTags(customTags);
com.microsoft.graph.models.security.Incident result = graphClient.security().incidents().byIncidentId("{incident-id}").patch(incident);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const incident = {
    classification: 'TruePositive',
    determination: 'MultiStagedAttack',
    customTags: [
      'Demo'
    ]
};

await client.api('/security/incidents/29')
	.update(incident);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\Incident;
use Microsoft\Graph\Generated\Models\Security\AlertClassification;
use Microsoft\Graph\Generated\Models\Security\AlertDetermination;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Incident();
$requestBody->setClassification(new AlertClassification('truePositive'));
$requestBody->setDetermination(new AlertDetermination('multiStagedAttack'));
$requestBody->setCustomTags(['Demo', 	]);

$result = $graphServiceClient->security()->incidents()->byIncidentId('incident-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	classification = "TruePositive"
	determination = "MultiStagedAttack"
	customTags = @(
	"Demo"
)
}

Update-MgSecurityIncident -IncidentId $incidentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.incident import Incident
from msgraph.generated.models.alert_classification import AlertClassification
from msgraph.generated.models.alert_determination import AlertDetermination
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Incident(
	classification = AlertClassification.TruePositive,
	determination = AlertDetermination.MultiStagedAttack,
	custom_tags = [
		"Demo",
	],
)

result = await graph_client.security.incidents.by_incident_id('incident-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/incidents/$entity",
    "id": "29",
    "tenantId": "cfcdbe43-297b-4c6b-ac7e-8d7f6befb514",
    "status": "active",
    "incidentWebUrl": "https://security.microsoft.com/incident2/29/overview?tid=cfcdbe43-297b-4c6b-ac7e-8d7f6befb514",
    "redirectIncidentId": null,
    "displayName": "Multi-stage incident involving Execution & Command and control on one endpoint",
    "createdDateTime": "2026-01-22T12:09:23.1433333Z",
    "lastUpdateDateTime": "2026-02-25T16:29:33.1Z",
    "assignedTo": "admin@contoso.com",
    "classification": "truePositive",
    "determination": "multiStagedAttack",
    "severity": "high",
    "customTags": [
        "Demo"
    ],
    "systemTags": [],
    "description": "Microsoft observed Raspberry Robin worm activity spreading through infected USB devices on multiple endpoints in your environment.",
    "lastModifiedBy": "API-App:admin@contoso.com",
    "resolvingComment": null,
    "summary": "Defender Experts has identified malicious activity. This incident has been raised for your awareness and should be investigated as usual.",
    "priorityScore": 100,
    "comments": []
}
```
