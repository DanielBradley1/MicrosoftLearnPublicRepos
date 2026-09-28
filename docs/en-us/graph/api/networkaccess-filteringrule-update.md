<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringrule-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update filteringRule

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) object. The following derived types are supported:

- [fqdnFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-fqdnfilteringrule?view=graph-rest-beta)
- [webCategoryFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategoryfilteringrule?view=graph-rest-beta)

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
PATCH /networkaccess/filteringPolicies/{filteringPolicyId}/policyRules/{filteringRuleId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must specify the **@odata.type** property and the value of the **filteringRule** object type to update. For example, `"@odata.type": "#microsoft.graph.networkaccess.webCategoryFilteringRule"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The display name. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). Required. |
| ruleType | microsoft.graph.networkaccess.networkDestinationType | The destination rule type. The possible values are `fqdn` and `webCategory`. Required. |
| destinations | [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta) collection | A collection of destinations to update. Optional. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/beta/networkaccess/filteringPolicies/bb1d249e-0691-477c-aae4-adfca179746a/policyRules/4619a550-7466-41ac-bdd9-b118bb6e004a
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.webCategoryFilteringRule",
  "name": "Gambling and Storage cateogries",
  "destinations": [
    {
      "@odata.type": "#microsoft.graph.networkaccess.webCategory",
      "name": "Gambling"
    },
    {
      "@odata.type": "#microsoft.graph.networkaccess.webCategory",
      "name": "WebRepositoryAndStorage"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new WebCategoryFilteringRule
{
	OdataType = "#microsoft.graph.networkaccess.webCategoryFilteringRule",
	Name = "Gambling and Storage cateogries",
	Destinations = new List<RuleDestination>
	{
		new WebCategory
		{
			OdataType = "#microsoft.graph.networkaccess.webCategory",
			Name = "Gambling",
		},
		new WebCategory
		{
			OdataType = "#microsoft.graph.networkaccess.webCategory",
			Name = "WebRepositoryAndStorage",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.FilteringPolicies["{filteringPolicy-id}"].PolicyRules["{policyRule-id}"].PatchAsync(requestBody);
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
name := "Gambling and Storage cateogries"
requestBody.SetName(&name) 


ruleDestination := graphmodelsnetworkaccess.NewWebCategory()
name := "Gambling"
ruleDestination.SetName(&name) 
ruleDestination1 := graphmodelsnetworkaccess.NewWebCategory()
name := "WebRepositoryAndStorage"
ruleDestination1.SetName(&name) 

destinations := []graphmodelsnetworkaccess.RuleDestinationable {
	ruleDestination,
	ruleDestination1,
}
requestBody.SetDestinations(destinations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policyRules, err := graphClient.NetworkAccess().FilteringPolicies().ByFilteringPolicyId("filteringPolicy-id").PolicyRules().ByPolicyRuleId("policyRule-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.WebCategoryFilteringRule policyRule = new com.microsoft.graph.beta.models.networkaccess.WebCategoryFilteringRule();
policyRule.setOdataType("#microsoft.graph.networkaccess.webCategoryFilteringRule");
policyRule.setName("Gambling and Storage cateogries");
LinkedList<com.microsoft.graph.beta.models.networkaccess.RuleDestination> destinations = new LinkedList<com.microsoft.graph.beta.models.networkaccess.RuleDestination>();
com.microsoft.graph.beta.models.networkaccess.WebCategory ruleDestination = new com.microsoft.graph.beta.models.networkaccess.WebCategory();
ruleDestination.setOdataType("#microsoft.graph.networkaccess.webCategory");
ruleDestination.setName("Gambling");
destinations.add(ruleDestination);
com.microsoft.graph.beta.models.networkaccess.WebCategory ruleDestination1 = new com.microsoft.graph.beta.models.networkaccess.WebCategory();
ruleDestination1.setOdataType("#microsoft.graph.networkaccess.webCategory");
ruleDestination1.setName("WebRepositoryAndStorage");
destinations.add(ruleDestination1);
policyRule.setDestinations(destinations);
com.microsoft.graph.models.networkaccess.PolicyRule result = graphClient.networkAccess().filteringPolicies().byFilteringPolicyId("{filteringPolicy-id}").policyRules().byPolicyRuleId("{policyRule-id}").patch(policyRule);
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
  '@odata.type': '#microsoft.graph.networkaccess.webCategoryFilteringRule',
  name: 'Gambling and Storage cateogries',
  destinations: [
    {
      '@odata.type': '#microsoft.graph.networkaccess.webCategory',
      name: 'Gambling'
    },
    {
      '@odata.type': '#microsoft.graph.networkaccess.webCategory',
      name: 'WebRepositoryAndStorage'
    }
  ]
};

await client.api('/networkaccess/filteringPolicies/bb1d249e-0691-477c-aae4-adfca179746a/policyRules/4619a550-7466-41ac-bdd9-b118bb6e004a')
	.version('beta')
	.update(policyRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\WebCategoryFilteringRule;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RuleDestination;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\WebCategory;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WebCategoryFilteringRule();
$requestBody->setOdataType('#microsoft.graph.networkaccess.webCategoryFilteringRule');
$requestBody->setName('Gambling and Storage cateogries');
$destinationsRuleDestination1 = new WebCategory();
$destinationsRuleDestination1->setOdataType('#microsoft.graph.networkaccess.webCategory');
$destinationsRuleDestination1->setName('Gambling');
$destinationsArray []= $destinationsRuleDestination1;
$destinationsRuleDestination2 = new WebCategory();
$destinationsRuleDestination2->setOdataType('#microsoft.graph.networkaccess.webCategory');
$destinationsRuleDestination2->setName('WebRepositoryAndStorage');
$destinationsArray []= $destinationsRuleDestination2;
$requestBody->setDestinations($destinationsArray);


$result = $graphServiceClient->networkAccess()->filteringPolicies()->byFilteringPolicyId('filteringPolicy-id')->policyRules()->byPolicyRuleId('policyRule-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	"@odata.type" = "#microsoft.graph.networkaccess.webCategoryFilteringRule"
	name = "Gambling and Storage cateogries"
	destinations = @(
		@{
			"@odata.type" = "#microsoft.graph.networkaccess.webCategory"
			name = "Gambling"
		}
		@{
			"@odata.type" = "#microsoft.graph.networkaccess.webCategory"
			name = "WebRepositoryAndStorage"
		}
	)
}

Update-MgBetaNetworkAccessFilteringPolicyRule -FilteringPolicyId $filteringPolicyId -PolicyRuleId $policyRuleId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.web_category_filtering_rule import WebCategoryFilteringRule
from msgraph_beta.generated.models.networkaccess.rule_destination import RuleDestination
from msgraph_beta.generated.models.networkaccess.web_category import WebCategory
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WebCategoryFilteringRule(
	odata_type = "#microsoft.graph.networkaccess.webCategoryFilteringRule",
	name = "Gambling and Storage cateogries",
	destinations = [
		WebCategory(
			odata_type = "#microsoft.graph.networkaccess.webCategory",
			name = "Gambling",
		),
		WebCategory(
			odata_type = "#microsoft.graph.networkaccess.webCategory",
			name = "WebRepositoryAndStorage",
		),
	],
)

result = await graph_client.network_access.filtering_policies.by_filtering_policy_id('filteringPolicy-id').policy_rules.by_policy_rule_id('policyRule-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
