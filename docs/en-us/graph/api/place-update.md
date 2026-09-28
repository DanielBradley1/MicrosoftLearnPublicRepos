<!-- Source: https://learn.microsoft.com/en-us/graph/api/place-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Update place

Namespace: microsoft.graph

Update the properties of [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object that can be a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0), [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0), [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0), [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0), [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0), [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0), or [roomList](https://learn.microsoft.com/en-us/graph/api/resources/roomlist?view=graph-rest-1.0). You can identify the place by specifying the **id** property.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Place.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Place.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Exchange Administrator* is the least privileged role supported for this operation. In Microsoft Entra ID, administrative roles can be assigned directly to individual users or through [role-assignable groups](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/groups-concept); other groups can't be used for role assignments. In contrast, the Microsoft 365 admin center supports assigning administrative roles either directly to users or through groups.

When using application permissions, you must configure the required `TenantPlacesManagement` role \(to manage Places\) and the `MailRecipient` role \(to manage users and mailboxes\). For more information on how to configure these roles, see [Role Based Access Control for Applications in Exchange Online](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac).

## HTTP request

```http
PATCH /places/{id}
```

> **Note:** `{id}` is the unique identifier of the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) to update.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

Only one instance of a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) resource can be updated at a time. In the request body, use **@odata.type** to specify the type of place and include the properties to update.

Note

You can't use this API to update the **id**, **placeId**, **emailAddress**, **displayName**, or **bookingType** of a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The physical address of the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0), including the street, city, state, country or region, and postal code. Optional. |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) location in latitude, longitude, and \(optionally\) altitude coordinates. Optional. |
| isWheelChairAccessible | Boolean | Indicates whether the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) is wheelchair accessible. Required. |
| label | String | User-defined description of the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). Optional. |
| parentId | String | **id** of a parent [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). Optional. |
| phone | String | The phone number of the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). Optional. |
| tags | String collection | Custom tags that are associated with the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) for categorization or filtering. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update a building

