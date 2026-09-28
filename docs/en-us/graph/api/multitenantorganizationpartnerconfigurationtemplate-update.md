<!-- Source: https://learn.microsoft.com/en-us/graph/api/multitenantorganizationpartnerconfigurationtemplate-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update multiTenantOrganizationPartnerConfigurationTemplate

Namespace: microsoft.graph

Update the cross-tenant access policy template with inbound and outbound partner configuration settings for a multitenant organization.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.CrossTenantAccess | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.CrossTenantAccess | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /policies/crossTenantAccessPolicy/templates/multiTenantOrganizationPartnerConfiguration
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
| inboundTrust | [crossTenantAccessPolicyInboundTrust](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyinboundtrust?view=graph-rest-1.0) | Determines the partner-specific configuration for trusting other Conditional Access claims from external Microsoft Entra organizations. Optional. |
| b2bCollaborationOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B collaboration. Optional. |
| b2bCollaborationInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B collaboration. Optional. |
| b2bDirectConnectOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B direct connect. Optional. |
| b2bDirectConnectInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B direct connect. Optional. |
| automaticUserConsentSettings | [inboundOutboundPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/inboundoutboundpolicyconfiguration?view=graph-rest-1.0) | Determines the partner-specific configuration for automatic user consent settings. Optional. |
| templateApplicationLevel | templateApplicationLevel | Specifies whether the template will be applied to partner configuration settings of certain tenants. The possible values are: `none`, `newPartners`, `existingPartners`, `unknownFutureValue`. You can also specify multiple values like `newPartners,existingPartners` \(default\). `none` indicates the template isn't applied to any new or existing partner tenants. `newPartners` indicates the template is applied to new partner tenants. `existingPartners` indicates the template is applied to existing partner tenants, those who already had partner-specific partner configurations in place. Optional. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

The following example configures the inbound trust settings to accept MFA, compliant, and Microsoft Entra hybrid joined devices from the partner tenant. It configures automatic redemption on behalf of your users and accepts admin consent for the users of the partner. It configures that the template is applied for new and existing partners. For more information, see [crossTenantAccessPolicyConfigurationPartner resource type](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0).

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
PATCH https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/templates/multiTenantOrganizationPartnerConfiguration
Content-Type: application/json

