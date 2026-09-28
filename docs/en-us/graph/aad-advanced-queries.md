<!-- Source: https://learn.microsoft.com/en-us/graph/aad-advanced-queries -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# Advanced query capabilities on Microsoft Entra ID objects

Microsoft Graph supports advanced query capabilities on various Microsoft Entra ID objects, also called *directory objects*, to help you efficiently access data. Examples include the addition of **not** \(`not`\), **not equals** \(`ne`\), and **ends with** \(`endsWith`\) operators on the `$filter` query parameter.

The Microsoft Graph query engine uses an index store to fulfill query requests. To add support for extra query capabilities on some properties, those properties are indexed in a separate store. This separate indexing improves query performance. However, these advanced query capabilities aren't available by default. The requestor must set the **ConsistencyLevel** header to `eventual` *and*, except for `$search`, use the `$count` query parameter. The **ConsistencyLevel** header and `$count` are referred to as *advanced query parameters*.

For example, to retrieve only inactive user accounts, you can run either of these queries that use the `$filter` query parameter:

**Option 1:** Use the `$filter` query parameter with the `eq` operator. This request works by default and doesn't require the advanced query parameters.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$filter=accountEnabled eq false
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "accountEnabled eq false";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestFilter := "accountEnabled eq false"

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserCollectionResponse result = graphClient.users().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "accountEnabled eq false";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.filter('accountEnabled eq false')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "accountEnabled eq false";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -Filter "accountEnabled eq false" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		filter = "accountEnabled eq false",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

**Option 2:** Use the `$filter` query parameter with the `ne` operator. This request isn't supported by default because the `ne` operator is only supported in advanced queries. Therefore, you must add the **ConsistencyLevel** header set to `eventual` *and* use the `$count=true` query string.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$filter=accountEnabled ne true&$count=true
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "accountEnabled ne true";
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestFilter := "accountEnabled ne true"
requestCount := true

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Count: &requestCount,
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserCollectionResponse result = graphClient.users().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "accountEnabled ne true";
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.header('ConsistencyLevel','eventual')
	.filter('accountEnabled ne true')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "accountEnabled ne true";
$queryParameters->count = true;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -Filter "accountEnabled ne true" -CountVariable CountVar  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		filter = "accountEnabled ne true",
		count = True,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Microsoft Entra ID \(directory\) objects that support advanced query capabilities

Advanced query capabilities are supported only on directory objects and their relationships, including the following objects:

