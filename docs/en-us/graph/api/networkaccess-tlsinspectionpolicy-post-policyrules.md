<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionpolicy-post-policyrules?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-06 -->

# Create tlsInspectionRule

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [tlsInspectionRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) object in a [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
POST /networkAccess/tlsInspectionPolicies/{tlsInspectionPolicyId}/policyRules
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [tlsInspectionRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) object.

You can specify the following properties when creating a **policyRule**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The display name of the rule. Required. |
| description | String | Optional description explaining the purpose of the rule. |
| action | microsoft.graph.networkaccess.tlsInspectionAction | The action to take when traffic matches this rule. The possible values are: `bypass`, `inspect`. Required. |
| priority | Int64 | The priority of the rule. Rules are evaluated in ascending order of priority. Lower numbers indicate higher priority. Required. |
| settings | [microsoft.graph.networkaccess.tlsInspectionRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrulesettings?view=graph-rest-beta) | Additional settings that configure the rule's behavior. Required. |
| matchingConditions | [microsoft.graph.networkaccess.tlsInspectionMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionmatchingconditions?view=graph-rest-beta) | The conditions that determine when this rule should be applied to traffic. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [tlsInspectionRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/networkAccess/tlsInspectionPolicies/b712c469-e7cd-e7cb-738f-94b199570b0d/policyRules
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionRule",
  "name": "Contoso TLS Rule 1",
  "priority": 100,
  "description": "My TLS rule",
  "action": "inspect",
  "settings": {
    "status": "enabled"
  },
  "matchingConditions": {
    "destinations": [
      {
        "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination",
        "values": [
          "www.contoso.test.com",
          "*.contoso.org"
        ]
      },
      {
        "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionWebCategoriesDestination",
        "values": [
          "Entertainment"
        ]
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new TlsInspectionRule
{
	OdataType = "#microsoft.graph.networkaccess.tlsInspectionRule",
	Name = "Contoso TLS Rule 1",
	Priority = 100L,
	Description = "My TLS rule",
	Settings = new TlsInspectionRuleSettings
	{
		Status = SecurityRuleStatus.Enabled,
	},
	MatchingConditions = new TlsInspectionMatchingConditions
	{
		Destinations = new List<TlsInspectionDestination>
		{
			new TlsInspectionFqdnDestination
			{
				OdataType = "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination",
				Values = new List<string>
				{
					"www.contoso.test.com",
					"*.contoso.org",
				},
			},
			new TlsInspectionDestination
			{
				OdataType = "#microsoft.graph.networkaccess.tlsInspectionWebCategoriesDestination",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"values" , new List<string>
						{
							"Entertainment",
						}
					},
				},
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"action" , "inspect"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.TlsInspectionPolicies["{tlsInspectionPolicy-id}"].PolicyRules.PostAsync(requestBody);
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
	  graphmodelsnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/models/networkaccess"
	  //other-imports
)

requestBody := graphmodelsnetworkaccess.NewPolicyRule()
name := "Contoso TLS Rule 1"
requestBody.SetName(&name) 
priority := int64(100)
requestBody.SetPriority(&priority) 
description := "My TLS rule"
requestBody.SetDescription(&description) 
settings := graphmodelsnetworkaccess.NewTlsInspectionRuleSettings()
status := graphmodels.ENABLED_SECURITYRULESTATUS 
settings.SetStatus(&status) 
requestBody.SetSettings(settings)
matchingConditions := graphmodelsnetworkaccess.NewTlsInspectionMatchingConditions()


tlsInspectionDestination := graphmodelsnetworkaccess.NewTlsInspectionFqdnDestination()
values := []string {
	"www.contoso.test.com",
	"*.contoso.org",
}
tlsInspectionDestination.SetValues(values)
tlsInspectionDestination1 := graphmodelsnetworkaccess.NewTlsInspectionDestination()
additionalData := map[string]interface{}{
	values := []string {
		"Entertainment",
	}
}
tlsInspectionDestination1.SetAdditionalData(additionalData)

destinations := []graphmodelsnetworkaccess.TlsInspectionDestinationable {
	tlsInspectionDestination,
	tlsInspectionDestination1,
}
matchingConditions.SetDestinations(destinations)
requestBody.SetMatchingConditions(matchingConditions)
additionalData := map[string]interface{}{
	"action" : "inspect", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policyRules, err := graphClient.NetworkAccess().TlsInspectionPolicies().ByTlsInspectionPolicyId("tlsInspectionPolicy-id").PolicyRules().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.TlsInspectionRule policyRule = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionRule();
policyRule.setOdataType("#microsoft.graph.networkaccess.tlsInspectionRule");
policyRule.setName("Contoso TLS Rule 1");
policyRule.setPriority(100L);
policyRule.setDescription("My TLS rule");
com.microsoft.graph.beta.models.networkaccess.TlsInspectionRuleSettings settings = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionRuleSettings();
settings.setStatus(com.microsoft.graph.beta.models.networkaccess.SecurityRuleStatus.Enabled);
policyRule.setSettings(settings);
com.microsoft.graph.beta.models.networkaccess.TlsInspectionMatchingConditions matchingConditions = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionMatchingConditions();
LinkedList<com.microsoft.graph.beta.models.networkaccess.TlsInspectionDestination> destinations = new LinkedList<com.microsoft.graph.beta.models.networkaccess.TlsInspectionDestination>();
com.microsoft.graph.beta.models.networkaccess.TlsInspectionFqdnDestination tlsInspectionDestination = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionFqdnDestination();
tlsInspectionDestination.setOdataType("#microsoft.graph.networkaccess.tlsInspectionFqdnDestination");
LinkedList<String> values = new LinkedList<String>();
values.add("www.contoso.test.com");
values.add("*.contoso.org");
tlsInspectionDestination.setValues(values);
destinations.add(tlsInspectionDestination);
com.microsoft.graph.beta.models.networkaccess.TlsInspectionDestination tlsInspectionDestination1 = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionDestination();
tlsInspectionDestination1.setOdataType("#microsoft.graph.networkaccess.tlsInspectionWebCategoriesDestination");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> values1 = new LinkedList<String>();
values1.add("Entertainment");
additionalData.put("values", values1);
tlsInspectionDestination1.setAdditionalData(additionalData);
destinations.add(tlsInspectionDestination1);
matchingConditions.setDestinations(destinations);
policyRule.setMatchingConditions(matchingConditions);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("action", "inspect");
policyRule.setAdditionalData(additionalData1);
com.microsoft.graph.models.networkaccess.PolicyRule result = graphClient.networkAccess().tlsInspectionPolicies().byTlsInspectionPolicyId("{tlsInspectionPolicy-id}").policyRules().post(policyRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const policyRule = {
  '@odata.type': '#microsoft.graph.networkaccess.tlsInspectionRule',
  name: 'Contoso TLS Rule 1',
  priority: 100,
  description: 'My TLS rule',
  action: 'inspect',
  settings: {
    status: 'enabled'
  },
  matchingConditions: {
    destinations: [
      {
        '@odata.type': '#microsoft.graph.networkaccess.tlsInspectionFqdnDestination',
        values: [
          'www.contoso.test.com',
          '*.contoso.org'
        ]
      },
      {
        '@odata.type': '#microsoft.graph.networkaccess.tlsInspectionWebCategoriesDestination',
        values: [
          'Entertainment'
        ]
      }
    ]
  }
};

await client.api('/networkAccess/tlsInspectionPolicies/b712c469-e7cd-e7cb-738f-94b199570b0d/policyRules')
	.version('beta')
	.post(policyRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionRule;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionRuleSettings;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\SecurityRuleStatus;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionMatchingConditions;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionDestination;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionFqdnDestination;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TlsInspectionRule();
$requestBody->setOdataType('#microsoft.graph.networkaccess.tlsInspectionRule');
$requestBody->setName('Contoso TLS Rule 1');
$requestBody->setPriority(100);
$requestBody->setDescription('My TLS rule');
$settings = new TlsInspectionRuleSettings();
$settings->setStatus(new SecurityRuleStatus('enabled'));
$requestBody->setSettings($settings);
$matchingConditions = new TlsInspectionMatchingConditions();
$destinationsTlsInspectionDestination1 = new TlsInspectionFqdnDestination();
$destinationsTlsInspectionDestination1->setOdataType('#microsoft.graph.networkaccess.tlsInspectionFqdnDestination');
$destinationsTlsInspectionDestination1->setValues(['www.contoso.test.com', '*.contoso.org', 	]);
$destinationsArray []= $destinationsTlsInspectionDestination1;
$destinationsTlsInspectionDestination2 = new TlsInspectionDestination();
$destinationsTlsInspectionDestination2->setOdataType('#microsoft.graph.networkaccess.tlsInspectionWebCategoriesDestination');
$additionalData = [
	'values' => [
'Entertainment', ],
];
$destinationsTlsInspectionDestination2->setAdditionalData($additionalData);
$destinationsArray []= $destinationsTlsInspectionDestination2;
$matchingConditions->setDestinations($destinationsArray);

$requestBody->setMatchingConditions($matchingConditions);
$additionalData = [
'action' => 'inspect',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->networkAccess()->tlsInspectionPolicies()->byTlsInspectionPolicyId('tlsInspectionPolicy-id')->policyRules()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	"@odata.type" = "#microsoft.graph.networkaccess.tlsInspectionRule"
	name = "Contoso TLS Rule 1"
	priority = 
	description = "My TLS rule"
	action = "inspect"
	settings = @{
		status = "enabled"
	}
	matchingConditions = @{
		destinations = @(
			@{
				"@odata.type" = "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination"
				values = @(
				"www.contoso.test.com"
			"*.contoso.org"
		)
	}
	@{
		"@odata.type" = "#microsoft.graph.networkaccess.tlsInspectionWebCategoriesDestination"
		values = @(
		"Entertainment"
	)
}
)
}
}

New-MgBetaNetworkAccessTlInspectionPolicyRule -TlsInspectionPolicyId $tlsInspectionPolicyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.tls_inspection_rule import TlsInspectionRule
from msgraph_beta.generated.models.networkaccess.tls_inspection_rule_settings import TlsInspectionRuleSettings
from msgraph_beta.generated.models.security_rule_status import SecurityRuleStatus
from msgraph_beta.generated.models.networkaccess.tls_inspection_matching_conditions import TlsInspectionMatchingConditions
from msgraph_beta.generated.models.networkaccess.tls_inspection_destination import TlsInspectionDestination
from msgraph_beta.generated.models.networkaccess.tls_inspection_fqdn_destination import TlsInspectionFqdnDestination
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TlsInspectionRule(
	odata_type = "#microsoft.graph.networkaccess.tlsInspectionRule",
	name = "Contoso TLS Rule 1",
	priority = 100,
	description = "My TLS rule",
	settings = TlsInspectionRuleSettings(
		status = SecurityRuleStatus.Enabled,
	),
	matching_conditions = TlsInspectionMatchingConditions(
		destinations = [
			TlsInspectionFqdnDestination(
				odata_type = "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination",
				values = [
					"www.contoso.test.com",
					"*.contoso.org",
				],
			),
			TlsInspectionDestination(
				odata_type = "#microsoft.graph.networkaccess.tlsInspectionWebCategoriesDestination",
				additional_data = {
						"values" : [
							"Entertainment",
						],
				}
			),
		],
	),
	additional_data = {
			"action" : "inspect",
	}
)

result = await graph_client.network_access.tls_inspection_policies.by_tls_inspection_policy_id('tlsInspectionPolicy-id').policy_rules.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionRule",
  "id": "ecf99dcc-6575-4d01-83dc-3fa5a940c76b",
  "name": "Contoso TLS Rule 1",
  "priority": 100,
  "description": "My TLS rule",
  "action": "inspect",
  "settings": {
    "status": "enabled"
  },
  "matchingConditions": {
    "destinations": [
      {
        "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination",
        "values": [
          "www.contoso.test.com",
          "*.contoso.org"
        ]
      },
      {
        "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionWebCategoriesDestination",
        "values": [
          "Entertainment"
        ]
      }
    ]
  }
}
```
