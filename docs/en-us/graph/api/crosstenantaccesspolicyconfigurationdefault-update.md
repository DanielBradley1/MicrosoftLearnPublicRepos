<!-- Source: https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationdefault-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Update crossTenantAccessPolicyConfigurationDefault

Namespace: microsoft.graph

Update the [default configuration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0) of a cross-tenant access policy.

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
PATCH /policies/crossTenantAccessPolicy/default
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
| appServiceConnectInbound | [crossTenantAccessPolicyAppServiceConnectSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyappserviceconnectsetting?view=graph-rest-1.0) | Defines your default configuration for inbound app service connect settings that control which applications can connect across tenant boundaries. |
| b2bCollaborationInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your default configuration for users from other organizations accessing your resources via Microsoft Entra B2B collaboration. |
| b2bCollaborationOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your default configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B collaboration. |
| b2bDirectConnectInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your default configuration for users from other organizations accessing your resources via Microsoft Entra B2B direct connect. |
| b2bDirectConnectOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your default configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B direct connect. |
| inboundTrust | [crossTenantAccessPolicyInboundTrust](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyinboundtrust?view=graph-rest-1.0) | Determines the default configuration for trusting other Conditional Access claims from external Microsoft Entra organizations. |
| m365CollaborationInbound | [crossTenantAccessPolicyM365CollaborationInboundSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationinboundsetting?view=graph-rest-1.0) | Defines your default configuration for inbound Microsoft 365 collaboration settings that determine which users from other organizations can collaborate with your organization using Microsoft 365 apps. |
| m365CollaborationOutbound | [crossTenantAccessPolicyM365CollaborationOutboundSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationoutboundsetting?view=graph-rest-1.0) | Defines your default configuration for outbound Microsoft 365 collaboration settings that determine which users in your organization can collaborate with other organizations using Microsoft 365 apps. |
| tenantRestrictions | [crossTenantAccessPolicyTenantRestrictions](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytenantrestrictions?view=graph-rest-1.0) | Defines the default tenant restrictions configuration for users in your organization who access an external organization on your network or devices. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Block outbound B2B collaboration for a group of users

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/default
Content-Type: application/json

