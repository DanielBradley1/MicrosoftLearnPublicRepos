<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionrule-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# Update tlsInspectionRule

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [tlsInspectionRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) object.

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
PATCH /networkAccess/tlsInspectionPolicies/{tlsInspectionPolicyId}/policyRules/{tlsInspectionRuleId}
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
| action | microsoft.graph.networkaccess.tlsInspectionAction | The action to take when traffic matches this rule. The possible values are: `bypass`, `inspect`. |
| description | String | Optional description explaining the purpose of the rule. |
| matchingConditions | [microsoft.graph.networkaccess.tlsInspectionMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionmatchingconditions?view=graph-rest-beta) | The conditions that determine when this rule should be applied to traffic. |
| name | String | The display name of the rule. |
| priority | Int64 | The priority of the rule. Rules are evaluated in ascending order of priority. Lower numbers indicate higher priority. |
| settings | [microsoft.graph.networkaccess.tlsInspectionRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrulesettings?view=graph-rest-beta) | Additional settings that configure the rule's behavior. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/networkAccess/tlsInspectionPolicies/b712c469-e7cd-e7cb-738f-94b199570b0d/policyRules/ecf99dcc-6575-4d01-83dc-3fa5a940c76b
Content-Type: application/json

{
  "name": "Contoso TLS Rule 1 - Updated",
  "priority": 200,
  "description": "My TLS rule - Updated",
  "action": "bypass",
  "settings": {
    "status": "disabled"
  },
  "matchingConditions": {
    "destinations": [
      {
        "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination",
        "values": [
          "www.contoso.test-updated.com",
          "*.contoso.org"
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
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new PolicyRule
{
	Name = "Contoso TLS Rule 1 - Updated",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"priority" , 200
		},
		{
			"description" , "My TLS rule - Updated"
		},
		{
			"action" , "bypass"
		},
		{
			"settings" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"status", new UntypedString("disabled")
				},
			})
		},
		{
			"matchingConditions" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"destinations", new UntypedArray(new List<UntypedNode>
					{
						new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"@odata.type", new UntypedString("#microsoft.graph.networkaccess.tlsInspectionFqdnDestination")
							},
							{
								"values", new UntypedArray(new List<UntypedNode>
								{
									new UntypedString("www.contoso.test-updated.com"),
									new UntypedString("*.contoso.org"),
								})
							},
						}),
					})
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.TlsInspectionPolicies["{tlsInspectionPolicy-id}"].PolicyRules["{policyRule-id}"].PatchAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.PolicyRule policyRule = new com.microsoft.graph.beta.models.networkaccess.PolicyRule();
policyRule.setName("Contoso TLS Rule 1 - Updated");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("priority", 200);
additionalData.put("description", "My TLS rule - Updated");
additionalData.put("action", "bypass");
 settings = new ();
settings.setStatus("disabled");
additionalData.put("settings", settings);
 matchingConditions = new ();
LinkedList<Object> destinations = new LinkedList<Object>();
 property = new ();
property.setOdataType("#microsoft.graph.networkaccess.tlsInspectionFqdnDestination");
LinkedList<String> values = new LinkedList<String>();
values.add("www.contoso.test-updated.com");
values.add("*.contoso.org");
property.setValues(values);
destinations.add(property);
matchingConditions.setDestinations(destinations);
additionalData.put("matchingConditions", matchingConditions);
policyRule.setAdditionalData(additionalData);
com.microsoft.graph.models.networkaccess.PolicyRule result = graphClient.networkAccess().tlsInspectionPolicies().byTlsInspectionPolicyId("{tlsInspectionPolicy-id}").policyRules().byPolicyRuleId("{policyRule-id}").patch(policyRule);
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
  name: 'Contoso TLS Rule 1 - Updated',
  priority: 200,
  description: 'My TLS rule - Updated',
  action: 'bypass',
  settings: {
    status: 'disabled'
  },
  matchingConditions: {
    destinations: [
      {
        '@odata.type': '#microsoft.graph.networkaccess.tlsInspectionFqdnDestination',
        values: [
          'www.contoso.test-updated.com',
          '*.contoso.org'
        ]
      }
    ]
  }
};

await client.api('/networkAccess/tlsInspectionPolicies/b712c469-e7cd-e7cb-738f-94b199570b0d/policyRules/ecf99dcc-6575-4d01-83dc-3fa5a940c76b')
	.version('beta')
	.update(policyRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\PolicyRule;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PolicyRule();
$requestBody->setName('Contoso TLS Rule 1 - Updated');
$additionalData = [
	'priority' => 200,
	'description' => 'My TLS rule - Updated',
	'action' => 'bypass',
	'settings' => [
		'status' => 'disabled',
	],
	'matchingConditions' => [
		'destinations' => [
				[
					'@odata.type' => '#microsoft.graph.networkaccess.tlsInspectionFqdnDestination',
					'values' => [
'www.contoso.test-updated.com', '*.contoso.org', ],
				],
			],
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->networkAccess()->tlsInspectionPolicies()->byTlsInspectionPolicyId('tlsInspectionPolicy-id')->policyRules()->byPolicyRuleId('policyRule-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "Contoso TLS Rule 1 - Updated"
	priority = 
	description = "My TLS rule - Updated"
	action = "bypass"
	settings = @{
		status = "disabled"
	}
	matchingConditions = @{
		destinations = @(
			@{
				"@odata.type" = "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination"
				values = @(
				"www.contoso.test-updated.com"
			"*.contoso.org"
		)
	}
)
}
}

Update-MgBetaNetworkAccessTlInspectionPolicyRule -TlsInspectionPolicyId $tlsInspectionPolicyId -PolicyRuleId $policyRuleId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.policy_rule import PolicyRule
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PolicyRule(
	name = "Contoso TLS Rule 1 - Updated",
	additional_data = {
			"priority" : 200,
			"description" : "My TLS rule - Updated",
			"action" : "bypass",
			"settings" : {
					"status" : "disabled",
			},
			"matching_conditions" : {
					"destinations" : [
						{
								"@odata_type" : "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination",
								"values" : [
									"www.contoso.test-updated.com",
									"*.contoso.org",
								],
						},
					],
			},
	}
)

result = await graph_client.network_access.tls_inspection_policies.by_tls_inspection_policy_id('tlsInspectionPolicy-id').policy_rules.by_policy_rule_id('policyRule-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
