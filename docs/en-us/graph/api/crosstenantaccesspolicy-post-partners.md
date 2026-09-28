<!-- Source: https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicy-post-partners?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-23 -->

# Create crossTenantAccessPolicyConfigurationPartner

Namespace: microsoft.graph

Create a new partner configuration in a cross-tenant access policy.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.CrossTenantAccess | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.CrossTenantAccess | Not available. |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Teams Administrator - excluding identity synchronization settings
- Security Administrator

## HTTP request

```http
POST /policies/crossTenantAccessPolicy/partners
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| automaticUserConsentSettings | [inboundOutboundPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/inboundoutboundpolicyconfiguration?view=graph-rest-1.0) | Determines the partner-specific configuration for automatic user consent settings. Unless specifically configured, the **inboundAllowed** and **outboundAllowed** properties are `null` and inherit from the default settings, which is always `false`. |
| b2bCollaborationInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B collaboration. |
| b2bCollaborationOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B collaboration. |
| b2bDirectConnectInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B direct connect. |
| b2bDirectConnectOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B direct connect. |
| inboundTrust | [crossTenantAccessPolicyInboundTrust](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyinboundtrust?view=graph-rest-1.0) | Determines the partner-specific configuration for trusting other Conditional Access claims from external Microsoft Entra organizations. |
| isServiceProvider | Boolean | Identifies whether the partner-specific configuration is a cloud service provider for your organization. |
| tenantId | String | The tenant identifier for the partner Microsoft Entra organization. Read-only. Key. |

## Response

If successful, this method returns a `201 Created` response code and a [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/partners
Content-Type: application/json

{
  "tenantId": "3d0f5dec-5d3d-455c-8016-e2af1ae4d31a",
  "b2bDirectConnectOutbound": 
  {
    "usersAndGroups": 
    {
      "accessType": "blocked",
      "targets": [
        {
            "target": "6f546279-4da5-4b53-a095-09ea0cef9971",
            "targetType": "group"
        }
      ]
    }
  },
  "b2bDirectConnectInbound": 
  {
    "applications":
    {
      "accessType": "allowed",
      "targets": [
        {
            "target": "Office365",
            "targetType": "application"
        }
      ]
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CrossTenantAccessPolicyConfigurationPartner
{
	TenantId = "3d0f5dec-5d3d-455c-8016-e2af1ae4d31a",
	B2bDirectConnectOutbound = new CrossTenantAccessPolicyB2BSetting
	{
		UsersAndGroups = new CrossTenantAccessPolicyTargetConfiguration
		{
			AccessType = CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked,
			Targets = new List<CrossTenantAccessPolicyTarget>
			{
				new CrossTenantAccessPolicyTarget
				{
					Target = "6f546279-4da5-4b53-a095-09ea0cef9971",
					TargetType = CrossTenantAccessPolicyTargetType.Group,
				},
			},
		},
	},
	B2bDirectConnectInbound = new CrossTenantAccessPolicyB2BSetting
	{
		Applications = new CrossTenantAccessPolicyTargetConfiguration
		{
			AccessType = CrossTenantAccessPolicyTargetConfigurationAccessType.Allowed,
			Targets = new List<CrossTenantAccessPolicyTarget>
			{
				new CrossTenantAccessPolicyTarget
				{
					Target = "Office365",
					TargetType = CrossTenantAccessPolicyTargetType.Application,
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Partners.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewCrossTenantAccessPolicyConfigurationPartner()
tenantId := "3d0f5dec-5d3d-455c-8016-e2af1ae4d31a"
requestBody.SetTenantId(&tenantId) 
b2bDirectConnectOutbound := graphmodels.NewCrossTenantAccessPolicyB2BSetting()
usersAndGroups := graphmodels.NewCrossTenantAccessPolicyTargetConfiguration()
accessType := graphmodels.BLOCKED_CROSSTENANTACCESSPOLICYTARGETCONFIGURATIONACCESSTYPE 
usersAndGroups.SetAccessType(&accessType) 


crossTenantAccessPolicyTarget := graphmodels.NewCrossTenantAccessPolicyTarget()
target := "6f546279-4da5-4b53-a095-09ea0cef9971"
crossTenantAccessPolicyTarget.SetTarget(&target) 
targetType := graphmodels.GROUP_CROSSTENANTACCESSPOLICYTARGETTYPE 
crossTenantAccessPolicyTarget.SetTargetType(&targetType) 

targets := []graphmodels.CrossTenantAccessPolicyTargetable {
	crossTenantAccessPolicyTarget,
}
usersAndGroups.SetTargets(targets)
b2bDirectConnectOutbound.SetUsersAndGroups(usersAndGroups)
requestBody.SetB2bDirectConnectOutbound(b2bDirectConnectOutbound)
b2bDirectConnectInbound := graphmodels.NewCrossTenantAccessPolicyB2BSetting()
applications := graphmodels.NewCrossTenantAccessPolicyTargetConfiguration()
accessType := graphmodels.ALLOWED_CROSSTENANTACCESSPOLICYTARGETCONFIGURATIONACCESSTYPE 
applications.SetAccessType(&accessType) 


crossTenantAccessPolicyTarget := graphmodels.NewCrossTenantAccessPolicyTarget()
target := "Office365"
crossTenantAccessPolicyTarget.SetTarget(&target) 
targetType := graphmodels.APPLICATION_CROSSTENANTACCESSPOLICYTARGETTYPE 
crossTenantAccessPolicyTarget.SetTargetType(&targetType) 

targets := []graphmodels.CrossTenantAccessPolicyTargetable {
	crossTenantAccessPolicyTarget,
}
applications.SetTargets(targets)
b2bDirectConnectInbound.SetApplications(applications)
requestBody.SetB2bDirectConnectInbound(b2bDirectConnectInbound)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
partners, err := graphClient.Policies().CrossTenantAccessPolicy().Partners().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantAccessPolicyConfigurationPartner crossTenantAccessPolicyConfigurationPartner = new CrossTenantAccessPolicyConfigurationPartner();
crossTenantAccessPolicyConfigurationPartner.setTenantId("3d0f5dec-5d3d-455c-8016-e2af1ae4d31a");
CrossTenantAccessPolicyB2BSetting b2bDirectConnectOutbound = new CrossTenantAccessPolicyB2BSetting();
CrossTenantAccessPolicyTargetConfiguration usersAndGroups = new CrossTenantAccessPolicyTargetConfiguration();
usersAndGroups.setAccessType(CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked);
LinkedList<CrossTenantAccessPolicyTarget> targets = new LinkedList<CrossTenantAccessPolicyTarget>();
CrossTenantAccessPolicyTarget crossTenantAccessPolicyTarget = new CrossTenantAccessPolicyTarget();
crossTenantAccessPolicyTarget.setTarget("6f546279-4da5-4b53-a095-09ea0cef9971");
crossTenantAccessPolicyTarget.setTargetType(CrossTenantAccessPolicyTargetType.Group);
targets.add(crossTenantAccessPolicyTarget);
usersAndGroups.setTargets(targets);
b2bDirectConnectOutbound.setUsersAndGroups(usersAndGroups);
crossTenantAccessPolicyConfigurationPartner.setB2bDirectConnectOutbound(b2bDirectConnectOutbound);
CrossTenantAccessPolicyB2BSetting b2bDirectConnectInbound = new CrossTenantAccessPolicyB2BSetting();
CrossTenantAccessPolicyTargetConfiguration applications = new CrossTenantAccessPolicyTargetConfiguration();
applications.setAccessType(CrossTenantAccessPolicyTargetConfigurationAccessType.Allowed);
LinkedList<CrossTenantAccessPolicyTarget> targets1 = new LinkedList<CrossTenantAccessPolicyTarget>();
CrossTenantAccessPolicyTarget crossTenantAccessPolicyTarget1 = new CrossTenantAccessPolicyTarget();
crossTenantAccessPolicyTarget1.setTarget("Office365");
crossTenantAccessPolicyTarget1.setTargetType(CrossTenantAccessPolicyTargetType.Application);
targets1.add(crossTenantAccessPolicyTarget1);
applications.setTargets(targets1);
b2bDirectConnectInbound.setApplications(applications);
crossTenantAccessPolicyConfigurationPartner.setB2bDirectConnectInbound(b2bDirectConnectInbound);
CrossTenantAccessPolicyConfigurationPartner result = graphClient.policies().crossTenantAccessPolicy().partners().post(crossTenantAccessPolicyConfigurationPartner);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const crossTenantAccessPolicyConfigurationPartner = {
  tenantId: '3d0f5dec-5d3d-455c-8016-e2af1ae4d31a',
  b2bDirectConnectOutbound: 
  {
    usersAndGroups: 
    {
      accessType: 'blocked',
      targets: [
        {
            target: '6f546279-4da5-4b53-a095-09ea0cef9971',
            targetType: 'group'
        }
      ]
    }
  },
  b2bDirectConnectInbound: 
  {
    applications: 
    {
      accessType: 'allowed',
      targets: [
        {
            target: 'Office365',
            targetType: 'application'
        }
      ]
    }
  }
};

await client.api('/policies/crossTenantAccessPolicy/partners')
	.post(crossTenantAccessPolicyConfigurationPartner);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyConfigurationPartner;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyB2BSetting;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetConfiguration;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetConfigurationAccessType;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTarget;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CrossTenantAccessPolicyConfigurationPartner();
$requestBody->setTenantId('3d0f5dec-5d3d-455c-8016-e2af1ae4d31a');
$b2bDirectConnectOutbound = new CrossTenantAccessPolicyB2BSetting();
$b2bDirectConnectOutboundUsersAndGroups = new CrossTenantAccessPolicyTargetConfiguration();
$b2bDirectConnectOutboundUsersAndGroups->setAccessType(new CrossTenantAccessPolicyTargetConfigurationAccessType('blocked'));
$targetsCrossTenantAccessPolicyTarget1 = new CrossTenantAccessPolicyTarget();
$targetsCrossTenantAccessPolicyTarget1->setTarget('6f546279-4da5-4b53-a095-09ea0cef9971');
$targetsCrossTenantAccessPolicyTarget1->setTargetType(new CrossTenantAccessPolicyTargetType('group'));
$targetsArray []= $targetsCrossTenantAccessPolicyTarget1;
$b2bDirectConnectOutboundUsersAndGroups->setTargets($targetsArray);

$b2bDirectConnectOutbound->setUsersAndGroups($b2bDirectConnectOutboundUsersAndGroups);
$requestBody->setB2bDirectConnectOutbound($b2bDirectConnectOutbound);
$b2bDirectConnectInbound = new CrossTenantAccessPolicyB2BSetting();
$b2bDirectConnectInboundApplications = new CrossTenantAccessPolicyTargetConfiguration();
$b2bDirectConnectInboundApplications->setAccessType(new CrossTenantAccessPolicyTargetConfigurationAccessType('allowed'));
$targetsCrossTenantAccessPolicyTarget1 = new CrossTenantAccessPolicyTarget();
$targetsCrossTenantAccessPolicyTarget1->setTarget('Office365');
$targetsCrossTenantAccessPolicyTarget1->setTargetType(new CrossTenantAccessPolicyTargetType('application'));
$targetsArray []= $targetsCrossTenantAccessPolicyTarget1;
$b2bDirectConnectInboundApplications->setTargets($targetsArray);

$b2bDirectConnectInbound->setApplications($b2bDirectConnectInboundApplications);
$requestBody->setB2bDirectConnectInbound($b2bDirectConnectInbound);

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->partners()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	tenantId = "3d0f5dec-5d3d-455c-8016-e2af1ae4d31a"
	b2bDirectConnectOutbound = @{
		usersAndGroups = @{
			accessType = "blocked"
			targets = @(
				@{
					target = "6f546279-4da5-4b53-a095-09ea0cef9971"
					targetType = "group"
				}
			)
		}
	}
	b2bDirectConnectInbound = @{
		applications = @{
			accessType = "allowed"
			targets = @(
				@{
					target = "Office365"
					targetType = "application"
				}
			)
		}
	}
}

New-MgPolicyCrossTenantAccessPolicyPartner -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cross_tenant_access_policy_configuration_partner import CrossTenantAccessPolicyConfigurationPartner
from msgraph.generated.models.cross_tenant_access_policy_b2_b_setting import CrossTenantAccessPolicyB2BSetting
from msgraph.generated.models.cross_tenant_access_policy_target_configuration import CrossTenantAccessPolicyTargetConfiguration
from msgraph.generated.models.cross_tenant_access_policy_target_configuration_access_type import CrossTenantAccessPolicyTargetConfigurationAccessType
from msgraph.generated.models.cross_tenant_access_policy_target import CrossTenantAccessPolicyTarget
from msgraph.generated.models.cross_tenant_access_policy_target_type import CrossTenantAccessPolicyTargetType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CrossTenantAccessPolicyConfigurationPartner(
	tenant_id = "3d0f5dec-5d3d-455c-8016-e2af1ae4d31a",
	b2b_direct_connect_outbound = CrossTenantAccessPolicyB2BSetting(
		users_and_groups = CrossTenantAccessPolicyTargetConfiguration(
			access_type = CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked,
			targets = [
				CrossTenantAccessPolicyTarget(
					target = "6f546279-4da5-4b53-a095-09ea0cef9971",
					target_type = CrossTenantAccessPolicyTargetType.Group,
				),
			],
		),
	),
	b2b_direct_connect_inbound = CrossTenantAccessPolicyB2BSetting(
		applications = CrossTenantAccessPolicyTargetConfiguration(
			access_type = CrossTenantAccessPolicyTargetConfigurationAccessType.Allowed,
			targets = [
				CrossTenantAccessPolicyTarget(
					target = "Office365",
					target_type = CrossTenantAccessPolicyTargetType.Application,
				),
			],
		),
	),
)

result = await graph_client.policies.cross_tenant_access_policy.partners.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "tenantId": "3d0f5dec-5d3d-455c-8016-e2af1ae4d31a",
  "inboundTrust": null,
  "b2bCollaborationInbound": null,
  "b2bCollaborationOutbound": null,
  "b2bDirectConnectOutbound": 
  {
    "usersAndGroups":
    {
      "accessType": "blocked",
      "targets": [
        {
          "target": "6f546279-4da5-4b53-a095-09ea0cef9971",
          "targetType": "group"
        }
      ]
    }
  },
  "b2bDirectConnectInbound":
  {
    "applications":
    {
      "accessType": "allowed",
      "targets": [
        {
          "target": "Office365",
          "targetType": "application"
        }
      ]
    }
  }
}
```
