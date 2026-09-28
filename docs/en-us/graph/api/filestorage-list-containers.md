<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestorage-list-containers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List containers

Namespace: microsoft.graph

Get a list of [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) objects that are accessible to a caller. The **containerTypeId** filter parameter is required.

Important

- Requests made on behalf of a user fail if the user doesn't have a OneDrive. This requirement doesn't apply when you call the endpoint without a user context \(app-only authentication\). The endpoint also only returns containers that the user is a direct member of. Containers that the user is a member of via a group aren't returned.
- Requests made without a user context \(app-only authentication\) aren't currently supported for multi-geo tenants.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | FileStorageContainer.Manage.All |
| Delegated \(personal Microsoft account\) | FileStorageContainer.Selected | Not available. |
| Application | FileStorageContainer.Selected | Not available. |

In addition to Microsoft Graph permissions, your app also must have the necessary container-type level permission or permissions to call this API. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container-type level permissions, see [SharePoint Embedded Authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

## HTTP request

```http
GET /storage/fileStorage/containers?$filter=containerTypeId eq {containerTypeId}
GET /storage/fileStorage/containers?$filter=containerTypeId eq {containerTypeId} and viewpoint/effectiveRole eq 'principalOwner'
```

## Query parameters

This method requires the **containerTypeId** parameter. It supports the `$expand` OData query parameter, except for the **drive**, **permissions**, and **customProperties** properties. If other `$filter` conditions are used, the endpoint might return intermediate pages with partial results or even no results, and the caller must continue to read all pages to get all applicable results. For more information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) objects in the response body. Only a limited subset of properties is returned for each **fileStorageContainer**.

## Examples

### Request

The following example enumerates all containers of a given container type.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/storage/fileStorage/containers?$filter=containerTypeId eq e2756c4d-fa33-4452-9c36-2325686e1082
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.Containers.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "containerTypeId eq e2756c4d-fa33-4452-9c36-2325686e1082";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphstorage "github.com/microsoftgraph/msgraph-sdk-go/storage"
	  //other-imports
)


requestFilter := "containerTypeId eq e2756c4d-fa33-4452-9c36-2325686e1082"

requestParameters := &graphstorage.FileStorageContainersRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphstorage.FileStorageContainersRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
containers, err := graphClient.Storage().FileStorage().Containers().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerCollectionResponse result = graphClient.storage().fileStorage().containers().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "containerTypeId eq e2756c4d-fa33-4452-9c36-2325686e1082";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let containers = await client.api('/storage/fileStorage/containers')
	.filter('containerTypeId eq e2756c4d-fa33-4452-9c36-2325686e1082')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Storage\FileStorage\Containers\ContainersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ContainersRequestBuilderGetRequestConfiguration();
$queryParameters = ContainersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "containerTypeId eq e2756c4d-fa33-4452-9c36-2325686e1082";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->storage()->fileStorage()->containers()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.storage.file_storage.containers.containers_request_builder import ContainersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ContainersRequestBuilder.ContainersRequestBuilderGetQueryParameters(
		filter = "containerTypeId eq e2756c4d-fa33-4452-9c36-2325686e1082",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.storage.file_storage.containers.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/storage/fileStorage/containers",
  "@odata.count": 1,
  "value": [
    {
      "@odata.type": "#microsoft.graph.fileStorageContainer",
      "id": "b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z",
      "displayName": "My File Storage Container",
      "containerTypeId": "e2756c4d-fa33-4452-9c36-2325686e1082",
      "createdDateTime": "2021-11-24T15:41:52.347Z"
    }
  ]
}
```
