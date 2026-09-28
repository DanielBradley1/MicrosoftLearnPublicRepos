<!-- Source: https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-post-m365capabilities?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Create Microsoft 365 capability for partner

Namespace: microsoft.graph

Create a new Microsoft 365 cross-tenant capability for a partner organization in the [cross-tenant access policy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy-overview?view=graph-rest-1.0). The **@odata.type** property in the request body is required to specify which type of capability to create.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.CrossTenantCapability | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.CrossTenantCapability | Not available. |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. Managing Microsoft 365 cross-tenant capabilities affects the entire cross-tenant access policy, so no lower-privileged built-in role covers all capabilities. This operation supports the following built-in roles:

- Global Administrator - required for all capabilities, because managing the cross-tenant access policy requires directory-wide privileges.
- Exchange Administrator - supported only for the MailTips, Calendar Sharing, and Free/Busy capabilities.

## HTTP request

```http
POST /policies/crossTenantAccessPolicy/partners/{crossTenantAccessPolicyConfigurationPartner-id}/m365Capabilities
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a derived type of [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0). The **@odata.type** property is required to specify the capability type.

You can specify the following properties when you create an **m365CapabilityBase** capability.

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | The type of capability to create. Required. Example values: `#microsoft.graph.crossTenantOpenProfileCard`, `#microsoft.graph.crossTenantMigration` |
| inboundAccess | [m365CapabilityInboundAccess](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityinboundaccess?view=graph-rest-1.0) | The inbound access settings for the capability. Required. |

## Response

If successful, this method returns a `201 Created` response code and the created capability object in the response body.

## Examples

### Example 1: Create a cross-tenant mail tips capability

