<!-- Source: https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-connectedorganizations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create connectedOrganization

Namespace: microsoft.graph

Create a new [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) where the least privileged role is *Identity Governance Administrator*. **This is the least privileged option.**

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Identity Governance Administrator* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/connectedOrganizations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) object.

You can specify the following properties when creating a **connectedOrganization**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The connected organization name. |
| description | String | The connected organization description. |
| identitySources | [identitySource](https://learn.microsoft.com/en-us/graph/api/resources/identitysource?view=graph-rest-1.0) collection | A collection with one element, the initial identity source in this connected organization. |
| state | connectedOrganizationState | The state of a connected organization defines whether assignment policies with requestor scope type `AllConfiguredConnectedOrganizationSubjects` are applicable or not. The possible values are: `configured`, `proposed`. |

## Response

If successful, this method returns a `201 Created` response code and a new [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a connected organization

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/connectedOrganizations/
Content-Type: application/json

{
  "displayName":"Connected organization name",
  "description":"Connected organization description",
  "identitySources": [
    {
      "@odata.type": "#microsoft.graph.domainIdentitySource",
      "domainName": "example.com",
      "displayName": "example.com"
      }
  ],
  "state":"proposed"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ConnectedOrganization
{
	DisplayName = "Connected organization name",
	Description = "Connected organization description",
	IdentitySources = new List<IdentitySource>
	{
		new DomainIdentitySource
		{
			OdataType = "#microsoft.graph.domainIdentitySource",
			DomainName = "example.com",
			DisplayName = "example.com",
		},
	},
	State = ConnectedOrganizationState.Proposed,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ConnectedOrganizations.PostAsync(requestBody);
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

requestBody := graphmodels.NewConnectedOrganization()
displayName := "Connected organization name"
requestBody.SetDisplayName(&displayName) 
description := "Connected organization description"
requestBody.SetDescription(&description) 


identitySource := graphmodels.NewDomainIdentitySource()
domainName := "example.com"
identitySource.SetDomainName(&domainName) 
displayName := "example.com"
identitySource.SetDisplayName(&displayName) 

identitySources := []graphmodels.IdentitySourceable {
	identitySource,
}
requestBody.SetIdentitySources(identitySources)
state := graphmodels.PROPOSED_CONNECTEDORGANIZATIONSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
connectedOrganizations, err := graphClient.IdentityGovernance().EntitlementManagement().ConnectedOrganizations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConnectedOrganization connectedOrganization = new ConnectedOrganization();
connectedOrganization.setDisplayName("Connected organization name");
connectedOrganization.setDescription("Connected organization description");
LinkedList<IdentitySource> identitySources = new LinkedList<IdentitySource>();
DomainIdentitySource identitySource = new DomainIdentitySource();
identitySource.setOdataType("#microsoft.graph.domainIdentitySource");
identitySource.setDomainName("example.com");
identitySource.setDisplayName("example.com");
identitySources.add(identitySource);
connectedOrganization.setIdentitySources(identitySources);
connectedOrganization.setState(ConnectedOrganizationState.Proposed);
ConnectedOrganization result = graphClient.identityGovernance().entitlementManagement().connectedOrganizations().post(connectedOrganization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const connectedOrganization = {
  displayName: 'Connected organization name',
  description: 'Connected organization description',
  identitySources: [
    {
      '@odata.type': '#microsoft.graph.domainIdentitySource',
      domainName: 'example.com',
      displayName: 'example.com'
      }
  ],
  state: 'proposed'
};

await client.api('/identityGovernance/entitlementManagement/connectedOrganizations/')
	.post(connectedOrganization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConnectedOrganization;
use Microsoft\Graph\Generated\Models\IdentitySource;
use Microsoft\Graph\Generated\Models\DomainIdentitySource;
use Microsoft\Graph\Generated\Models\ConnectedOrganizationState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConnectedOrganization();
$requestBody->setDisplayName('Connected organization name');
$requestBody->setDescription('Connected organization description');
$identitySourcesIdentitySource1 = new DomainIdentitySource();
$identitySourcesIdentitySource1->setOdataType('#microsoft.graph.domainIdentitySource');
$identitySourcesIdentitySource1->setDomainName('example.com');
$identitySourcesIdentitySource1->setDisplayName('example.com');
$identitySourcesArray []= $identitySourcesIdentitySource1;
$requestBody->setIdentitySources($identitySourcesArray);

$requestBody->setState(new ConnectedOrganizationState('proposed'));

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->connectedOrganizations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Connected organization name"
	description = "Connected organization description"
	identitySources = @(
		@{
			"@odata.type" = "#microsoft.graph.domainIdentitySource"
			domainName = "example.com"
			displayName = "example.com"
		}
	)
	state = "proposed"
}

New-MgEntitlementManagementConnectedOrganization -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.connected_organization import ConnectedOrganization
from msgraph.generated.models.identity_source import IdentitySource
from msgraph.generated.models.domain_identity_source import DomainIdentitySource
from msgraph.generated.models.connected_organization_state import ConnectedOrganizationState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConnectedOrganization(
	display_name = "Connected organization name",
	description = "Connected organization description",
	identity_sources = [
		DomainIdentitySource(
			odata_type = "#microsoft.graph.domainIdentitySource",
			domain_name = "example.com",
			display_name = "example.com",
		),
	],
	state = ConnectedOrganizationState.Proposed,
)

result = await graph_client.identity_governance.entitlement_management.connected_organizations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "35ff48a8-e9d8-4405-8425-0b23694287a4",
  "displayName": "Connected organization name",
  "description": "Connected organization description",
  "createdDateTime": "2021-11-10T01:13:15.541617Z",
  "modifiedDateTime": "2021-11-10T01:13:15.541617Z",
  "state": "proposed",
  "identitySources": []
}
```

### Example 2: Create a connected organization with an identitySource based on a tenant ID

This example shows creating a connected organization with an identity source based on a tenant ID. The tenant ID can be found, by the domain name, using the [tenantRelationship: findTenantInformationByDomainName](https://learn.microsoft.com/en-us/graph/api/tenantrelationship-findtenantinformationbydomainname?view=graph-rest-1.0) call.

### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/connectedOrganizations/
Content-Type: application/json

{
  "displayName":"Connected organization name",
  "description":"Connected organization description",
  "identitySources": [
    {
      "@odata.type": "#microsoft.graph.azureActiveDirectoryTenant",
      "displayName": "Contoso",
      "tenantId": "aaaabbbb-0000-cccc-1111-dddd2222eeee"
      }
  ],
  "state":"proposed"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ConnectedOrganization
{
	DisplayName = "Connected organization name",
	Description = "Connected organization description",
	IdentitySources = new List<IdentitySource>
	{
		new AzureActiveDirectoryTenant
		{
			OdataType = "#microsoft.graph.azureActiveDirectoryTenant",
			DisplayName = "Contoso",
			TenantId = "aaaabbbb-0000-cccc-1111-dddd2222eeee",
		},
	},
	State = ConnectedOrganizationState.Proposed,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ConnectedOrganizations.PostAsync(requestBody);
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

requestBody := graphmodels.NewConnectedOrganization()
displayName := "Connected organization name"
requestBody.SetDisplayName(&displayName) 
description := "Connected organization description"
requestBody.SetDescription(&description) 


identitySource := graphmodels.NewAzureActiveDirectoryTenant()
displayName := "Contoso"
identitySource.SetDisplayName(&displayName) 
tenantId := "aaaabbbb-0000-cccc-1111-dddd2222eeee"
identitySource.SetTenantId(&tenantId) 

identitySources := []graphmodels.IdentitySourceable {
	identitySource,
}
requestBody.SetIdentitySources(identitySources)
state := graphmodels.PROPOSED_CONNECTEDORGANIZATIONSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
connectedOrganizations, err := graphClient.IdentityGovernance().EntitlementManagement().ConnectedOrganizations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConnectedOrganization connectedOrganization = new ConnectedOrganization();
connectedOrganization.setDisplayName("Connected organization name");
connectedOrganization.setDescription("Connected organization description");
LinkedList<IdentitySource> identitySources = new LinkedList<IdentitySource>();
AzureActiveDirectoryTenant identitySource = new AzureActiveDirectoryTenant();
identitySource.setOdataType("#microsoft.graph.azureActiveDirectoryTenant");
identitySource.setDisplayName("Contoso");
identitySource.setTenantId("aaaabbbb-0000-cccc-1111-dddd2222eeee");
identitySources.add(identitySource);
connectedOrganization.setIdentitySources(identitySources);
connectedOrganization.setState(ConnectedOrganizationState.Proposed);
ConnectedOrganization result = graphClient.identityGovernance().entitlementManagement().connectedOrganizations().post(connectedOrganization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const connectedOrganization = {
  displayName: 'Connected organization name',
  description: 'Connected organization description',
  identitySources: [
    {
      '@odata.type': '#microsoft.graph.azureActiveDirectoryTenant',
      displayName: 'Contoso',
      tenantId: 'aaaabbbb-0000-cccc-1111-dddd2222eeee'
      }
  ],
  state: 'proposed'
};

await client.api('/identityGovernance/entitlementManagement/connectedOrganizations/')
	.post(connectedOrganization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConnectedOrganization;
use Microsoft\Graph\Generated\Models\IdentitySource;
use Microsoft\Graph\Generated\Models\AzureActiveDirectoryTenant;
use Microsoft\Graph\Generated\Models\ConnectedOrganizationState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConnectedOrganization();
$requestBody->setDisplayName('Connected organization name');
$requestBody->setDescription('Connected organization description');
$identitySourcesIdentitySource1 = new AzureActiveDirectoryTenant();
$identitySourcesIdentitySource1->setOdataType('#microsoft.graph.azureActiveDirectoryTenant');
$identitySourcesIdentitySource1->setDisplayName('Contoso');
$identitySourcesIdentitySource1->setTenantId('aaaabbbb-0000-cccc-1111-dddd2222eeee');
$identitySourcesArray []= $identitySourcesIdentitySource1;
$requestBody->setIdentitySources($identitySourcesArray);

$requestBody->setState(new ConnectedOrganizationState('proposed'));

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->connectedOrganizations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Connected organization name"
	description = "Connected organization description"
	identitySources = @(
		@{
			"@odata.type" = "#microsoft.graph.azureActiveDirectoryTenant"
			displayName = "Contoso"
			tenantId = "aaaabbbb-0000-cccc-1111-dddd2222eeee"
		}
	)
	state = "proposed"
}

New-MgEntitlementManagementConnectedOrganization -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.connected_organization import ConnectedOrganization
from msgraph.generated.models.identity_source import IdentitySource
from msgraph.generated.models.azure_active_directory_tenant import AzureActiveDirectoryTenant
from msgraph.generated.models.connected_organization_state import ConnectedOrganizationState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConnectedOrganization(
	display_name = "Connected organization name",
	description = "Connected organization description",
	identity_sources = [
		AzureActiveDirectoryTenant(
			odata_type = "#microsoft.graph.azureActiveDirectoryTenant",
			display_name = "Contoso",
			tenant_id = "aaaabbbb-0000-cccc-1111-dddd2222eeee",
		),
	],
	state = ConnectedOrganizationState.Proposed,
)

result = await graph_client.identity_governance.entitlement_management.connected_organizations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/connectedOrganizations/$entity",
  "id": "922c86cf-65b8-4d94-b6a6-477dde331c7b",
  "displayName": "Connected organization name",
  "description": "Connected organization description",
  "createdDateTime": "2024-10-29T21:55:39.6051923Z",
  "modifiedDateTime": "2024-10-29T21:55:39.6051923Z",
  "state": "proposed",
  "identitySources": []
}
```