| Object | Relationships |
| --- | --- |
| [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit) | <li><a href="https://learn.microsoft.com/en-us/graph/api/administrativeunit-list-members" data-linktype="absolute-path">members</a></li> |
| [application](https://learn.microsoft.com/en-us/graph/api/resources/application) | <li><a href="https://learn.microsoft.com/en-us/graph/api/application-list-owners" data-linktype="absolute-path">owners</a></li> |
| [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment) | - |
| [device](https://learn.microsoft.com/en-us/graph/api/resources/device) | <li><a href="https://learn.microsoft.com/en-us/graph/api/device-list-memberof" data-linktype="absolute-path">memberOf</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/device-list-transitivememberof" data-linktype="absolute-path">transitiveMemberOf</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/device-list-registeredusers" data-linktype="absolute-path">registeredUsers</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/device-list-registeredowners" data-linktype="absolute-path">registeredOwners</a></li> |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group) | <li><a href="https://learn.microsoft.com/en-us/graph/api/group-list-members" data-linktype="absolute-path">members</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/group-list-transitivemembers" data-linktype="absolute-path">transitiveMembers</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/group-list-memberof" data-linktype="absolute-path">memberOf</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/group-list-transitivememberof" data-linktype="absolute-path">transitiveMemberOf</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/group-list-owners" data-linktype="absolute-path">owners</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/group-list-approleassignments" data-linktype="absolute-path">appRoleAssignments</a></li> |
| [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant) \(delegated permission grants\) | - |
| [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgContact) | <li><a href="https://learn.microsoft.com/en-us/graph/api/orgcontact-list-memberof" data-linktype="absolute-path">memberOf</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/orgcontact-list-transitiveMemberOf" data-linktype="absolute-path">transitiveMemberOf</a></li> |
| [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal) | <li><a href="https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-memberof" data-linktype="absolute-path">memberOf</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-owners" data-linktype="absolute-path">owners</a></li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-transitivememberof" data-linktype="absolute-path">transitiveMemberOf</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignments" data-linktype="absolute-path">appRoleAssignments</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignedto" data-linktype="absolute-path">appRoleAssignedTo</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-oauth2permissiongrants" data-linktype="absolute-path">oAuth2PermissionGrant</a></li> |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user) | <li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-memberof" data-linktype="absolute-path">memberOf</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-transitivememberof" data-linktype="absolute-path">transitiveMemberOf</a></li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-ownedobjects" data-linktype="absolute-path">ownedObjects</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-registereddevices" data-linktype="absolute-path">registeredDevices</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-owneddevices" data-linktype="absolute-path">ownedDevices</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-manager" data-linktype="absolute-path">transitiveManagers</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-directreports" data-linktype="absolute-path">directReports</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-get-transitivereports" data-linktype="absolute-path">transitiveReports</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-approleassignments" data-linktype="absolute-path">appRoleAssignments</a> </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/user-list-oauth2permissiongrants" data-linktype="absolute-path">oAuth2PermissionGrant</a></li> |

Note

Use of `$filter` on the relationships of the preceding list of directory objects is supported only with advanced query parameters. However, in such cases, don't use `$expand` in the same request because it isn't supported with advanced query parameters.

## Query scenarios that require advanced query capabilities

The following table lists query scenarios on directory objects that advanced queries support:

| Description | Example |
| :--- | :--- |
| Use of `$count` as a URL segment | [GET](https://developer.microsoft.com/graph/graph-explorer?request=groups%2F%24count&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/groups/$count` |
| Use of `$count` as a query string parameter | [GET](https://developer.microsoft.com/graph/graph-explorer?request=servicePrincipals%3F%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/servicePrincipals?$count=true` |
| Use of `$count` in a `$filter` expression | [GET](https://developer.microsoft.com/en-us/graph/graph-explorer?request=users%3F%24filter%3DassignedLicenses%2F%24count%2Bne%2B0%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$filter=assignedLicenses/$count eq 0&$count=true` |
| Use of `$search` | [GET](https://developer.microsoft.com/graph/graph-explorer?request=applications%3F%24search%3D%22displayName%3ABrowser%22&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/applications?$search="displayName:Browser"` |
| Use of `$orderby` on select properties | [GET](https://developer.microsoft.com/graph/graph-explorer?request=applications%3F%24orderby%3DdisplayName%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/applications?$orderby=displayName&$count=true` |
| Use of `$filter` with the `endsWith` operator | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24count%3Dtrue%26%24filter%3DendsWith\(mail%2C%27%40outlook.com%27\)&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$count=true&$filter=endsWith(mail,'@outlook.com')` |
| Use of `$filter` and `$orderby` in the same query | [GET](https://developer.microsoft.com/graph/graph-explorer?request=applications%3F%24orderby%3DdisplayName%26%24filter%3DstartsWith\(displayName%2C%20%27Box%27\)%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `../applications?$orderby=displayName&$filter=startsWith(displayName, 'Box')&$count=true` |
| Use of `$filter` with the `startsWith` operators on specific properties. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24filter%3DstartsWith\(mobilePhone%2C%20%2725478%27\)%20OR%20startsWith\(mobilePhone%2C%20%2725473%27\)%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$filter=startsWith(mobilePhone, '25478') OR startsWith(mobilePhone, '25473')&$count=true` |
| Use of `$filter` with `ne` and `not` operators | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24filter%3DcompanyName%20ne%20null%20and%20NOT\(companyName%20eq%20%27Microsoft%27\)%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$filter=companyName ne null and NOT(companyName eq 'Microsoft')&$count=true` |
| Use of `$filter` with `not` and `startsWith` operators | [GET](https://developer.microsoft.com/graph/graph-explorer?request=%2Fusers%3F%24filter%3DNOT%20startsWith\(displayName%2C%20%27Conf%27\)%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$filter=NOT startsWith(displayName, 'Conf')&$count=true` |
| Use of `$filter` on a collection with `endsWith` operator | [GET](https://developer.microsoft.com/en-us/graph/graph-explorer?request=users%3F%24count%3Dtrue%26%24filter%3DproxyAddresses%2Fany\(p%3AendsWith\(p%2C%2B%27contoso.com%27\)\)%26select%3Did%2CdisplayName%2Cproxyaddresses&method=GET&version=beta&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$count=true&$filter=proxyAddresses/any (p:endsWith(p, 'contoso.com'))&$select=id,displayName,proxyaddresses` |
| Use of OData cast with transitive members list | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me%2FtransitiveMemberOf%2Fmicrosoft.graph.group%3F%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/me/transitiveMemberOf/microsoft.graph.group?$count=true` |

Note

- You can use `$filter` and `$orderby` together only with advanced queries.
- Advanced queries don't currently support `$expand`.
- Azure AD B2C tenants don't currently support advanced query capabilities.
- To use advanced query capabilities in [batch requests](https://learn.microsoft.com/en-us/graph/json-batching), specify the **ConsistencyLevel** header in the JSON body of the `POST` request.

## Support for filter by properties of Microsoft Entra ID \(directory\) objects

Properties of directory objects behave differently in their support for query parameters. The following are common scenarios for directory objects:

- The `in` operator is supported by default whenever `eq` operator is supported by default.
- The `endswith` operator is supported only with advanced query parameters and only by **mail**, **otherMails**, **userPrincipalName**, and **proxyAddresses** properties.
- Getting empty collections \(`/$count eq 0`, `/$count ne 0`\) and collections with less than one object \(`/$count eq 1`, `/$count ne 1`\) is supported only with advanced query parameters.
- The `not` and `ne` negation operators are supported only with advanced query parameters.

  - All properties that support the `eq` operator also supports the `ne` or `not` operators.
  - For queries that use the `any` lambda operator, use the `not` operator. See [Filter using lambda operators](https://learn.microsoft.com/en-us/graph/filter-query-parameter#filter-using-lambda-operators).

The following tables summarize support for `$filter` operators by properties of directory objects, and indicates where querying is supported through advanced query capabilities.

### Legend

- ![Filter works by default. Doesn't require advanced query parameters but still works with advanced query parameters.](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) The `$filter` operator works by default for that property.
- ![Filter only works without advanced query parameters.](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/checkmark-circle-green.svg) The `$filter` operator only works *without* advanced query parameters.
- ![Filter requires advanced query parameters.](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg) The `$filter` operator **requires** *advanced query parameters*, which are:

  - `ConsistencyLevel=eventual` header
  - `$count=true` query string

- ![Not supported.](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg) The `$filter` operator isn't supported on that property. [Send us feedback](https://aka.ms/MsGraphAADSurveyDocs) to request that this property support `$filter` for your scenarios.
- Blank cells indicate that the query isn't valid for that property.
- The **null value** column indicates that the property is nullable and filterable using `null`.
- Properties that aren't listed here don't support `$filter` at all.

## Administrative unit properties

| Property | eq | startsWith | eq Null |
| --- | --- | --- | --- |
| description | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| isMemberManagementRestricted | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| membershipRule | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |
| membershipRuleProcessingState | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |

## Application properties

| Property | eq | startsWith | ge/le | eq Null |
| --- | --- | --- | --- | --- |
| appId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| createdDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| description | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| disabledByMicrosoftStatus | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| federatedIdentityCredentials/any\(f:f/issuer\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| federatedIdentityCredentials/any\(f:f/name\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| federatedIdentityCredentials/any\(f:f/subject\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| identifierUris/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| info/logoUrl |  |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| info/termsOfServiceUrl | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| notes | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| publicClient/redirectUris/any\(p:p\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| publisherDomain | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| requiredResourceAccess/any\(r:r/resourceAppId\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| serviceManagementReference | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| signInAudience | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| spa/redirectUris/any\(p:p\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| tags/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| uniqueName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| verifiedPublisher/displayName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| web/homePageUrl | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| web/redirectUris/any\(p:p\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |

The following properties of the application entity support `$count` of a collection in a filter expression.

| Property | eq Count 0 | eq Count 1 |
| --- | --- | --- |
| extensionProperties/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| federatedIdentityCredentials/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |

## Contract properties

| Property | eq | startsWith |
| --- | --- | --- |
| customerId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |
| defaultDomainName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |

## Device properties

| Property | eq | startsWith | ge/le | eq Null |
| --- | --- | --- | --- | --- |
| accountEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| alternativeSecurityIds/any\(a:a/identityProvider\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| alternativeSecurityIds/any\(a:a/type\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| approximateLastSignInDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| deviceCategory | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| deviceId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| deviceOwnership | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| enrollmentProfileName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| extensionAttributes/extensionAttribute1-15 | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| hostnames/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| isCompliant | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| isManaged | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| isRooted | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| managementType | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| manufacturer | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| mdmAppId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| model | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| onPremisesLastSyncDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |
| onPremisesSecurityIdentifier | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| onPremisesSyncEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| operatingSystem | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| operatingSystemVersion | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| physicalIds/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| profileType | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| registrationDateTime |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| trustType | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |

The following properties of the **device** entity support `$count` of a collection in a filter expression.

| Property | eq Count 0 | eq Count 1 |
| --- | --- | --- |
| physicalIds/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| systemLabels/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |

## Directory role properties

| Property | eq | startsWith | eq Null |
| --- | --- | --- | --- |
| description | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| roleTemplateId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |

## Group properties

| Property | eq | startsWith | ge/le | eq Null |
| --- | --- | --- | --- | --- |
| assignedLicenses/any\(a:a/skuId\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| classification | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| createdByAppId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| createdDateTime |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| description | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| expirationDateTime |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |
| groupTypes/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| hasMembersWithLicenseErrors | ![DefaultOnly](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/checkmark-circle-green.svg "DefaultOnly") |  |  | ![DefaultOnly](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/checkmark-circle-green.svg "DefaultOnly") |
| infoCatalogs/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| isAssignableToRole | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| mail | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| mailEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| mailNickname | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| membershipRule | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| membershipRuleProcessingState | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesLastSyncDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |
| onPremisesProvisioningErrors/any\(o:o/category\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesProvisioningErrors/any\(o:o/propertyCausingError\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesSamAccountName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| onPremisesSecurityIdentifier | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| onPremisesSyncEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| preferredLanguage | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| proxyAddresses/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| renewedDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |
| resourceBehaviorOptions/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| resourceProvisioningOptions/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| securityEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| uniqueName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |

The following properties of the **group** entity support `$count` of a collection in a filter expression.

| Property | eq Count 0 | eq Count 1 |
| --- | --- | --- |
| assignedLicenses/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| onPremisesProvisioningErrors/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| proxyAddresses/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |

## Organizational contact properties

| Property | eq | startsWith | ge/le | eq Null |
| --- | --- | --- | --- | --- |
| companyName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| department | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| givenName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| jobTitle | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| mail | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| mailNickname | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| manager/id | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesLastSyncDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |
| onPremisesProvisioningErrors/any\(o:o/category\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesProvisioningErrors/any\(o:o/propertyCausingError\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesSyncEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| proxyAddresses/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| surname | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |

The following properties of the **orgContact** entity support `$count` of a collection in a filter expression.

| Property | eq Count 0 | eq Count 1 |
| --- | --- | --- |
| onPremisesProvisioningErrors/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| proxyAddresses/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |

## Service principal properties

| Property | eq | startsWith | ge/le | eq Null |
| --- | --- | --- | --- | --- |
| accountEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| alternativeNames/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| appId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| appOwnerOrganizationId | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| appRoleAssignmentRequired | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| applicationTemplateId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| claimsPolicy/id | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| createdObjects/any\(c:c/id\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| description | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| federatedIdentityCredentials/any\(f:f/issuer\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| federatedIdentityCredentials/any\(f:f/name\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| federatedIdentityCredentials/any\(f:f/subject\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| homepage | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| info/logoUrl |  |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| info/termsOfServiceUrl | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| notes | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| preferredSingleSignOnMode | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| preferredTokenSigningKeyEndDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |
| publisherName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| remoteDesktopSecurityConfiguration/id | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| servicePrincipalNames/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| servicePrincipalType | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| tags/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| verifiedPublisher/displayName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |

The following properties of the **servicePrincipal** entity support `$count` of a collection in a filter expression.

| Property | eq Count 0 | eq Count 1 |
| --- | --- | --- |
| federatedIdentityCredentials/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |

## User properties

| Property | eq | startsWith | ge/le | eq Null |
| --- | --- | --- | --- | --- |
| accountEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| ageGroup | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| assignedLicenses/any\(a:a/skuId\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| assignedPlans/any\(a:a/capabilityStatus\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| assignedPlans/any\(a:a/service\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| assignedPlans/any\(a:a/servicePlanId\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| authorizationInfo/certificateUserIds/any\(p:p\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| businessPhones/any\(p:p\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| city | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| cloudRealtimeCommunicationInfo/isSipEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| companyName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| consentProvidedForMinor | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| country | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| createdDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| createdObjects/any\(c:c/id\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| creationType | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| department | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| displayName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| employeeHireDate |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |
| employeeId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| employeeOrgData/costCenter | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| employeeOrgData/division | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| employeeType | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| externalUserState | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| faxNumber | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| givenName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| identities/any\(i:i/issuer\) | ![DefaultOnly](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/checkmark-circle-green.svg "DefaultOnly") |  |  | ![DefaultOnly](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/checkmark-circle-green.svg "DefaultOnly") |
| imAddresses/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| infoCatalogs/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| isLicenseReconciliationNeeded | ![DefaultOnly](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/checkmark-circle-green.svg "DefaultOnly") |  |  |  |
| isResourceAccount | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| jobTitle | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| mail | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| mailNickname | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| mobilePhone | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| officeLocation | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| onPremisesDistinguishedName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| onPremisesExtensionAttributes/extensionAttribute1-15 | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| onPremisesImmutableId | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesLastSyncDateTime |  |  | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |
| onPremisesProvisioningErrors/any\(o:o/category\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesProvisioningErrors/any\(o:o/propertyCausingError\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |  |
| onPremisesSamAccountName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| onPremisesSecurityIdentifier | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| onPremisesSipInfo/isSipEnabled | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| onPremisesSyncEnabled | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| otherMails/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| passwordPolicies |  |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| passwordProfile/forceChangePasswordNextSignIn | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| passwordProfile/forceChangePasswordNextSignInWithMfa | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| postalCode | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| preferredLanguage | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| provisionedPlans/any\(p:p/provisioningStatus\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |  |
| provisionedPlans/any\(p:p/service\) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  |  |
| proxyAddresses/any\(p:p\) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| state | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| streetAddress | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| surname | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| usageLocation | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| userPrincipalName | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  |
| userType | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") |  |  | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |

The following properties of the **user** entity support `$count` of a collection in a filter expression.

| Property | eq Count 0 | eq Count 1 |
| --- | --- | --- |
| assignedLicenses/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| onPremisesProvisioningErrors/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| otherMails/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| ownedObjects/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| proxyAddresses/$count | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |

The following table shows support for `$filter` by other extension properties on the **user** object.

| Extension type | eq | startsWith | eq null |
| --- | --- | --- | --- |
| [Schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview#schema-extensions) | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| [Open extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview#open-extensions) | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |
| [Directory extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview#directory-azure-ad-extensions) | ![Default+Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default+Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |

## Support for sorting by properties of Microsoft Entra ID \(directory\) objects

The following table summarizes support for `$orderby` by properties of directory objects and indicates where sorting is supported through advanced query capabilities.

### Legend

- ![Sorting works by default. Does not require advanced query parameters.](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg) The `$orderby` operator works by default for that property.
- ![Sorting requires advanced query parameters.](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg) The `$orderby` operator **requires** *advanced query parameters*, which are:

  - `ConsistencyLevel=eventual` header
  - `$count=true` query string

- Use of `$filter` and `$orderby` in the same query for directory objects always requires advanced query parameters. For more information, see [Query scenarios that require advanced query capabilities](#query-scenarios-that-require-advanced-query-capabilities).

| Directory object | Property name | $orderby |
| --- | --- | --- |
| administrativeUnit | createdDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| administrativeUnit | deletedDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| administrativeUnit | displayName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| application | createdDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| application | deletedDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| application | displayName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| orgContact | createdDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| orgContact | displayName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| device | approximateLastSignInDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| device | createdDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| device | deletedDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| device | displayName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| group | createdDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| group | deletedDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| group | displayName | ![Default](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default") |
| servicePrincipal | createdDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| servicePrincipal | deletedDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| servicePrincipal | displayName | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| user | createdDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| user | deletedDateTime | ![Advanced](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/whitecheck-in-greencircle.svg "Advanced") |
| user | displayName | ![Default](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default") |
| user | userPrincipalName | ![Default](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/greencheck.svg "Default") |
| \[*all others*\] | \[*all others*\] | ![NotSupported](https://learn.microsoft.com/en-us/graph/images/yesandnosymbols/no.svg "NotSupported") |

## Error handling for advanced queries on directory objects

The following section provides examples of common error scenarios when you don't use advanced query parameters where required.

You can count directory objects only by using the advanced queries parameters. If you don't specify the `ConsistencyLevel=eventual` header, the request returns an error when you use the `$count` URL segment \(`/$count`\) or silently ignores the `$count` query parameter \(`?$count=true`\) if you use it.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/$count
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users.Count.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().Count().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().count().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let int32 = await client.api('/users/$count')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->users()->count()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUserCount
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.users.count.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```json
{
    "error": {
        "code": "Request_BadRequest",
        "message": "$count is not currently supported.",
        "innerError": {
            "date": "2021-05-18T19:03:10",
            "request-id": "d9bbd4d8-bb2d-44e6-99a1-71a9516da744",
            "client-request-id": "539da3bd-942f-25db-636b-27f6f6e8eae4"
        }
    }
}
```

For directory objects, `$search` works only in advanced queries. If you don't specify the **ConsistencyLevel** header, the request returns an error.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/applications?$search="displayName:Browser"
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Search = "\"displayName:Browser\"";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphapplications "github.com/microsoftgraph/msgraph-sdk-go/applications"
	  //other-imports
)


requestSearch := "\"displayName:Browser\""

requestParameters := &graphapplications.ApplicationsRequestBuilderGetQueryParameters{
	Search: &requestSearch,
}
configuration := &graphapplications.ApplicationsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApplicationCollectionResponse result = graphClient.applications().get(requestConfiguration -> {
	requestConfiguration.queryParameters.search = "\"displayName:Browser\"";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let applications = await client.api('/applications')
	.search('displayName:Browser')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Applications\ApplicationsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ApplicationsRequestBuilderGetRequestConfiguration();
$queryParameters = ApplicationsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->search = "\"displayName:Browser\"";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->applications()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgApplication -Search '"displayName:Browser"' 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.applications.applications_request_builder import ApplicationsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ApplicationsRequestBuilder.ApplicationsRequestBuilderGetQueryParameters(
		search = "\"displayName:Browser\"",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.applications.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```json
{
    "error": {
        "code": "Request_UnsupportedQuery",
        "message": "Request with $search query parameter only works through MSGraph with a special request header: 'ConsistencyLevel: eventual'",
        "innerError": {
            "date": "2021-05-27T14:26:47",
            "request-id": "9b600954-ba11-4899-8ce9-6abad341f299",
            "client-request-id": "7964ef27-13a3-6ca4-ed7b-73c271110867"
        }
    }
}
```

If a property or query parameter in the URL supports only advanced queries but either the **ConsistencyLevel** header or the `$count=true` query string is missing, the request returns an error.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/beta/users?$filter=endsWith(userPrincipalName,'%23EXT%23@contoso.com')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "endsWith(userPrincipalName,'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)


requestFilter := "endsWith(userPrincipalName,'"

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserCollectionResponse result = graphClient.users().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "endsWith(userPrincipalName,'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "endsWith(userPrincipalName,'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Users

Get-MgBetaUser -Filter "endsWith(userPrincipalName,'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		filter = "endsWith(userPrincipalName,'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```json
{
    "error": {
        "code": "Request_UnsupportedQuery",
        "message": "Operator 'endsWith' is not supported because the required parameters might be missing. Try adding $count=true query parameter and ConsistencyLevel:eventual header. Refer to https://aka.ms/graph-docs/advanced-queries for more information",
        "innerError": {
            "date": "2023-07-14T08:43:39",
            "request-id": "b3731da7-5c46-4c37-a8e5-b190124d2531",
            "client-request-id": "a1556ddf-4794-929d-0105-b753a78b4c68"
        }
    }
}
```

If a property isn't indexed to support a query parameter, the request returns an error even if advanced query parameters are specified. For example, the **createdDateTime** property of the **group** resource isn't indexed for query capabilities.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```msgraph
GET https://graph.microsoft.com/beta/groups?$filter=createdDateTime ge 2021-11-01&$count=true
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "createdDateTime ge 2021-11-01";
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-beta-sdk-go/groups"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestFilter := "createdDateTime ge 2021-11-01"
requestCount := true

requestParameters := &graphgroups.GroupsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Count: &requestCount,
}
configuration := &graphgroups.GroupsRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupCollectionResponse result = graphClient.groups().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "createdDateTime ge 2021-11-01";
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let groups = await client.api('/groups')
	.version('beta')
	.header('ConsistencyLevel','eventual')
	.filter('createdDateTime ge 2021-11-01')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Groups\GroupsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GroupsRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = GroupsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "createdDateTime ge 2021-11-01";
$queryParameters->count = true;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->groups()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Groups

Get-MgBetaGroup -Filter "createdDateTime ge 2021-11-01" -CountVariable CountVar  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.groups.groups_request_builder import GroupsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GroupsRequestBuilder.GroupsRequestBuilderGetQueryParameters(
		filter = "createdDateTime ge 2021-11-01",
		count = True,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.groups.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```json
{
    "error": {
        "code": "Request_UnsupportedQuery",
        "message": "Unsupported or invalid query filter clause specified for property 'createdDateTime' of resource 'Group'.",
        "innerError": {
            "date": "2023-07-14T08:42:44",
            "request-id": "b6a5f998-94c8-430d-846d-2eaae3031492",
            "client-request-id": "2be83e05-649e-2508-bcd9-62e666168fc8"
        }
    }
}
```

However, a request that includes query parameters might fail silently. For example, the request might fail for unsupported query parameters and for unsupported combinations of query parameters. In these cases, examine the data returned by the request to determine whether the query parameters you specified had the desired effect. For example, in the following example, the `@odata.count` parameter is missing even if the query is successful.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$count=true
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestCount := true

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Count: &requestCount,
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserCollectionResponse result = graphClient.users().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -CountVariable CountVar 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		count = True,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#users",
  "value":[
    {
      "displayName":"Oscar Ward",
      "mail":"oscarward@contoso.com",
      "userPrincipalName":"oscarward@contoso.com"
    }
  ]
}
```

## Related content

- [Use query parameters to customize responses](https://learn.microsoft.com/en-us/graph/query-parameters)
- [Query parameter limitations](https://learn.microsoft.com/en-us/graph/known-issues#some-limitations-apply-to-query-parameters)
- [Use the $search query parameter to match a search criterion](https://learn.microsoft.com/en-us/graph/search-query-parameter#using-search-on-directory-object-collections)
- [Explore advanced query capabilities for Microsoft Entra ID objects with the .NET SDK](https://github.com/microsoftgraph/dotnet-aad-query-sample/)