The following example shows how to update a **building** object.

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
PATCH https://graph.microsoft.com/v1.0/places/e18a8e21-0494-4296-a5bc-f848dba2740d
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.building",
  "tags": ["most popular building"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Building
{
	OdataType = "microsoft.graph.building",
	Tags = new List<string>
	{
		"most popular building",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
tags := []string {
	"most popular building",
}
requestBody.SetTags(tags)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().ByPlaceId("place-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Building place = new Building();
place.setOdataType("microsoft.graph.building");
LinkedList<String> tags = new LinkedList<String>();
tags.add("most popular building");
place.setTags(tags);
Place result = graphClient.places().byPlaceId("{place-id}").patch(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.building',
  tags: ['most popular building']
};

await client.api('/places/e18a8e21-0494-4296-a5bc-f848dba2740d')
	.update(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Building;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Building();
$requestBody->setOdataType('microsoft.graph.building');
$requestBody->setTags(['most popular building', 	]);

$result = $graphServiceClient->places()->byPlaceId('place-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.building"
	tags = @(
	"most popular building"
)
}

Update-MgPlace -PlaceId $placeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.building import Building
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Building(
	odata_type = "microsoft.graph.building",
	tags = [
		"most popular building",
	],
)

result = await graph_client.places.by_place_id('place-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.building",
  "id": "e18a8e21-0494-4296-a5bc-f848dba2740d",
  "placeId": "e18a8e21-0494-4296-a5bc-f848dba2740d",
  "displayName": "MRS",
  "phone": "8801733457",
  "tags": [
    "most popular building"
  ],
  "isWheelChairAccessible": true,
  "label": "this is a building not open to all",
  "hasWiFi": false,
  "geoCoordinates": {
    "latitude": 31.2513263,
    "longitude": 121.3912291,
    "accuracy": null,
    "altitude": null,
    "altitudeAccuracy": null
  },
  "resourceLinks": []
}
```

### Example 2: Update a floor

The following example shows how to update a **floor** object.

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
PATCH https://graph.microsoft.com/v1.0/places/c64205d0-1a2d-4cfe-9012-3f5d668d28ea
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.floor",
  "isWheelChairAccessible": true,
  "sortOrder": 2
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Floor
{
	OdataType = "microsoft.graph.floor",
	IsWheelChairAccessible = true,
	SortOrder = 2,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
isWheelChairAccessible := true
requestBody.SetIsWheelChairAccessible(&isWheelChairAccessible) 
sortOrder := int32(2)
requestBody.SetSortOrder(&sortOrder) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().ByPlaceId("place-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Floor place = new Floor();
place.setOdataType("microsoft.graph.floor");
place.setIsWheelChairAccessible(true);
place.setSortOrder(2);
Place result = graphClient.places().byPlaceId("{place-id}").patch(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.floor',
  isWheelChairAccessible: true,
  sortOrder: 2
};

await client.api('/places/c64205d0-1a2d-4cfe-9012-3f5d668d28ea')
	.update(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Floor;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Floor();
$requestBody->setOdataType('microsoft.graph.floor');
$requestBody->setIsWheelChairAccessible(true);
$requestBody->setSortOrder(2);

$result = $graphServiceClient->places()->byPlaceId('place-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.floor"
	isWheelChairAccessible = $true
	sortOrder = 
}

Update-MgPlace -PlaceId $placeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.floor import Floor
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Floor(
	odata_type = "microsoft.graph.floor",
	is_wheel_chair_accessible = True,
	sort_order = 2,
)

result = await graph_client.places.by_place_id('place-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.floor",
  "id": "c64205d0-1a2d-4cfe-9012-3f5d668d28ea",
  "placeId": "c64205d0-1a2d-4cfe-9012-3f5d668d28ea",
  "displayName": "Floor X",
  "parentId": "be7b53f1-7c63-4533-91d4-52c3ca856afb",
  "isWheelChairAccessible": true,
  "sortOrder": 2,
  "geoCoordinates": {
    "latitude": 0.0,
    "longitude": 0.0,
    "accuracy": null,
    "altitude": null,
    "altitudeAccuracy": null
  }
}
```

### Example 3: Update a section

The following example shows how to update a **section** object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/places/3e7160bb-75da-4456-ab3c-5ee061f4611a
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.section",
  "label": "discuss area"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Section
{
	OdataType = "microsoft.graph.section",
	Label = "discuss area",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
label := "discuss area"
requestBody.SetLabel(&label) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().ByPlaceId("place-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Section place = new Section();
place.setOdataType("microsoft.graph.section");
place.setLabel("discuss area");
Place result = graphClient.places().byPlaceId("{place-id}").patch(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.section',
  label: 'discuss area'
};

await client.api('/places/3e7160bb-75da-4456-ab3c-5ee061f4611a')
	.update(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Section;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Section();
$requestBody->setOdataType('microsoft.graph.section');
$requestBody->setLabel('discuss area');

$result = $graphServiceClient->places()->byPlaceId('place-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.section"
	label = "discuss area"
}

Update-MgPlace -PlaceId $placeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.section import Section
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Section(
	odata_type = "microsoft.graph.section",
	label = "discuss area",
)

result = await graph_client.places.by_place_id('place-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.section",
  "id": "3e7160bb-75da-4456-ab3c-5ee061f4611a",
  "placeId": "3e7160bb-75da-4456-ab3c-5ee061f4611a",
  "displayName": "section_1",
  "parentId": "e30d4c71-95bf-4576-be4f-b6b7a8d2eeb7",
  "isWheelChairAccessible": false,
  "label": "discuss area"
}
```

### Example 4: Update a desk

The following example shows how to update a **desk** object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
PATCH https://graph.microsoft.com/v1.0/places/530f7900-8063-4daf-9cc1-168cb3ac26e9
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.desk",
  "mode": {
    "@odata.type": "microsoft.graph.dropInPlaceMode"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Desk
{
	OdataType = "microsoft.graph.desk",
	Mode = new DropInPlaceMode
	{
		OdataType = "microsoft.graph.dropInPlaceMode",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
mode := graphmodels.NewDropInPlaceMode()
requestBody.SetMode(mode)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().ByPlaceId("place-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Desk place = new Desk();
place.setOdataType("microsoft.graph.desk");
DropInPlaceMode mode = new DropInPlaceMode();
mode.setOdataType("microsoft.graph.dropInPlaceMode");
place.setMode(mode);
Place result = graphClient.places().byPlaceId("{place-id}").patch(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.desk',
  mode: {
    '@odata.type': 'microsoft.graph.dropInPlaceMode'
  }
};

await client.api('/places/530f7900-8063-4daf-9cc1-168cb3ac26e9')
	.update(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Desk;
use Microsoft\Graph\Generated\Models\DropInPlaceMode;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Desk();
$requestBody->setOdataType('microsoft.graph.desk');
$mode = new DropInPlaceMode();
$mode->setOdataType('microsoft.graph.dropInPlaceMode');
$requestBody->setMode($mode);

$result = $graphServiceClient->places()->byPlaceId('place-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.desk"
	mode = @{
		"@odata.type" = "microsoft.graph.dropInPlaceMode"
	}
}

Update-MgPlace -PlaceId $placeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.desk import Desk
from msgraph.generated.models.drop_in_place_mode import DropInPlaceMode
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Desk(
	odata_type = "microsoft.graph.desk",
	mode = DropInPlaceMode(
		odata_type = "microsoft.graph.dropInPlaceMode",
	),
)

result = await graph_client.places.by_place_id('place-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.desk",
  "id": "530f7900-8063-4daf-9cc1-168cb3ac26e9",
  "placeId": "530f7900-8063-4daf-9cc1-168cb3ac26e9",
  "displayName": "desk 5",
  "parentId": "ca163ae1-14a3-4e2a-8a97-5f82d672186f",
  "isWheelChairAccessible": true,
  "mailboxDetails": {
    "externalDirectoryObjectId": "04c6ff74-9268-41aa-96b5-5637d9f039bf",
    "emailAddress": "desk5ca86f9b61753443541750@contoso.com"
  },
  "mode": {
    "@odata.type": "#microsoft.graph.dropInPlaceMode"
  }
}
```

### Example 5: Update a room

The following example shows how to update a **room** object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
PATCH https://graph.microsoft.com/v1.0/places/cf100@contoso.com
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.room",
  "nickname": "Conf Room",
  "building": "1",
  "label": "100",
  "capacity": 50,
  "isWheelChairAccessible": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Room
{
	OdataType = "microsoft.graph.room",
	Nickname = "Conf Room",
	Building = "1",
	Label = "100",
	Capacity = 50,
	IsWheelChairAccessible = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
nickname := "Conf Room"
requestBody.SetNickname(&nickname) 
building := "1"
requestBody.SetBuilding(&building) 
label := "100"
requestBody.SetLabel(&label) 
capacity := int32(50)
requestBody.SetCapacity(&capacity) 
isWheelChairAccessible := false
requestBody.SetIsWheelChairAccessible(&isWheelChairAccessible) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().ByPlaceId("place-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Room place = new Room();
place.setOdataType("microsoft.graph.room");
place.setNickname("Conf Room");
place.setBuilding("1");
place.setLabel("100");
place.setCapacity(50);
place.setIsWheelChairAccessible(false);
Place result = graphClient.places().byPlaceId("{place-id}").patch(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.room',
  nickname: 'Conf Room',
  building: '1',
  label: '100',
  capacity: 50,
  isWheelChairAccessible: false
};

await client.api('/places/cf100@contoso.com')
	.update(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Room;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Room();
$requestBody->setOdataType('microsoft.graph.room');
$requestBody->setNickname('Conf Room');
$requestBody->setBuilding('1');
$requestBody->setLabel('100');
$requestBody->setCapacity(50);
$requestBody->setIsWheelChairAccessible(false);

$result = $graphServiceClient->places()->byPlaceId('place-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.room"
	nickname = "Conf Room"
	building = "1"
	label = "100"
	capacity = 
	isWheelChairAccessible = $false
}

Update-MgPlace -PlaceId $placeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.room import Room
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Room(
	odata_type = "microsoft.graph.room",
	nickname = "Conf Room",
	building = "1",
	label = "100",
	capacity = 50,
	is_wheel_chair_accessible = False,
)

result = await graph_client.places.by_place_id('place-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#places/$entity",
  "@odata.type": "#microsoft.graph.room",
  "id": "3162F1E1-C4C0-604B-51D8-91DA78989EB1",
  "emailAddress": "cf100@contoso.com",
  "displayName": "Conf Room 100",
  "address": {
    "street": "4567 Main Street",
    "city": "Buffalo",
    "state": "NY",
    "postalCode": "98052",
    "countryOrRegion": "US"
  },
  "geoCoordinates": {
    "latitude": 47.0,
    "longitude": -122.0
  },
  "phone": "555-555-0100",
  "nickname": "Conf Room",
  "label": "100",
  "capacity": 50,
  "building": "1",
  "floorLabel": "1P",
  "floorNumber": 1,
  "isWheelChairAccessible": false,
  "bookingType": "standard",
  "tags": [
    "bean bags"
  ],
  "audioDeviceName": null,
  "videoDeviceName": null,
  "displayDeviceName": "surface hub",
  "placeId": "080ed1a0-7b54-4995-85a5-eeec751786f5"
}
```

### Example 6: Update a workspace

The following example shows how to update a **workspace** object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
PATCH https://graph.microsoft.com/v1.0/places/ws100@contoso.com
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.workspace",
  "nickname": "Conf Room",
  "building": "1",
  "label": "100",
  "capacity": 50,
  "isWheelChairAccessible": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Workspace
{
	OdataType = "microsoft.graph.workspace",
	Nickname = "Conf Room",
	Label = "100",
	Capacity = 50,
	IsWheelChairAccessible = false,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"building" , "1"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
nickname := "Conf Room"
requestBody.SetNickname(&nickname) 
label := "100"
requestBody.SetLabel(&label) 
capacity := int32(50)
requestBody.SetCapacity(&capacity) 
isWheelChairAccessible := false
requestBody.SetIsWheelChairAccessible(&isWheelChairAccessible) 
additionalData := map[string]interface{}{
	"building" : "1", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().ByPlaceId("place-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Workspace place = new Workspace();
place.setOdataType("microsoft.graph.workspace");
place.setNickname("Conf Room");
place.setLabel("100");
place.setCapacity(50);
place.setIsWheelChairAccessible(false);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("building", "1");
place.setAdditionalData(additionalData);
Place result = graphClient.places().byPlaceId("{place-id}").patch(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.workspace',
  nickname: 'Conf Room',
  building: '1',
  label: '100',
  capacity: 50,
  isWheelChairAccessible: false
};

await client.api('/places/ws100@contoso.com')
	.update(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Workspace;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Workspace();
$requestBody->setOdataType('microsoft.graph.workspace');
$requestBody->setNickname('Conf Room');
$requestBody->setLabel('100');
$requestBody->setCapacity(50);
$requestBody->setIsWheelChairAccessible(false);
$additionalData = [
	'building' => '1',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->places()->byPlaceId('place-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.workspace"
	nickname = "Conf Room"
	building = "1"
	label = "100"
	capacity = 
	isWheelChairAccessible = $false
}

Update-MgPlace -PlaceId $placeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.workspace import Workspace
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Workspace(
	odata_type = "microsoft.graph.workspace",
	nickname = "Conf Room",
	label = "100",
	capacity = 50,
	is_wheel_chair_accessible = False,
	additional_data = {
			"building" : "1",
	}
)

result = await graph_client.places.by_place_id('place-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note**: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#places/$entity",
  "@odata.type": "#microsoft.graph.workspace",
  "id": "3162F1E1-C4C0-604B-51D8-91DA78989EB1",
  "emailAddress": "ws100@contoso.com",
  "displayName": "Workspace 100",
  "address": {
    "street": "4567 Main Street",
    "city": "Buffalo",
    "state": "NY",
    "postalCode": "98052",
    "countryOrRegion": "US"
  },
  "geoCoordinates": {
    "latitude": 47.0,
    "longitude": -122.0
  },
  "phone": "555-555-0100",
  "nickname": "Workspace",
  "label": "100",
  "capacity": 50,
  "building": "1",
  "floorLabel": "1P",
  "floorNumber": 1,
  "isWheelChairAccessible": false,
  "tags": [
    "bean bags"
  ],
  "placeId": "357e8ddc-8af5-4c7c-bc38-ddb3bcfec0d9"
}
```

### Example 7: Update a room list

The following example shows how to update a **roomList** object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
PATCH https://graph.microsoft.com/v1.0/places/Building1RroomList@contoso.com
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.roomList",
  "displayName": "Building 1",
  "phone": "555-555-0100",
  "address": {
    "street": "4567 Main Street",
    "city": "Buffalo",
    "state": "NY",
    "postalCode": "98052",
    "countryOrRegion": "US"
  },
  "geoCoordinates": {
    "altitude": null,
    "latitude": 47.0,
    "longitude": -122.0,
    "accuracy": null,
    "altitudeAccuracy": null
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new RoomList
{
	OdataType = "microsoft.graph.roomList",
	DisplayName = "Building 1",
	Phone = "555-555-0100",
	Address = new PhysicalAddress
	{
		Street = "4567 Main Street",
		City = "Buffalo",
		State = "NY",
		PostalCode = "98052",
		CountryOrRegion = "US",
	},
	GeoCoordinates = new OutlookGeoCoordinates
	{
		Altitude = null,
		Latitude = 47d,
		Longitude = -122d,
		Accuracy = null,
		AltitudeAccuracy = null,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
displayName := "Building 1"
requestBody.SetDisplayName(&displayName) 
phone := "555-555-0100"
requestBody.SetPhone(&phone) 
address := graphmodels.NewPhysicalAddress()
street := "4567 Main Street"
address.SetStreet(&street) 
city := "Buffalo"
address.SetCity(&city) 
state := "NY"
address.SetState(&state) 
postalCode := "98052"
address.SetPostalCode(&postalCode) 
countryOrRegion := "US"
address.SetCountryOrRegion(&countryOrRegion) 
requestBody.SetAddress(address)
geoCoordinates := graphmodels.NewOutlookGeoCoordinates()
altitude := null
geoCoordinates.SetAltitude(&altitude) 
latitude := float64(47)
geoCoordinates.SetLatitude(&latitude) 
longitude := float64(-122)
geoCoordinates.SetLongitude(&longitude) 
accuracy := null
geoCoordinates.SetAccuracy(&accuracy) 
altitudeAccuracy := null
geoCoordinates.SetAltitudeAccuracy(&altitudeAccuracy) 
requestBody.SetGeoCoordinates(geoCoordinates)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().ByPlaceId("place-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

RoomList place = new RoomList();
place.setOdataType("microsoft.graph.roomList");
place.setDisplayName("Building 1");
place.setPhone("555-555-0100");
PhysicalAddress address = new PhysicalAddress();
address.setStreet("4567 Main Street");
address.setCity("Buffalo");
address.setState("NY");
address.setPostalCode("98052");
address.setCountryOrRegion("US");
place.setAddress(address);
OutlookGeoCoordinates geoCoordinates = new OutlookGeoCoordinates();
geoCoordinates.setAltitude(null);
geoCoordinates.setLatitude(47d);
geoCoordinates.setLongitude(-122d);
geoCoordinates.setAccuracy(null);
geoCoordinates.setAltitudeAccuracy(null);
place.setGeoCoordinates(geoCoordinates);
Place result = graphClient.places().byPlaceId("{place-id}").patch(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.roomList',
  displayName: 'Building 1',
  phone: '555-555-0100',
  address: {
    street: '4567 Main Street',
    city: 'Buffalo',
    state: 'NY',
    postalCode: '98052',
    countryOrRegion: 'US'
  },
  geoCoordinates: {
    altitude: null,
    latitude: 47.0,
    longitude: -122.0,
    accuracy: null,
    altitudeAccuracy: null
  }
};

await client.api('/places/Building1RroomList@contoso.com')
	.update(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\RoomList;
use Microsoft\Graph\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Generated\Models\OutlookGeoCoordinates;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RoomList();
$requestBody->setOdataType('microsoft.graph.roomList');
$requestBody->setDisplayName('Building 1');
$requestBody->setPhone('555-555-0100');
$address = new PhysicalAddress();
$address->setStreet('4567 Main Street');
$address->setCity('Buffalo');
$address->setState('NY');
$address->setPostalCode('98052');
$address->setCountryOrRegion('US');
$requestBody->setAddress($address);
$geoCoordinates = new OutlookGeoCoordinates();
$geoCoordinates->setAltitude(null);
$geoCoordinates->setLatitude(47);
$geoCoordinates->setLongitude(-122);
$geoCoordinates->setAccuracy(null);
$geoCoordinates->setAltitudeAccuracy(null);
$requestBody->setGeoCoordinates($geoCoordinates);

$result = $graphServiceClient->places()->byPlaceId('place-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.room_list import RoomList
from msgraph.generated.models.physical_address import PhysicalAddress
from msgraph.generated.models.outlook_geo_coordinates import OutlookGeoCoordinates
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RoomList(
	odata_type = "microsoft.graph.roomList",
	display_name = "Building 1",
	phone = "555-555-0100",
	address = PhysicalAddress(
		street = "4567 Main Street",
		city = "Buffalo",
		state = "NY",
		postal_code = "98052",
		country_or_region = "US",
	),
	geo_coordinates = OutlookGeoCoordinates(
		altitude = None,
		latitude = 47,
		longitude = -122,
		accuracy = None,
		altitude_accuracy = None,
	),
)

result = await graph_client.places.by_place_id('place-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note**: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#places/$entity",
  "@odata.type": "#microsoft.graph.roomList",
  "id": "DC404124-302A-92AA-F98D-7B4DEB0C1705",
  "displayName": "Building 1",
  "address": {
    "street": "4567 Main Street",
    "city": "Buffalo",
    "state": "NY",
    "postalCode": "98052",
    "countryOrRegion": "US"
  },
  "geoCoordinates": {
    "altitude": null,
    "latitude": 47.0,
    "longitude": -122.0,
    "accuracy": null,
    "altitudeAccuracy": null
  },
  "phone": "555-555-0100",
  "emailAddress": "bldg1@contoso.com",
  "placeId": "406bd1b2-237c-4710-bda2-8b7900d61b27"
}
```
