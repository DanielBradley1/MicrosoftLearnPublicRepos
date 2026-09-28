<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationcategory-delta?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# educationCategory: delta

Namespace: microsoft.graph

Get a list of newly created or updated [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) objects without having to perform a full read of the collection.

> This method doesn't return deleted categories.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduAssignments.ReadBasic | EduAssignments.Read, EduAssignments.ReadWrite, EduAssignments.ReadWriteBasic |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduAssignments.ReadBasic.All | EduAssignments.Read.All, EduAssignments.ReadWrite.All, EduAssignments.ReadWriteBasic.All |

## Optional query parameters

This method only supports the `$top` OData query parameter.

## HTTP request

```http
GET /education/classes/{educationClassId}/assignmentCategories/delta
GET /education/classes/{educationClassId}/assignments/{educationAssignmentId}/categories/delta
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and an [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) collection in the response body.

## Examples

### Example 1: Get assignment categories

#### Request

The following example shows a request.

Use the `$top` parameter to specify the number of categories to be returned. The parameter is optional. Use it when you have a long list of categories; otherwise, you will get all the categories in the class.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$top=3
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].AssignmentCategories.Delta.GetAsDeltaGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Top = 3;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  grapheducation "github.com/microsoftgraph/msgraph-sdk-go/education"
	  //other-imports
)


requestTop := int32(3)

requestParameters := &grapheducation.ClassesItemAssignmentCategoriesDeltaRequestBuilderGetQueryParameters{
	Top: &requestTop,
}
configuration := &grapheducation.ClassesItemAssignmentCategoriesDeltaRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").AssignmentCategories().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignmentCategories().delta().get(requestConfiguration -> {
	requestConfiguration.queryParameters.top = 3;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta')
	.top(3)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Education\Classes\Item\AssignmentCategories\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->top = 3;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignmentCategories()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationClassAssignmentCategoryDelta -EducationClassId $educationClassId -Top 3 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.education.classes.item.assignment_categories.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		top = 3,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignment_categories.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** Take the `@odata.nextLink` from the response to make another call and get the next set of categories.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 344

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(educationCategory)",
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$skiptoken=U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY",
    "value": [
        {
            "@odata.type": "#microsoft.graph.educationCategory",
            "displayName": "Fall 21",
            "id": "f0fd3e18-87a7-4060-b348-bd2d7a178a9d"
        },
        {
            "@odata.type": "#microsoft.graph.educationCategory",
            "displayName": "reading",
            "id": "10aa7bb1-7f5b-4c12-b1d4-0bf1429a12de"
        },
        {
            "@odata.type": "#microsoft.graph.educationCategory",
            "displayName": "expand",
            "id": "02f60051-806d-4729-a251-4156f7d8e8a5"
        }
    ]
}
```

### Example 2: Get next set of categories

#### Request

The following example shows a request.

Use the `@odata.nextLink` value from the previous call for this request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET /education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$skiptoken=U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
// Note: The URI string parameter used with WithUrl() can be retrieved using the OdataNextLink or OdataDeltaLink property from a response object
var result = await graphClient.Education.Classes["{educationClass-id}"].AssignmentCategories.Delta.WithUrl("https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$skiptoken=U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY").GetAsDeltaGetResponseAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  grapheducation "github.com/microsoftgraph/msgraph-sdk-go/education"
	  //other-imports
)


requestSkiptoken := "U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY"

