<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantrelationship-post-delegatedadminrelationships?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create delegatedAdminRelationship

Namespace: microsoft.graph

Create a new [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DelegatedAdminRelationship.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DelegatedAdminRelationship.ReadWrite.All | Not available. |

Important

To call this API using application permissions, you must provision the service principal identified by **appId** `2832473f-ec63-45fb-976f-5d45a7d4bb91` and named **Partner Customer Delegated Administration** in the partner tenant. To provision the service principal in the partner tenant, call the [Create servicePrincipal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-serviceprincipals) API.

## HTTP request

```http
POST /tenantRelationships/delegatedAdminRelationships
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) object.

You can specify the following properties when creating a **delegatedAdminRelationship**.

| Property | Type | Description |
| :--- | :--- | :--- |
| accessDetails | [microsoft.graph.delegatedAdminAccessDetails](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessdetails?view=graph-rest-1.0) | The identifiers of the administrative roles that the partner requests or has access to in the customer tenant. Required. |
| autoExtendDuration | Duration | The duration by which the validity of the relationship is automatically extended, denoted in ISO 8601 format. Supported values are: `P0D`, `PT0S`, `P180D`. The default value is `PT0S`. `PT0S` indicates that the relationship expires when the **endDateTime** is reached and it isn't automatically extended. Optional. |
| customer | [microsoft.graph.delegatedAdminRelationshipCustomerParticipant](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshipcustomerparticipant?view=graph-rest-1.0) | The display name and unique identifier of the customer of the relationship. Optional. |
| displayName | String | The display name of the relationship used for ease of identification. Must be unique across *all* delegated admin relationships of the partner. Required. Maximum length is 50 characters. |
| duration | Duration | The duration of the relationship in ISO 8601 format. Must be a value between `P1D` and `P2Y` inclusive. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) object in the response body.

The response contains a **Location** header which contains a URL to the created delegated admin relationship. Each **delegatedAdminRelationship** object contains an **@odata.etag** property as per RFC2616.

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
POST https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships
Content-Type: application/json

{
  "displayName": "Contoso admin relationship",
  "duration": "P730D",
  "customer": {
    "tenantId": "4b827261-d21f-4aa9-b7db-7fa1f56fb163",
    "displayName": "Contoso subsidiary Inc"
  },
  "accessDetails": {
    "unifiedRoles": [
      {
        "roleDefinitionId": "29232cdf-9323-42fd-ade2-1d097af3e4de"
      },
      {
        "roleDefinitionId": "3a2c62db-5318-420d-8d74-23affee5d9d5"
      }
    ]
  },
  "autoExtendDuration": "P180D"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new DelegatedAdminRelationship
{
	DisplayName = "Contoso admin relationship",
	Duration = TimeSpan.Parse("P730D"),
	Customer = new DelegatedAdminRelationshipCustomerParticipant
	{
		TenantId = "4b827261-d21f-4aa9-b7db-7fa1f56fb163",
		DisplayName = "Contoso subsidiary Inc",
	},
	AccessDetails = new DelegatedAdminAccessDetails
	{
		UnifiedRoles = new List<UnifiedRole>
		{
			new UnifiedRole
			{
				RoleDefinitionId = "29232cdf-9323-42fd-ade2-1d097af3e4de",
			},
			new UnifiedRole
			{
				RoleDefinitionId = "3a2c62db-5318-420d-8d74-23affee5d9d5",
			},
		},
	},
	AutoExtendDuration = TimeSpan.Parse("P180D"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.DelegatedAdminRelationships.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewDelegatedAdminRelationship()
displayName := "Contoso admin relationship"
requestBody.SetDisplayName(&displayName) 
duration , err := abstractions.ParseISODuration("P730D")
requestBody.SetDuration(&duration) 
customer := graphmodels.NewDelegatedAdminRelationshipCustomerParticipant()
tenantId := "4b827261-d21f-4aa9-b7db-7fa1f56fb163"
customer.SetTenantId(&tenantId) 
displayName := "Contoso subsidiary Inc"
customer.SetDisplayName(&displayName) 
requestBody.SetCustomer(customer)
accessDetails := graphmodels.NewDelegatedAdminAccessDetails()


unifiedRole := graphmodels.NewUnifiedRole()
roleDefinitionId := "29232cdf-9323-42fd-ade2-1d097af3e4de"
unifiedRole.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole1 := graphmodels.NewUnifiedRole()
roleDefinitionId := "3a2c62db-5318-420d-8d74-23affee5d9d5"
unifiedRole1.SetRoleDefinitionId(&roleDefinitionId) 

unifiedRoles := []graphmodels.UnifiedRoleable {
	unifiedRole,
	unifiedRole1,
}
accessDetails.SetUnifiedRoles(unifiedRoles)
requestBody.SetAccessDetails(accessDetails)
autoExtendDuration , err := abstractions.ParseISODuration("P180D")
requestBody.SetAutoExtendDuration(&autoExtendDuration) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delegatedAdminRelationships, err := graphClient.TenantRelationships().DelegatedAdminRelationships().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DelegatedAdminRelationship delegatedAdminRelationship = new DelegatedAdminRelationship();
delegatedAdminRelationship.setDisplayName("Contoso admin relationship");
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("P730D"));
delegatedAdminRelationship.setDuration(duration);
DelegatedAdminRelationshipCustomerParticipant customer = new DelegatedAdminRelationshipCustomerParticipant();
customer.setTenantId("4b827261-d21f-4aa9-b7db-7fa1f56fb163");
customer.setDisplayName("Contoso subsidiary Inc");
delegatedAdminRelationship.setCustomer(customer);
DelegatedAdminAccessDetails accessDetails = new DelegatedAdminAccessDetails();
LinkedList<UnifiedRole> unifiedRoles = new LinkedList<UnifiedRole>();
UnifiedRole unifiedRole = new UnifiedRole();
unifiedRole.setRoleDefinitionId("29232cdf-9323-42fd-ade2-1d097af3e4de");
unifiedRoles.add(unifiedRole);
UnifiedRole unifiedRole1 = new UnifiedRole();
unifiedRole1.setRoleDefinitionId("3a2c62db-5318-420d-8d74-23affee5d9d5");
unifiedRoles.add(unifiedRole1);
accessDetails.setUnifiedRoles(unifiedRoles);
delegatedAdminRelationship.setAccessDetails(accessDetails);
PeriodAndDuration autoExtendDuration = PeriodAndDuration.ofDuration(Duration.parse("P180D"));
delegatedAdminRelationship.setAutoExtendDuration(autoExtendDuration);
DelegatedAdminRelationship result = graphClient.tenantRelationships().delegatedAdminRelationships().post(delegatedAdminRelationship);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const delegatedAdminRelationship = {
  displayName: 'Contoso admin relationship',
  duration: 'P730D',
  customer: {
    tenantId: '4b827261-d21f-4aa9-b7db-7fa1f56fb163',
    displayName: 'Contoso subsidiary Inc'
  },
  accessDetails: {
    unifiedRoles: [
      {
        roleDefinitionId: '29232cdf-9323-42fd-ade2-1d097af3e4de'
      },
      {
        roleDefinitionId: '3a2c62db-5318-420d-8d74-23affee5d9d5'
      }
    ]
  },
  autoExtendDuration: 'P180D'
};

await client.api('/tenantRelationships/delegatedAdminRelationships')
	.post(delegatedAdminRelationship);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\DelegatedAdminRelationship;
use Microsoft\Graph\Generated\Models\DelegatedAdminRelationshipCustomerParticipant;
use Microsoft\Graph\Generated\Models\DelegatedAdminAccessDetails;
use Microsoft\Graph\Generated\Models\UnifiedRole;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DelegatedAdminRelationship();
$requestBody->setDisplayName('Contoso admin relationship');
$requestBody->setDuration(new \DateInterval('P730D'));
$customer = new DelegatedAdminRelationshipCustomerParticipant();
$customer->setTenantId('4b827261-d21f-4aa9-b7db-7fa1f56fb163');
$customer->setDisplayName('Contoso subsidiary Inc');
$requestBody->setCustomer($customer);
$accessDetails = new DelegatedAdminAccessDetails();
$unifiedRolesUnifiedRole1 = new UnifiedRole();
$unifiedRolesUnifiedRole1->setRoleDefinitionId('29232cdf-9323-42fd-ade2-1d097af3e4de');
$unifiedRolesArray []= $unifiedRolesUnifiedRole1;
$unifiedRolesUnifiedRole2 = new UnifiedRole();
$unifiedRolesUnifiedRole2->setRoleDefinitionId('3a2c62db-5318-420d-8d74-23affee5d9d5');
$unifiedRolesArray []= $unifiedRolesUnifiedRole2;
$accessDetails->setUnifiedRoles($unifiedRolesArray);

$requestBody->setAccessDetails($accessDetails);
$requestBody->setAutoExtendDuration(new \DateInterval('P180D'));

$result = $graphServiceClient->tenantRelationships()->delegatedAdminRelationships()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Partner

$params = @{
	displayName = "Contoso admin relationship"
	duration = "P730D"
	customer = @{
		tenantId = "4b827261-d21f-4aa9-b7db-7fa1f56fb163"
		displayName = "Contoso subsidiary Inc"
	}
	accessDetails = @{
		unifiedRoles = @(
			@{
				roleDefinitionId = "29232cdf-9323-42fd-ade2-1d097af3e4de"
			}
			@{
				roleDefinitionId = "3a2c62db-5318-420d-8d74-23affee5d9d5"
			}
		)
	}
	autoExtendDuration = "P180D"
}

New-MgTenantRelationshipDelegatedAdminRelationship -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.delegated_admin_relationship import DelegatedAdminRelationship
from msgraph.generated.models.delegated_admin_relationship_customer_participant import DelegatedAdminRelationshipCustomerParticipant
from msgraph.generated.models.delegated_admin_access_details import DelegatedAdminAccessDetails
from msgraph.generated.models.unified_role import UnifiedRole
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DelegatedAdminRelationship(
	display_name = "Contoso admin relationship",
	duration = "P730D",
	customer = DelegatedAdminRelationshipCustomerParticipant(
		tenant_id = "4b827261-d21f-4aa9-b7db-7fa1f56fb163",
		display_name = "Contoso subsidiary Inc",
	),
	access_details = DelegatedAdminAccessDetails(
		unified_roles = [
			UnifiedRole(
				role_definition_id = "29232cdf-9323-42fd-ade2-1d097af3e4de",
			),
			UnifiedRole(
				role_definition_id = "3a2c62db-5318-420d-8d74-23affee5d9d5",
			),
		],
	),
	auto_extend_duration = "P180D",
)

result = await graph_client.tenant_relationships.delegated_admin_relationships.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Location: https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships/5d027261-d21f-4aa9-b7db-7fa1f56fb163-8777b240-c6f0-4469-9e98-a3205431b836

{
  "@odata.type": "#microsoft.graph.delegatedAdminRelationship",
  "@odata.context": "https://graph.microsoft.com/v1.0/tenantRelationships/$metadata#delegatedAdminRelationships",
  "@odata.etag": "W/\"JyIxODAwZTY4My0wMDAwLTAyMDAtMDAwMC02MTU0OWFmMDAwMDAiJw==\"",
  "id": "5d027261-d21f-4aa9-b7db-7fa1f56fb163-8777b240-c6f0-4469-9e98-a3205431b836",
  "displayName": "Contoso admin relationship",
  "duration": "P730D",
  "customer": {
    "tenantId": "4b827261-d21f-4aa9-b7db-7fa1f56fb163",
    "displayName": "Contoso subsidiary Inc"
  },
  "accessDetails": {
    "unifiedRoles": [
      {
        "roleDefinitionId": "29232cdf-9323-42fd-ade2-1d097af3e4de"
      },
      {
        "roleDefinitionId": "3a2c62db-5318-420d-8d74-23affee5d9d5"
      }
    ]
  },
  "status": "created",
  "autoExtendDuration": "P180D",
  "createdDateTime": "2022-02-10T11:24:42.3148266Z",
  "lastModifiedDateTime": "2022-02-10T11:24:42.3148266Z",
  "activatedDateTime": "",
  "endDateTime": "2024-02-10T11:24:42.3148266Z"
}
```
