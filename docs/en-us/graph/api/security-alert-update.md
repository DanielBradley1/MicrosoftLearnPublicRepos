<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-alert-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Update alert

Namespace: microsoft.graph

Update the properties of an [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) object in an organization based on the specified alert **id** property.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityAlert.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityAlert.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Operator
- Security Administrator

## HTTP request

```http
PATCH /security/alerts_v2/{alertId}
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
| status | microsoft.graph.security.alertStatus | The status of the alert. The possible values are: `new`, `inProgress`, `resolved`, `unknownFutureValue`. |
| classification | microsoft.graph.security.alertClassification | Specifies the classification of the alert. The possible values are: `unknown`, `falsePositive`, `truePositive`, `informationalExpectedActivity`, `unknownFutureValue`. |
| customDetails | microsoft.graph.security.dictionary | User defined custom fields with string values. |
| determination | microsoft.graph.security.alertDetermination | Specifies the determination of the alert. The possible values are: `unknown`, `apt`, `malware`, `securityPersonnel`, `securityTesting`, `unwantedSoftware`, `other`, `multiStagedAttack`, `compromisedUser`, `phishing`, `maliciousUserActivity`, `clean`, `insufficientData`, `confirmedUserActivity`, `lineOfBusinessApplication`, `unknownFutureValue`. |
| assignedTo | String | Owner of the incident, or `null` if no owner is assigned. |

## Response

If successful, this method returns a `200 OK` response code and an updated [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/security/alerts_v2/da637551227677560813_-961444813
Content-Type: application/json
Content-length: 2450

{
    "assignedTo": "secAdmin@contoso.com",
    "classification": "truePositive",
    "determination": "malware",
    "status": "inProgress"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new Alert
{
	AssignedTo = "secAdmin@contoso.com",
	Classification = AlertClassification.TruePositive,
	Determination = AlertDetermination.Malware,
	Status = AlertStatus.InProgress,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Alerts_v2["{alert-id}"].PatchAsync(requestBody);
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

requestBody := graphmodelssecurity.NewAlert()
assignedTo := "secAdmin@contoso.com"
requestBody.SetAssignedTo(&assignedTo) 
classification := graphmodels.TRUEPOSITIVE_ALERTCLASSIFICATION 
requestBody.SetClassification(&classification) 
determination := graphmodels.MALWARE_ALERTDETERMINATION 
requestBody.SetDetermination(&determination) 
status := graphmodels.INPROGRESS_ALERTSTATUS 
requestBody.SetStatus(&status) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alerts_v2, err := graphClient.Security().Alerts_v2().ByAlertId("alert-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.Alert alert = new com.microsoft.graph.models.security.Alert();
alert.setAssignedTo("secAdmin@contoso.com");
alert.setClassification(com.microsoft.graph.models.security.AlertClassification.TruePositive);
alert.setDetermination(com.microsoft.graph.models.security.AlertDetermination.Malware);
alert.setStatus(com.microsoft.graph.models.security.AlertStatus.InProgress);
com.microsoft.graph.models.security.Alert result = graphClient.security().alertsV2().byAlertId("{alert-id}").patch(alert);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const alert = {
    assignedTo: 'secAdmin@contoso.com',
    classification: 'truePositive',
    determination: 'malware',
    status: 'inProgress'
};

await client.api('/security/alerts_v2/da637551227677560813_-961444813')
	.update(alert);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\Alert;
use Microsoft\Graph\Generated\Models\Security\AlertClassification;
use Microsoft\Graph\Generated\Models\Security\AlertDetermination;
use Microsoft\Graph\Generated\Models\Security\AlertStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Alert();
$requestBody->setAssignedTo('secAdmin@contoso.com');
$requestBody->setClassification(new AlertClassification('truePositive'));
$requestBody->setDetermination(new AlertDetermination('malware'));
$requestBody->setStatus(new AlertStatus('inProgress'));

$result = $graphServiceClient->security()->alerts_v2()->byAlertId('alert-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	assignedTo = "secAdmin@contoso.com"
	classification = "truePositive"
	determination = "malware"
	status = "inProgress"
}

Update-MgSecurityAlertV2 -AlertId $alertId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.alert import Alert
from msgraph.generated.models.alert_classification import AlertClassification
from msgraph.generated.models.alert_determination import AlertDetermination
from msgraph.generated.models.alert_status import AlertStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Alert(
	assigned_to = "secAdmin@contoso.com",
	classification = AlertClassification.TruePositive,
	determination = AlertDetermination.Malware,
	status = AlertStatus.InProgress,
)

result = await graph_client.security.alerts_v2.by_alert_id('alert-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.security.alert",
    "id": "da637551227677560813_-961444813",
    "providerAlertId": "da637551227677560813_-961444813",
    "incidentId": "28282",
    "status": "inProgress",
    "severity": "low",
    "classification": "truePositive",
    "determination": "malware",
    "serviceSource": "microsoftDefenderForEndpoint",
    "detectionSource": "antivirus",
    "detectorId": "e0da400f-affd-43ef-b1d5-afc2eb6f2756",
    "tenantId": "b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
    "title": "Suspicious execution of hidden file",
    "description": "A hidden file has been launched. This activity could indicate a compromised host. Attackers often hide files associated with malicious tools to evade file system inspection and defenses.",
    "recommendedActions": "Collect artifacts and determine scope\n�\tReview the machine timeline for suspicious activities that may have occurred before and after the time of the alert, and record additional related artifacts (files, IPs/URLs) \n�\tLook for the presence of relevant artifacts on other systems. Identify commonalities and differences between potentially compromised systems.\n�\tSubmit relevant files for deep analysis and review resulting detailed behavioral information.\n�\tSubmit undetected files to the MMPC malware portal\n\nInitiate containment & mitigation \n�\tContact the user to verify intent and initiate local remediation actions as needed.\n�\tUpdate AV signatures and run a full scan. The scan might reveal and remove previously-undetected malware components.\n�\tEnsure that the machine has the latest security updates. In particular, ensure that you have installed the latest software, web browser, and Operating System versions.\n�\tIf credential theft is suspected, reset all relevant users passwords.\n�\tBlock communication with relevant URLs or IPs at the organization�s perimeter.",
    "category": "DefenseEvasion",
    "assignedTo": "secAdmin@contoso.com",
    "alertWebUrl": "https://security.microsoft.com/alerts/da637551227677560813_-961444813?tid=b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
    "incidentWebUrl": "https://security.microsoft.com/incidents/28282?tid=b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
    "actorDisplayName": null,
    "threatDisplayName": null,
    "threatFamilyName": null,
    "mitreTechniques": [
        "T1564.001"
    ],
    "createdDateTime": "2021-04-27T12:19:27.7211305Z",
    "lastUpdateDateTime": "2021-05-02T14:19:01.3266667Z",
    "resolvedDateTime": null,
    "firstActivityDateTime": "2021-04-26T07:45:50.116Z",
    "lastActivityDateTime": "2021-05-02T07:56:58.222Z",
    "comments": [],
    "evidence": [],
    "systemTags" : [],
    "customDetails": {
      "threatIntelligenceVerdict": "KnownMalicious",
      "matchedThreatActor": "DEV-0537",
      "automationPlaybookName": "BlockIPAndIsolateHost",
      "automationExecutionStatus": "Succeeded",
      "iocTypeMatched": "IPAddress",
      "firstSeenInOrg": "2026-04-14T08:12:00Z"
    }
}
```