requestParameters := &grapheducation.ClassesItemAssignmentCategoriesDeltaRequestBuilderGetQueryParameters{
	Skiptoken: &requestSkiptoken,
}
configuration := &grapheducation.ClassesItemAssignmentCategoriesDeltaRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").AssignmentCategories().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.education.classes.item.assignmentcategories.delta.DeltaRequestBuilder deltaRequestBuilder = new com.microsoft.graph.education.classes.item.assignmentcategories.delta.DeltaRequestBuilder("https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$skiptoken=U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY", graphClient.getRequestAdapter());
com.microsoft.graph.education.classes.item.assignmentcategories.delta.DeltaGetResponse result = deltaRequestBuilder.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta')
	.skiptoken('U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Education\Classes\Item\AssignmentCategories\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->skiptoken = "U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignmentCategories()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationClassAssignmentCategoryDelta -EducationClassId $educationClassId -Skiptoken "U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.education.classes.item.assignment_categories.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		skiptoken = "U43TyYWKlRvJ6wWxZOfJvkp22nMqShRw9f-GxBtG2FDy9b1hMDaAJGdLb7n2fh1IVSFtBcXz0jxjIEihcR91dS3R7i8Z2IMtxIn9rKbK9Jvurj6jCH-lDbSNatdesrK0PJ5zpZ_-i8HyqkdtLhWD9tewXVArIqQWJA7gJz8z4paG2q0MU9rixrQOTe7WIXikPiBTUPilHuUW-o1k7cvqke3K7llJbU3G7z_O7WGoVGE.l8-2OcBi9ZWAhwhPnXvJ-kyyk8GNb6-H4o6qofP5YBY",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignment_categories.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** You must continue using the `@odata.nextLink` value for the consequent calls until you get the `@odata.deltaLink` property in the response.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 344

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(educationCategory)",
    "@odata.deltaLink": "https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$deltatoken=7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApZYl6uZqiXcR7H0G14btPqR761sKWNc0jgiczrHGF6dGfSQwsLzPT46og-84ArhOU.Jnxvkr08FE-QBvEYstYel3JZUrgwgTauo-GmpbdWeSA",
    "value": [
        {
            "@odata.type": "#microsoft.graph.educationCategory",
            "displayName": "apps",
            "id": "62cee656-f3e7-45c9-958f-5dc3ff47dd97"
        },
        {
            "@odata.type": "#microsoft.graph.educationCategory",
            "displayName": "homework",
            "id": "440c56ea-6c2a-4566-a8ab-56fcda3bc1e3"
        }
    ]
}
```

### Example 3: Get the created and modified categories using delta token

#### Request

The following example shows a request.

Use the `@odata.deltaLink` value from the previous call for this request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET /education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$deltatoken=7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApZYl6uZqiXcR7H0G14btPqR761sKWNc0jgiczrHGF6dGfSQwsLzPT46og-84ArhOU.Jnxvkr08FE-QBvEYstYel3JZUrgwgTauo-GmpbdWeSA
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
// Note: The URI string parameter used with WithUrl() can be retrieved using the OdataNextLink or OdataDeltaLink property from a response object
var result = await graphClient.Education.Classes["{educationClass-id}"].AssignmentCategories.Delta.WithUrl("https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$deltatoken=7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApZYl6uZqiXcR7H0G14btPqR761sKWNc0jgiczrHGF6dGfSQwsLzPT46og-84ArhOU.Jnxvkr08FE-QBvEYstYel3JZUrgwgTauo-GmpbdWeSA").GetAsDeltaGetResponseAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  grapheducation "github.com/microsoftgraph/msgraph-sdk-go/education"
	  //other-imports
)


requestDeltatoken := "7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApZYl6uZqiXcR7H0G14btPqR761sKWNc0jgiczrHGF6dGfSQwsLzPT46og-84ArhOU.Jnxvkr08FE-QBvEYstYel3JZUrgwgTauo-GmpbdWeSA"

requestParameters := &grapheducation.ClassesItemAssignmentCategoriesDeltaRequestBuilderGetQueryParameters{
	Deltatoken: &requestDeltatoken,
}
configuration := &grapheducation.ClassesItemAssignmentCategoriesDeltaRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").AssignmentCategories().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.education.classes.item.assignmentcategories.delta.DeltaRequestBuilder deltaRequestBuilder = new com.microsoft.graph.education.classes.item.assignmentcategories.delta.DeltaRequestBuilder("https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$deltatoken=7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApZYl6uZqiXcR7H0G14btPqR761sKWNc0jgiczrHGF6dGfSQwsLzPT46og-84ArhOU.Jnxvkr08FE-QBvEYstYel3JZUrgwgTauo-GmpbdWeSA", graphClient.getRequestAdapter());
com.microsoft.graph.education.classes.item.assignmentcategories.delta.DeltaGetResponse result = deltaRequestBuilder.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Education\Classes\Item\AssignmentCategories\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->deltatoken = "7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApZYl6uZqiXcR7H0G14btPqR761sKWNc0jgiczrHGF6dGfSQwsLzPT46og-84ArhOU.Jnxvkr08FE-QBvEYstYel3JZUrgwgTauo-GmpbdWeSA";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignmentCategories()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationClassAssignmentCategoryDelta -EducationClassId $educationClassId -Deltatoken "7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApZYl6uZqiXcR7H0G14btPqR761sKWNc0jgiczrHGF6dGfSQwsLzPT46og-84ArhOU.Jnxvkr08FE-QBvEYstYel3JZUrgwgTauo-GmpbdWeSA" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.education.classes.item.assignment_categories.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		deltatoken = "7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApZYl6uZqiXcR7H0G14btPqR761sKWNc0jgiczrHGF6dGfSQwsLzPT46og-84ArhOU.Jnxvkr08FE-QBvEYstYel3JZUrgwgTauo-GmpbdWeSA",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignment_categories.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** You must continue using the `@odata.deltaLink` to get the newly created or modified categories since the initial Delta call.

> Sometimes the delta response will be very large in which case an `@odata.nextLink` will be returned to continue fetching changes until you hit an `@odata.deltaLink` again.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 344

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(educationCategory)",
    "@odata.deltaLink": "https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignmentcategories/delta?$deltatoken=7ORzTfzlUEGDy6BRE3OC-3ePBbvLHCRe4aJ_hjaBKJxUHmn_ODgoM4xreLS7YRaxc-iACeqCQsT5Tb0u9vn6QXYflO6j0sRgRQlhcfR7DApVu5vuUKP3uuUhFpYW8Ku3RtYbkmxRlHbDAkK-NyvPczuDOJqONtesUhKgaoXQGmM.4Rw7IYlmUFBcaDmEbJoGDLMbchYNgoLiPNyp4e7z2po",
    "value": [
        {
            "@odata.type": "#microsoft.graph.educationCategory",
            "displayName": "arts",
            "id": "d9fa9b82-04d5-4411-ae4d-848e6fd75575"
        }
    ]
}
```