{
  "b2bCollaborationOutbound":
  {
    "usersAndGroups":
    {
      "accessType": "blocked",
      "targets": [
        {
          "target": "0be493dc-cb56-4a53-936f-9cf64410b8b0",
          "targetType": "group"
        }
      ]
    },
    "applications":
    {
      "accessType": "blocked",
      "targets": [
        {
          "target": "AllApplications",
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

var requestBody = new CrossTenantAccessPolicyConfigurationDefault
{
	B2bCollaborationOutbound = new CrossTenantAccessPolicyB2BSetting
	{
		UsersAndGroups = new CrossTenantAccessPolicyTargetConfiguration
		{
			AccessType = CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked,
			Targets = new List<CrossTenantAccessPolicyTarget>
			{
				new CrossTenantAccessPolicyTarget
				{
					Target = "0be493dc-cb56-4a53-936f-9cf64410b8b0",
					TargetType = CrossTenantAccessPolicyTargetType.Group,
				},
			},
		},
		Applications = new CrossTenantAccessPolicyTargetConfiguration
		{
			AccessType = CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked,
			Targets = new List<CrossTenantAccessPolicyTarget>
			{
				new CrossTenantAccessPolicyTarget
				{
					Target = "AllApplications",
					TargetType = CrossTenantAccessPolicyTargetType.Application,
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Default.PatchAsync(requestBody);
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

requestBody := graphmodels.NewCrossTenantAccessPolicyConfigurationDefault()
b2bCollaborationOutbound := graphmodels.NewCrossTenantAccessPolicyB2BSetting()
usersAndGroups := graphmodels.NewCrossTenantAccessPolicyTargetConfiguration()
accessType := graphmodels.BLOCKED_CROSSTENANTACCESSPOLICYTARGETCONFIGURATIONACCESSTYPE 
usersAndGroups.SetAccessType(&accessType) 


crossTenantAccessPolicyTarget := graphmodels.NewCrossTenantAccessPolicyTarget()
target := "0be493dc-cb56-4a53-936f-9cf64410b8b0"
crossTenantAccessPolicyTarget.SetTarget(&target) 
targetType := graphmodels.GROUP_CROSSTENANTACCESSPOLICYTARGETTYPE 
crossTenantAccessPolicyTarget.SetTargetType(&targetType) 

targets := []graphmodels.CrossTenantAccessPolicyTargetable {
	crossTenantAccessPolicyTarget,
}
usersAndGroups.SetTargets(targets)
b2bCollaborationOutbound.SetUsersAndGroups(usersAndGroups)
applications := graphmodels.NewCrossTenantAccessPolicyTargetConfiguration()
accessType := graphmodels.BLOCKED_CROSSTENANTACCESSPOLICYTARGETCONFIGURATIONACCESSTYPE 
applications.SetAccessType(&accessType) 


crossTenantAccessPolicyTarget := graphmodels.NewCrossTenantAccessPolicyTarget()
target := "AllApplications"
crossTenantAccessPolicyTarget.SetTarget(&target) 
targetType := graphmodels.APPLICATION_CROSSTENANTACCESSPOLICYTARGETTYPE 
crossTenantAccessPolicyTarget.SetTargetType(&targetType) 

targets := []graphmodels.CrossTenantAccessPolicyTargetable {
	crossTenantAccessPolicyTarget,
}
applications.SetTargets(targets)
b2bCollaborationOutbound.SetApplications(applications)
requestBody.SetB2bCollaborationOutbound(b2bCollaborationOutbound)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
default, err := graphClient.Policies().CrossTenantAccessPolicy().Default().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantAccessPolicyConfigurationDefault crossTenantAccessPolicyConfigurationDefault = new CrossTenantAccessPolicyConfigurationDefault();
CrossTenantAccessPolicyB2BSetting b2bCollaborationOutbound = new CrossTenantAccessPolicyB2BSetting();
CrossTenantAccessPolicyTargetConfiguration usersAndGroups = new CrossTenantAccessPolicyTargetConfiguration();
usersAndGroups.setAccessType(CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked);
LinkedList<CrossTenantAccessPolicyTarget> targets = new LinkedList<CrossTenantAccessPolicyTarget>();
CrossTenantAccessPolicyTarget crossTenantAccessPolicyTarget = new CrossTenantAccessPolicyTarget();
crossTenantAccessPolicyTarget.setTarget("0be493dc-cb56-4a53-936f-9cf64410b8b0");
crossTenantAccessPolicyTarget.setTargetType(CrossTenantAccessPolicyTargetType.Group);
targets.add(crossTenantAccessPolicyTarget);
usersAndGroups.setTargets(targets);
b2bCollaborationOutbound.setUsersAndGroups(usersAndGroups);
CrossTenantAccessPolicyTargetConfiguration applications = new CrossTenantAccessPolicyTargetConfiguration();
applications.setAccessType(CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked);
LinkedList<CrossTenantAccessPolicyTarget> targets1 = new LinkedList<CrossTenantAccessPolicyTarget>();
CrossTenantAccessPolicyTarget crossTenantAccessPolicyTarget1 = new CrossTenantAccessPolicyTarget();
crossTenantAccessPolicyTarget1.setTarget("AllApplications");
crossTenantAccessPolicyTarget1.setTargetType(CrossTenantAccessPolicyTargetType.Application);
targets1.add(crossTenantAccessPolicyTarget1);
applications.setTargets(targets1);
b2bCollaborationOutbound.setApplications(applications);
crossTenantAccessPolicyConfigurationDefault.setB2bCollaborationOutbound(b2bCollaborationOutbound);
CrossTenantAccessPolicyConfigurationDefault result = graphClient.policies().crossTenantAccessPolicy().defaultEscaped().patch(crossTenantAccessPolicyConfigurationDefault);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const crossTenantAccessPolicyConfigurationDefault = {
  b2bCollaborationOutbound: 
  {
    usersAndGroups: 
    {
      accessType: 'blocked',
      targets: [
        {
          target: '0be493dc-cb56-4a53-936f-9cf64410b8b0',
          targetType: 'group'
        }
      ]
    },
    applications: 
    {
      accessType: 'blocked',
      targets: [
        {
          target: 'AllApplications',
          targetType: 'application'
        }
      ]
    }
  }
};

await client.api('/policies/crossTenantAccessPolicy/default')
	.update(crossTenantAccessPolicyConfigurationDefault);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyConfigurationDefault;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyB2BSetting;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetConfiguration;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetConfigurationAccessType;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTarget;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CrossTenantAccessPolicyConfigurationDefault();
$b2bCollaborationOutbound = new CrossTenantAccessPolicyB2BSetting();
$b2bCollaborationOutboundUsersAndGroups = new CrossTenantAccessPolicyTargetConfiguration();
$b2bCollaborationOutboundUsersAndGroups->setAccessType(new CrossTenantAccessPolicyTargetConfigurationAccessType('blocked'));
$targetsCrossTenantAccessPolicyTarget1 = new CrossTenantAccessPolicyTarget();
$targetsCrossTenantAccessPolicyTarget1->setTarget('0be493dc-cb56-4a53-936f-9cf64410b8b0');
$targetsCrossTenantAccessPolicyTarget1->setTargetType(new CrossTenantAccessPolicyTargetType('group'));
$targetsArray []= $targetsCrossTenantAccessPolicyTarget1;
$b2bCollaborationOutboundUsersAndGroups->setTargets($targetsArray);

$b2bCollaborationOutbound->setUsersAndGroups($b2bCollaborationOutboundUsersAndGroups);
$b2bCollaborationOutboundApplications = new CrossTenantAccessPolicyTargetConfiguration();
$b2bCollaborationOutboundApplications->setAccessType(new CrossTenantAccessPolicyTargetConfigurationAccessType('blocked'));
$targetsCrossTenantAccessPolicyTarget1 = new CrossTenantAccessPolicyTarget();
$targetsCrossTenantAccessPolicyTarget1->setTarget('AllApplications');
$targetsCrossTenantAccessPolicyTarget1->setTargetType(new CrossTenantAccessPolicyTargetType('application'));
$targetsArray []= $targetsCrossTenantAccessPolicyTarget1;
$b2bCollaborationOutboundApplications->setTargets($targetsArray);

$b2bCollaborationOutbound->setApplications($b2bCollaborationOutboundApplications);
$requestBody->setB2bCollaborationOutbound($b2bCollaborationOutbound);

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->escapedDefault()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	b2bCollaborationOutbound = @{
		usersAndGroups = @{
			accessType = "blocked"
			targets = @(
				@{
					target = "0be493dc-cb56-4a53-936f-9cf64410b8b0"
					targetType = "group"
				}
			)
		}
		applications = @{
			accessType = "blocked"
			targets = @(
				@{
					target = "AllApplications"
					targetType = "application"
				}
			)
		}
	}
}

Update-MgPolicyCrossTenantAccessPolicyDefault -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cross_tenant_access_policy_configuration_default import CrossTenantAccessPolicyConfigurationDefault
from msgraph.generated.models.cross_tenant_access_policy_b2_b_setting import CrossTenantAccessPolicyB2BSetting
from msgraph.generated.models.cross_tenant_access_policy_target_configuration import CrossTenantAccessPolicyTargetConfiguration
from msgraph.generated.models.cross_tenant_access_policy_target_configuration_access_type import CrossTenantAccessPolicyTargetConfigurationAccessType
from msgraph.generated.models.cross_tenant_access_policy_target import CrossTenantAccessPolicyTarget
from msgraph.generated.models.cross_tenant_access_policy_target_type import CrossTenantAccessPolicyTargetType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CrossTenantAccessPolicyConfigurationDefault(
	b2b_collaboration_outbound = CrossTenantAccessPolicyB2BSetting(
		users_and_groups = CrossTenantAccessPolicyTargetConfiguration(
			access_type = CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked,
			targets = [
				CrossTenantAccessPolicyTarget(
					target = "0be493dc-cb56-4a53-936f-9cf64410b8b0",
					target_type = CrossTenantAccessPolicyTargetType.Group,
				),
			],
		),
		applications = CrossTenantAccessPolicyTargetConfiguration(
			access_type = CrossTenantAccessPolicyTargetConfigurationAccessType.Blocked,
			targets = [
				CrossTenantAccessPolicyTarget(
					target = "AllApplications",
					target_type = CrossTenantAccessPolicyTargetType.Application,
				),
			],
		),
	),
)

result = await graph_client.policies.cross_tenant_access_policy.default.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Update default invitation redemption configuration

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/default
Content-Type: application/json

{
  "invitationRedemptionIdentityProviderConfiguration": { 
    "primaryIdentityProviderPrecedenceOrder": [ 
        "externalFederation", 
        "azureActiveDirectory", 
        "socialIdentityProviders" 
    ], 
    "fallbackIdentityProvider": "defaultConfiguredIdp" 
  } 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CrossTenantAccessPolicyConfigurationDefault
{
	InvitationRedemptionIdentityProviderConfiguration = new DefaultInvitationRedemptionIdentityProviderConfiguration
	{
		PrimaryIdentityProviderPrecedenceOrder = new List<B2bIdentityProvidersType?>
		{
			B2bIdentityProvidersType.ExternalFederation,
			B2bIdentityProvidersType.AzureActiveDirectory,
			B2bIdentityProvidersType.SocialIdentityProviders,
		},
		FallbackIdentityProvider = B2bIdentityProvidersType.DefaultConfiguredIdp,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Default.PatchAsync(requestBody);
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

requestBody := graphmodels.NewCrossTenantAccessPolicyConfigurationDefault()
invitationRedemptionIdentityProviderConfiguration := graphmodels.NewDefaultInvitationRedemptionIdentityProviderConfiguration()
primaryIdentityProviderPrecedenceOrder := []graphmodels.B2bIdentityProvidersTypeable {
	b2bIdentityProvidersType := graphmodels.EXTERNALFEDERATION_B2BIDENTITYPROVIDERSTYPE 
	invitationRedemptionIdentityProviderConfiguration.SetB2bIdentityProvidersType(&b2bIdentityProvidersType) 
	b2bIdentityProvidersType := graphmodels.AZUREACTIVEDIRECTORY_B2BIDENTITYPROVIDERSTYPE 
	invitationRedemptionIdentityProviderConfiguration.SetB2bIdentityProvidersType(&b2bIdentityProvidersType) 
	b2bIdentityProvidersType := graphmodels.SOCIALIDENTITYPROVIDERS_B2BIDENTITYPROVIDERSTYPE 
	invitationRedemptionIdentityProviderConfiguration.SetB2bIdentityProvidersType(&b2bIdentityProvidersType)
}
invitationRedemptionIdentityProviderConfiguration.SetPrimaryIdentityProviderPrecedenceOrder(primaryIdentityProviderPrecedenceOrder)
fallbackIdentityProvider := graphmodels.DEFAULTCONFIGUREDIDP_B2BIDENTITYPROVIDERSTYPE 
invitationRedemptionIdentityProviderConfiguration.SetFallbackIdentityProvider(&fallbackIdentityProvider) 
requestBody.SetInvitationRedemptionIdentityProviderConfiguration(invitationRedemptionIdentityProviderConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
default, err := graphClient.Policies().CrossTenantAccessPolicy().Default().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantAccessPolicyConfigurationDefault crossTenantAccessPolicyConfigurationDefault = new CrossTenantAccessPolicyConfigurationDefault();
DefaultInvitationRedemptionIdentityProviderConfiguration invitationRedemptionIdentityProviderConfiguration = new DefaultInvitationRedemptionIdentityProviderConfiguration();
LinkedList<B2bIdentityProvidersType> primaryIdentityProviderPrecedenceOrder = new LinkedList<B2bIdentityProvidersType>();
primaryIdentityProviderPrecedenceOrder.add(B2bIdentityProvidersType.ExternalFederation);
primaryIdentityProviderPrecedenceOrder.add(B2bIdentityProvidersType.AzureActiveDirectory);
primaryIdentityProviderPrecedenceOrder.add(B2bIdentityProvidersType.SocialIdentityProviders);
invitationRedemptionIdentityProviderConfiguration.setPrimaryIdentityProviderPrecedenceOrder(primaryIdentityProviderPrecedenceOrder);
invitationRedemptionIdentityProviderConfiguration.setFallbackIdentityProvider(B2bIdentityProvidersType.DefaultConfiguredIdp);
crossTenantAccessPolicyConfigurationDefault.setInvitationRedemptionIdentityProviderConfiguration(invitationRedemptionIdentityProviderConfiguration);
CrossTenantAccessPolicyConfigurationDefault result = graphClient.policies().crossTenantAccessPolicy().defaultEscaped().patch(crossTenantAccessPolicyConfigurationDefault);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const crossTenantAccessPolicyConfigurationDefault = {
  invitationRedemptionIdentityProviderConfiguration: { 
    primaryIdentityProviderPrecedenceOrder: [ 
        'externalFederation', 
        'azureActiveDirectory', 
        'socialIdentityProviders' 
    ], 
    fallbackIdentityProvider: 'defaultConfiguredIdp' 
  } 
};

await client.api('/policies/crossTenantAccessPolicy/default')
	.update(crossTenantAccessPolicyConfigurationDefault);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyConfigurationDefault;
use Microsoft\Graph\Generated\Models\DefaultInvitationRedemptionIdentityProviderConfiguration;
use Microsoft\Graph\Generated\Models\B2bIdentityProvidersType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CrossTenantAccessPolicyConfigurationDefault();
$invitationRedemptionIdentityProviderConfiguration = new DefaultInvitationRedemptionIdentityProviderConfiguration();
$invitationRedemptionIdentityProviderConfiguration->setPrimaryIdentityProviderPrecedenceOrder([new B2bIdentityProvidersType('externalFederation'),new B2bIdentityProvidersType('azureActiveDirectory'),new B2bIdentityProvidersType('socialIdentityProviders'),	]);
$invitationRedemptionIdentityProviderConfiguration->setFallbackIdentityProvider(new B2bIdentityProvidersType('defaultConfiguredIdp'));
$requestBody->setInvitationRedemptionIdentityProviderConfiguration($invitationRedemptionIdentityProviderConfiguration);

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->escapedDefault()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	invitationRedemptionIdentityProviderConfiguration = @{
		primaryIdentityProviderPrecedenceOrder = @(
		"externalFederation"
	"azureActiveDirectory"
"socialIdentityProviders"
)
fallbackIdentityProvider = "defaultConfiguredIdp"
}
}

Update-MgPolicyCrossTenantAccessPolicyDefault -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cross_tenant_access_policy_configuration_default import CrossTenantAccessPolicyConfigurationDefault
from msgraph.generated.models.default_invitation_redemption_identity_provider_configuration import DefaultInvitationRedemptionIdentityProviderConfiguration
from msgraph.generated.models.b2b_identity_providers_type import B2bIdentityProvidersType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CrossTenantAccessPolicyConfigurationDefault(
	invitation_redemption_identity_provider_configuration = DefaultInvitationRedemptionIdentityProviderConfiguration(
		primary_identity_provider_precedence_order = [
			B2bIdentityProvidersType.ExternalFederation,
			B2bIdentityProvidersType.AzureActiveDirectory,
			B2bIdentityProvidersType.SocialIdentityProviders,
		],
		fallback_identity_provider = B2bIdentityProvidersType.DefaultConfiguredIdp,
	),
)

result = await graph_client.policies.cross_tenant_access_policy.default.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 3: Disallow Microsoft accounts as an option for redeeming B2B invitations

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/default
Content-Type: application/json

{
  "invitationRedemptionIdentityProviderConfiguration": { 
    "primaryIdentityProviderPrecedenceOrder": [ 
        "externalFederation", 
        "azureActiveDirectory", 
        "socialIdentityProviders" 
    ], 
    "fallbackIdentityProvider": "emailOneTimePasscode" 
  } 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CrossTenantAccessPolicyConfigurationDefault
{
	InvitationRedemptionIdentityProviderConfiguration = new DefaultInvitationRedemptionIdentityProviderConfiguration
	{
		PrimaryIdentityProviderPrecedenceOrder = new List<B2bIdentityProvidersType?>
		{
			B2bIdentityProvidersType.ExternalFederation,
			B2bIdentityProvidersType.AzureActiveDirectory,
			B2bIdentityProvidersType.SocialIdentityProviders,
		},
		FallbackIdentityProvider = B2bIdentityProvidersType.EmailOneTimePasscode,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Default.PatchAsync(requestBody);
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

requestBody := graphmodels.NewCrossTenantAccessPolicyConfigurationDefault()
invitationRedemptionIdentityProviderConfiguration := graphmodels.NewDefaultInvitationRedemptionIdentityProviderConfiguration()
primaryIdentityProviderPrecedenceOrder := []graphmodels.B2bIdentityProvidersTypeable {
	b2bIdentityProvidersType := graphmodels.EXTERNALFEDERATION_B2BIDENTITYPROVIDERSTYPE 
	invitationRedemptionIdentityProviderConfiguration.SetB2bIdentityProvidersType(&b2bIdentityProvidersType) 
	b2bIdentityProvidersType := graphmodels.AZUREACTIVEDIRECTORY_B2BIDENTITYPROVIDERSTYPE 
	invitationRedemptionIdentityProviderConfiguration.SetB2bIdentityProvidersType(&b2bIdentityProvidersType) 
	b2bIdentityProvidersType := graphmodels.SOCIALIDENTITYPROVIDERS_B2BIDENTITYPROVIDERSTYPE 
	invitationRedemptionIdentityProviderConfiguration.SetB2bIdentityProvidersType(&b2bIdentityProvidersType)
}
invitationRedemptionIdentityProviderConfiguration.SetPrimaryIdentityProviderPrecedenceOrder(primaryIdentityProviderPrecedenceOrder)
fallbackIdentityProvider := graphmodels.EMAILONETIMEPASSCODE_B2BIDENTITYPROVIDERSTYPE 
invitationRedemptionIdentityProviderConfiguration.SetFallbackIdentityProvider(&fallbackIdentityProvider) 
requestBody.SetInvitationRedemptionIdentityProviderConfiguration(invitationRedemptionIdentityProviderConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
default, err := graphClient.Policies().CrossTenantAccessPolicy().Default().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantAccessPolicyConfigurationDefault crossTenantAccessPolicyConfigurationDefault = new CrossTenantAccessPolicyConfigurationDefault();
DefaultInvitationRedemptionIdentityProviderConfiguration invitationRedemptionIdentityProviderConfiguration = new DefaultInvitationRedemptionIdentityProviderConfiguration();
LinkedList<B2bIdentityProvidersType> primaryIdentityProviderPrecedenceOrder = new LinkedList<B2bIdentityProvidersType>();
primaryIdentityProviderPrecedenceOrder.add(B2bIdentityProvidersType.ExternalFederation);
primaryIdentityProviderPrecedenceOrder.add(B2bIdentityProvidersType.AzureActiveDirectory);
primaryIdentityProviderPrecedenceOrder.add(B2bIdentityProvidersType.SocialIdentityProviders);
invitationRedemptionIdentityProviderConfiguration.setPrimaryIdentityProviderPrecedenceOrder(primaryIdentityProviderPrecedenceOrder);
invitationRedemptionIdentityProviderConfiguration.setFallbackIdentityProvider(B2bIdentityProvidersType.EmailOneTimePasscode);
crossTenantAccessPolicyConfigurationDefault.setInvitationRedemptionIdentityProviderConfiguration(invitationRedemptionIdentityProviderConfiguration);
CrossTenantAccessPolicyConfigurationDefault result = graphClient.policies().crossTenantAccessPolicy().defaultEscaped().patch(crossTenantAccessPolicyConfigurationDefault);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const crossTenantAccessPolicyConfigurationDefault = {
  invitationRedemptionIdentityProviderConfiguration: { 
    primaryIdentityProviderPrecedenceOrder: [ 
        'externalFederation', 
        'azureActiveDirectory', 
        'socialIdentityProviders' 
    ], 
    fallbackIdentityProvider: 'emailOneTimePasscode' 
  } 
};

await client.api('/policies/crossTenantAccessPolicy/default')
	.update(crossTenantAccessPolicyConfigurationDefault);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyConfigurationDefault;
use Microsoft\Graph\Generated\Models\DefaultInvitationRedemptionIdentityProviderConfiguration;
use Microsoft\Graph\Generated\Models\B2bIdentityProvidersType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CrossTenantAccessPolicyConfigurationDefault();
$invitationRedemptionIdentityProviderConfiguration = new DefaultInvitationRedemptionIdentityProviderConfiguration();
$invitationRedemptionIdentityProviderConfiguration->setPrimaryIdentityProviderPrecedenceOrder([new B2bIdentityProvidersType('externalFederation'),new B2bIdentityProvidersType('azureActiveDirectory'),new B2bIdentityProvidersType('socialIdentityProviders'),	]);
$invitationRedemptionIdentityProviderConfiguration->setFallbackIdentityProvider(new B2bIdentityProvidersType('emailOneTimePasscode'));
$requestBody->setInvitationRedemptionIdentityProviderConfiguration($invitationRedemptionIdentityProviderConfiguration);

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->escapedDefault()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	invitationRedemptionIdentityProviderConfiguration = @{
		primaryIdentityProviderPrecedenceOrder = @(
		"externalFederation"
	"azureActiveDirectory"
"socialIdentityProviders"
)
fallbackIdentityProvider = "emailOneTimePasscode"
}
}

Update-MgPolicyCrossTenantAccessPolicyDefault -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cross_tenant_access_policy_configuration_default import CrossTenantAccessPolicyConfigurationDefault
from msgraph.generated.models.default_invitation_redemption_identity_provider_configuration import DefaultInvitationRedemptionIdentityProviderConfiguration
from msgraph.generated.models.b2b_identity_providers_type import B2bIdentityProvidersType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CrossTenantAccessPolicyConfigurationDefault(
	invitation_redemption_identity_provider_configuration = DefaultInvitationRedemptionIdentityProviderConfiguration(
		primary_identity_provider_precedence_order = [
			B2bIdentityProvidersType.ExternalFederation,
			B2bIdentityProvidersType.AzureActiveDirectory,
			B2bIdentityProvidersType.SocialIdentityProviders,
		],
		fallback_identity_provider = B2bIdentityProvidersType.EmailOneTimePasscode,
	),
)

result = await graph_client.policies.cross_tenant_access_policy.default.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 4: Configure Microsoft 365 collaboration settings

The following example shows how to configure the default cross-tenant access policy to allow inbound Microsoft 365 collaboration for all users.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/default
Content-Type: application/json

{
  "m365CollaborationInbound": {
    "users": {
      "accessType": "allowed",
      "targets": [
        {
          "target": "AllUsers",
          "targetType": "user"
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

var requestBody = new CrossTenantAccessPolicyConfigurationDefault
{
	M365CollaborationInbound = new CrossTenantAccessPolicyM365CollaborationInboundSetting
	{
		Users = new CrossTenantAccessPolicyTargetConfiguration
		{
			AccessType = CrossTenantAccessPolicyTargetConfigurationAccessType.Allowed,
			Targets = new List<CrossTenantAccessPolicyTarget>
			{
				new CrossTenantAccessPolicyTarget
				{
					Target = "AllUsers",
					TargetType = CrossTenantAccessPolicyTargetType.User,
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Default.PatchAsync(requestBody);
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

requestBody := graphmodels.NewCrossTenantAccessPolicyConfigurationDefault()
m365CollaborationInbound := graphmodels.NewCrossTenantAccessPolicyM365CollaborationInboundSetting()
users := graphmodels.NewCrossTenantAccessPolicyTargetConfiguration()
accessType := graphmodels.ALLOWED_CROSSTENANTACCESSPOLICYTARGETCONFIGURATIONACCESSTYPE 
users.SetAccessType(&accessType) 


crossTenantAccessPolicyTarget := graphmodels.NewCrossTenantAccessPolicyTarget()
target := "AllUsers"
crossTenantAccessPolicyTarget.SetTarget(&target) 
targetType := graphmodels.USER_CROSSTENANTACCESSPOLICYTARGETTYPE 
crossTenantAccessPolicyTarget.SetTargetType(&targetType) 

targets := []graphmodels.CrossTenantAccessPolicyTargetable {
	crossTenantAccessPolicyTarget,
}
users.SetTargets(targets)
m365CollaborationInbound.SetUsers(users)
requestBody.SetM365CollaborationInbound(m365CollaborationInbound)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
default, err := graphClient.Policies().CrossTenantAccessPolicy().Default().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantAccessPolicyConfigurationDefault crossTenantAccessPolicyConfigurationDefault = new CrossTenantAccessPolicyConfigurationDefault();
CrossTenantAccessPolicyM365CollaborationInboundSetting m365CollaborationInbound = new CrossTenantAccessPolicyM365CollaborationInboundSetting();
CrossTenantAccessPolicyTargetConfiguration users = new CrossTenantAccessPolicyTargetConfiguration();
users.setAccessType(CrossTenantAccessPolicyTargetConfigurationAccessType.Allowed);
LinkedList<CrossTenantAccessPolicyTarget> targets = new LinkedList<CrossTenantAccessPolicyTarget>();
CrossTenantAccessPolicyTarget crossTenantAccessPolicyTarget = new CrossTenantAccessPolicyTarget();
crossTenantAccessPolicyTarget.setTarget("AllUsers");
crossTenantAccessPolicyTarget.setTargetType(CrossTenantAccessPolicyTargetType.User);
targets.add(crossTenantAccessPolicyTarget);
users.setTargets(targets);
m365CollaborationInbound.setUsers(users);
crossTenantAccessPolicyConfigurationDefault.setM365CollaborationInbound(m365CollaborationInbound);
CrossTenantAccessPolicyConfigurationDefault result = graphClient.policies().crossTenantAccessPolicy().defaultEscaped().patch(crossTenantAccessPolicyConfigurationDefault);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const crossTenantAccessPolicyConfigurationDefault = {
  m365CollaborationInbound: {
    users: {
      accessType: 'allowed',
      targets: [
        {
          target: 'AllUsers',
          targetType: 'user'
        }
      ]
    }
  }
};

await client.api('/policies/crossTenantAccessPolicy/default')
	.update(crossTenantAccessPolicyConfigurationDefault);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyConfigurationDefault;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyM365CollaborationInboundSetting;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetConfiguration;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetConfigurationAccessType;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTarget;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyTargetType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CrossTenantAccessPolicyConfigurationDefault();
$m365CollaborationInbound = new CrossTenantAccessPolicyM365CollaborationInboundSetting();
$m365CollaborationInboundUsers = new CrossTenantAccessPolicyTargetConfiguration();
$m365CollaborationInboundUsers->setAccessType(new CrossTenantAccessPolicyTargetConfigurationAccessType('allowed'));
$targetsCrossTenantAccessPolicyTarget1 = new CrossTenantAccessPolicyTarget();
$targetsCrossTenantAccessPolicyTarget1->setTarget('AllUsers');
$targetsCrossTenantAccessPolicyTarget1->setTargetType(new CrossTenantAccessPolicyTargetType('user'));
$targetsArray []= $targetsCrossTenantAccessPolicyTarget1;
$m365CollaborationInboundUsers->setTargets($targetsArray);

$m365CollaborationInbound->setUsers($m365CollaborationInboundUsers);
$requestBody->setM365CollaborationInbound($m365CollaborationInbound);

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->escapedDefault()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	m365CollaborationInbound = @{
		users = @{
			accessType = "allowed"
			targets = @(
				@{
					target = "AllUsers"
					targetType = "user"
				}
			)
		}
	}
}

Update-MgPolicyCrossTenantAccessPolicyDefault -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cross_tenant_access_policy_configuration_default import CrossTenantAccessPolicyConfigurationDefault
from msgraph.generated.models.cross_tenant_access_policy_m365_collaboration_inbound_setting import CrossTenantAccessPolicyM365CollaborationInboundSetting
from msgraph.generated.models.cross_tenant_access_policy_target_configuration import CrossTenantAccessPolicyTargetConfiguration
from msgraph.generated.models.cross_tenant_access_policy_target_configuration_access_type import CrossTenantAccessPolicyTargetConfigurationAccessType
from msgraph.generated.models.cross_tenant_access_policy_target import CrossTenantAccessPolicyTarget
from msgraph.generated.models.cross_tenant_access_policy_target_type import CrossTenantAccessPolicyTargetType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CrossTenantAccessPolicyConfigurationDefault(
	m365_collaboration_inbound = CrossTenantAccessPolicyM365CollaborationInboundSetting(
		users = CrossTenantAccessPolicyTargetConfiguration(
			access_type = CrossTenantAccessPolicyTargetConfigurationAccessType.Allowed,
			targets = [
				CrossTenantAccessPolicyTarget(
					target = "AllUsers",
					target_type = CrossTenantAccessPolicyTargetType.User,
				),
			],
		),
	),
)

result = await graph_client.policies.cross_tenant_access_policy.default.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the request.

```http
HTTP/1.1 204 No Content
```
