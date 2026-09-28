<!-- Source: https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationship-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-27 -->

# Update delegatedAdminRelationship

Namespace: microsoft.graph

Update the properties of a [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) object.

The following restrictions apply:

- You can update this relationship when its **status** property is `created`.
- You can update the **autoExtendDuration** property when **status** is either `created` or `active`.
- You can only remove the Microsoft Entra Global Administrator role when the **status** property is `active`, which indicates a long-running operation.

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
PATCH /tenantRelationships/delegatedAdminRelationships/{delegatedAdminRelationshipId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| If-Match | If-match: {etag}. Last known ETag value for the **delegatedAdminRelationship** to be updated. Retrieve the ETag value from a LIST or GET operation. Required. |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| accessDetails | [microsoft.graph.delegatedAdminAccessDetails](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessdetails?view=graph-rest-1.0) | The identifiers of the administrative roles that the partner requests or has access to in the customer tenant. |
| autoExtendDuration | Duration | The duration by which the validity of the relationship is automatically extended, denoted in ISO 8601 format. Supported values are: `P0D`, `PT0S`, `P180D`. The default value is `PT0S`. `PT0S` indicates that the relationship expires when the **endDateTime** is reached and it isn't automatically extended. |
| customer | [microsoft.graph.delegatedAdminRelationshipCustomerParticipant](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshipcustomerparticipant?view=graph-rest-1.0) | The display name and unique identifier of the customer of the relationship. |
| displayName | String | The display name of the relationship used for ease of identification. Must be unique across *all* delegated admin relationships of the partner. Maximum length is 50 characters. |
| duration | Duration | The duration of the relationship in ISO 8601 format. Must be a value between `P1D` and `P2Y` inclusive. |

## Response

If successful, this method returns either a `200 OK` or a `202 Accepted` response code. The response body contains a [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) object when the response is `200 OK`.

### Response headers

| Name | Description |
| :--- | :--- |
| Content-Type | application/json. |
| Location | The location of the long-running operation. |
| Retry-After | The time after which a subsequent API call can be made to the Location URL to check the status of the long-running operation. |

This method returns a `202 Accepted` response if you remove the Microsoft Entra Global Administrator role from the relationship while its **status** property is `active`. The response includes a URL in the Location header that you can use to monitor the operation's progress.

If you don't supply the template ID that corresponds to the Microsoft Entra Global Administrator role in the `unifiedRoles` array in the `accessDetails` property of the request body, then the API returns `200 OK` and the original [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships/5d027261-d21f-4aa9-b7db-7fa1f56fb163-8777b240-c6f0-4469-9e98-a3205431b836
If-Match: W/"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw=="
Content-Type: application/json

{
  "displayName": "Updated Contoso admin relationship",
  "duration": "P31D",
  "customer": {
    "tenantId": "52eaad04-13a2-4a2f-9ce8-93a294fadf36"
  },
  "accessDetails": {
    "unifiedRoles": [
      {
        "roleDefinitionId": "44367163-eba1-44c3-98af-f5787879f96a"
      },
      {
        "roleDefinitionId": "29232cdf-9323-42fd-ade2-1d097af3e4de"
      },
      {
        "roleDefinitionId": "69091246-20e8-4a56-aa4d-066075b2a7a8"
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
	DisplayName = "Updated Contoso admin relationship",
	Duration = TimeSpan.Parse("P31D"),
	Customer = new DelegatedAdminRelationshipCustomerParticipant
	{
		TenantId = "52eaad04-13a2-4a2f-9ce8-93a294fadf36",
	},
	AccessDetails = new DelegatedAdminAccessDetails
	{
		UnifiedRoles = new List<UnifiedRole>
		{
			new UnifiedRole
			{
				RoleDefinitionId = "44367163-eba1-44c3-98af-f5787879f96a",
			},
			new UnifiedRole
			{
				RoleDefinitionId = "29232cdf-9323-42fd-ade2-1d097af3e4de",
			},
			new UnifiedRole
			{
				RoleDefinitionId = "69091246-20e8-4a56-aa4d-066075b2a7a8",
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
var result = await graphClient.TenantRelationships.DelegatedAdminRelationships["{delegatedAdminRelationship-id}"].PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("If-Match", "W/\"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw==\"");
});
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
	  graphtenantrelationships "github.com/microsoftgraph/msgraph-sdk-go/tenantrelationships"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("If-Match", "W/\"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw==\"")

configuration := &graphtenantrelationships.DelegatedAdminRelationshipsItemRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewDelegatedAdminRelationship()
displayName := "Updated Contoso admin relationship"
requestBody.SetDisplayName(&displayName) 
duration , err := abstractions.ParseISODuration("P31D")
requestBody.SetDuration(&duration) 
customer := graphmodels.NewDelegatedAdminRelationshipCustomerParticipant()
tenantId := "52eaad04-13a2-4a2f-9ce8-93a294fadf36"
customer.SetTenantId(&tenantId) 
requestBody.SetCustomer(customer)
accessDetails := graphmodels.NewDelegatedAdminAccessDetails()


unifiedRole := graphmodels.NewUnifiedRole()
roleDefinitionId := "44367163-eba1-44c3-98af-f5787879f96a"
unifiedRole.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole1 := graphmodels.NewUnifiedRole()
roleDefinitionId := "29232cdf-9323-42fd-ade2-1d097af3e4de"
unifiedRole1.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole2 := graphmodels.NewUnifiedRole()
roleDefinitionId := "69091246-20e8-4a56-aa4d-066075b2a7a8"
unifiedRole2.SetRoleDefinitionId(&roleDefinitionId) 
unifiedRole3 := graphmodels.NewUnifiedRole()
roleDefinitionId := "3a2c62db-5318-420d-8d74-23affee5d9d5"
unifiedRole3.SetRoleDefinitionId(&roleDefinitionId) 

unifiedRoles := []graphmodels.UnifiedRoleable {
	unifiedRole,
	unifiedRole1,
	unifiedRole2,
	unifiedRole3,
}
accessDetails.SetUnifiedRoles(unifiedRoles)
requestBody.SetAccessDetails(accessDetails)
autoExtendDuration , err := abstractions.ParseISODuration("P180D")
requestBody.SetAutoExtendDuration(&autoExtendDuration) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delegatedAdminRelationships, err := graphClient.TenantRelationships().DelegatedAdminRelationships().ByDelegatedAdminRelationshipId("delegatedAdminRelationship-id").Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DelegatedAdminRelationship delegatedAdminRelationship = new DelegatedAdminRelationship();
delegatedAdminRelationship.setDisplayName("Updated Contoso admin relationship");
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("P31D"));
delegatedAdminRelationship.setDuration(duration);
DelegatedAdminRelationshipCustomerParticipant customer = new DelegatedAdminRelationshipCustomerParticipant();
customer.setTenantId("52eaad04-13a2-4a2f-9ce8-93a294fadf36");
delegatedAdminRelationship.setCustomer(customer);
DelegatedAdminAccessDetails accessDetails = new DelegatedAdminAccessDetails();
LinkedList<UnifiedRole> unifiedRoles = new LinkedList<UnifiedRole>();
UnifiedRole unifiedRole = new UnifiedRole();
unifiedRole.setRoleDefinitionId("44367163-eba1-44c3-98af-f5787879f96a");
unifiedRoles.add(unifiedRole);
UnifiedRole unifiedRole1 = new UnifiedRole();
unifiedRole1.setRoleDefinitionId("29232cdf-9323-42fd-ade2-1d097af3e4de");
unifiedRoles.add(unifiedRole1);
UnifiedRole unifiedRole2 = new UnifiedRole();
unifiedRole2.setRoleDefinitionId("69091246-20e8-4a56-aa4d-066075b2a7a8");
unifiedRoles.add(unifiedRole2);
UnifiedRole unifiedRole3 = new UnifiedRole();
unifiedRole3.setRoleDefinitionId("3a2c62db-5318-420d-8d74-23affee5d9d5");
unifiedRoles.add(unifiedRole3);
accessDetails.setUnifiedRoles(unifiedRoles);
delegatedAdminRelationship.setAccessDetails(accessDetails);
PeriodAndDuration autoExtendDuration = PeriodAndDuration.ofDuration(Duration.parse("P180D"));
delegatedAdminRelationship.setAutoExtendDuration(autoExtendDuration);
DelegatedAdminRelationship result = graphClient.tenantRelationships().delegatedAdminRelationships().byDelegatedAdminRelationshipId("{delegatedAdminRelationship-id}").patch(delegatedAdminRelationship, requestConfiguration -> {
	requestConfiguration.headers.add("If-Match", "W/\"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw==\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const delegatedAdminRelationship = {
  displayName: 'Updated Contoso admin relationship',
  duration: 'P31D',
  customer: {
    tenantId: '52eaad04-13a2-4a2f-9ce8-93a294fadf36'
  },
  accessDetails: {
    unifiedRoles: [
      {
        roleDefinitionId: '44367163-eba1-44c3-98af-f5787879f96a'
      },
      {
        roleDefinitionId: '29232cdf-9323-42fd-ade2-1d097af3e4de'
      },
      {
        roleDefinitionId: '69091246-20e8-4a56-aa4d-066075b2a7a8'
      },
      {
        roleDefinitionId: '3a2c62db-5318-420d-8d74-23affee5d9d5'
      }
    ]
  },
  autoExtendDuration: 'P180D'
};

await client.api('/tenantRelationships/delegatedAdminRelationships/5d027261-d21f-4aa9-b7db-7fa1f56fb163-8777b240-c6f0-4469-9e98-a3205431b836')
	.update(delegatedAdminRelationship);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\TenantRelationships\DelegatedAdminRelationships\Item\DelegatedAdminRelationshipItemRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\DelegatedAdminRelationship;
use Microsoft\Graph\Generated\Models\DelegatedAdminRelationshipCustomerParticipant;
use Microsoft\Graph\Generated\Models\DelegatedAdminAccessDetails;
use Microsoft\Graph\Generated\Models\UnifiedRole;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DelegatedAdminRelationship();
$requestBody->setDisplayName('Updated Contoso admin relationship');
$requestBody->setDuration(new \DateInterval('P31D'));
$customer = new DelegatedAdminRelationshipCustomerParticipant();
$customer->setTenantId('52eaad04-13a2-4a2f-9ce8-93a294fadf36');
$requestBody->setCustomer($customer);
$accessDetails = new DelegatedAdminAccessDetails();
$unifiedRolesUnifiedRole1 = new UnifiedRole();
$unifiedRolesUnifiedRole1->setRoleDefinitionId('44367163-eba1-44c3-98af-f5787879f96a');
$unifiedRolesArray []= $unifiedRolesUnifiedRole1;
$unifiedRolesUnifiedRole2 = new UnifiedRole();
$unifiedRolesUnifiedRole2->setRoleDefinitionId('29232cdf-9323-42fd-ade2-1d097af3e4de');
$unifiedRolesArray []= $unifiedRolesUnifiedRole2;
$unifiedRolesUnifiedRole3 = new UnifiedRole();
$unifiedRolesUnifiedRole3->setRoleDefinitionId('69091246-20e8-4a56-aa4d-066075b2a7a8');
$unifiedRolesArray []= $unifiedRolesUnifiedRole3;
$unifiedRolesUnifiedRole4 = new UnifiedRole();
$unifiedRolesUnifiedRole4->setRoleDefinitionId('3a2c62db-5318-420d-8d74-23affee5d9d5');
$unifiedRolesArray []= $unifiedRolesUnifiedRole4;
$accessDetails->setUnifiedRoles($unifiedRolesArray);

$requestBody->setAccessDetails($accessDetails);
$requestBody->setAutoExtendDuration(new \DateInterval('P180D'));
$requestConfiguration = new DelegatedAdminRelationshipItemRequestBuilderPatchRequestConfiguration();
$headers = [
	'If-Match' => 'W/"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw=="',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->tenantRelationships()->delegatedAdminRelationships()->byDelegatedAdminRelationshipId('delegatedAdminRelationship-id')->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Partner

$params = @{
	displayName = "Updated Contoso admin relationship"
	duration = "P31D"
	customer = @{
		tenantId = "52eaad04-13a2-4a2f-9ce8-93a294fadf36"
	}
	accessDetails = @{
		unifiedRoles = @(
			@{
				roleDefinitionId = "44367163-eba1-44c3-98af-f5787879f96a"
			}
			@{
				roleDefinitionId = "29232cdf-9323-42fd-ade2-1d097af3e4de"
			}
			@{
				roleDefinitionId = "69091246-20e8-4a56-aa4d-066075b2a7a8"
			}
			@{
				roleDefinitionId = "3a2c62db-5318-420d-8d74-23affee5d9d5"
			}
		)
	}
	autoExtendDuration = "P180D"
}

Update-MgTenantRelationshipDelegatedAdminRelationship -DelegatedAdminRelationshipId $delegatedAdminRelationshipId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.tenant_relationships.delegated_admin_relationships.item.delegated_admin_relationship_item_request_builder import DelegatedAdminRelationshipItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.delegated_admin_relationship import DelegatedAdminRelationship
from msgraph.generated.models.delegated_admin_relationship_customer_participant import DelegatedAdminRelationshipCustomerParticipant
from msgraph.generated.models.delegated_admin_access_details import DelegatedAdminAccessDetails
from msgraph.generated.models.unified_role import UnifiedRole
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DelegatedAdminRelationship(
	display_name = "Updated Contoso admin relationship",
	duration = "P31D",
	customer = DelegatedAdminRelationshipCustomerParticipant(
		tenant_id = "52eaad04-13a2-4a2f-9ce8-93a294fadf36",
	),
	access_details = DelegatedAdminAccessDetails(
		unified_roles = [
			UnifiedRole(
				role_definition_id = "44367163-eba1-44c3-98af-f5787879f96a",
			),
			UnifiedRole(
				role_definition_id = "29232cdf-9323-42fd-ade2-1d097af3e4de",
			),
			UnifiedRole(
				role_definition_id = "69091246-20e8-4a56-aa4d-066075b2a7a8",
			),
			UnifiedRole(
				role_definition_id = "3a2c62db-5318-420d-8d74-23affee5d9d5",
			),
		],
	),
	auto_extend_duration = "P180D",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "W/\"JyI0NzAwNjg0NS0wMDAwLTE5MDAtMDAwMC02MGY0Yjg4MzAwMDAiJw==\"")


result = await graph_client.tenant_relationships.delegated_admin_relationships.by_delegated_admin_relationship_id('delegatedAdminRelationship-id').patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the request.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.delegatedAdminRelationship",
  "@odata.context": "https://graph.microsoft.com/v1.0/tenantRelationships/$metadata#delegatedAdminRelationships/$entity",
  "@odata.etag": "W/\"JyIwMzAwZTM0ZS0wMDAwLTAyMDAtMDAwMC02MTRjZjI1YzAwMDAiJw==\"",
  "id": "5d027261-d21f-4aa9-b7db-7fa1f56fb163-8777b240-c6f0-4469-9e98-a3205431b836",
  "displayName": "Updated Contoso admin relationship",
  "duration": "P31D",
  "status": "created",
  "createdDateTime": "2022-02-10T11:24:42.3148266Z",
  "lastModifiedDateTime": "2022-02-10T11:26:44.9941884Z",
  "customer": {
    "tenantId": "52eaad04-13a2-4a2f-9ce8-93a294fadf36"
  },
  "accessDetails": {
    "unifiedRoles": [
      {
        "roleDefinitionId": "44367163-eba1-44c3-98af-f5787879f96a"
      },
      {
        "roleDefinitionId": "29232cdf-9323-42fd-ade2-1d097af3e4de"
      },
      {
        "roleDefinitionId": "69091246-20e8-4a56-aa4d-066075b2a7a8"
      },
      {
        "roleDefinitionId": "3a2c62db-5318-420d-8d74-23affee5d9d5"
      }
    ]
  },
  "autoExtendDuration": "P180D"
}
```

The following is an example response that returns a `202 Accepted` response code along with **Location** and **Retry-After** headers.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships/5e5594d3-6f82-458b-b567-77db4811f0cd-00000000-0000-0000-0000-000000001234/operations/d8dbb27b-7fe7-4523-a3df-f766355fe0f2
Retry-After: 10
Content-Type: application/json

{
}
```
