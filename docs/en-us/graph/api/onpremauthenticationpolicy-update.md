<!-- Source: https://learn.microsoft.com/en-us/graph/api/onpremauthenticationpolicy-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update onPremAuthenticationPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of an [onPremAuthenticationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onpremauthenticationpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.OnPremAuthenticationPolicy | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

*Global Administrator* is the only built-in role supported for this operation.

## HTTP request

```http
PATCH /policies/onPremAuthenticationPolicies/{onPremAuthenticationPolicyId}
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
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for this policy. See below for more details about the JSON schema for this property. Required. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). |
| description | String | Description for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). |
| displayName | String | Display name for this policy. Required. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). |
| isOrganizationDefault | Boolean | If set to true, this instance of the policy will be considered the default for the organization. There can be many policies for the same policy type, but only one can be activated as the organization default. Optional, default value is false. Inherited from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-beta). |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/beta/policies/onPremAuthenticationPolicies/2e68a8f2-50ce-b21d-d25d-c34b59675ee2
Content-Type: application/json

{
  "deletedDateTime": null,
  "description": "Updates to policy definition to manage and control authentication settings.",
  "displayName": "Update policy name",
  "definition": [
    "{\"Version\":1,\"LastUpdatedTimestamp\":\"2025-02-29T22:47:12.7764932Z\", \"Key1\": \"Value1\", \"Key2\": {\"SubKey1\": \"SubValue1\"}}"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new OnPremAuthenticationPolicy
{
	DeletedDateTime = null,
	Description = "Updates to policy definition to manage and control authentication settings.",
	DisplayName = "Update policy name",
	Definition = new List<string>
	{
		"{\"Version\":1,\"LastUpdatedTimestamp\":\"2025-02-29T22:47:12.7764932Z\", \"Key1\": \"Value1\", \"Key2\": {\"SubKey1\": \"SubValue1\"}}",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.OnPremAuthenticationPolicies["{onPremAuthenticationPolicy-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewOnPremAuthenticationPolicy()
deletedDateTime := null
requestBody.SetDeletedDateTime(&deletedDateTime) 
description := "Updates to policy definition to manage and control authentication settings."
requestBody.SetDescription(&description) 
displayName := "Update policy name"
requestBody.SetDisplayName(&displayName) 
definition := []string {
	"{\"Version\":1,\"LastUpdatedTimestamp\":\"2025-02-29T22:47:12.7764932Z\", \"Key1\": \"Value1\", \"Key2\": {\"SubKey1\": \"SubValue1\"}}",
}
requestBody.SetDefinition(definition)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onPremAuthenticationPolicies, err := graphClient.Policies().OnPremAuthenticationPolicies().ByOnPremAuthenticationPolicyId("onPremAuthenticationPolicy-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnPremAuthenticationPolicy onPremAuthenticationPolicy = new OnPremAuthenticationPolicy();
onPremAuthenticationPolicy.setDeletedDateTime(null);
onPremAuthenticationPolicy.setDescription("Updates to policy definition to manage and control authentication settings.");
onPremAuthenticationPolicy.setDisplayName("Update policy name");
LinkedList<String> definition = new LinkedList<String>();
definition.add("{\"Version\":1,\"LastUpdatedTimestamp\":\"2025-02-29T22:47:12.7764932Z\", \"Key1\": \"Value1\", \"Key2\": {\"SubKey1\": \"SubValue1\"}}");
onPremAuthenticationPolicy.setDefinition(definition);
OnPremAuthenticationPolicy result = graphClient.policies().onPremAuthenticationPolicies().byOnPremAuthenticationPolicyId("{onPremAuthenticationPolicy-id}").patch(onPremAuthenticationPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onPremAuthenticationPolicy = {
  deletedDateTime: null,
  description: 'Updates to policy definition to manage and control authentication settings.',
  displayName: 'Update policy name',
  definition: [
    '{\"Version\':1,\'LastUpdatedTimestamp\':\'2025-02-29T22:47:12.7764932Z\", \"Key1\': \'Value1\", \"Key2\': {\'SubKey1\': \"SubValue1\"}}"
  ]
};

await client.api('/policies/onPremAuthenticationPolicies/2e68a8f2-50ce-b21d-d25d-c34b59675ee2')
	.version('beta')
	.update(onPremAuthenticationPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\OnPremAuthenticationPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnPremAuthenticationPolicy();
$requestBody->setDeletedDateTime(null);
$requestBody->setDescription('Updates to policy definition to manage and control authentication settings.');
$requestBody->setDisplayName('Update policy name');
$requestBody->setDefinition(['{\"Version\":1,\"LastUpdatedTimestamp\":\"2025-02-29T22:47:12.7764932Z\", \"Key1\": \"Value1\", \"Key2\": {\"SubKey1\": \"SubValue1\"}}', 	]);

$result = $graphServiceClient->policies()->onPremAuthenticationPolicies()->byOnPremAuthenticationPolicyId('onPremAuthenticationPolicy-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	deletedDateTime = $null
	description = "Updates to policy definition to manage and control authentication settings."
	displayName = "Update policy name"
	definition = @(
	'{"Version":1,"LastUpdatedTimestamp":"2025-02-29T22:47:12.7764932Z", "Key1": "Value1", "Key2": {"SubKey1": "SubValue1"}}'
)
}

Update-MgBetaPolicyOnPremAuthenticationPolicy -OnPremAuthenticationPolicyId $onPremAuthenticationPolicyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.on_prem_authentication_policy import OnPremAuthenticationPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnPremAuthenticationPolicy(
	deleted_date_time = None,
	description = "Updates to policy definition to manage and control authentication settings.",
	display_name = "Update policy name",
	definition = [
		"{\"Version\":1,\"LastUpdatedTimestamp\":\"2025-02-29T22:47:12.7764932Z\", \"Key1\": \"Value1\", \"Key2\": {\"SubKey1\": \"SubValue1\"}}",
	],
)

result = await graph_client.policies.on_prem_authentication_policies.by_on_prem_authentication_policy_id('onPremAuthenticationPolicy-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
