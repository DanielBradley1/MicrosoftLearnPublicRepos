<!-- Source: https://learn.microsoft.com/en-us/graph/api/sectionmap-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update sectionMap

Namespace: microsoft.graph

Update the properties of an existing [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) object in IMDF format on a specified floor, or create one if it doesn't exist.

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

The Exchange Admin role is required to create or update a **sectionMap**.

## HTTP request

```http
PATCH /places/{buildingPlaceId}/microsoft.graph.building/map/levels/{levelImdfID}/sections/{sectionImdfID}
```

> **Note:**
> 
> - `{buildingPlaceId}` is the **placeId** of a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) with which this [section](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) is associated.
> - `{levelImdfId}` is the **id** of the level in the IMDF file.
> - `{sectionImdfID}` is the **id** of the section in the IMDF file.

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
| placeId | String | Identifier for the [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0) to which this section map belongs. Optional. |
| properties | String | Concatenated key-value pair of all properties of a GeoJSON file for this section. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). Optional. |

## Response

If the update is successful, this method returns a `200 OK` response code and an updated [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) object in the response body. If the creation is successful, this method returns a `201 Created` response code and a [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update an existing sectionMap

The following example shows how to update an existing [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) object.

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
PATCH https://graph.microsoft.com/v1.0/places/151e85a7-c0b8-4519-997e-1a0858255704/microsoft.graph.building/map/levels/e537d463-475b-43c3-a650-184566c68bc9/sections/005eb3b8-c95d-4d35-a8a0-22d6nb4d6003
Content-Type: application/json

{
  "placeId": "67149ec1-4b99-42d4-88a4-d92cd23cb606",
  "properties": "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section update\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SectionMap
{
	PlaceId = "67149ec1-4b99-42d4-88a4-d92cd23cb606",
	Properties = "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section update\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].GraphBuilding.Map.Levels["{levelMap-id}"].Sections["{sectionMap-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewSectionMap()
placeId := "67149ec1-4b99-42d4-88a4-d92cd23cb606"
requestBody.SetPlaceId(&placeId) 
properties := "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section update\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}"
requestBody.SetProperties(&properties) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sections, err := graphClient.Places().ByPlaceId("place-id").GraphBuilding().Map().Levels().ByLevelMapId("levelMap-id").Sections().BySectionMapId("sectionMap-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SectionMap sectionMap = new SectionMap();
sectionMap.setPlaceId("67149ec1-4b99-42d4-88a4-d92cd23cb606");
sectionMap.setProperties("{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section update\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}");
SectionMap result = graphClient.places().byPlaceId("{place-id}").graphBuilding().map().levels().byLevelMapId("{levelMap-id}").sections().bySectionMapId("{sectionMap-id}").patch(sectionMap);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sectionMap = {
  placeId: '67149ec1-4b99-42d4-88a4-d92cd23cb606',
  properties: '{\"id\':\'005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\':\'Feature\",\"feature_type\':\'section\",\"geometry\':{\'type\':\'Polygon\",\"coordinates\':[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\'properties\':{\'name\':{\'en\':\'Test section update\"},\"restriction\':\'restricted222222\",\"level_id\':\'e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\':\'mockAddressId\",\"accessibility\':\'wheelchair222222\",\"display_point\':{\'type\':\'Point\",\"coordinates\':[-121.8888983,37.3295292]},\'places_category\':\"unspecified\"}}"
};

await client.api('/places/151e85a7-c0b8-4519-997e-1a0858255704/microsoft.graph.building/map/levels/e537d463-475b-43c3-a650-184566c68bc9/sections/005eb3b8-c95d-4d35-a8a0-22d6nb4d6003')
	.update(sectionMap);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SectionMap;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SectionMap();
$requestBody->setPlaceId('67149ec1-4b99-42d4-88a4-d92cd23cb606');
$requestBody->setProperties('{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section update\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}');

$result = $graphServiceClient->places()->byPlaceId('place-id')->graphBuilding()->map()->levels()->byLevelMapId('levelMap-id')->sections()->bySectionMapId('sectionMap-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	placeId = "67149ec1-4b99-42d4-88a4-d92cd23cb606"
	properties = '{"id":"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003","type":"Feature","feature_type":"section","geometry":{"type":"Polygon","coordinates":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},"properties":{"name":{"en":"Test section update"},"restriction":"restricted222222","level_id":"e537d463-475b-43c3-a650-184566c68bc9","address_id":"mockAddressId","accessibility":"wheelchair222222","display_point":{"type":"Point","coordinates":[-121.8888983,37.3295292]},"places_category":"unspecified"}}'
}

Update-MgPlaceAsBuildingMapLevelSection -PlaceId $placeId -LevelMapId $levelMapId -SectionMapId $sectionMapId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.section_map import SectionMap
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SectionMap(
	place_id = "67149ec1-4b99-42d4-88a4-d92cd23cb606",
	properties = "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section update\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}",
)

result = await graph_client.places.by_place_id('place-id').graph_building.map.levels.by_level_map_id('levelMap-id').sections.by_section_map_id('sectionMap-id').patch(request_body)
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
  "id": "005eb3b8-c95d-4d35-a8a0-22d6nb4d6003",
  "properties": "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section update\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}"
}
```

### Example 2: Create a sectionMap if it doesn't exist

The following example shows how to create a new [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) object if it doesn't exist.

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
PATCH https://graph.microsoft.com/v1.0/places/151e85a7-c0b8-4519-997e-1a0858255704/microsoft.graph.building/map/levels/e537d463-475b-43c3-a650-184566c68bc9/sections/005eb3b8-c95d-4d35-a8a0-22d6nb4d6003
Content-Type: application/json

{
  "placeId": "67149ec1-4b99-42d4-88a4-d92cd23cb606",
  "properties": "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section 02\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SectionMap
{
	PlaceId = "67149ec1-4b99-42d4-88a4-d92cd23cb606",
	Properties = "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section 02\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].GraphBuilding.Map.Levels["{levelMap-id}"].Sections["{sectionMap-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewSectionMap()
placeId := "67149ec1-4b99-42d4-88a4-d92cd23cb606"
requestBody.SetPlaceId(&placeId) 
properties := "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section 02\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}"
requestBody.SetProperties(&properties) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sections, err := graphClient.Places().ByPlaceId("place-id").GraphBuilding().Map().Levels().ByLevelMapId("levelMap-id").Sections().BySectionMapId("sectionMap-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SectionMap sectionMap = new SectionMap();
sectionMap.setPlaceId("67149ec1-4b99-42d4-88a4-d92cd23cb606");
sectionMap.setProperties("{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section 02\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}");
SectionMap result = graphClient.places().byPlaceId("{place-id}").graphBuilding().map().levels().byLevelMapId("{levelMap-id}").sections().bySectionMapId("{sectionMap-id}").patch(sectionMap);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sectionMap = {
  placeId: '67149ec1-4b99-42d4-88a4-d92cd23cb606',
  properties: '{\"id\':\'005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\':\'Feature\",\"feature_type\':\'section\",\"geometry\':{\'type\':\'Polygon\",\"coordinates\':[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\'properties\':{\'name\':{\'en\':\'Test section 02\"},\"restriction\':\'restricted222222\",\"level_id\':\'e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\':\'mockAddressId\",\"accessibility\':\'wheelchair222222\",\"display_point\':{\'type\':\'Point\",\"coordinates\':[-121.8888983,37.3295292]},\'places_category\':\"unspecified\"}}"
};

await client.api('/places/151e85a7-c0b8-4519-997e-1a0858255704/microsoft.graph.building/map/levels/e537d463-475b-43c3-a650-184566c68bc9/sections/005eb3b8-c95d-4d35-a8a0-22d6nb4d6003')
	.update(sectionMap);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SectionMap;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SectionMap();
$requestBody->setPlaceId('67149ec1-4b99-42d4-88a4-d92cd23cb606');
$requestBody->setProperties('{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section 02\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}');

$result = $graphServiceClient->places()->byPlaceId('place-id')->graphBuilding()->map()->levels()->byLevelMapId('levelMap-id')->sections()->bySectionMapId('sectionMap-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	placeId = "67149ec1-4b99-42d4-88a4-d92cd23cb606"
	properties = '{"id":"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003","type":"Feature","feature_type":"section","geometry":{"type":"Polygon","coordinates":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},"properties":{"name":{"en":"Test section 02"},"restriction":"restricted222222","level_id":"e537d463-475b-43c3-a650-184566c68bc9","address_id":"mockAddressId","accessibility":"wheelchair222222","display_point":{"type":"Point","coordinates":[-121.8888983,37.3295292]},"places_category":"unspecified"}}'
}

Update-MgPlaceAsBuildingMapLevelSection -PlaceId $placeId -LevelMapId $levelMapId -SectionMapId $sectionMapId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.section_map import SectionMap
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SectionMap(
	place_id = "67149ec1-4b99-42d4-88a4-d92cd23cb606",
	properties = "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section 02\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}",
)

result = await graph_client.places.by_place_id('place-id').graph_building.map.levels.by_level_map_id('levelMap-id').sections.by_section_map_id('sectionMap-id').patch(request_body)
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
  "id": "005eb3b8-c95d-4d35-a8a0-22d6nb4d6003",
  "properties": "{\"id\":\"005eb3b8-c95d-4d35-a8a0-22d6nb4d6003\",\"type\":\"Feature\",\"feature_type\":\"section\",\"geometry\":{\"type\":\"Polygon\",\"coordinates\":[[[-121.8889415,37.3295396],[-121.8889137,37.329503],[-121.8889082,37.3294956],[-121.888907,37.3294941],[-121.8888551,37.3295189],[-121.8888895,37.3295644],[-121.8889415,37.3295396]]]},\"properties\":{\"name\":{\"en\":\"Test section 02\"},\"restriction\":\"restricted222222\",\"level_id\":\"e537d463-475b-43c3-a650-184566c68bc9\",\"address_id\":\"mockAddressId\",\"accessibility\":\"wheelchair222222\",\"display_point\":{\"type\":\"Point\",\"coordinates\":[-121.8888983,37.3295292]},\"places_category\":\"unspecified\"}}"
}
```
