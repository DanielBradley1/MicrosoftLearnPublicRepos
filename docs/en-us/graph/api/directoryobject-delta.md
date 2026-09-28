<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryobject-delta?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-28 -->

# directoryObject: delta

Namespace: microsoft.graph

Get newly created, updated, or deleted directory objects without performing a full read of the entire directoryObject collection. For more information, see [Use delta query to track changes in Microsoft Graph data](https://learn.microsoft.com/en-us/graph/delta-query-overview) for details.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following table shows the least privileged permission that's required by each resource type when calling this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Application | Delegated \(personal Microsoft account\) |
| :--- | :--- | --- | --- |
| [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) | Application.Read.All | Application.Read.All | Not supported |
| [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) | AdministrativeUnit.Read.All | AdministrativeUnit.Read.All | Not supported |
| [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | User.Read.All | User.Read.All | Not supported |
| [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | Device.Read.All | Device.Read.All | Not supported |
| [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) | RoleManagement.Read.Directory | RoleManagement.Read.Directory | Not supported |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.Read.All | Group.Read.All | Not supported |
| [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0) | OrgContact.Read.All | OrgContact.Read.All | Not supported |
| [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Application.Read.All | Application.Read.All | Not supported |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.Read.All | User.Read.All | Not supported |

## HTTP request

Track changes for a collection of a directory object type.

```http
GET /directoryObjects/delta?$filter=isof('microsoft.graph.application')
GET /directoryObjects/delta?$filter=isof('microsoft.graph.administrativeUnit')
GET /directoryObjects/delta?$filter=isof('microsoft.graph.appRoleAssignment') or isof('microsoft.graph.user')
GET /directoryObjects/delta?$filter=isof('microsoft.graph.device')
GET /directoryObjects/delta?$filter=isof('microsoft.graph.directoryRole')
GET /directoryObjects/delta?$filter=isof('microsoft.graph.group')
GET /directoryObjects/delta?$filter=isof('microsoft.graph.orgContact')
GET /directoryObjects/delta?$filter=isof('microsoft.graph.servicePrincipal')
GET /directoryObjects/delta?$filter=isof('microsoft.graph.user')
```

Track changes for a directory object. This request isn't supported on the `appRoleAssignment` resource.

```http
GET /directoryObjects/delta?$filter=id eq '{id}'
```

### OData query parameters

This method supports optional OData query parameters to help customize the response.

- You can use a `$select` query parameter as in any GET request to specify only the properties your need for best performance. The *id* property is always returned.
- When filtering multiple objects, for example, `/directoryObjects/delta/?$filter=id eq '477e9fc6-5de7-4406-bb2a-7e5c83c9ffff' or id eq '004d6a07-fe70-4b92-add5-e6e37b8affff'`, there's a limit of 50 filter expressions.
- You can combine the `$filter` syntaxes. For example, `$filter=isof('{resource type}') or id eq '{id}'`. This provides an **intersection** of objects specified by matching `{resource type}` and the resource type of `{id}`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |
| Prefer | return=minimal  <br>  <br>Specifying this header with a request that uses a `@odata.deltaLink` returns only the object's properties that have changed since the last round. Optional. |

## Request body

Don't supply a request body for this method.

### Response

If successful, this method returns `200 OK` response code and [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection object in the response body. The response also includes a state token that is either a `@odata.nextLink` URL or a `@odata.deltaLink` URL.

- If a `@odata.nextLink` URL is returned:

  - This indicates there are more pages of data to be retrieved in the session. The application continues making requests by using the `@odata.nextLink` URL until a `@odata.deltaLink` URL is included in the response.
  - The response includes the same set of properties as in the initial delta query request. This allows you to capture the full current state of the objects when initiating the delta cycle.

- If a `@odata.deltaLink` URL is returned:

  - This indicates there's no more data about the existing state of the resource to be returned. Save and use the `@odata.deltaLink` URL to learn about changes to the resource in the next round.
  - You have a choice to specify the `Prefer:return=minimal` header, to include in the response values for only the properties that have changed since the time the `@odata.deltaLink` was issued.

#### Default: return the same properties as initial delta request

By default, requests using a `@odata.deltaLink` or `@odata.nextLink` return the same properties as selected in the initial delta query in the following ways:

- If the property has changed, the new value is included in the response. This includes properties being set to null value.
- If the property hasn't changed, the old value is included in the response.
- If the property has never been set before it will not be included in the response at all.

> **Note:** With this behavior, by looking at the response it is not possible to tell whether a property is changing or not. Also, the delta responses tend to be large because they contain all property values - as shown in [Example 3](#example-3-retrieve-changes-to-specific-properties-for-a-collection-of-users-and-groups).

#### Alternative: return only the changed properties

Adding an optional `prefer:return=minimal` request header results in the following behavior:

- If the property has changed, the new value is included in the response. This includes properties being set to null value.
- If the property hasn't changed, the property isn't included in the response at all. This is different from the default behavior.

> **Note:** The header can be added to a `@odata.deltaLink` request at any point in time in the delta cycle. The header only affects the set of properties included in the response and it doesn't affect how the delta query is executed. See [Example 4](#example-4-retrieve-specific-properties-only-if-they-changed-for-a-collection-of-users-and-groups).

## Examples

### Example 1: Retrieve changes for a collection of users and groups

#### Request

The following example shows a request using the `$filter=isof('{resource type}')` parameter on users and groups. There's no `$select` parameter, so a default set of properties is tracked and returned.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/directoryObjects/delta?filter=isof('microsoft.graph.user') or isof('microsoft.graph.group')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryObjects.Delta.GetAsDeltaGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectoryobjects "github.com/microsoftgraph/msgraph-sdk-go/directoryobjects"
	  //other-imports
)


requestFilter := "isof('microsoft.graph.user') or isof('microsoft.graph.group')"

requestParameters := &graphdirectoryobjects.DirectoryObjectsDeltaRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphdirectoryobjects.DirectoryObjectsDeltaRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.DirectoryObjects().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.directoryObjects().delta().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/directoryObjects/delta?filter=isof(\'microsoft.graph.user\') or isof(\'microsoft.graph.group\')')
	.filter('isof(\'microsoft.graph.user\') or isof(\'microsoft.graph.group\')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->directoryObjects()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

Get-MgDirectoryObjectDelta -Filter "isof('microsoft.graph.user') or isof('microsoft.graph.group')" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directory_objects.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.directory_objects.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Here's an example of the response when using `@odata.deltaLink` obtained from the query initialization with `$filter=isof('{resource type}')`. Note the presence of the *members@delta* property that includes the ids of member objects in the group.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#directoryObjects","@odata.nextLink":"https://graph.microsoft.com/v1.0/directoryObjects/delta?$skiptoken=pqwSUjGYvb3jQpbwVAwEL7yuI3dU1LecfkkfLPtnIjvY1FSSc_",
  "value":[
    {
      "@odata.type": "#microsoft.graph.user",
      "displayName": "Adele Vance",
      "givenName": "Adele",
      "jobTitle": "Retail Manager",
      "surname": "Vance",
      "userPrincipalName": "AdeleV@contoso.com",
      "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd"
    },
    {
      "@odata.type": "#microsoft.graph.group",
      "createdDateTime":"2021-03-12T10:36:14Z",
      "description":"This is the default group for everyone in the network",
      "displayName":"All Company",
      "groupTypes": [
        "Unified"
      ],
      "mail": "allcompany@contoso.com",
      "id": "72052a9a-c466-4995-8210-95a1c1221995",
      "members@delta": [
        {
          "@odata.type": "#microsoft.graph.user",
          "id": "693acd06-2877-4339-8ade-b704261fe7a0"
        },
        {
          "@odata.type": "#microsoft.graph.user",
          "id": "49320844-be99-4164-8167-87ff5d047ace"
        }
      ]
    }
  ]
}
```

### Example 2: Retrieve a collection of changes for a directory object

#### Request

Here's an example shows the request using the `$filter=id eq '{id}'` parameter. There's no `$select` parameter, so a default set of properties is tracked and returned.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/directoryObjects/delta?$filter=id eq '87d349ed-44d7-43e1-9a83-5f2406dee5bd'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryObjects.Delta.GetAsDeltaGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "id eq '87d349ed-44d7-43e1-9a83-5f2406dee5bd'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectoryobjects "github.com/microsoftgraph/msgraph-sdk-go/directoryobjects"
	  //other-imports
)


requestFilter := "id eq '87d349ed-44d7-43e1-9a83-5f2406dee5bd'"

requestParameters := &graphdirectoryobjects.DirectoryObjectsDeltaRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphdirectoryobjects.DirectoryObjectsDeltaRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.DirectoryObjects().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.directoryObjects().delta().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "id eq '87d349ed-44d7-43e1-9a83-5f2406dee5bd'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/directoryObjects/delta')
	.filter('id eq \'87d349ed-44d7-43e1-9a83-5f2406dee5bd\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "id eq '87d349ed-44d7-43e1-9a83-5f2406dee5bd'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->directoryObjects()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

Get-MgDirectoryObjectDelta -Filter "id eq '87d349ed-44d7-43e1-9a83-5f2406dee5bd'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directory_objects.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		filter = "id eq '87d349ed-44d7-43e1-9a83-5f2406dee5bd'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.directory_objects.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Here's an example of the response when using `@odata.deltaLink` obtained from the query initialization with `$filter=id eq '{id}'`.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#directoryObjects",
  "@odata.nextLink":"https://graph.microsoft.com/v1.0/directoryObjects/delta?$skiptoken=pqwSUjGYvb3jQpbwVAwEL7yuI3dU1LecfkkfLPtnIjsXoYQp_dpA3cNJWc",
  "value": [
    {
      "@odata.type": "#microsoft.graph.group",
      "createdDateTime":"2021-03-12T10:36:14Z",
      "description":"This is the default group for everyone in the network",
      "displayName":"All Company",
      "groupTypes": [
        "Unified"
      ],
      "mail": "allcompany@contoso.com",
      "id": "72052a9a-c466-4995-8210-95a1c1221995",
      "members@delta": [
        {
          "@odata.type": "#microsoft.graph.user",
          "id": "693acd06-2877-4339-8ade-b704261fe7a0"
        },
        {
          "@odata.type": "#microsoft.graph.user",
          "id": "49320844-be99-4164-8167-87ff5d047ace"
        }
      ]
    }
  ]
}
```

### Example 3: Retrieve changes to specific properties for a collection of users and groups

#### Request

The following example shows the initial request selecting one property each from a user and group for change tracking, with default response behavior:

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/directoryObjects/delta?$filter=isof('microsoft.graph.user') or isof('microsoft.graph.group')&$select=microsoft.graph.user/surname,microsoft.graph.group/displayName
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryObjects.Delta.GetAsDeltaGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
	requestConfiguration.QueryParameters.Select = new string []{ "microsoft.graph.user/surname","microsoft.graph.group/displayName" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectoryobjects "github.com/microsoftgraph/msgraph-sdk-go/directoryobjects"
	  //other-imports
)


requestFilter := "isof('microsoft.graph.user') or isof('microsoft.graph.group')"

requestParameters := &graphdirectoryobjects.DirectoryObjectsDeltaRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"microsoft.graph.user/surname","microsoft.graph.group/displayName"},
}
configuration := &graphdirectoryobjects.DirectoryObjectsDeltaRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.DirectoryObjects().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.directoryObjects().delta().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
	requestConfiguration.queryParameters.select = new String []{"microsoft.graph.user/surname", "microsoft.graph.group/displayName"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/directoryObjects/delta')
	.filter('isof(\'microsoft.graph.user\') or isof(\'microsoft.graph.group\')')
	.select('microsoft.graph.user,microsoft.graph.group')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
$queryParameters->select = ["microsoft.graph.user/surname","microsoft.graph.group/displayName"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->directoryObjects()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

Get-MgDirectoryObjectDelta -Filter "isof('microsoft.graph.user') or isof('microsoft.graph.group')" -Property "microsoft.graph.user/surname,microsoft.graph.group/displayName" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directory_objects.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')",
		select = ["microsoft.graph.user/surname","microsoft.graph.group/displayName"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.directory_objects.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Here's an example of the response when using `@odata.deltaLink` obtained from the query initialization. Both properties are included in the response and it isn't known which ones have changed since the `@odata.deltaLink` was obtained.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#directoryObjects",
  "@odata.nextLink":"https://graph.microsoft.com/v1.0/directoryObjects/delta?$skiptoken=pqwSUjGYvb3jQpbwVAwEL7yuI3dU1LecfkkfLPtnIjsXoYQp_dpA3cNJWc",
  "value": [
    {
      "@odata.type": "#microsoft.graph.user",
      "surname": "Vance",
      "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd"
    },
    {
      "@odata.type": "#microsoft.graph.group",
      "displayName":"All Company",
      "id": "72052a9a-c466-4995-8210-95a1c1221995",
    }
  ]
}
```

### Example 4: Retrieve specific properties only if they changed for a collection of users and groups

#### Request

The following example shows the initial request selecting one property each from a user and group for change tracking, with alternative minimal response behavior:

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/directoryObjects/delta?$filter=isof('microsoft.graph.user') or isof('microsoft.graph.group')&$select=microsoft.graph.user/surname,microsoft.graph.group/displayName
Prefer: return=minimal
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryObjects.Delta.GetAsDeltaGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
	requestConfiguration.QueryParameters.Select = new string []{ "microsoft.graph.user/surname","microsoft.graph.group/displayName" };
	requestConfiguration.Headers.Add("Prefer", "return=minimal");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectoryobjects "github.com/microsoftgraph/msgraph-sdk-go/directoryobjects"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "return=minimal")


requestFilter := "isof('microsoft.graph.user') or isof('microsoft.graph.group')"

requestParameters := &graphdirectoryobjects.DirectoryObjectsDeltaRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"microsoft.graph.user/surname","microsoft.graph.group/displayName"},
}
configuration := &graphdirectoryobjects.DirectoryObjectsDeltaRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.DirectoryObjects().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.directoryObjects().delta().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
	requestConfiguration.queryParameters.select = new String []{"microsoft.graph.user/surname", "microsoft.graph.group/displayName"};
	requestConfiguration.headers.add("Prefer", "return=minimal");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/directoryObjects/delta')
	.header('Prefer','return=minimal')
	.filter('isof(\'microsoft.graph.user\') or isof(\'microsoft.graph.group\')')
	.select('microsoft.graph.user,microsoft.graph.group')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$headers = [
		'Prefer' => 'return=minimal',
	];
$requestConfiguration->headers = $headers;

$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')";
$queryParameters->select = ["microsoft.graph.user/surname","microsoft.graph.group/displayName"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->directoryObjects()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

Get-MgDirectoryObjectDelta -Filter "isof('microsoft.graph.user') or isof('microsoft.graph.group')" -Property "microsoft.graph.user/surname,microsoft.graph.group/displayName" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directory_objects.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		filter = "isof('microsoft.graph.user') or isof('microsoft.graph.group')",
		select = ["microsoft.graph.user/surname","microsoft.graph.group/displayName"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("Prefer", "return=minimal")


result = await graph_client.directory_objects.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Here's an example of the response when using `@odata.deltaLink` obtained from the query initialization. The `microsoft.graph.user/surname` property isn't included, which means it hasn't changed since the last delta query; `microsoft.graph.group/displayName` is included which means its value has changed.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#directoryObjects",
  "@odata.nextLink":"https://graph.microsoft.com/v1.0/directoryObjects/delta?$skiptoken=pqwSUjGYvb3jQpbwVAwEL7yuI3dU1LecfkkfLPtnIjsXoYQp_dpA3cNJWc",
  "value": [
    {
      "@odata.type": "#microsoft.graph.group",
      "displayName":"Everyone",
      "id": "72052a9a-c466-4995-8210-95a1c1221995",
    }
  ]
}
```

## Related content

- [Use delta query to track changes in Microsoft Graph data](https://learn.microsoft.com/en-us/graph/delta-query-overview).
- [Get incremental changes for groups](https://learn.microsoft.com/en-us/graph/delta-query-groups).
- [Get incremental changes for users](https://learn.microsoft.com/en-us/graph/delta-query-users).
