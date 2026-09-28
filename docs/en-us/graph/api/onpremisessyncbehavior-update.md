<!-- Source: https://learn.microsoft.com/en-us/graph/api/onpremisessyncbehavior-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-09 -->

# Update onPremisesSyncBehavior

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of an [onPremisesSyncBehavior](https://learn.microsoft.com/en-us/graph/api/resources/onpremisessyncbehavior?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) | Group-OnPremisesSyncBehavior.ReadWrite.All | Not supported. | Group-OnPremisesSyncBehavior.ReadWrite.All |
| [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-beta) | Contacts-OnPremisesSyncBehavior.ReadWrite.All | Not supported. | Contacts-OnPremisesSyncBehavior.ReadWrite.All |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | User-OnPremisesSyncBehavior.ReadWrite.All | Not supported. | User-OnPremisesSyncBehavior.ReadWrite.All |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. *Hybrid Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /contacts/{id}/onPremisesSyncBehavior
PATCH /groups/{id}/onPremisesSyncBehavior
PATCH /users/{id}/onPremisesSyncBehavior
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
| isCloudManaged | Boolean | Indicates whether the object’s source of authority is set to the cloud. If `true`, updates from on-premises Active Directory are blocked in the cloud; if `false`, updates from on-premises Active Directory are allowed in the cloud and object can be taken over by the on-premises Active Directory. |

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
PATCH https://graph.microsoft.com/beta/groups/e7c2f02a-7a59-40de-8d6e-1e0197b8cfba/onPremisesSyncBehavior
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onPremisesSyncBehavior",
  "isCloudManaged": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new OnPremisesSyncBehavior
{
	OdataType = "#microsoft.graph.onPremisesSyncBehavior",
	IsCloudManaged = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].OnPremisesSyncBehavior.PatchAsync(requestBody);
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

requestBody := graphmodels.NewOnPremisesSyncBehavior()
isCloudManaged := true
requestBody.SetIsCloudManaged(&isCloudManaged) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onPremisesSyncBehavior, err := graphClient.Groups().ByGroupId("group-id").OnPremisesSyncBehavior().Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnPremisesSyncBehavior onPremisesSyncBehavior = new OnPremisesSyncBehavior();
onPremisesSyncBehavior.setOdataType("#microsoft.graph.onPremisesSyncBehavior");
onPremisesSyncBehavior.setIsCloudManaged(true);
OnPremisesSyncBehavior result = graphClient.groups().byGroupId("{group-id}").onPremisesSyncBehavior().patch(onPremisesSyncBehavior);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onPremisesSyncBehavior = {
  '@odata.type': '#microsoft.graph.onPremisesSyncBehavior',
  isCloudManaged: true
};

await client.api('/groups/e7c2f02a-7a59-40de-8d6e-1e0197b8cfba/onPremisesSyncBehavior')
	.version('beta')
	.update(onPremisesSyncBehavior);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\OnPremisesSyncBehavior;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnPremisesSyncBehavior();
$requestBody->setOdataType('#microsoft.graph.onPremisesSyncBehavior');
$requestBody->setIsCloudManaged(true);

$result = $graphServiceClient->groups()->byGroupId('group-id')->onPremisesSyncBehavior()->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Groups

$params = @{
	"@odata.type" = "#microsoft.graph.onPremisesSyncBehavior"
	isCloudManaged = $true
}

Update-MgBetaGroupOnPremiseSyncBehavior -GroupId $groupId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.on_premises_sync_behavior import OnPremisesSyncBehavior
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnPremisesSyncBehavior(
	odata_type = "#microsoft.graph.onPremisesSyncBehavior",
	is_cloud_managed = True,
)

result = await graph_client.groups.by_group_id('group-id').on_premises_sync_behavior.patch(request_body)
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
