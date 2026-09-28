<!-- Source: https://learn.microsoft.com/en-us/graph/api/b2bmanagementpolicy-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update b2bManagementPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.B2BManagementPolicy | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.B2BManagementPolicy | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Administrator* is the only role supported for this operation.

## HTTP request

```http
PATCH /policies/b2bManagementPolicies/{b2bManagementPolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

In the request body, supply a JSON representation of the [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) object.

You can specify the following properties when creating a **b2bManagementPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and Time when the policy object was deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). Optional. |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for a policy. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). Required. |
| description | String | Description for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). Required. |
| displayName | String | Display name for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). Required. |
| isOrganizationDefault | Boolean | If set to true, activates this policy. There can be many policies for the same policy type, but only one can be activated as the organization default. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/policies/b2bManagementPolicies/f596ef0d-42f9-0359-1aaa-12d02b38802a
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.b2bManagementPolicy",
  "description": "Policy used for B2B features",
  "displayName": "Policy1",
  "definition": [
    "{'B2BManagementPolicy':{'Version':1}}"
  ],
  "isOrganizationDefault": "true"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new B2bManagementPolicy
{
	OdataType = "#microsoft.graph.b2bManagementPolicy",
	Description = "Policy used for B2B features",
	DisplayName = "Policy1",
	Definition = new List<string>
	{
		"{'B2BManagementPolicy':{'Version':1}}",
	},
	IsOrganizationDefault = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.B2bManagementPolicies["{b2bManagementPolicy-id}"].PatchAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewB2bManagementPolicy()
description := "Policy used for B2B features"
requestBody.SetDescription(&description) 
displayName := "Policy1"
requestBody.SetDisplayName(&displayName) 
definition := []string {
	"{'B2BManagementPolicy':{'Version':1}}",
}
requestBody.SetDefinition(definition)
isOrganizationDefault := true
requestBody.SetIsOrganizationDefault(&isOrganizationDefault) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
b2bManagementPolicies, err := graphClient.Policies().B2bManagementPolicies().ByB2bManagementPolicyId("b2bManagementPolicy-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

B2bManagementPolicy b2bManagementPolicy = new B2bManagementPolicy();
b2bManagementPolicy.setOdataType("#microsoft.graph.b2bManagementPolicy");
b2bManagementPolicy.setDescription("Policy used for B2B features");
b2bManagementPolicy.setDisplayName("Policy1");
LinkedList<String> definition = new LinkedList<String>();
definition.add("{'B2BManagementPolicy':{'Version':1}}");
b2bManagementPolicy.setDefinition(definition);
b2bManagementPolicy.setIsOrganizationDefault(true);
B2bManagementPolicy result = graphClient.policies().b2bManagementPolicies().byB2bManagementPolicyId("{b2bManagementPolicy-id}").patch(b2bManagementPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const b2bManagementPolicy = {
  '@odata.type': '#microsoft.graph.b2bManagementPolicy',
  description: 'Policy used for B2B features',
  displayName: 'Policy1',
  definition: [
    '{\'B2BManagementPolicy\':{\'Version\':1}}'
  ],
  isOrganizationDefault: 'true'
};

await client.api('/policies/b2bManagementPolicies/f596ef0d-42f9-0359-1aaa-12d02b38802a')
	.version('beta')
	.update(b2bManagementPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\B2bManagementPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new B2bManagementPolicy();
$requestBody->setOdataType('#microsoft.graph.b2bManagementPolicy');
$requestBody->setDescription('Policy used for B2B features');
$requestBody->setDisplayName('Policy1');
$requestBody->setDefinition(['{\'B2BManagementPolicy\':{\'Version\':1}}', 	]);
$requestBody->setIsOrganizationDefault(true);

$result = $graphServiceClient->policies()->b2bManagementPolicies()->byB2bManagementPolicyId('b2bManagementPolicy-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.b2bManagementPolicy"
	description = "Policy used for B2B features"
	displayName = "Policy1"
	definition = @(
	'{'B2BManagementPolicy':{'Version':1}}'
)
isOrganizationDefault = "true"
}

Update-MgBetaPolicyB2BManagementPolicy -B2bManagementPolicyId $b2bManagementPolicyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.b2b_management_policy import B2bManagementPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = B2bManagementPolicy(
	odata_type = "#microsoft.graph.b2bManagementPolicy",
	description = "Policy used for B2B features",
	display_name = "Policy1",
	definition = [
		"{'B2BManagementPolicy':{'Version':1}}",
	],
	is_organization_default = True,
)

result = await graph_client.policies.b2b_management_policies.by_b2b_management_policy_id('b2bManagementPolicy-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.b2bManagementPolicy",
  "id": "f596ef0d-42f9-0359-1aaa-12d02b38802a",
  "deletedDateTime": null,
  "description": "Policy used for B2B features",
  "displayName": "Policy1",
  "definition": [
    "{'B2BManagementPolicy':{'Version':1}}"
  ],
  "isOrganizationDefault": true
}
```
