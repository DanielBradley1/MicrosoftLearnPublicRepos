<!-- Source: https://learn.microsoft.com/en-us/graph/api/identityanalyticsroot-list-groups?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# List groupAnalytics

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [groupAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/groupanalytics?view=graph-rest-beta) objects and their properties for a Microsoft Entra tenant. Each object holds point-in-time [identity analytics](https://learn.microsoft.com/en-us/graph/api/resources/identityanalyticsroot?view=graph-rest-beta) for one group.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Reports.Read.All | Directory.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Reports.Read.All | Directory.Read.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Reports Reader
- Security Reader
- Security Administrator

## HTTP request

```http
GET /reports/identityAnalytics/groups
```

## Optional query parameters

This method supports the `$count`, `$filter`, `$orderby`, `$select`, and `$top` OData query parameters to help customize the response. The `$filter` operators and `$orderby` support available for each property are listed in the [groupAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/groupanalytics?view=graph-rest-beta) properties table.

Across the resource, `$filter` supports the `eq`, `ne`, `gt`, `ge`, `lt`, and `le` operators, the `and` and `or` logical operators, and the `startsWith`, `endsWith`, and `contains` string functions, depending on the property type. The `not` and `has` operators aren't supported.

To get the number of matching groups, append `/$count` to the request URL \(for example, `GET /reports/identityAnalytics/groups/$count`\) or add the `$count=true` query parameter to return the count inline as the `@odata.count` property. Large result sets are paged; follow the `@odata.nextLink` URL in the response to retrieve the next page. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [groupAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/groupanalytics?view=graph-rest-beta) objects in the response body.

## Examples

### Example 1: Get a list of groupAnalytics objects

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

```msgraph
GET https://graph.microsoft.com/beta/reports/identityAnalytics/groups
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.IdentityAnalytics.Groups.GetAsync();
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
groups, err := graphClient.Reports().IdentityAnalytics().Groups().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupAnalyticsCollectionResponse result = graphClient.reports().identityAnalytics().groups().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let groups = await client.api('/reports/identityAnalytics/groups')
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


$result = $graphServiceClient->reports()->identityAnalytics()->groups()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaReportIdentityAnalyticGroup
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.reports.identity_analytics.groups.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#reports/identityAnalytics/groups",
  "value": [
    {
      "id": "1f3a3b9c-6e2c-4f0a-9b2c-9a6d4d2e8f10",
      "tenantId": "5d6f7a8b-1c2d-3e4f-5a6b-7c8d9e0f1a2b",
      "displayName": "Sales Team",
      "calculatedDateTime": "2026-06-08T00:00:00Z",
      "createdDateTime": "2023-02-15T10:30:00Z",
      "groupType": "isCloudGroup",
      "isValidGroup": true,
      "isCloudM365Group": true,
      "isDynamicGroup": false,
      "directGroupMemberCount": 3,
      "transitiveUserCount": 412,
      "memberTransitiveUserCount": 405,
      "guestTransitiveUserCount": 7,
      "assignedRoleCount": 1
    },
    {
      "id": "9a8b7c6d-5e4f-3a2b-1c0d-9e8f7a6b5c4d",
      "tenantId": "5d6f7a8b-1c2d-3e4f-5a6b-7c8d9e0f1a2b",
      "displayName": "Engineering - All",
      "calculatedDateTime": "2026-06-08T00:00:00Z",
      "createdDateTime": "2021-11-03T08:00:00Z",
      "groupType": "isCloudGroup",
      "isValidGroup": true,
      "isCloudM365Group": false,
      "isCloudSecurityGroup": true,
      "isDynamicGroup": true,
      "directGroupMemberCount": 12,
      "transitiveUserCount": 1890,
      "memberTransitiveUserCount": 1890,
      "guestTransitiveUserCount": 0,
      "assignedRoleCount": 0
    }
  ]
}
```

### Example 2: Get valid groups that contain guests, with selected properties

#### Request

The following example uses `$filter` to return only valid groups that contain at least one transitive guest user. It uses `$select` to limit the returned properties, `$orderby` to sort the results by creation date, and `$top` to return at most 10 results.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/beta/reports/identityAnalytics/groups?$filter=isValidGroup eq true and guestTransitiveUserCount gt 0&$select=id,displayName,createdDateTime,groupType,transitiveUserCount,guestTransitiveUserCount&$orderby=createdDateTime desc&$top=10
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.IdentityAnalytics.Groups.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "isValidGroup eq true and guestTransitiveUserCount gt 0";
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","createdDateTime","groupType","transitiveUserCount","guestTransitiveUserCount" };
	requestConfiguration.QueryParameters.Orderby = new string []{ "createdDateTime desc" };
	requestConfiguration.QueryParameters.Top = 10;
});
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
	  graphreports "github.com/microsoftgraph/msgraph-beta-sdk-go/reports"
	  //other-imports
)


