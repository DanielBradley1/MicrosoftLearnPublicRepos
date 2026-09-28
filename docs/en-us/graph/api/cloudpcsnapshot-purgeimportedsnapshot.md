<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcsnapshot-purgeimportedsnapshot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# cloudPCSnapshot: purgeImportedSnapshot

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Purge \(delete\) the unused imported [snapshot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta) from the Windows 365 service-managed storage account.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/snapshots/purgeImportedSnapshot
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this method.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| snapshotIds | String collection | The list of unique identifiers for imported snapshots. |

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
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/snapshots/purgeImportedSnapshot
Content-Type: application/json

{
  "snapshotIds": [
    "7e8c3054-bda1-4e37-81c5-7d1b080a8849",
    "715c8075-6892-42f3-9550-40b4b48e13d2"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Snapshots.PurgeImportedSnapshot;

var requestBody = new PurgeImportedSnapshotPostRequestBody
{
	SnapshotIds = new List<string>
	{
		"7e8c3054-bda1-4e37-81c5-7d1b080a8849",
		"715c8075-6892-42f3-9550-40b4b48e13d2",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Snapshots.PurgeImportedSnapshot.PostAsync(requestBody);
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
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/devicemanagement"
	  //other-imports
)

requestBody := graphdevicemanagement.NewPurgeImportedSnapshotPostRequestBody()
snapshotIds := []string {
	"7e8c3054-bda1-4e37-81c5-7d1b080a8849",
	"715c8075-6892-42f3-9550-40b4b48e13d2",
}
requestBody.SetSnapshotIds(snapshotIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Snapshots().PurgeImportedSnapshot().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.snapshots.purgeimportedsnapshot.PurgeImportedSnapshotPostRequestBody purgeImportedSnapshotPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.snapshots.purgeimportedsnapshot.PurgeImportedSnapshotPostRequestBody();
LinkedList<String> snapshotIds = new LinkedList<String>();
snapshotIds.add("7e8c3054-bda1-4e37-81c5-7d1b080a8849");
snapshotIds.add("715c8075-6892-42f3-9550-40b4b48e13d2");
purgeImportedSnapshotPostRequestBody.setSnapshotIds(snapshotIds);
graphClient.deviceManagement().virtualEndpoint().snapshots().purgeImportedSnapshot().post(purgeImportedSnapshotPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const purgeImportedSnapshot = {
  snapshotIds: [
    '7e8c3054-bda1-4e37-81c5-7d1b080a8849',
    '715c8075-6892-42f3-9550-40b4b48e13d2'
  ]
};

await client.api('/deviceManagement/virtualEndpoint/snapshots/purgeImportedSnapshot')
	.version('beta')
	.post(purgeImportedSnapshot);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Snapshots\PurgeImportedSnapshot\PurgeImportedSnapshotPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PurgeImportedSnapshotPostRequestBody();
$requestBody->setSnapshotIds(['7e8c3054-bda1-4e37-81c5-7d1b080a8849', '715c8075-6892-42f3-9550-40b4b48e13d2', 	]);

$graphServiceClient->deviceManagement()->virtualEndpoint()->snapshots()->purgeImportedSnapshot()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.snapshots.purge_imported_snapshot.purge_imported_snapshot_post_request_body import PurgeImportedSnapshotPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PurgeImportedSnapshotPostRequestBody(
	snapshot_ids = [
		"7e8c3054-bda1-4e37-81c5-7d1b080a8849",
		"715c8075-6892-42f3-9550-40b4b48e13d2",
	],
)

await graph_client.device_management.virtual_endpoint.snapshots.purge_imported_snapshot.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
