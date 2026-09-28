<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicy-post-policyrules?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create filteringPolicy

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) object.

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
POST /networkaccess/filteringPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) object.

You can specify the following properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Display Name. Required. |
| policyRules | Collection\(microsoft.graph.networkaccess.policyRule\) | policyRules maintains the definition of the policy ruleset that makes up the core definition of a policy. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/networkaccess/filteringPolicies
Content-Type: application/json

{
    "name": "Block Social",
    "policyRules": [
        {
            "@odata.type": "#microsoft.graph.networkaccess.webCategoryFilteringRule",
            "name": "Block Social",
            "ruleType": "webCategory",
            "destinations": [
                {
                    "@odata.type": "#microsoft.graph.networkaccess.webCategory",
                    "name": "SocialNetworking"
                }
            ]
        }
    ],
    "action": "block",
    "description": "Block Social Sites",
    "@odata.type": "#microsoft.graph.networkaccess.filteringPolicy"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new FilteringPolicy
{
	Name = "Block Social",
	PolicyRules = new List<PolicyRule>
	{
		new WebCategoryFilteringRule
		{
			OdataType = "#microsoft.graph.networkaccess.webCategoryFilteringRule",
			Name = "Block Social",
			RuleType = NetworkDestinationType.WebCategory,
			Destinations = new List<RuleDestination>
			{
				new WebCategory
				{
					OdataType = "#microsoft.graph.networkaccess.webCategory",
					Name = "SocialNetworking",
				},
			},
		},
	},
	Action = FilteringPolicyAction.Block,
	Description = "Block Social Sites",
	OdataType = "#microsoft.graph.networkaccess.filteringPolicy",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.FilteringPolicies.PostAsync(requestBody);
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

requestBody := graphmodelsnetworkaccess.NewFilteringPolicy()
name := "Block Social"
requestBody.SetName(&name) 


policyRule := graphmodelsnetworkaccess.NewWebCategoryFilteringRule()
name := "Block Social"
policyRule.SetName(&name) 
ruleType := graphmodels.WEBCATEGORY_NETWORKDESTINATIONTYPE 
policyRule.SetRuleType(&ruleType) 


ruleDestination := graphmodelsnetworkaccess.NewWebCategory()
name := "SocialNetworking"
ruleDestination.SetName(&name) 

destinations := []graphmodelsnetworkaccess.RuleDestinationable {
	ruleDestination,
}
policyRule.SetDestinations(destinations)

policyRules := []graphmodelsnetworkaccess.PolicyRuleable {
	policyRule,
}
requestBody.SetPolicyRules(policyRules)
action := graphmodels.BLOCK_FILTERINGPOLICYACTION 
requestBody.SetAction(&action) 
description := "Block Social Sites"
requestBody.SetDescription(&description) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
filteringPolicies, err := graphClient.NetworkAccess().FilteringPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.FilteringPolicy filteringPolicy = new com.microsoft.graph.beta.models.networkaccess.FilteringPolicy();
filteringPolicy.setName("Block Social");
LinkedList<com.microsoft.graph.beta.models.networkaccess.PolicyRule> policyRules = new LinkedList<com.microsoft.graph.beta.models.networkaccess.PolicyRule>();
com.microsoft.graph.beta.models.networkaccess.WebCategoryFilteringRule policyRule = new com.microsoft.graph.beta.models.networkaccess.WebCategoryFilteringRule();
policyRule.setOdataType("#microsoft.graph.networkaccess.webCategoryFilteringRule");
policyRule.setName("Block Social");
policyRule.setRuleType(com.microsoft.graph.beta.models.networkaccess.NetworkDestinationType.WebCategory);
LinkedList<com.microsoft.graph.beta.models.networkaccess.RuleDestination> destinations = new LinkedList<com.microsoft.graph.beta.models.networkaccess.RuleDestination>();
com.microsoft.graph.beta.models.networkaccess.WebCategory ruleDestination = new com.microsoft.graph.beta.models.networkaccess.WebCategory();
ruleDestination.setOdataType("#microsoft.graph.networkaccess.webCategory");
ruleDestination.setName("SocialNetworking");
destinations.add(ruleDestination);
policyRule.setDestinations(destinations);
policyRules.add(policyRule);
filteringPolicy.setPolicyRules(policyRules);
filteringPolicy.setAction(com.microsoft.graph.beta.models.networkaccess.FilteringPolicyAction.Block);
filteringPolicy.setDescription("Block Social Sites");
filteringPolicy.setOdataType("#microsoft.graph.networkaccess.filteringPolicy");
com.microsoft.graph.models.networkaccess.FilteringPolicy result = graphClient.networkAccess().filteringPolicies().post(filteringPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const filteringPolicy = {
    name: 'Block Social',
    policyRules: [
        {
            '@odata.type': '#microsoft.graph.networkaccess.webCategoryFilteringRule',
            name: 'Block Social',
            ruleType: 'webCategory',
            destinations: [
                {
                    '@odata.type': '#microsoft.graph.networkaccess.webCategory',
                    name: 'SocialNetworking'
                }
            ]
        }
    ],
    action: 'block',
    description: 'Block Social Sites',
    '@odata.type': '#microsoft.graph.networkaccess.filteringPolicy'
};

await client.api('/networkaccess/filteringPolicies')
	.version('beta')
	.post(filteringPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\FilteringPolicy;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\PolicyRule;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\WebCategoryFilteringRule;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\NetworkDestinationType;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RuleDestination;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\WebCategory;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\FilteringPolicyAction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FilteringPolicy();
$requestBody->setName('Block Social');
$policyRulesPolicyRule1 = new WebCategoryFilteringRule();
$policyRulesPolicyRule1->setOdataType('#microsoft.graph.networkaccess.webCategoryFilteringRule');
$policyRulesPolicyRule1->setName('Block Social');
$policyRulesPolicyRule1->setRuleType(new NetworkDestinationType('webCategory'));
$destinationsRuleDestination1 = new WebCategory();
$destinationsRuleDestination1->setOdataType('#microsoft.graph.networkaccess.webCategory');
$destinationsRuleDestination1->setName('SocialNetworking');
$destinationsArray []= $destinationsRuleDestination1;
$policyRulesPolicyRule1->setDestinations($destinationsArray);

$policyRulesArray []= $policyRulesPolicyRule1;
$requestBody->setPolicyRules($policyRulesArray);

$requestBody->setAction(new FilteringPolicyAction('block'));
$requestBody->setDescription('Block Social Sites');
$requestBody->setOdataType('#microsoft.graph.networkaccess.filteringPolicy');

$result = $graphServiceClient->networkAccess()->filteringPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "Block Social"
	policyRules = @(
		@{
			"@odata.type" = "#microsoft.graph.networkaccess.webCategoryFilteringRule"
			name = "Block Social"
			ruleType = "webCategory"
			destinations = @(
				@{
					"@odata.type" = "#microsoft.graph.networkaccess.webCategory"
					name = "SocialNetworking"
				}
			)
		}
	)
	action = "block"
	description = "Block Social Sites"
	"@odata.type" = "#microsoft.graph.networkaccess.filteringPolicy"
}

New-MgBetaNetworkAccessFilteringPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.filtering_policy import FilteringPolicy
from msgraph_beta.generated.models.networkaccess.policy_rule import PolicyRule
from msgraph_beta.generated.models.networkaccess.web_category_filtering_rule import WebCategoryFilteringRule
from msgraph_beta.generated.models.network_destination_type import NetworkDestinationType
from msgraph_beta.generated.models.networkaccess.rule_destination import RuleDestination
from msgraph_beta.generated.models.networkaccess.web_category import WebCategory
from msgraph_beta.generated.models.filtering_policy_action import FilteringPolicyAction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FilteringPolicy(
	name = "Block Social",
	policy_rules = [
		WebCategoryFilteringRule(
			odata_type = "#microsoft.graph.networkaccess.webCategoryFilteringRule",
			name = "Block Social",
			rule_type = NetworkDestinationType.WebCategory,
			destinations = [
				WebCategory(
					odata_type = "#microsoft.graph.networkaccess.webCategory",
					name = "SocialNetworking",
				),
			],
		),
	],
	action = FilteringPolicyAction.Block,
	description = "Block Social Sites",
	odata_type = "#microsoft.graph.networkaccess.filteringPolicy",
)

result = await graph_client.network_access.filtering_policies.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/filteringPolicies/$entity",
    "id": "60aced7d-2dbe-4ffc-bcd3-1321b8425cbf",
    "name": "Block Social",
    "description": "Block Social Sites",
    "version": "1.0.0",
    "lastModifiedDateTime": "2023-11-01T06:04:31Z",
    "createdDateTime": "2023-11-01T06:04:31Z",
    "action": "block"
}
```