requestFilter := "isValidGroup eq true and guestTransitiveUserCount gt 0"
requestTop := int32(10)

requestParameters := &graphreports.IdentityAnalyticsGroupsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"id","displayName","createdDateTime","groupType","transitiveUserCount","guestTransitiveUserCount"},
	Orderby: [] string {"createdDateTime desc"},
	Top: &requestTop,
}
configuration := &graphreports.IdentityAnalyticsGroupsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Reports().IdentityAnalytics().Groups().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupAnalyticsCollectionResponse result = graphClient.reports().identityAnalytics().groups().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "isValidGroup eq true and guestTransitiveUserCount gt 0";
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "createdDateTime", "groupType", "transitiveUserCount", "guestTransitiveUserCount"};
	requestConfiguration.queryParameters.orderby = new String []{"createdDateTime desc"};
	requestConfiguration.queryParameters.top = 10;
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let groups = await client.api('/reports/identityAnalytics/groups')
	.version('beta')
	.filter('isValidGroup eq true and guestTransitiveUserCount gt 0')
	.select('id,displayName,createdDateTime,groupType,transitiveUserCount,guestTransitiveUserCount')
	.orderby('createdDateTime desc')
	.top(10)
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Reports\IdentityAnalytics\Groups\GroupsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GroupsRequestBuilderGetRequestConfiguration();
$queryParameters = GroupsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "isValidGroup eq true and guestTransitiveUserCount gt 0";
$queryParameters->select = ["id","displayName","createdDateTime","groupType","transitiveUserCount","guestTransitiveUserCount"];
$queryParameters->orderby = ["createdDateTime desc"];
$queryParameters->top = 10;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->reports()->identityAnalytics()->groups()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaReportIdentityAnalyticGroup -Filter "isValidGroup eq true and guestTransitiveUserCount gt 0" -Property "id,displayName,createdDateTime,groupType,transitiveUserCount,guestTransitiveUserCount" -Sort "createdDateTime desc" -Top 10 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.reports.identity_analytics.groups.groups_request_builder import GroupsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GroupsRequestBuilder.GroupsRequestBuilderGetQueryParameters(
		filter = "isValidGroup eq true and guestTransitiveUserCount gt 0",
		select = ["id","displayName","createdDateTime","groupType","transitiveUserCount","guestTransitiveUserCount"],
		orderby = ["createdDateTime desc"],
		top = 10,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.reports.identity_analytics.groups.get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#reports/identityAnalytics/groups(id,displayName,createdDateTime,groupType,transitiveUserCount,guestTransitiveUserCount)",
  "value": [
    {
      "id": "1f3a3b9c-6e2c-4f0a-9b2c-9a6d4d2e8f10",
      "displayName": "Sales Team",
      "createdDateTime": "2023-02-15T10:30:00Z",
      "groupType": "isCloudGroup",
      "transitiveUserCount": 412,
      "guestTransitiveUserCount": 7
    }
  ]
}
```