The following example shows how to create a [cross-tenant mail tips](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmailtipslimited?view=graph-rest-1.0) capability.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/partners/af7b70b0-d161-4628-82b4-16190344c029/m365Capabilities
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.crossTenantMailTipsLimited",
  "inboundAccess": {
    "isAllowed": false,
    "resourceScopes": {
      "included": [
        {
          "resourceId": "ad4fc698-74dc-4f62-9e71-ba9b591e8e74",
          "resourceType": "group"
        }
      ],
      "excluded": []
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CrossTenantMailTipsLimited
{
	OdataType = "#microsoft.graph.crossTenantMailTipsLimited",
	InboundAccess = new M365CapabilityInboundAccess
	{
		IsAllowed = false,
		ResourceScopes = new M365CapabilityResourceScopes
		{
			Included = new List<M365CapabilityResourceScope>
			{
				new M365CapabilityResourceScope
				{
					ResourceId = "ad4fc698-74dc-4f62-9e71-ba9b591e8e74",
					ResourceType = M365ResourceType.Group,
				},
			},
			Excluded = new List<M365CapabilityResourceScope>
			{
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Partners["{crossTenantAccessPolicyConfigurationPartner-tenantId}"].M365Capabilities.PostAsync(requestBody);
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

requestBody := graphmodels.NewM365CapabilityBase()
inboundAccess := graphmodels.NewM365CapabilityInboundAccess()
isAllowed := false
inboundAccess.SetIsAllowed(&isAllowed) 
resourceScopes := graphmodels.NewM365CapabilityResourceScopes()


m365CapabilityResourceScope := graphmodels.NewM365CapabilityResourceScope()
resourceId := "ad4fc698-74dc-4f62-9e71-ba9b591e8e74"
m365CapabilityResourceScope.SetResourceId(&resourceId) 
resourceType := graphmodels.GROUP_M365RESOURCETYPE 
m365CapabilityResourceScope.SetResourceType(&resourceType) 

included := []graphmodels.M365CapabilityResourceScopeable {
	m365CapabilityResourceScope,
}
resourceScopes.SetIncluded(included)
excluded := []graphmodels.M365CapabilityResourceScopeable {

}
resourceScopes.SetExcluded(excluded)
inboundAccess.SetResourceScopes(resourceScopes)
requestBody.SetInboundAccess(inboundAccess)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
m365Capabilities, err := graphClient.Policies().CrossTenantAccessPolicy().Partners().ByCrossTenantAccessPolicyConfigurationPartnerTenantId("crossTenantAccessPolicyConfigurationPartner-tenantId").M365Capabilities().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantMailTipsLimited m365CapabilityBase = new CrossTenantMailTipsLimited();
m365CapabilityBase.setOdataType("#microsoft.graph.crossTenantMailTipsLimited");
M365CapabilityInboundAccess inboundAccess = new M365CapabilityInboundAccess();
inboundAccess.setIsAllowed(false);
M365CapabilityResourceScopes resourceScopes = new M365CapabilityResourceScopes();
LinkedList<M365CapabilityResourceScope> included = new LinkedList<M365CapabilityResourceScope>();
M365CapabilityResourceScope m365CapabilityResourceScope = new M365CapabilityResourceScope();
m365CapabilityResourceScope.setResourceId("ad4fc698-74dc-4f62-9e71-ba9b591e8e74");
m365CapabilityResourceScope.setResourceType(M365ResourceType.Group);
included.add(m365CapabilityResourceScope);
resourceScopes.setIncluded(included);
LinkedList<M365CapabilityResourceScope> excluded = new LinkedList<M365CapabilityResourceScope>();
resourceScopes.setExcluded(excluded);
inboundAccess.setResourceScopes(resourceScopes);
m365CapabilityBase.setInboundAccess(inboundAccess);
M365CapabilityBase result = graphClient.policies().crossTenantAccessPolicy().partners().byCrossTenantAccessPolicyConfigurationPartnerTenantId("{crossTenantAccessPolicyConfigurationPartner-tenantId}").m365Capabilities().post(m365CapabilityBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const m365CapabilityBase = {
  '@odata.type': '#microsoft.graph.crossTenantMailTipsLimited',
  inboundAccess: {
    isAllowed: false,
    resourceScopes: {
      included: [
        {
          resourceId: 'ad4fc698-74dc-4f62-9e71-ba9b591e8e74',
          resourceType: 'group'
        }
      ],
      excluded: []
    }
  }
};

await client.api('/policies/crossTenantAccessPolicy/partners/af7b70b0-d161-4628-82b4-16190344c029/m365Capabilities')
	.post(m365CapabilityBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CrossTenantMailTipsLimited;
use Microsoft\Graph\Generated\Models\M365CapabilityInboundAccess;
use Microsoft\Graph\Generated\Models\M365CapabilityResourceScopes;
use Microsoft\Graph\Generated\Models\M365CapabilityResourceScope;
use Microsoft\Graph\Generated\Models\M365ResourceType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CrossTenantMailTipsLimited();
$requestBody->setOdataType('#microsoft.graph.crossTenantMailTipsLimited');
$inboundAccess = new M365CapabilityInboundAccess();
$inboundAccess->setIsAllowed(false);
$inboundAccessResourceScopes = new M365CapabilityResourceScopes();
$includedM365CapabilityResourceScope1 = new M365CapabilityResourceScope();
$includedM365CapabilityResourceScope1->setResourceId('ad4fc698-74dc-4f62-9e71-ba9b591e8e74');
$includedM365CapabilityResourceScope1->setResourceType(new M365ResourceType('group'));
$includedArray []= $includedM365CapabilityResourceScope1;
$inboundAccessResourceScopes->setIncluded($includedArray);

$inboundAccessResourceScopes->setExcluded([]);
$inboundAccess->setResourceScopes($inboundAccessResourceScopes);
$requestBody->setInboundAccess($inboundAccess);

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->partners()->byCrossTenantAccessPolicyConfigurationPartnerTenantId('crossTenantAccessPolicyConfigurationPartner-tenantId')->m365Capabilities()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cross_tenant_mail_tips_limited import CrossTenantMailTipsLimited
from msgraph.generated.models.m365_capability_inbound_access import M365CapabilityInboundAccess
from msgraph.generated.models.m365_capability_resource_scopes import M365CapabilityResourceScopes
from msgraph.generated.models.m365_capability_resource_scope import M365CapabilityResourceScope
from msgraph.generated.models.m365_resource_type import M365ResourceType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CrossTenantMailTipsLimited(
	odata_type = "#microsoft.graph.crossTenantMailTipsLimited",
	inbound_access = M365CapabilityInboundAccess(
		is_allowed = False,
		resource_scopes = M365CapabilityResourceScopes(
			included = [
				M365CapabilityResourceScope(
					resource_id = "ad4fc698-74dc-4f62-9e71-ba9b591e8e74",
					resource_type = M365ResourceType.Group,
				),
			],
			excluded = [
			],
		),
	),
)

result = await graph_client.policies.cross_tenant_access_policy.partners.by_cross_tenant_access_policy_configuration_partner_tenant_id('crossTenantAccessPolicyConfigurationPartner-tenantId').m365_capabilities.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.crossTenantMailTipsLimited",
  "name": "crossTenantMailTipsLimited",
  "lastModifiedDateTime": "2026-01-15T09:57:58.6364196Z",
  "inboundAccess": {
    "isAllowed": false,
    "resourceScopes": {
      "included": [
        {
          "resourceId": "ad4fc698-74dc-4f62-9e71-ba9b591e8e74",
          "resourceType": "group"
        }
      ],
      "excluded": []
    }
  }
}
```

### Example 2: Create a cross-tenant places room booking capability

The following example shows how to create a [cross-tenant places room booking](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantplacesroombooking?view=graph-rest-1.0) capability.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/partners/af7b70b0-d161-4628-82b4-16190344c029/m365Capabilities
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.crossTenantPlacesRoomBooking",
  "inboundAccess": {
    "isAllowed": true,
    "resourceScopes": {
      "included": [
        {
          "resourceId": "ad4fc698-74dc-4f62-9e71-ba9b591e8e74",
          "resourceType": "group"
        }
      ],
      "excluded": []
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CrossTenantPlacesRoomBooking
{
	OdataType = "#microsoft.graph.crossTenantPlacesRoomBooking",
	InboundAccess = new M365CapabilityInboundAccess
	{
		IsAllowed = true,
		ResourceScopes = new M365CapabilityResourceScopes
		{
			Included = new List<M365CapabilityResourceScope>
			{
				new M365CapabilityResourceScope
				{
					ResourceId = "ad4fc698-74dc-4f62-9e71-ba9b591e8e74",
					ResourceType = M365ResourceType.Group,
				},
			},
			Excluded = new List<M365CapabilityResourceScope>
			{
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.CrossTenantAccessPolicy.Partners["{crossTenantAccessPolicyConfigurationPartner-tenantId}"].M365Capabilities.PostAsync(requestBody);
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

requestBody := graphmodels.NewM365CapabilityBase()
inboundAccess := graphmodels.NewM365CapabilityInboundAccess()
isAllowed := true
inboundAccess.SetIsAllowed(&isAllowed) 
resourceScopes := graphmodels.NewM365CapabilityResourceScopes()


m365CapabilityResourceScope := graphmodels.NewM365CapabilityResourceScope()
resourceId := "ad4fc698-74dc-4f62-9e71-ba9b591e8e74"
m365CapabilityResourceScope.SetResourceId(&resourceId) 
resourceType := graphmodels.GROUP_M365RESOURCETYPE 
m365CapabilityResourceScope.SetResourceType(&resourceType) 

included := []graphmodels.M365CapabilityResourceScopeable {
	m365CapabilityResourceScope,
}
resourceScopes.SetIncluded(included)
excluded := []graphmodels.M365CapabilityResourceScopeable {

}
resourceScopes.SetExcluded(excluded)
inboundAccess.SetResourceScopes(resourceScopes)
requestBody.SetInboundAccess(inboundAccess)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
m365Capabilities, err := graphClient.Policies().CrossTenantAccessPolicy().Partners().ByCrossTenantAccessPolicyConfigurationPartnerTenantId("crossTenantAccessPolicyConfigurationPartner-tenantId").M365Capabilities().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantPlacesRoomBooking m365CapabilityBase = new CrossTenantPlacesRoomBooking();
m365CapabilityBase.setOdataType("#microsoft.graph.crossTenantPlacesRoomBooking");
M365CapabilityInboundAccess inboundAccess = new M365CapabilityInboundAccess();
inboundAccess.setIsAllowed(true);
M365CapabilityResourceScopes resourceScopes = new M365CapabilityResourceScopes();
LinkedList<M365CapabilityResourceScope> included = new LinkedList<M365CapabilityResourceScope>();
M365CapabilityResourceScope m365CapabilityResourceScope = new M365CapabilityResourceScope();
m365CapabilityResourceScope.setResourceId("ad4fc698-74dc-4f62-9e71-ba9b591e8e74");
m365CapabilityResourceScope.setResourceType(M365ResourceType.Group);
included.add(m365CapabilityResourceScope);
resourceScopes.setIncluded(included);
LinkedList<M365CapabilityResourceScope> excluded = new LinkedList<M365CapabilityResourceScope>();
resourceScopes.setExcluded(excluded);
inboundAccess.setResourceScopes(resourceScopes);
m365CapabilityBase.setInboundAccess(inboundAccess);
M365CapabilityBase result = graphClient.policies().crossTenantAccessPolicy().partners().byCrossTenantAccessPolicyConfigurationPartnerTenantId("{crossTenantAccessPolicyConfigurationPartner-tenantId}").m365Capabilities().post(m365CapabilityBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const m365CapabilityBase = {
  '@odata.type': '#microsoft.graph.crossTenantPlacesRoomBooking',
  inboundAccess: {
    isAllowed: true,
    resourceScopes: {
      included: [
        {
          resourceId: 'ad4fc698-74dc-4f62-9e71-ba9b591e8e74',
          resourceType: 'group'
        }
      ],
      excluded: []
    }
  }
};

await client.api('/policies/crossTenantAccessPolicy/partners/af7b70b0-d161-4628-82b4-16190344c029/m365Capabilities')
	.post(m365CapabilityBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CrossTenantPlacesRoomBooking;
use Microsoft\Graph\Generated\Models\M365CapabilityInboundAccess;
use Microsoft\Graph\Generated\Models\M365CapabilityResourceScopes;
use Microsoft\Graph\Generated\Models\M365CapabilityResourceScope;
use Microsoft\Graph\Generated\Models\M365ResourceType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CrossTenantPlacesRoomBooking();
$requestBody->setOdataType('#microsoft.graph.crossTenantPlacesRoomBooking');
$inboundAccess = new M365CapabilityInboundAccess();
$inboundAccess->setIsAllowed(true);
$inboundAccessResourceScopes = new M365CapabilityResourceScopes();
$includedM365CapabilityResourceScope1 = new M365CapabilityResourceScope();
$includedM365CapabilityResourceScope1->setResourceId('ad4fc698-74dc-4f62-9e71-ba9b591e8e74');
$includedM365CapabilityResourceScope1->setResourceType(new M365ResourceType('group'));
$includedArray []= $includedM365CapabilityResourceScope1;
$inboundAccessResourceScopes->setIncluded($includedArray);

$inboundAccessResourceScopes->setExcluded([]);
$inboundAccess->setResourceScopes($inboundAccessResourceScopes);
$requestBody->setInboundAccess($inboundAccess);

$result = $graphServiceClient->policies()->crossTenantAccessPolicy()->partners()->byCrossTenantAccessPolicyConfigurationPartnerTenantId('crossTenantAccessPolicyConfigurationPartner-tenantId')->m365Capabilities()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cross_tenant_places_room_booking import CrossTenantPlacesRoomBooking
from msgraph.generated.models.m365_capability_inbound_access import M365CapabilityInboundAccess
from msgraph.generated.models.m365_capability_resource_scopes import M365CapabilityResourceScopes
from msgraph.generated.models.m365_capability_resource_scope import M365CapabilityResourceScope
from msgraph.generated.models.m365_resource_type import M365ResourceType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CrossTenantPlacesRoomBooking(
	odata_type = "#microsoft.graph.crossTenantPlacesRoomBooking",
	inbound_access = M365CapabilityInboundAccess(
		is_allowed = True,
		resource_scopes = M365CapabilityResourceScopes(
			included = [
				M365CapabilityResourceScope(
					resource_id = "ad4fc698-74dc-4f62-9e71-ba9b591e8e74",
					resource_type = M365ResourceType.Group,
				),
			],
			excluded = [
			],
		),
	),
)

result = await graph_client.policies.cross_tenant_access_policy.partners.by_cross_tenant_access_policy_configuration_partner_tenant_id('crossTenantAccessPolicyConfigurationPartner-tenantId').m365_capabilities.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.crossTenantPlacesRoomBooking",
  "name": "crossTenantPlacesRoomBooking",
  "lastModifiedDateTime": "2026-01-15T10:27:34.8241493Z",
  "inboundAccess": {
    "isAllowed": true,
    "resourceScopes": {
      "included": [
        {
          "resourceId": "ad4fc698-74dc-4f62-9e71-ba9b591e8e74",
          "resourceType": "group"
        }
      ],
      "excluded": []
    }
  }
}
```
