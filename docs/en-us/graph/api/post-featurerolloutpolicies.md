<!-- Source: https://learn.microsoft.com/en-us/graph/api/post-featurerolloutpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create featureRolloutPolicy

Namespace: microsoft.graph

Caution

The featureRolloutPolicy API moved from /directory/featureRolloutPolicies to **/policies/featureRolloutPolicies** on March 5, 2021. The previous /directory/featureRolloutPolicies endpoint stopped returning returning data after June 30, 2021.

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.ReadWrite.All | Policy.ReadWrite.HybridAuthentication |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /policies/featureRolloutPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-beta) object.

The following table shows the properties that are required when you create a [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-beta).

| Parameter | Type | Description |
| :--- | :--- | :--- |
| displayName | string | The display name for this feature rollout policy. |
| feature | stagedFeatureName | The feature that would be rolled out using this policy. |
| isEnabled | string | Indicates whether the feature rollout is enabled. |

## Response

If successful, this method returns a `201 Created` response code and a new [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/policies/featureRolloutPolicies
Content-type: application/json

{
  "displayName": "PassthroughAuthentication rollout policy",
  "description": "PassthroughAuthentication rollout policy",
  "feature": "passthroughAuthentication",
  "isEnabled": true,
  "isAppliedToOrganization": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new FeatureRolloutPolicy
{
	DisplayName = "PassthroughAuthentication rollout policy",
	Description = "PassthroughAuthentication rollout policy",
	Feature = StagedFeatureName.PassthroughAuthentication,
	IsEnabled = true,
	IsAppliedToOrganization = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.FeatureRolloutPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewFeatureRolloutPolicy()
displayName := "PassthroughAuthentication rollout policy"
requestBody.SetDisplayName(&displayName) 
description := "PassthroughAuthentication rollout policy"
requestBody.SetDescription(&description) 
feature := graphmodels.PASSTHROUGHAUTHENTICATION_STAGEDFEATURENAME 
requestBody.SetFeature(&feature) 
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
isAppliedToOrganization := false
requestBody.SetIsAppliedToOrganization(&isAppliedToOrganization) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
featureRolloutPolicies, err := graphClient.Policies().FeatureRolloutPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FeatureRolloutPolicy featureRolloutPolicy = new FeatureRolloutPolicy();
featureRolloutPolicy.setDisplayName("PassthroughAuthentication rollout policy");
featureRolloutPolicy.setDescription("PassthroughAuthentication rollout policy");
featureRolloutPolicy.setFeature(StagedFeatureName.PassthroughAuthentication);
featureRolloutPolicy.setIsEnabled(true);
featureRolloutPolicy.setIsAppliedToOrganization(false);
FeatureRolloutPolicy result = graphClient.policies().featureRolloutPolicies().post(featureRolloutPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const featureRolloutPolicy = {
  displayName: 'PassthroughAuthentication rollout policy',
  description: 'PassthroughAuthentication rollout policy',
  feature: 'passthroughAuthentication',
  isEnabled: true,
  isAppliedToOrganization: false
};

await client.api('/policies/featureRolloutPolicies')
	.version('beta')
	.post(featureRolloutPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\FeatureRolloutPolicy;
use Microsoft\Graph\Beta\Generated\Models\StagedFeatureName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FeatureRolloutPolicy();
$requestBody->setDisplayName('PassthroughAuthentication rollout policy');
$requestBody->setDescription('PassthroughAuthentication rollout policy');
$requestBody->setFeature(new StagedFeatureName('passthroughAuthentication'));
$requestBody->setIsEnabled(true);
$requestBody->setIsAppliedToOrganization(false);

$result = $graphServiceClient->policies()->featureRolloutPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	displayName = "PassthroughAuthentication rollout policy"
	description = "PassthroughAuthentication rollout policy"
	feature = "passthroughAuthentication"
	isEnabled = $true
	isAppliedToOrganization = $false
}

New-MgBetaPolicyFeatureRolloutPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.feature_rollout_policy import FeatureRolloutPolicy
from msgraph_beta.generated.models.staged_feature_name import StagedFeatureName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FeatureRolloutPolicy(
	display_name = "PassthroughAuthentication rollout policy",
	description = "PassthroughAuthentication rollout policy",
	feature = StagedFeatureName.PassthroughAuthentication,
	is_enabled = True,
	is_applied_to_organization = False,
)

result = await graph_client.policies.feature_rollout_policies.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "e3c2f23a-edd2-43a8-849f-154e70794ac5",
  "displayName": "PassthroughAuthentication rollout policy",
  "description": "PassthroughAuthentication rollout policy",
  "feature": "passthroughAuthentication",
  "isEnabled": true,
  "isAppliedToOrganization": false
}
```
