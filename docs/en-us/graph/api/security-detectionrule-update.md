<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-detectionrule-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Update detectionRule

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CustomDetection.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CustomDetection.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a role that grants the permissions required for this operation. Custom detection rules use the Microsoft Defender XDR Unified role-based access control \(RBAC\) model. The following roles are supported:

- **Detection tuning \(Manage\)** - A [Microsoft Defender XDR Unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details) permission that grants manage access to detections in the Microsoft Defender portal, including custom detections, alert tuning, and threat indicators of compromise.
- **Security Administrator** - A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#security-administrator) that grants manage permissions across Microsoft Defender portals and services.
- **Security Operator** - A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#security-operator). Sufficient for managing custom detection rules only when role-based access control is turned off in Microsoft Defender for Endpoint. If RBAC is configured, the **Manage Security Settings** permission for Defender for Endpoint is also required.

Additional workload-specific permissions might be required to manage rules that target data from specific Defender workloads \(for example, Defender for Endpoint, Defender for Office 365\). For more information, see [Required permissions for managing custom detections](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules#required-permissions-for-managing-custom-detections).

## HTTP request

```http
PATCH /security/rules/detectionRules/{detectionRuleId}
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
| description | String | A user-supplied description of the detection rule. |
| detectionAction | [microsoft.graph.security.detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta) | The actions taken when a detection is made by this rule, including the alert that is created and any automated response actions. |
| displayName | String | The display name of the rule. |
| isEnabled | Boolean | **Deprecated.** Use **status** instead. The `isEnabled` property will be removed from this resource on 2026-10-01. |
| queryCondition | [microsoft.graph.security.queryCondition](https://learn.microsoft.com/en-us/graph/api/resources/security-querycondition?view=graph-rest-beta) | The advanced hunting query that defines the detection logic of this rule. |
| schedule | [microsoft.graph.security.ruleSchedule](https://learn.microsoft.com/en-us/graph/api/resources/security-ruleschedule?view=graph-rest-beta) | The triggering schedule of this rule. |
| status | [microsoft.graph.security.detectionRuleStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#detectionrulestatus-values) | The current run status of the rule. The possible values are: `enabled`, `disabled`, `autoDisabled`, `unknownFutureValue`. |

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object in the response body.

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
PATCH https://graph.microsoft.com/beta/security/rules/detectionRules/office-encoded-powershell
Content-Type: application/json

{
  "status": "disabled",
  "queryCondition": {
    "queryText": "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new DetectionRule
{
	Status = DetectionRuleStatus.Disabled,
	QueryCondition = new QueryCondition
	{
		QueryText = "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Rules.DetectionRules["{detectionRule-id}"].PatchAsync(requestBody);
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
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewDetectionRule()
status := graphmodels.DISABLED_DETECTIONRULESTATUS 
requestBody.SetStatus(&status) 
queryCondition := graphmodelssecurity.NewQueryCondition()
queryText := "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
queryCondition.SetQueryText(&queryText) 
requestBody.SetQueryCondition(queryCondition)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
detectionRules, err := graphClient.Security().Rules().DetectionRules().ByDetectionRuleId("detectionRule-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.DetectionRule detectionRule = new com.microsoft.graph.beta.models.security.DetectionRule();
detectionRule.setStatus(com.microsoft.graph.beta.models.security.DetectionRuleStatus.Disabled);
com.microsoft.graph.beta.models.security.QueryCondition queryCondition = new com.microsoft.graph.beta.models.security.QueryCondition();
queryCondition.setQueryText("DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'");
detectionRule.setQueryCondition(queryCondition);
com.microsoft.graph.models.security.DetectionRule result = graphClient.security().rules().detectionRules().byDetectionRuleId("{detectionRule-id}").patch(detectionRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const detectionRule = {
  status: 'disabled',
  queryCondition: {
    queryText: 'DeviceProcessEvents | where InitiatingProcessFileName in~ (\'winword.exe\',\'excel.exe\',\'outlook.exe\') | where FileName == \'powershell.exe\' | where ProcessCommandLine has \'-enc\''
  }
};

await client.api('/security/rules/detectionRules/office-encoded-powershell')
	.version('beta')
	.update(detectionRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\DetectionRule;
use Microsoft\Graph\Beta\Generated\Models\Security\DetectionRuleStatus;
use Microsoft\Graph\Beta\Generated\Models\Security\QueryCondition;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DetectionRule();
$requestBody->setStatus(new DetectionRuleStatus('disabled'));
$queryCondition = new QueryCondition();
$queryCondition->setQueryText('DeviceProcessEvents | where InitiatingProcessFileName in~ (\'winword.exe\',\'excel.exe\',\'outlook.exe\') | where FileName == \'powershell.exe\' | where ProcessCommandLine has \'-enc\'');
$requestBody->setQueryCondition($queryCondition);

$result = $graphServiceClient->security()->rules()->detectionRules()->byDetectionRuleId('detectionRule-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	status = "disabled"
	queryCondition = @{
		queryText = "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
	}
}

Update-MgBetaSecurityRuleDetectionRule -DetectionRuleId $detectionRuleId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.detection_rule import DetectionRule
from msgraph_beta.generated.models.detection_rule_status import DetectionRuleStatus
from msgraph_beta.generated.models.security.query_condition import QueryCondition
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DetectionRule(
	status = DetectionRuleStatus.Disabled,
	query_condition = QueryCondition(
		query_text = "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'",
	),
)

result = await graph_client.security.rules.detection_rules.by_detection_rule_id('detectionRule-id').patch(request_body)
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
  "@odata.type": "#microsoft.graph.security.detectionRule",
  "id": "office-encoded-powershell",
  "displayName": "Suspicious encoded PowerShell from Office",
  "description": "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.",
  "status": "disabled",
  "createdBy": "alice@contoso.com",
  "createdDateTime": "2026-05-25T10:15:00Z",
  "lastModifiedBy": "alice@contoso.com",
  "lastModifiedDateTime": "2026-05-28T14:30:00Z",
  "queryCondition": {
    "queryText": "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
  },
  "schedule": {
    "frequency": "PT1H"
  },
  "detectionAction": {
    "alertTemplate": {
      "title": "Suspicious encoded PowerShell from Office",
      "description": "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.",
      "severity": "high",
      "recommendedActions": "Investigate the parent Office document, isolate the device, and review the user's recent email activity.",
      "entityMappings": {
        "accounts": [
          {
            "nameColumn": "AccountName",
            "sidColumn": "AccountSid"
          }
        ]
      },
      "tactics": [
        {
          "tactic": "Execution",
          "techniques": [
            {
              "technique": "T1059.001"
            }
          ]
        }
      ]
    },
    "automatedActions": {
      "isolateDevices": [
        {
          "deviceIdColumn": "DeviceId",
          "isolationType": "full"
        }
      ],
      "initiateInvestigations": [
        {
          "deviceIdColumn": "DeviceId"
        }
      ]
    }
  }
}
```
