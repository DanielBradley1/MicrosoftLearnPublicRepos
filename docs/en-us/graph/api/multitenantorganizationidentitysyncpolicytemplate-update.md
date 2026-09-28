<!-- Source: https://learn.microsoft.com/en-us/graph/api/multitenantorganizationidentitysyncpolicytemplate-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update multiTenantOrganizationIdentitySyncPolicyTemplate

Namespace: microsoft.graph

Update the cross-tenant access policy template with user synchronization settings for a multitenant organization.

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
PATCH /policies/crossTenantAccessPolicy/templates/multiTenantOrganizationIdentitySynchronization
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
| userSyncInbound | [crossTenantUserSyncInbound](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantusersyncinbound?view=graph-rest-1.0) | Determines whether users can be synchronized from the partner tenant. `false` causes any current user synchronization from the source tenant to the target tenant to stop. This property has no impact on existing users who have already been synchronized. |
| templateApplicationLevel | templateApplicationLevel | Specifies whether the template will be applied to user synchronization settings of certain tenants. The possible values are: `none`, `newPartners`, `existingPartners`, `unknownFutureValue`. You can also specify multiple values like `newPartners,existingPartners` \(default\). `none` indicates the template is not applied to any new or existing partner tenants. `newPartners` indicates the template is applied to new partner tenants. `existingPartners` indicates the template is applied to existing partner tenants, those who already had partner-specific user synchronization settings in place. Optional. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

The following example updates the user synchronization settings of the template. It configures that the template is applied for new and existing partners. For more information, see [crossTenantIdentitySyncPolicyPartner resource type](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantidentitysyncpolicypartner?view=graph-rest-1.0).

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
PATCH https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/templates/multiTenantOrganizationIdentitySynchronization
Content-Type: application/json

{
    "templateApplicationLevel": "newPartners,existingPartners",
    "userSyncInbound": {
        "isSyncAllowed": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MultiTenantOrganizationIdentitySyncPolicyTemplate
{
	TemplateApplicationLevel = TemplateApplicationLevel.NewPartners | TemplateApplicationLevel.ExistingPartners,
	UserSyncInbound = new CrossTenantUserSyncInbound
	{
		IsSyncAllowed = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Templates.MultiTenantOrganizationIdentitySynchronization.PatchAsync(requestBody);
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

requestBody := graphmodels.NewMultiTenantOrganizationIdentitySyncPolicyTemplate()
templateApplicationLevel := graphmodels.NEWPARTNERS,EXISTINGPARTNERS_TEMPLATEAPPLICATIONLEVEL 
requestBody.SetTemplateApplicationLevel(&templateApplicationLevel) 
userSyncInbound := graphmodels.NewCrossTenantUserSyncInbound()
isSyncAllowed := true
userSyncInbound.SetIsSyncAllowed(&isSyncAllowed) 
requestBody.SetUserSyncInbound(userSyncInbound)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
multiTenantOrganizationIdentitySynchronization, err := graphClient.Policies().CrossTenantAccessPolicy().Templates().MultiTenantOrganizationIdentitySynchronization().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MultiTenantOrganizationIdentitySyncPolicyTemplate multiTenantOrganizationIdentitySyncPolicyTemplate = new MultiTenantOrganizationIdentitySyncPolicyTemplate();
multiTenantOrganizationIdentitySyncPolicyTemplate.setTemplateApplicationLevel(EnumSet.of(TemplateApplicationLevel.NewPartners, TemplateApplicationLevel.ExistingPartners));
CrossTenantUserSyncInbound userSyncInbound = new CrossTenantUserSyncInbound();
userSyncInbound.setIsSyncAllowed(true);
multiTenantOrganizationIdentitySyncPolicyTemplate.setUserSyncInbound(userSyncInbound);
MultiTenantOrganizationIdentitySyncPolicyTemplate result = graphClient.policies().crossTenantAccessPolicy().templates().multiTenantOrganizationIdentitySynchronization().patch(multiTenantOrganizationIdentitySyncPolicyTemplate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const multiTenantOrganizationIdentitySyncPolicyTemplate = {
    templateApplicationLevel: 'newPartners,existingPartners',
    userSyncInbound: {
        isSyncAllowed: true
    }
};

await client.api('/policies/crossTenantAccessPolicy/templates/multiTenantOrganizationIdentitySynchronization')
	.update(multiTenantOrganizationIdentitySyncPolicyTemplate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MultiTenantOrganizationIdentitySyncPolicyTemplate;
use Microsoft\Graph\Generated\Models\TemplateApplicationLevel;
use Microsoft\Graph\Generated\Models\CrossTenantUserSyncInbound;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MultiTenantOrganizationIdentitySyncPolicyTemplate();
$requestBody->setTemplateApplicationLevel(new TemplateApplicationLevel('newPartners,existingPartners'));
$userSyncInbound = new CrossTenantUserSyncInbound();
$userSyncInbound->setIsSyncAllowed(true);
$requestBody->setUserSyncInbound($userSyncInbound);

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->templates()->multiTenantOrganizationIdentitySynchronization()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	templateApplicationLevel = "newPartners,existingPartners"
	userSyncInbound = @{
		isSyncAllowed = $true
	}
}

Update-MgPolicyCrossTenantAccessPolicyTemplateMultiTenantOrganizationIdentitySynchronization -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.multi_tenant_organization_identity_sync_policy_template import MultiTenantOrganizationIdentitySyncPolicyTemplate
from msgraph.generated.models.template_application_level import TemplateApplicationLevel
from msgraph.generated.models.cross_tenant_user_sync_inbound import CrossTenantUserSyncInbound
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MultiTenantOrganizationIdentitySyncPolicyTemplate(
	template_application_level = TemplateApplicationLevel.NewPartners | TemplateApplicationLevel.ExistingPartners,
	user_sync_inbound = CrossTenantUserSyncInbound(
		is_sync_allowed = True,
	),
)

result = await graph_client.policies.cross_tenant_access_policy.templates.multi_tenant_organization_identity_synchronization.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
