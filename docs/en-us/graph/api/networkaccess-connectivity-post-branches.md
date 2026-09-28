<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-post-branches?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create branch \(deprecated\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

Deprecated and to be retired soon. Use the [remoteNetwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) and its associated methods instead.

Create a new branch.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
POST /networkAccess/connectivity/branches
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) object.

You can specify the following properties when creating a **branchSite**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the branch. Required. |
| country | String | The country the branch is created in. Required. |
| region | String | The location the branch is created in. Required. |
| bandwidthCapacity | Int64 | Determines the maximum allowed Mbps \(megabits per second\) bandwidth from a branch. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/networkAccess/connectivity/branches
Content-Type: application/json

{
    "name": "test branch - 11:50",
    "country": "United States",
    "region": "East US",
    "bandwidthCapacity": 500
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new BranchSite
{
	Name = "test branch - 11:50",
	Country = "United States",
	Region = Region.EastUS,
	BandwidthCapacity = 500L,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Connectivity.Branches.PostAsync(requestBody);
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
	  graphmodelsnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/models/networkaccess"
	  //other-imports
)

requestBody := graphmodelsnetworkaccess.NewBranchSite()
name := "test branch - 11:50"
requestBody.SetName(&name) 
country := "United States"
requestBody.SetCountry(&country) 
region := graphmodels.EAST US_REGION 
requestBody.SetRegion(&region) 
bandwidthCapacity := int64(500)
requestBody.SetBandwidthCapacity(&bandwidthCapacity) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
branches, err := graphClient.NetworkAccess().Connectivity().Branches().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.BranchSite branchSite = new com.microsoft.graph.beta.models.networkaccess.BranchSite();
branchSite.setName("test branch - 11:50");
branchSite.setCountry("United States");
branchSite.setRegion(com.microsoft.graph.beta.models.networkaccess.Region.EastUS);
branchSite.setBandwidthCapacity(500L);
com.microsoft.graph.models.networkaccess.BranchSite result = graphClient.networkAccess().connectivity().branches().post(branchSite);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const branchSite = {
    name: 'test branch - 11:50',
    country: 'United States',
    region: 'East US',
    bandwidthCapacity: 500
};

await client.api('/networkAccess/connectivity/branches')
	.version('beta')
	.post(branchSite);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\BranchSite;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\Region;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BranchSite();
$requestBody->setName('test branch - 11:50');
$requestBody->setCountry('United States');
$requestBody->setRegion(new Region('east US'));
$requestBody->setBandwidthCapacity(500);

$result = $graphServiceClient->networkAccess()->connectivity()->branches()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "test branch - 11:50"
	country = "United States"
	region = "East US"
	bandwidthCapacity = 500
}

New-MgBetaNetworkAccessConnectivityBranch -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.branch_site import BranchSite
from msgraph_beta.generated.models.region import Region
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BranchSite(
	name = "test branch - 11:50",
	country = "United States",
	region = Region.EastUS,
	bandwidth_capacity = 500,
)

result = await graph_client.network_access.connectivity.branches.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/branches/$entity",
    "id": "88e5a488-92c3-45d6-ba56-e5cfa63677e8",
    "name": "test branch - 11:50",
    "country": "United States",
    "region": "East US",
    "version": "1.0.0",
    "bandwidthCapacity": 500,
    "lastModifiedDateTime": "2023-05-24T08:22:02Z"
}
```
