<!-- Source: https://learn.microsoft.com/en-us/graph/api/buildingmap-list-levels?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List levels

Namespace: microsoft.graph

Get a list of the [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Place.Read.All | Place.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Place.Read.All | Place.ReadWrite.All |

## HTTP request

```http
GET /places/{buildingPlaceId}/microsoft.graph.building/map/levels
```

> **Note:** `{buildingPlaceId}` is the unique **placeId** of a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) with which the [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) objects are associated.

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/places/4bff9586-c9ee-401d-9d35-c476231a33e6/microsoft.graph.building/map/levels
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].GraphBuilding.Map.Levels.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
levels, err := graphClient.Places().ByPlaceId("place-id").GraphBuilding().Map().Levels().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LevelMapCollectionResponse result = graphClient.places().byPlaceId("{place-id}").graphBuilding().map().levels().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let levels = await client.api('/places/4bff9586-c9ee-401d-9d35-c476231a33e6/microsoft.graph.building/map/levels')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->places()->byPlaceId('place-id')->graphBuilding()->map()->levels()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

Get-MgPlaceAsBuildingMapLevel -PlaceId $placeId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.places.by_place_id('place-id').graph_building.map.levels.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "placeId": "4bff9586-c9ee-401d-9d35-c476231a33e6",
      "id": "e537d463-475b-43c3-a650-184566c68bc9",
      "properties": "{\"id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"type\":\"Feature\",\"feature_type\":\"level\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8891473,37.3297928],[-121.8893961,37.3299621],[-121.8894513,37.3300349],[-121.8894531,37.3300373],[-121.8891236,37.3297614],[-121.8891473,37.3297928]……]]},\"properties\":{\"name\":{\"en\":\"Test Floor 1\"},\"building_ids\":[\"26f04b4f-9ae2-45e3-99d1-393c66d58eb4\"],\"address_id\":\"e105efb7-b0d1-4144-8b8e-72eadf95724f\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.88904,37.3289553]},\"places_category\":\"unspecified\",\"directory_id\":\"4bff9586-c9ee-401d-9d35-c476231a33e6\",\"ordinal\":0}}"
    }
  ]
}
```
