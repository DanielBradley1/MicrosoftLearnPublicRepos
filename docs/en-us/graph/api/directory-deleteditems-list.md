<!-- Source: https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# List deletedItems \(directory objects\)

Namespace: microsoft.graph

Retrieve a list of recently deleted directory objects from [deleted items](https://learn.microsoft.com/en-us/graph/api/resources/directory?view=graph-rest-1.0). The following types are supported:

- [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0)
- [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0)
- [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0)
- [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0)
- [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0)
- [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0)
- [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0)
- [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0)
- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following table shows the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) | AdministrativeUnit.Read.All | Not supported. | AdministrativeUnit.Read.All |
| [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) | Application.Read.All | Not supported. | Application.Read.All |
| [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) | AgentIdentity.Read.All | Not supported. | AgentIdentity.Read.All |
| [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) | AgentIdentityBlueprint.Read.All | Not supported. | AgentIdentityBlueprint.Read.All |
| [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) | AgentIdentityBlueprintPrincipal.Read.All | Not supported. | AgentIdentityBlueprintPrincipal.Read.All |
| [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) | User.ReadBasic.All | Not supported. | User.ReadBasic.All |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.Read.All | Not supported. | Group.Read.All |
| [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Application.Read.All | Not supported. | Application.Read.All |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.Read.All | Not supported. | User.Read.All |
| [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) | PublicKeyInfrastructure.Read.All | Not supported. | PublicKeyInfrastructure.Read.All |
| [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) | PublicKeyInfrastructure.Read.All | Not supported. | PublicKeyInfrastructure.Read.All |

Important

When an application queries a relationship that returns a **directoryObject** type collection, if it doesn't have permission to read a certain resource type, members of that type are returned but with limited information. For example, only the **@odata.type** property for the object type and the **id** is returned, while other properties are indicated as `null`. With this behavior, applications can request the least privileged permissions they need, rather than rely on the set of *Directory.*\* permissions. For details, see [Limited information returned for inaccessible member objects](https://learn.microsoft.com/en-us/graph/permissions-overview#limited-information-returned-for-inaccessible-member-objects).

## HTTP request

```http
GET /directory/deletedItems/microsoft.graph.application
GET /directory/deletedItems/microsoft.graph.servicePrincipal
GET /directory/deletedItems/microsoft.graph.group
GET /directory/deletedItems/microsoft.graph.user
GET /directory/deletedItems/microsoft.graph.administrativeUnit
GET /directory/deletedItems/microsoft.graph.certificateBasedAuthPki
GET /directory/deletedItems/microsoft.graph.certificateAuthorityDetail
```

Important

For soft deleted security groups, the **securityEnabled** property returns `false` instead of `true` due to a known limitation.

To identify the group type, use the **groupTypes** property:

- `["Unified"]`indicates a Microsoft 365 group.
- An empty array \(`[]`\) indicates a security group.

The OData cast type is a required part of the URI and calling `GET /directory/deletedItems` without a type is **not** supported.

## Optional query parameters

This method supports the query parameters that are supported by the resource that is specified by the OData cast. That is, `$count`, `$expand`, `$filter`, `$orderby`, `$search`, `$select`, and `$top` query parameters. This API returns 100 objects by default and supports returning up to 999 objects per page using `$top`.

Some queries are supported only when you use the **ConsistencyLevel** header set to `eventual` and `$count`. For example:

```msgraph
https://graph.microsoft.com/v1.0/directory/deletedItems/microsoft.graph.group?&$count=true&$orderby=deletedDateTime desc&$select=id,displayName,deletedDateTime
ConsistencyLevel: eventual
```

This example requires the **ConsistencyLevel** header because the `$orderby` and `$count` query parameters are used in the query.

### $orderby OData query parameter examples

The `$orderby` OData query parameter is supported on the **deletedDateTime**, **displayName**, and **userPrincipalName** properties of the deleted object types. On the **deletedDateTime** property, the query requires adding the [advanced query parameters](https://learn.microsoft.com/en-us/graph/aad-advanced-queries) \(**ConsistencyLevel** header set to `eventual` and `$count=true` query string\).

| OData cast | Properties supporting $orderby | Example |
| :--- | :--- | :--- |
| microsoft.graph.user | deletedDateTime, displayName, userPrincipalName | /directory/deletedItems/microsoft.graph.user?$orderby=userPrincipalName |
| microsoft.graph.group | deletedDateTime, displayName | /directory/deletedItems/microsoft.graph.group?$orderby=deletedDateTime asc&$count=true |
| microsoft.graph.application | deletedDateTime, displayName | /directory/deletedItems/microsoft.graph.application?$orderby=displayName |
| microsoft.graph.device | deletedDateTime, displayName | /directory/deletedItems/microsoft.graph.device?$orderby=deletedDateTime&$count=true |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and collection of [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Retrieve deleted groups

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/directory/deletedItems/microsoft.graph.group
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.DeletedItems.GraphGroup.GetAsync();
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
graphGroup, err := graphClient.Directory().DeletedItems().GraphGroup().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupCollectionResponse result = graphClient.directory().deletedItems().graphGroup().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let group = await client.api('/directory/deletedItems/microsoft.graph.group')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->directory()->deletedItems()->graphGroup()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Get-MgDirectoryDeletedItemAsGroup
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.directory.deleted_items.graph_group.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#groups",
  "value": [
    {
      "id":"46cc6179-19d0-473e-97ad-6ff84347bbbb",
      "displayName":"SampleGroup",
      "groupTypes":["Unified"],
      "mail":"example@contoso.com",
      "mailEnabled":true,
      "mailNickname":"Example",
      "securityEnabled":false,
      "visibility":"Public"
    }
  ]
}
```

### Example 2: Retrieve the count of deleted user objects and order the results by the deletedDateTime property

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/directory/deletedItems/microsoft.graph.group?$count=true&$orderby=deletedDateTime asc&$select=id,displayName,deletedDateTime
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.DeletedItems.GraphGroup.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Orderby = new string []{ "deletedDateTime asc" };
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","deletedDateTime" };
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
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
	  graphdirectory "github.com/microsoftgraph/msgraph-sdk-go/directory"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestCount := true

requestParameters := &graphdirectory.DeletedItemsGraph.groupRequestBuilderGetQueryParameters{
	Count: &requestCount,
	Orderby: [] string {"deletedDateTime asc"},
	Select: [] string {"id","displayName","deletedDateTime"},
}
configuration := &graphdirectory.DeletedItemsGraph.groupRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphGroup, err := graphClient.Directory().DeletedItems().GraphGroup().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupCollectionResponse result = graphClient.directory().deletedItems().graphGroup().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.orderby = new String []{"deletedDateTime asc"};
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "deletedDateTime"};
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let group = await client.api('/directory/deletedItems/microsoft.graph.group')
	.header('ConsistencyLevel','eventual')
	.select('id,displayName,deletedDateTime')
	.orderby('deletedDateTime asc')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Directory\DeletedItems\Graph\Group\GroupRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GraphGroupRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = GraphGroupRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$queryParameters->orderby = ["deletedDateTime asc"];
$queryParameters->select = ["id","displayName","deletedDateTime"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->directory()->deletedItems()->graphGroup()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Get-MgDirectoryDeletedItemAsGroup -CountVariable CountVar -Sort "deletedDateTime asc" -Property "id,displayName,deletedDateTime" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directory.deleted_items.graph.group.group_request_builder import GroupRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GroupRequestBuilder.GroupRequestBuilderGetQueryParameters(
		count = True,
		orderby = ["deletedDateTime asc"],
		select = ["id","displayName","deletedDateTime"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.directory.deleted_items.graph_group.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups(id,displayName,deletedDateTime)",
    "@odata.count": 2,
    "value": [
        {
            "id": "c31799b8-0683-4d70-9e91-e032c89d3035",
            "displayName": "Role assignable group",
            "deletedDateTime": "2021-10-26T16:56:36Z"
        },
        {
            "id": "74e45ce0-a52a-4766-976c-7201b0f99370",
            "displayName": "Role assignable group",
            "deletedDateTime": "2021-10-26T16:58:37Z"
        }
    ]
}
```
