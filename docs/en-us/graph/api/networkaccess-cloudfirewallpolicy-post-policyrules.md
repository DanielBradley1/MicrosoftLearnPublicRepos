<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallpolicy-post-policyrules?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Create cloudFirewallRule

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudFirewallRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) object in a [cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta).

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
POST /networkAccess/cloudFirewallPolicies/{cloudFirewallPolicyId}/policyRules
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudFirewallRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) object.

You can specify the following properties when creating a **cloudFirewallRule**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | A unique display name for the rule. Required. |
| description | String | A description of the rule. Optional. |
| priority | Int64 | A unique priority value that determines the rule evaluation order. Required. |
| action | [microsoft.graph.networkaccess.cloudFirewallAction](https://learn.microsoft.com/en-us/graph/api/resources/enums-networkaccess?view=graph-rest-beta#cloudfirewallaction-values) | The action to take when traffic matches the rule. The possible values are: `allow`, `block`, `unknownFutureValue`. Required. |
| settings | [microsoft.graph.networkaccess.cloudFirewallRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrulesettings?view=graph-rest-beta) | Configuration settings for the rule. Required. |
| matchingConditions | [microsoft.graph.networkaccess.cloudFirewallMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallmatchingconditions?view=graph-rest-beta) | The conditions that traffic must match for the rule to apply. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [cloudFirewallRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request that creates a rule to block specific traffic. The matching conditions use AND logic between properties \(sources AND destinations must match\), while items within collections use OR logic \(any one address or port can match\).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/networkAccess/cloudFirewallPolicies/80b58b7d-572f-4457-8944-c804fcf3b694/policyRules
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallRule",
  "name": "Block outbound to risky destinations",
  "description": "Block traffic to specific IPs on common ports",
  "priority": 100,
  "action": "block",
  "settings": {
    "status": "enabled"
  },
  "matchingConditions": {
    "sources": {
      "addresses": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress",
          "values": ["192.168.1.1", "192.168.0.0/16", "172.16.0.0-172.16.255.255"]
        }
      ],
      "ports": ["80", "443", "445-447"]
    },
    "destinations": {
      "addresses": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress",
          "values": ["10.0.0.1"]
        }
      ],
      "ports": ["80", "443", "445-447"],
      "protocols": "tcp"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new CloudFirewallRule
{
	OdataType = "#microsoft.graph.networkaccess.cloudFirewallRule",
	Name = "Block outbound to risky destinations",
	Description = "Block traffic to specific IPs on common ports",
	Priority = 100L,
	Action = CloudFirewallAction.Block,
	Settings = new CloudFirewallRuleSettings
	{
		Status = SecurityRuleStatus.Enabled,
	},
	MatchingConditions = new CloudFirewallMatchingConditions
	{
		Sources = new CloudFirewallSourceMatching
		{
			Addresses = new List<CloudFirewallSourceAddress>
			{
				new CloudFirewallSourceIpAddress
				{
					OdataType = "#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress",
					Values = new List<string>
					{
						"192.168.1.1",
						"192.168.0.0/16",
						"172.16.0.0-172.16.255.255",
					},
				},
			},
			Ports = new List<string>
			{
				"80",
				"443",
				"445-447",
			},
		},
		Destinations = new CloudFirewallDestinationMatching
		{
			Addresses = new List<CloudFirewallDestinationAddress>
			{
				new CloudFirewallDestinationIpAddress
				{
					OdataType = "#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress",
					Values = new List<string>
					{
						"10.0.0.1",
					},
				},
			},
			Ports = new List<string>
			{
				"80",
				"443",
				"445-447",
			},
			Protocols = CloudFirewallProtocol.Tcp,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.CloudFirewallPolicies["{cloudFirewallPolicy-id}"].PolicyRules.PostAsync(requestBody);
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
name := "Block outbound to risky destinations"
requestBody.SetName(&name) 
description := "Block traffic to specific IPs on common ports"
requestBody.SetDescription(&description) 
priority := int64(100)
requestBody.SetPriority(&priority) 
action := graphmodels.BLOCK_CLOUDFIREWALLACTION 
requestBody.SetAction(&action) 
settings := graphmodelsnetworkaccess.NewCloudFirewallRuleSettings()
status := graphmodels.ENABLED_SECURITYRULESTATUS 
settings.SetStatus(&status) 
requestBody.SetSettings(settings)
matchingConditions := graphmodelsnetworkaccess.NewCloudFirewallMatchingConditions()
sources := graphmodelsnetworkaccess.NewCloudFirewallSourceMatching()


cloudFirewallSourceAddress := graphmodelsnetworkaccess.NewCloudFirewallSourceIpAddress()
values := []string {
	"192.168.1.1",
	"192.168.0.0/16",
	"172.16.0.0-172.16.255.255",
}
cloudFirewallSourceAddress.SetValues(values)

addresses := []graphmodelsnetworkaccess.CloudFirewallSourceAddressable {
	cloudFirewallSourceAddress,
}
sources.SetAddresses(addresses)
ports := []string {
	"80",
	"443",
	"445-447",
}
sources.SetPorts(ports)
matchingConditions.SetSources(sources)
destinations := graphmodelsnetworkaccess.NewCloudFirewallDestinationMatching()


cloudFirewallDestinationAddress := graphmodelsnetworkaccess.NewCloudFirewallDestinationIpAddress()
values := []string {
	"10.0.0.1",
}
cloudFirewallDestinationAddress.SetValues(values)

addresses := []graphmodelsnetworkaccess.CloudFirewallDestinationAddressable {
	cloudFirewallDestinationAddress,
}
destinations.SetAddresses(addresses)
ports := []string {
	"80",
	"443",
	"445-447",
}
destinations.SetPorts(ports)
protocols := graphmodels.TCP_CLOUDFIREWALLPROTOCOL 
destinations.SetProtocols(&protocols) 
matchingConditions.SetDestinations(destinations)
requestBody.SetMatchingConditions(matchingConditions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policyRules, err := graphClient.NetworkAccess().CloudFirewallPolicies().ByCloudFirewallPolicyId("cloudFirewallPolicy-id").PolicyRules().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.CloudFirewallRule policyRule = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallRule();
policyRule.setOdataType("#microsoft.graph.networkaccess.cloudFirewallRule");
policyRule.setName("Block outbound to risky destinations");
policyRule.setDescription("Block traffic to specific IPs on common ports");
policyRule.setPriority(100L);
policyRule.setAction(com.microsoft.graph.beta.models.networkaccess.CloudFirewallAction.Block);
com.microsoft.graph.beta.models.networkaccess.CloudFirewallRuleSettings settings = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallRuleSettings();
settings.setStatus(com.microsoft.graph.beta.models.networkaccess.SecurityRuleStatus.Enabled);
policyRule.setSettings(settings);
com.microsoft.graph.beta.models.networkaccess.CloudFirewallMatchingConditions matchingConditions = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallMatchingConditions();
com.microsoft.graph.beta.models.networkaccess.CloudFirewallSourceMatching sources = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallSourceMatching();
LinkedList<com.microsoft.graph.beta.models.networkaccess.CloudFirewallSourceAddress> addresses = new LinkedList<com.microsoft.graph.beta.models.networkaccess.CloudFirewallSourceAddress>();
com.microsoft.graph.beta.models.networkaccess.CloudFirewallSourceIpAddress cloudFirewallSourceAddress = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallSourceIpAddress();
cloudFirewallSourceAddress.setOdataType("#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress");
LinkedList<String> values = new LinkedList<String>();
values.add("192.168.1.1");
values.add("192.168.0.0/16");
values.add("172.16.0.0-172.16.255.255");
cloudFirewallSourceAddress.setValues(values);
addresses.add(cloudFirewallSourceAddress);
sources.setAddresses(addresses);
LinkedList<String> ports = new LinkedList<String>();
ports.add("80");
ports.add("443");
ports.add("445-447");
sources.setPorts(ports);
matchingConditions.setSources(sources);
com.microsoft.graph.beta.models.networkaccess.CloudFirewallDestinationMatching destinations = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallDestinationMatching();
LinkedList<com.microsoft.graph.beta.models.networkaccess.CloudFirewallDestinationAddress> addresses1 = new LinkedList<com.microsoft.graph.beta.models.networkaccess.CloudFirewallDestinationAddress>();
com.microsoft.graph.beta.models.networkaccess.CloudFirewallDestinationIpAddress cloudFirewallDestinationAddress = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallDestinationIpAddress();
cloudFirewallDestinationAddress.setOdataType("#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress");
LinkedList<String> values1 = new LinkedList<String>();
values1.add("10.0.0.1");
cloudFirewallDestinationAddress.setValues(values1);
addresses1.add(cloudFirewallDestinationAddress);
destinations.setAddresses(addresses1);
LinkedList<String> ports1 = new LinkedList<String>();
ports1.add("80");
ports1.add("443");
ports1.add("445-447");
destinations.setPorts(ports1);
destinations.setProtocols(EnumSet.of(com.microsoft.graph.beta.models.networkaccess.CloudFirewallProtocol.Tcp));
matchingConditions.setDestinations(destinations);
policyRule.setMatchingConditions(matchingConditions);
com.microsoft.graph.models.networkaccess.PolicyRule result = graphClient.networkAccess().cloudFirewallPolicies().byCloudFirewallPolicyId("{cloudFirewallPolicy-id}").policyRules().post(policyRule);
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
  '@odata.type': '#microsoft.graph.networkaccess.cloudFirewallRule',
  name: 'Block outbound to risky destinations',
  description: 'Block traffic to specific IPs on common ports',
  priority: 100,
  action: 'block',
  settings: {
    status: 'enabled'
  },
  matchingConditions: {
    sources: {
      addresses: [
        {
          '@odata.type': '#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress',
          values: ['192.168.1.1', '192.168.0.0/16', '172.16.0.0-172.16.255.255']
        }
      ],
      ports: ['80', '443', '445-447']
    },
    destinations: {
      addresses: [
        {
          '@odata.type': '#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress',
          values: ['10.0.0.1']
        }
      ],
      ports: ['80', '443', '445-447'],
      protocols: 'tcp'
    }
  }
};

await client.api('/networkAccess/cloudFirewallPolicies/80b58b7d-572f-4457-8944-c804fcf3b694/policyRules')
	.version('beta')
	.post(policyRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallRule;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallAction;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallRuleSettings;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\SecurityRuleStatus;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallMatchingConditions;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallSourceMatching;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallSourceAddress;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallSourceIpAddress;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallDestinationMatching;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallDestinationAddress;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallDestinationIpAddress;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallProtocol;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudFirewallRule();
$requestBody->setOdataType('#microsoft.graph.networkaccess.cloudFirewallRule');
$requestBody->setName('Block outbound to risky destinations');
$requestBody->setDescription('Block traffic to specific IPs on common ports');
$requestBody->setPriority(100);
$requestBody->setAction(new CloudFirewallAction('block'));
$settings = new CloudFirewallRuleSettings();
$settings->setStatus(new SecurityRuleStatus('enabled'));
$requestBody->setSettings($settings);
$matchingConditions = new CloudFirewallMatchingConditions();
$matchingConditionsSources = new CloudFirewallSourceMatching();
$addressesCloudFirewallSourceAddress1 = new CloudFirewallSourceIpAddress();
$addressesCloudFirewallSourceAddress1->setOdataType('#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress');
$addressesCloudFirewallSourceAddress1->setValues(['192.168.1.1', '192.168.0.0/16', '172.16.0.0-172.16.255.255', 	]);
$addressesArray []= $addressesCloudFirewallSourceAddress1;
$matchingConditionsSources->setAddresses($addressesArray);

$matchingConditionsSources->setPorts(['80', '443', '445-447', ]);
$matchingConditions->setSources($matchingConditionsSources);
$matchingConditionsDestinations = new CloudFirewallDestinationMatching();
$addressesCloudFirewallDestinationAddress1 = new CloudFirewallDestinationIpAddress();
$addressesCloudFirewallDestinationAddress1->setOdataType('#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress');
$addressesCloudFirewallDestinationAddress1->setValues(['10.0.0.1', ]);
$addressesArray []= $addressesCloudFirewallDestinationAddress1;
$matchingConditionsDestinations->setAddresses($addressesArray);

$matchingConditionsDestinations->setPorts(['80', '443', '445-447', ]);
$matchingConditionsDestinations->setProtocols(new CloudFirewallProtocol('tcp'));
$matchingConditions->setDestinations($matchingConditionsDestinations);
$requestBody->setMatchingConditions($matchingConditions);

$result = $graphServiceClient->networkAccess()->cloudFirewallPolicies()->byCloudFirewallPolicyId('cloudFirewallPolicy-id')->policyRules()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	"@odata.type" = "#microsoft.graph.networkaccess.cloudFirewallRule"
	name = "Block outbound to risky destinations"
	description = "Block traffic to specific IPs on common ports"
	priority = 
	action = "block"
	settings = @{
		status = "enabled"
	}
	matchingConditions = @{
		sources = @{
			addresses = @(
				@{
					"@odata.type" = "#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress"
					values = @(
					"192.168.1.1"
				"192.168.0.0/16"
			"172.16.0.0-172.16.255.255"
		)
	}
)
ports = @(
"80"
"443"
"445-447"
)
}
destinations = @{
addresses = @(
@{
"@odata.type" = "#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress"
values = @(
"10.0.0.1"
)
}
)
ports = @(
"80"
"443"
"445-447"
)
protocols = "tcp"
}
}
}

New-MgBetaNetworkAccessCloudFirewallPolicyRule -CloudFirewallPolicyId $cloudFirewallPolicyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.cloud_firewall_rule import CloudFirewallRule
from msgraph_beta.generated.models.cloud_firewall_action import CloudFirewallAction
from msgraph_beta.generated.models.networkaccess.cloud_firewall_rule_settings import CloudFirewallRuleSettings
from msgraph_beta.generated.models.security_rule_status import SecurityRuleStatus
from msgraph_beta.generated.models.networkaccess.cloud_firewall_matching_conditions import CloudFirewallMatchingConditions
from msgraph_beta.generated.models.networkaccess.cloud_firewall_source_matching import CloudFirewallSourceMatching
from msgraph_beta.generated.models.networkaccess.cloud_firewall_source_address import CloudFirewallSourceAddress
from msgraph_beta.generated.models.networkaccess.cloud_firewall_source_ip_address import CloudFirewallSourceIpAddress
from msgraph_beta.generated.models.networkaccess.cloud_firewall_destination_matching import CloudFirewallDestinationMatching
from msgraph_beta.generated.models.networkaccess.cloud_firewall_destination_address import CloudFirewallDestinationAddress
from msgraph_beta.generated.models.networkaccess.cloud_firewall_destination_ip_address import CloudFirewallDestinationIpAddress
from msgraph_beta.generated.models.cloud_firewall_protocol import CloudFirewallProtocol
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudFirewallRule(
	odata_type = "#microsoft.graph.networkaccess.cloudFirewallRule",
	name = "Block outbound to risky destinations",
	description = "Block traffic to specific IPs on common ports",
	priority = 100,
	action = CloudFirewallAction.Block,
	settings = CloudFirewallRuleSettings(
		status = SecurityRuleStatus.Enabled,
	),
	matching_conditions = CloudFirewallMatchingConditions(
		sources = CloudFirewallSourceMatching(
			addresses = [
				CloudFirewallSourceIpAddress(
					odata_type = "#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress",
					values = [
						"192.168.1.1",
						"192.168.0.0/16",
						"172.16.0.0-172.16.255.255",
					],
				),
			],
			ports = [
				"80",
				"443",
				"445-447",
			],
		),
		destinations = CloudFirewallDestinationMatching(
			addresses = [
				CloudFirewallDestinationIpAddress(
					odata_type = "#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress",
					values = [
						"10.0.0.1",
					],
				),
			],
			ports = [
				"80",
				"443",
				"445-447",
			],
			protocols = CloudFirewallProtocol.Tcp,
		),
	),
)

result = await graph_client.network_access.cloud_firewall_policies.by_cloud_firewall_policy_id('cloudFirewallPolicy-id').policy_rules.post(request_body)
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
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallRule",
  "id": "406ebb24-e229-4011-8240-e11bbaa4f49d",
  "name": "Block outbound to risky destinations",
  "description": "Block traffic to specific IPs on common ports",
  "priority": 100,
  "action": "block",
  "settings": {
    "status": "enabled"
  },
  "matchingConditions": {
    "sources": {
      "addresses": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress",
          "values": ["192.168.1.1", "192.168.0.0/16", "172.16.0.0-172.16.255.255"]
        }
      ],
      "ports": ["80", "443", "445-447"]
    },
    "destinations": {
      "addresses": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress",
          "values": ["10.0.0.1"]
        }
      ],
      "ports": ["80", "443", "445-447"],
      "protocols": "tcp"
    }
  }
}
```
