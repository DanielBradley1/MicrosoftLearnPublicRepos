<!-- Source: https://learn.microsoft.com/en-us/graph/api/place-getoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# place: getOperation

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a [placeOperation](https://learn.microsoft.com/en-us/graph/api/resources/placeoperation?view=graph-rest-beta) by ID.

Note

The following aspects apply when you work with this API:

- Operations are retained for 15 days from creation.
- API-level throttling:

  - This API has a throttling limit of three calls per second. For more information, see [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits).
  - The progress of long-running operations updates every 30 seconds; therefore, you shouldn't retrieve an operation more frequently than once every 30 seconds.

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
GET /places/getOperation(id='{id}')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the place operation. Required. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [placeOperation](https://learn.microsoft.com/en-us/graph/api/resources/placeoperation?view=graph-rest-beta) object in the response body.

### Operation details structure

The operation details in the response mirror the hierarchical structure of the request payload:

- Each top-level place in the request appears as a top-level entry in the **details** array, in the same order as the request.
- The hierarchy specified using **children@delta** in the request is preserved in the **children** array of the response, in the same order as the request.
- Successfully created or updated places are returned in the **succeededPlace** property.
- Any errors encountered during processing are returned in the **error** property.

## Examples

### Example 1: Get a succeeded operation

The following example demonstrates the operation response for the upsert places request shown in the [example section of the upsert places API](https://learn.microsoft.com/en-us/graph/api/place-patch-places?view=graph-rest-beta#example). The response structure mirrors the request hierarchy, with each top-level place from the request appearing in the **details** array and child places nested in the **children** arrays.

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
GET https://graph.microsoft.com/beta/places/getOperation(id='0f5d3cc5-d1bd-4cba-9b0e-e9ad68527ab5')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places.GetOperationWithId("{id}").GetAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
id := "{id}"
getOperation, err := graphClient.Places().GetOperationWithId(&id).Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.places().getOperationWithId("{id}").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let placeOperation = await client.api('/places/getOperation(id='0f5d3cc5-d1bd-4cba-9b0e-e9ad68527ab5')')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->places()->getOperationWithId('{id}', )->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Calendar

Get-MgBetaPlaceOperation
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.places.get_operation_with_id("{id}").get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.placeOperation",
  "id": "0f5d3cc5-d1bd-4cba-9b0e-e9ad68527ab5",
  "status": "succeeded",
  "progress": {
    "totalPlaceCount": 9,
    "succeededPlaceCount": 9,
    "failedPlaceCount": 0
  },
  "details": [
    {
      "children": [
        {
          "succeededPlace": {
            "@odata.type": "#microsoft.graph.floor",
            "id": "5f54d496-7328-415a-930e-990be3a98766",
            "displayName": "Demo Floor 1",
            "parentId": "25e5905a-7fee-4f36-ba31-29e85c14bf18"
          }
        }
      ],
      "succeededPlace": {
        "@odata.type": "#microsoft.graph.building",
        "id": "25e5905a-7fee-4f36-ba31-29e85c14bf18",
        "displayName": "Demo Building A",
        "hasWiFi": true,
        "wifiState": "enabled"
      }
    },
    {
      "children": [
        {
          "children": [
            {
              "children": [
                {
                  "succeededPlace": {
                    "@odata.type": "#microsoft.graph.desk",
                    "id": "211ffb37-e880-475a-b73a-43f484609536",
                    "displayName": "desk1",
                    "parentId": "f5b54c22-5474-47aa-878a-0bfdc72e30f1",
                    "mode": {
                      "@odata.type": "#microsoft.graph.unavailablePlaceMode",
                      "reason": "New"
                    }
                  }
                },
                {
                  "succeededPlace": {
                    "@odata.type": "#microsoft.graph.room",
                    "id": "ddb3bfc7-c7af-40fb-a8be-26af40ee6cf3",
                    "placeId": "9112a87a-7994-4f73-9037-0939ef1c7d55",
                    "displayName": "Demo Room 1",
                    "parentId": "f5b54c22-5474-47aa-878a-0bfdc72e30f1",
                    "emailAddress": "DemoRoom19975d7971764579926925@contoso.onmicrosoft.com"
                  }
                }
              ],
              "succeededPlace": {
                "@odata.type": "#microsoft.graph.section",
                "id": "f5b54c22-5474-47aa-878a-0bfdc72e30f1",
                "displayName": "Demo Section A",
                "parentId": "23bfdc52-59d6-419d-ab18-54a51fe060f6"
              }
            }
          ],
          "succeededPlace": {
            "@odata.type": "#microsoft.graph.floor",
            "id": "23bfdc52-59d6-419d-ab18-54a51fe060f6",
            "displayName": "Demo Floor 1",
            "parentId": "15369a66-e9f4-4803-8e7e-fa6b811fbd92"
          }
        }
      ],
      "succeededPlace": {
        "@odata.type": "#microsoft.graph.building",
        "id": "15369a66-e9f4-4803-8e7e-fa6b811fbd92",
        "displayName": "Demo Building B"
      }
    },
    {
      "succeededPlace": {
        "@odata.type": "#microsoft.graph.workspace",
        "id": "8628af02-04c3-4882-88cc-06108de2d637",
        "placeId": "ebbc6ed0-8fda-41d2-9d07-c0f990337515",
        "displayName": "Demo Workspace 1",
        "parentId": "2cb2701d-0896-4c69-91bb-582d82d7c68c",
        "emailAddress": "DemoWorkspace1bb13cf171764579932835@contoso.onmicrosoft.com",
        "mode": {
          "@odata.type": "#microsoft.graph.reservablePlaceMode"
        }
      }
    },
    {
      "succeededPlace": {
        "@odata.type": "#microsoft.graph.section",
        "id": "2cb2701d-0896-4c69-91bb-582d82d7c68c",
        "displayName": "HR",
        "parentId": "94eb964a-b166-4f0a-953d-54dc9032d9d5"
      }
    }
  ]
}
```

### Example 2: Get a partially succeeded operation with errors

The following example shows an operation that partially succeeded.

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
GET https://graph.microsoft.com/beta/places/getOperation(id='116d12e4-3361-43f9-b722-af5b510760c9')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places.GetOperationWithId("{id}").GetAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
id := "{id}"
getOperation, err := graphClient.Places().GetOperationWithId(&id).Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.places().getOperationWithId("{id}").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let placeOperation = await client.api('/places/getOperation(id='116d12e4-3361-43f9-b722-af5b510760c9')')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->places()->getOperationWithId('{id}', )->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Calendar

Get-MgBetaPlaceOperation
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.places.get_operation_with_id("{id}").get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response with **partiallySucceeded**. The operation partially succeeded with one place created and two places failed.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.placeOperation",
  "id": "15cc23bd-f215-42bf-92ad-bb84fbcd6606",
  "status": "partiallySucceeded",
  "progress": {
    "totalPlaceCount": 3,
    "succeededPlaceCount": 1,
    "failedPlaceCount": 2
  },
  "details": [
    {
      "error": null,
      "children": [
        {
          "error": {
            "code": "BadRequest",
            "message": "Requested Place not found: 881a74c1-a092-4f67-b354-174ca814df8b"
          }
        }
      ],
      "succeededPlace": {
        "@odata.type": "#microsoft.graph.building",
        "id": "25e5905a-7fee-4f36-ba31-29e85c14bf18",
        "displayName": "Demo Building 3"
      }
    },
    {
      "error": {
        "code": "BadRequest",
        "message": "A Place with the same name, type, parentId and address already exists with ID 9ba9753e-181a-471f-aa84-9ed238afae58."
      }
    }
  ]
}
```