{
    "inboundTrust":  {
        "isMfaAccepted": true,
        "isCompliantDeviceAccepted": true,
        "isHybridAzureADJoinedDeviceAccepted": true
    },
    "automaticUserConsentSettings": {
        "inboundAllowed": true,
        "outboundAllowed": true
    },
    "templateApplicationLevel": "newPartners,existingPartners"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MultiTenantOrganizationPartnerConfigurationTemplate
{
	InboundTrust = new CrossTenantAccessPolicyInboundTrust
	{
		IsMfaAccepted = true,
		IsCompliantDeviceAccepted = true,
		IsHybridAzureADJoinedDeviceAccepted = true,
	},
	AutomaticUserConsentSettings = new InboundOutboundPolicyConfiguration
	{
		InboundAllowed = true,
		OutboundAllowed = true,
	},
	TemplateApplicationLevel = TemplateApplicationLevel.NewPartners | TemplateApplicationLevel.ExistingPartners,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Templates.MultiTenantOrganizationPartnerConfiguration.PatchAsync(requestBody);
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

requestBody := graphmodels.NewMultiTenantOrganizationPartnerConfigurationTemplate()
inboundTrust := graphmodels.NewCrossTenantAccessPolicyInboundTrust()
isMfaAccepted := true
inboundTrust.SetIsMfaAccepted(&isMfaAccepted) 
isCompliantDeviceAccepted := true
inboundTrust.SetIsCompliantDeviceAccepted(&isCompliantDeviceAccepted) 
isHybridAzureADJoinedDeviceAccepted := true
inboundTrust.SetIsHybridAzureADJoinedDeviceAccepted(&isHybridAzureADJoinedDeviceAccepted) 
requestBody.SetInboundTrust(inboundTrust)
automaticUserConsentSettings := graphmodels.NewInboundOutboundPolicyConfiguration()
inboundAllowed := true
automaticUserConsentSettings.SetInboundAllowed(&inboundAllowed) 
outboundAllowed := true
automaticUserConsentSettings.SetOutboundAllowed(&outboundAllowed) 
requestBody.SetAutomaticUserConsentSettings(automaticUserConsentSettings)
templateApplicationLevel := graphmodels.NEWPARTNERS,EXISTINGPARTNERS_TEMPLATEAPPLICATIONLEVEL 
requestBody.SetTemplateApplicationLevel(&templateApplicationLevel) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
multiTenantOrganizationPartnerConfiguration, err := graphClient.Policies().CrossTenantAccessPolicy().Templates().MultiTenantOrganizationPartnerConfiguration().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MultiTenantOrganizationPartnerConfigurationTemplate multiTenantOrganizationPartnerConfigurationTemplate = new MultiTenantOrganizationPartnerConfigurationTemplate();
CrossTenantAccessPolicyInboundTrust inboundTrust = new CrossTenantAccessPolicyInboundTrust();
inboundTrust.setIsMfaAccepted(true);
inboundTrust.setIsCompliantDeviceAccepted(true);
inboundTrust.setIsHybridAzureADJoinedDeviceAccepted(true);
multiTenantOrganizationPartnerConfigurationTemplate.setInboundTrust(inboundTrust);
InboundOutboundPolicyConfiguration automaticUserConsentSettings = new InboundOutboundPolicyConfiguration();
automaticUserConsentSettings.setInboundAllowed(true);
automaticUserConsentSettings.setOutboundAllowed(true);
multiTenantOrganizationPartnerConfigurationTemplate.setAutomaticUserConsentSettings(automaticUserConsentSettings);
multiTenantOrganizationPartnerConfigurationTemplate.setTemplateApplicationLevel(EnumSet.of(TemplateApplicationLevel.NewPartners, TemplateApplicationLevel.ExistingPartners));
MultiTenantOrganizationPartnerConfigurationTemplate result = graphClient.policies().crossTenantAccessPolicy().templates().multiTenantOrganizationPartnerConfiguration().patch(multiTenantOrganizationPartnerConfigurationTemplate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const multiTenantOrganizationPartnerConfigurationTemplate = {
    inboundTrust: {
        isMfaAccepted: true,
        isCompliantDeviceAccepted: true,
        isHybridAzureADJoinedDeviceAccepted: true
    },
    automaticUserConsentSettings: {
        inboundAllowed: true,
        outboundAllowed: true
    },
    templateApplicationLevel: 'newPartners,existingPartners'
};

await client.api('/policies/crossTenantAccessPolicy/templates/multiTenantOrganizationPartnerConfiguration')
	.update(multiTenantOrganizationPartnerConfigurationTemplate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MultiTenantOrganizationPartnerConfigurationTemplate;
use Microsoft\Graph\Generated\Models\CrossTenantAccessPolicyInboundTrust;
use Microsoft\Graph\Generated\Models\InboundOutboundPolicyConfiguration;
use Microsoft\Graph\Generated\Models\TemplateApplicationLevel;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MultiTenantOrganizationPartnerConfigurationTemplate();
$inboundTrust = new CrossTenantAccessPolicyInboundTrust();
$inboundTrust->setIsMfaAccepted(true);
$inboundTrust->setIsCompliantDeviceAccepted(true);
$inboundTrust->setIsHybridAzureADJoinedDeviceAccepted(true);
$requestBody->setInboundTrust($inboundTrust);
$automaticUserConsentSettings = new InboundOutboundPolicyConfiguration();
$automaticUserConsentSettings->setInboundAllowed(true);
$automaticUserConsentSettings->setOutboundAllowed(true);
$requestBody->setAutomaticUserConsentSettings($automaticUserConsentSettings);
$requestBody->setTemplateApplicationLevel(new TemplateApplicationLevel('newPartners,existingPartners'));

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->templates()->multiTenantOrganizationPartnerConfiguration()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	inboundTrust = @{
		isMfaAccepted = $true
		isCompliantDeviceAccepted = $true
		isHybridAzureADJoinedDeviceAccepted = $true
	}
	automaticUserConsentSettings = @{
		inboundAllowed = $true
		outboundAllowed = $true
	}
	templateApplicationLevel = "newPartners,existingPartners"
}

Update-MgPolicyCrossTenantAccessPolicyTemplateMultiTenantOrganizationPartnerConfiguration -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.multi_tenant_organization_partner_configuration_template import MultiTenantOrganizationPartnerConfigurationTemplate
from msgraph.generated.models.cross_tenant_access_policy_inbound_trust import CrossTenantAccessPolicyInboundTrust
from msgraph.generated.models.inbound_outbound_policy_configuration import InboundOutboundPolicyConfiguration
from msgraph.generated.models.template_application_level import TemplateApplicationLevel
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MultiTenantOrganizationPartnerConfigurationTemplate(
	inbound_trust = CrossTenantAccessPolicyInboundTrust(
		is_mfa_accepted = True,
		is_compliant_device_accepted = True,
		is_hybrid_azure_a_d_joined_device_accepted = True,
	),
	automatic_user_consent_settings = InboundOutboundPolicyConfiguration(
		inbound_allowed = True,
		outbound_allowed = True,
	),
	template_application_level = TemplateApplicationLevel.NewPartners | TemplateApplicationLevel.ExistingPartners,
)

result = await graph_client.policies.cross_tenant_access_policy.templates.multi_tenant_organization_partner_configuration.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
