<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringrule-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-13 -->

# Create filteringRule

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta). The following derived types are supported:

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
POST /networkaccess/filteringPolicies/{filteringPoliciesId}/policyRules
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [fqdnFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-fqdnfilteringrule?view=graph-rest-beta) or [webCategoryFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategoryfilteringrule?view=graph-rest-beta) resource type.

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) object in the response body. The **@odata.type** property specifies the type of the created object.

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
POST https://graph.microsoft.com/beta/networkaccess/filteringPolicies/ac253559-37a0-4f72-b666-103420b94e38/policyRules
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.networkaccess.webCategoryFilteringRule",
    "name": "Block Gambling Sites",
    "ruleType": "webCategory",
    "destinations": [
        {
            "@odata.type": "#microsoft.graph.networkaccess.webCategory",
            "name": "Gambling"
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
	Name = "Block Gambling Sites",
	RuleType = NetworkDestinationType.WebCategory,
	Destinations = new List<RuleDestination>
	{
		new WebCategory
		{
			OdataType = "#microsoft.graph.networkaccess.webCategory",
			Name = "Gambling",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.FilteringPolicies["{filteringPolicy-id}"].PolicyRules.PostAsync(requestBody);
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
name := "Block Gambling Sites"
requestBody.SetName(&name) 
ruleType := graphmodels.WEBCATEGORY_NETWORKDESTINATIONTYPE 
requestBody.SetRuleType(&ruleType) 


ruleDestination := graphmodelsnetworkaccess.NewWebCategory()
name := "Gambling"
ruleDestination.SetName(&name) 

destinations := []graphmodelsnetworkaccess.RuleDestinationable {
	ruleDestination,
}
requestBody.SetDestinations(destinations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policyRules, err := graphClient.NetworkAccess().FilteringPolicies().ByFilteringPolicyId("filteringPolicy-id").PolicyRules().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.WebCategoryFilteringRule policyRule = new com.microsoft.graph.beta.models.networkaccess.WebCategoryFilteringRule();
policyRule.setOdataType("#microsoft.graph.networkaccess.webCategoryFilteringRule");
policyRule.setName("Block Gambling Sites");
policyRule.setRuleType(com.microsoft.graph.beta.models.networkaccess.NetworkDestinationType.WebCategory);
LinkedList<com.microsoft.graph.beta.models.networkaccess.RuleDestination> destinations = new LinkedList<com.microsoft.graph.beta.models.networkaccess.RuleDestination>();
com.microsoft.graph.beta.models.networkaccess.WebCategory ruleDestination = new com.microsoft.graph.beta.models.networkaccess.WebCategory();
ruleDestination.setOdataType("#microsoft.graph.networkaccess.webCategory");
ruleDestination.setName("Gambling");
destinations.add(ruleDestination);
policyRule.setDestinations(destinations);
com.microsoft.graph.models.networkaccess.PolicyRule result = graphClient.networkAccess().filteringPolicies().byFilteringPolicyId("{filteringPolicy-id}").policyRules().post(policyRule);
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
    name: 'Block Gambling Sites',
    ruleType: 'webCategory',
    destinations: [
        {
            '@odata.type': '#microsoft.graph.networkaccess.webCategory',
            name: 'Gambling'
        }
    ]
};

await client.api('/networkaccess/filteringPolicies/ac253559-37a0-4f72-b666-103420b94e38/policyRules')
	.version('beta')
	.post(policyRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\WebCategoryFilteringRule;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\NetworkDestinationType;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RuleDestination;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\WebCategory;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WebCategoryFilteringRule();
$requestBody->setOdataType('#microsoft.graph.networkaccess.webCategoryFilteringRule');
$requestBody->setName('Block Gambling Sites');
$requestBody->setRuleType(new NetworkDestinationType('webCategory'));
$destinationsRuleDestination1 = new WebCategory();
$destinationsRuleDestination1->setOdataType('#microsoft.graph.networkaccess.webCategory');
$destinationsRuleDestination1->setName('Gambling');
$destinationsArray []= $destinationsRuleDestination1;
$requestBody->setDestinations($destinationsArray);


$result = $graphServiceClient->networkAccess()->filteringPolicies()->byFilteringPolicyId('filteringPolicy-id')->policyRules()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	"@odata.type" = "#microsoft.graph.networkaccess.webCategoryFilteringRule"
	name = "Block Gambling Sites"
	ruleType = "webCategory"
	destinations = @(
		@{
			"@odata.type" = "#microsoft.graph.networkaccess.webCategory"
			name = "Gambling"
		}
	)
}

New-MgBetaNetworkAccessFilteringPolicyRule -FilteringPolicyId $filteringPolicyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.web_category_filtering_rule import WebCategoryFilteringRule
from msgraph_beta.generated.models.network_destination_type import NetworkDestinationType
from msgraph_beta.generated.models.networkaccess.rule_destination import RuleDestination
from msgraph_beta.generated.models.networkaccess.web_category import WebCategory
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WebCategoryFilteringRule(
	odata_type = "#microsoft.graph.networkaccess.webCategoryFilteringRule",
	name = "Block Gambling Sites",
	rule_type = NetworkDestinationType.WebCategory,
	destinations = [
		WebCategory(
			odata_type = "#microsoft.graph.networkaccess.webCategory",
			name = "Gambling",
		),
	],
)

result = await graph_client.network_access.filtering_policies.by_filtering_policy_id('filteringPolicy-id').policy_rules.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/filteringPolicies('49159c8f-3e5c-4a10-a2b8-ef7a734a586d')/policyRules/$entity",
    "@odata.type": "#microsoft.graph.networkaccess.webCategoryFilteringRule",
    "id": "47024899-7304-453e-9421-0febf7b57ad8",
    "name": "Block Gambling Sites",
    "ruleType": "webCategory",
    "destinations": [
        {
            "@odata.type": "#microsoft.graph.networkaccess.webCategory",
            "name": "Gambling",
            "displayName": "Gambling",
            "group": "Liability"
        }
    ]
}
```
