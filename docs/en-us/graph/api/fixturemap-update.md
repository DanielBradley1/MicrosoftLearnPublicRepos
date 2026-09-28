<!-- Source: https://learn.microsoft.com/en-us/graph/api/fixturemap-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update fixtureMap

Namespace: microsoft.graph

Update the properties of an existing [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) object in IMDF format on a specified floor, or create one if it doesn't exist.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Place.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Place.ReadWrite.All | Not available. |

Note

The Exchange Admin role is required to create or update a **fixtureMap**.

## HTTP request

```http
PATCH /places/{buildingPlaceId}/microsoft.graph.building/map/levels/{levelImdfId}/fixtures/{fixtureImdfId}
```

> **Note:**
> 
> - `{buildingPlaceId}` is the **placeId** of a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) with which this [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) is associated.
> - `{levelImdfId}` is the **id** of the level in the IMDF file.
> - `{fixtureImdfId}` is the **id** of the fixture in the IMDF file.

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
| placeId | String | ID for the [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) object. Optional. |
| properties | String | Concatenated key-value pairs of all properties from a GeoJSON file for this **fixtureMap**. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). Optional. |

## Response

If the update is successful, this method returns a `200 OK` response code and an updated [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) object in the response body. If the creation is successful, this method returns a `201 Created` response code and a [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update an existing fixtureMap

The following example shows how to update an existing [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) object.

#### Request

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
PATCH https://graph.microsoft.com/v1.0/places/91ac6c16-cda9-4506-b55d-e1f4dac3cbe7/microsoft.graph.building/map/levels/e537d463-475b-43c3-a650-184566c68bc9/fixtures/005eb3b8-c95d-4d35-a8a0-22d3cb4d6002
Content-Type: application/json

{
  "placeId": "67149ec1-4b99-42d4-88a4-d92cd23cb606",
  "properties": "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture update\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FixtureMap
{
	PlaceId = "67149ec1-4b99-42d4-88a4-d92cd23cb606",
	Properties = "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture update\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].GraphBuilding.Map.Levels["{levelMap-id}"].Fixtures["{fixtureMap-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewFixtureMap()
placeId := "67149ec1-4b99-42d4-88a4-d92cd23cb606"
requestBody.SetPlaceId(&placeId) 
properties := "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture update\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}"
requestBody.SetProperties(&properties) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
fixtures, err := graphClient.Places().ByPlaceId("place-id").GraphBuilding().Map().Levels().ByLevelMapId("levelMap-id").Fixtures().ByFixtureMapId("fixtureMap-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FixtureMap fixtureMap = new FixtureMap();
fixtureMap.setPlaceId("67149ec1-4b99-42d4-88a4-d92cd23cb606");
fixtureMap.setProperties("{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture update\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}");
FixtureMap result = graphClient.places().byPlaceId("{place-id}").graphBuilding().map().levels().byLevelMapId("{levelMap-id}").fixtures().byFixtureMapId("{fixtureMap-id}").patch(fixtureMap);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fixtureMap = {
  placeId: '67149ec1-4b99-42d4-88a4-d92cd23cb606',
  properties: '{\"id\':\'005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\':\'Feature\",\"feature_type\':\'fixture\",\"geometry\':{\'type\':\'Polygon\",\"coordinates\':[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\'properties\':{\'name\':{\'en\':\'Test Fixture update\"},\"level_id\':\'e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\':{\'type\':\'Point\",\"coordinates\':[-121.8888983,37.3295292]}}}"
};

await client.api('/places/91ac6c16-cda9-4506-b55d-e1f4dac3cbe7/microsoft.graph.building/map/levels/e537d463-475b-43c3-a650-184566c68bc9/fixtures/005eb3b8-c95d-4d35-a8a0-22d3cb4d6002')
	.update(fixtureMap);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FixtureMap;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FixtureMap();
$requestBody->setPlaceId('67149ec1-4b99-42d4-88a4-d92cd23cb606');
$requestBody->setProperties('{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture update\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}');

$result = $graphServiceClient->places()->byPlaceId('place-id')->graphBuilding()->map()->levels()->byLevelMapId('levelMap-id')->fixtures()->byFixtureMapId('fixtureMap-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	placeId = "67149ec1-4b99-42d4-88a4-d92cd23cb606"
	properties = '{"id":"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002","type":"Feature","feature_type":"fixture","geometry":{"type":"Polygon","coordinates":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},"properties":{"name":{"en":"Test Fixture update"},"level_id":"e537d463-475b-43c3-a650-184566c68bc9","display_point":{"type":"Point","coordinates":[-121.8888983,37.3295292]}}}'
}

Update-MgPlaceAsBuildingMapLevelFixture -PlaceId $placeId -LevelMapId $levelMapId -FixtureMapId $fixtureMapId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.fixture_map import FixtureMap
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FixtureMap(
	place_id = "67149ec1-4b99-42d4-88a4-d92cd23cb606",
	properties = "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture update\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}",
)

result = await graph_client.places.by_place_id('place-id').graph_building.map.levels.by_level_map_id('levelMap-id').fixtures.by_fixture_map_id('fixtureMap-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "placeId": "67149ec1-4b99-42d4-88a4-d92cd23cb606",
  "id": "005eb3b8-c95d-4d35-a8a0-22d3cb4d6002",
  "properties": "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture update\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}"
}
```

### Example 2: Create a fixtureMap if it doesn't exist

The following example shows how to create a new [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) object if it doesn't exist.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/places/151e85a7-c0b8-4519-997e-1a0858255704/microsoft.graph.building/map/levels/e537d463-475b-43c3-a650-184566c68bc9/fixtures/005eb3b8-c95d-4d35-a8a0-22d3cb4d6002
Content-Type: application/json

{
  "placeId": "67149ec1-4b99-42d4-88a4-d92cd23cb606",
  "properties": "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture 01\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FixtureMap
{
	PlaceId = "67149ec1-4b99-42d4-88a4-d92cd23cb606",
	Properties = "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture 01\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].GraphBuilding.Map.Levels["{levelMap-id}"].Fixtures["{fixtureMap-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewFixtureMap()
placeId := "67149ec1-4b99-42d4-88a4-d92cd23cb606"
requestBody.SetPlaceId(&placeId) 
properties := "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture 01\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}"
requestBody.SetProperties(&properties) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
fixtures, err := graphClient.Places().ByPlaceId("place-id").GraphBuilding().Map().Levels().ByLevelMapId("levelMap-id").Fixtures().ByFixtureMapId("fixtureMap-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FixtureMap fixtureMap = new FixtureMap();
fixtureMap.setPlaceId("67149ec1-4b99-42d4-88a4-d92cd23cb606");
fixtureMap.setProperties("{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture 01\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}");
FixtureMap result = graphClient.places().byPlaceId("{place-id}").graphBuilding().map().levels().byLevelMapId("{levelMap-id}").fixtures().byFixtureMapId("{fixtureMap-id}").patch(fixtureMap);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fixtureMap = {
  placeId: '67149ec1-4b99-42d4-88a4-d92cd23cb606',
  properties: '{\"id\':\'005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\':\'Feature\",\"feature_type\':\'fixture\",\"geometry\':{\'type\':\'Polygon\",\"coordinates\':[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\'properties\':{\'name\':{\'en\':\'Test Fixture 01\"},\"level_id\':\'e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\':{\'type\':\'Point\",\"coordinates\':[-121.8888983,37.3295292]}}}"
};

await client.api('/places/151e85a7-c0b8-4519-997e-1a0858255704/microsoft.graph.building/map/levels/e537d463-475b-43c3-a650-184566c68bc9/fixtures/005eb3b8-c95d-4d35-a8a0-22d3cb4d6002')
	.update(fixtureMap);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FixtureMap;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FixtureMap();
$requestBody->setPlaceId('67149ec1-4b99-42d4-88a4-d92cd23cb606');
$requestBody->setProperties('{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture 01\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}');

$result = $graphServiceClient->places()->byPlaceId('place-id')->graphBuilding()->map()->levels()->byLevelMapId('levelMap-id')->fixtures()->byFixtureMapId('fixtureMap-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	placeId = "67149ec1-4b99-42d4-88a4-d92cd23cb606"
	properties = '{"id":"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002","type":"Feature","feature_type":"fixture","geometry":{"type":"Polygon","coordinates":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},"properties":{"name":{"en":"Test Fixture 01"},"level_id":"e537d463-475b-43c3-a650-184566c68bc9","display_point":{"type":"Point","coordinates":[-121.8888983,37.3295292]}}}'
}

Update-MgPlaceAsBuildingMapLevelFixture -PlaceId $placeId -LevelMapId $levelMapId -FixtureMapId $fixtureMapId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.fixture_map import FixtureMap
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FixtureMap(
	place_id = "67149ec1-4b99-42d4-88a4-d92cd23cb606",
	properties = "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture 01\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}",
)

result = await graph_client.places.by_place_id('place-id').graph_building.map.levels.by_level_map_id('levelMap-id').fixtures.by_fixture_map_id('fixtureMap-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "placeId": "67149ec1-4b99-42d4-88a4-d92cd23cb606",
  "id": "005eb3b8-c95d-4d35-a8a0-22d3cb4d6002",
  "properties": "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d3cb4d6002\",\"type\":\"Feature\",\"feature_type\":\"fixture\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test Fixture 01\"},\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]}}}"
}
```
