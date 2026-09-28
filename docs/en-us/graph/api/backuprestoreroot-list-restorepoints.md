<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-restorepoints?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# List restorePoints

Namespace: microsoft.graph

Get a list of the [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) objects and their properties.

> **Note:** This API returns a maximum of five **restorePoint** objects. If you don't include the `orderBy` parameter, the five most recent restore points are returned.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Search.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Search.Read.All | Not available. |

## HTTP request

```http
GET /solutions/backupRestore/restorePoints?$expand=protectionUnit($filter=id eq '{ProtectionUnitID}')&$filter=protectionDateTime lt YYYY-MM-DDTHH:mm:ssZ
```

## Optional query parameters

This method supports the `$expand`, `$filter`, and `orderBy` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters), as shown in the [example](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-restorepoints?view=graph-rest-1.0#request) later in this topic.

The `$expand` and `$filter` query parameters are required.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

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

```msgraph
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/restorePoints?$expand=protectionUnit($filter=id eq 'd234cf54-e0fb-49b7-9c8a-5bcd1439e853')&$filter=protectionDateTime lt 2024-05-12T10:01:00Z
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.RestorePoints.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "protectionUnit($filter=id eq 'd234cf54-e0fb-49b7-9c8a-5bcd1439e853')" };
	requestConfiguration.QueryParameters.Filter = "protectionDateTime lt 2024-05-12T10:01:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsolutions "github.com/microsoftgraph/msgraph-sdk-go/solutions"
	  //other-imports
)


requestFilter := "protectionDateTime lt 2024-05-12T10:01:00Z"

requestParameters := &graphsolutions.BackupRestoreRestorePointsRequestBuilderGetQueryParameters{
	Expand: [] string {"protectionUnit($filter=id eq 'd234cf54-e0fb-49b7-9c8a-5bcd1439e853')"},
	Filter: &requestFilter,
}
configuration := &graphsolutions.BackupRestoreRestorePointsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
restorePoints, err := graphClient.Solutions().BackupRestore().RestorePoints().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

RestorePointCollectionResponse result = graphClient.solutions().backupRestore().restorePoints().get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"protectionUnit($filter=id eq 'd234cf54-e0fb-49b7-9c8a-5bcd1439e853')"};
	requestConfiguration.queryParameters.filter = "protectionDateTime lt 2024-05-12T10:01:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let restorePoints = await client.api('/solutions/backupRestore/restorePoints')
	.filter('protectionDateTime lt 2024-05-12T10:01:00Z')
	.expand('protectionUnit($filter=id eq \'d234cf54-e0fb-49b7-9c8a-5bcd1439e853\')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Solutions\BackupRestore\RestorePoints\RestorePointsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RestorePointsRequestBuilderGetRequestConfiguration();
$queryParameters = RestorePointsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["protectionUnit(\$filter=id eq 'd234cf54-e0fb-49b7-9c8a-5bcd1439e853')"];
$queryParameters->filter = "protectionDateTime lt 2024-05-12T10:01:00Z";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->solutions()->backupRestore()->restorePoints()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Get-MgSolutionBackupRestorePoint -ExpandProperty "protectionUnit(`$filter=id eq 'd234cf54-e0fb-49b7-9c8a-5bcd1439e853')" -Filter "protectionDateTime lt 2024-05-12T10:01:00Z" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.solutions.backup_restore.restore_points.restore_points_request_builder import RestorePointsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = RestorePointsRequestBuilder.RestorePointsRequestBuilderGetQueryParameters(
		expand = ["protectionUnit($filter=id eq 'd234cf54-e0fb-49b7-9c8a-5bcd1439e853')"],
		filter = "protectionDateTime lt 2024-05-12T10:01:00Z",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.solutions.backup_restore.restore_points.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/restorePoints",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/solutions/backupRestore/restorePoints?$skiptoken=M2UyZDAwMDAwMDMxMzkzYTMyNjQ2MTM0NjMzMjM5NjYzNjY0k2NDUwOTgzMg%3d%3d",
  "value": [
    {
      "@odata.type": "#microsoft.graph.restorePoint",
      "id": "cdf4a823-sfde-ki2s-kmsj-clu2nsdkk2as",
      "protectionDateTime": "2023-01-01T00:00:00Z",
      "expirationDateTime": "2024-01-01T00:00:00Z",
      "protectionUnit": {
        "@odata.type": "#microsoft.graph.siteProtectionUnit",
        "id": "32514d8c-71fe-4d00-a01a-31850bc5b32c",
        "siteId": "contoso-jpn.sharepoint.com,da60e844-ba1d-49bc-b4d4-d5e36bae9019,0271110f-634f-4300-a841-3a8a2e851852",
        "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "tags": "fastRestore" // Newly Added
    },
    {
      "@odata.type": "#microsoft.graph.restorePoint",
      "id": "cdf4a823-sfde-ki2s-kmsj-clu2nsdk43as",
      "protectionDateTime": "2023-01-01T00:00:00Z",
      "expirationDateTime": "2024-01-01T00:00:00Z",
      "protectionUnit": {
        "@odata.type": "#microsoft.graph.siteProtectionUnit",
        "id": "17014d8c-71fe-4d00-a01a-31850bc5b32c",
        "siteId": "contoso-jpn.sharepoint.com,da60e844-ba1d-49bc-b4d4-d5e36bae9019,0271110f-634f-4300-a841-3a8a2e851861",
        "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "tags": "fastRestore" // Newly Added
    },
    {
      "@odata.type": "#microsoft.graph.restorePoint",
      "id": "cdf4a823-sfde-ki2s-kmsj-clu2nsdk43ga",
      "protectionDateTime": "2023-01-07T00:00:00Z",
      "expirationDateTime": "2024-01-07T00:00:00Z",
      "protectionUnit": {
        "@odata.type": "#microsoft.graph.siteProtectionUnit",
        "id": "23014d8c-71fe-4d00-a01a-31850bc5b42a",
        "siteId": "contoso-jpn.sharepoint.com,da60e844-ba1d-49bc-b4d4-d5e36bae9019,0271110f-634f-4300-a841-3a8a2e857893",
        "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "tags": "fastRestore" // Newly Added
    }
  ]
}
```
