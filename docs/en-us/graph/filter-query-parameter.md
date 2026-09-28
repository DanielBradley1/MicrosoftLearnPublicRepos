<!-- Source: https://learn.microsoft.com/en-us/graph/filter-query-parameter -->
<!-- Sitemap-Last-Modified: 2024-12-30 -->

# Use the $filter query parameter

Microsoft Graph supports the `$filter` [OData](http://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part2-url-conventions.html#_Toc31360955) query parameter to retrieve a subset of a collection.

The expression specified with `$filter` is evaluated for each resource in the collection, and only items where the expression evaluates to `true` are included in the response. Resources for which the expression evaluates to `false` or to `null`, or which reference properties that are unavailable due to permissions, are omitted from the response.

The `$filter` query parameter can also be applied against relationships like **members**, **memberOf**, **transitiveMembers**, and **transitiveMemberOf**. For example, "get all the security groups that I'm a member of".

## Operators and functions supported in filter expressions

Microsoft Graph supports the use of following operators and functions. However, support by individual resources and its properties or relationships varies. In addition, some properties and relationships support `$filter` only with [advanced queries](https://learn.microsoft.com/en-us/graph/aad-advanced-queries). See the specific resource documentation for details, and [Syntax for using the filter OData query parameter](#syntax-for-using-the-filter-odata-query-parameter) for examples of how to use these operators and functions. Also, [some limitations apply](https://learn.microsoft.com/en-us/graph/known-issues#some-limitations-apply-to-query-parameters).

| Operator type | Operator |
| --- | --- |
| Equality operators | - Equals \(`eq`\)<br>- Not equals \(`ne`\)<br>- Logical negation \(`not`\)<br>- In \(`in`\)<br>- Has \(`has`\)<br><br>  <br>  <br>**Note:** See [query parameter limitations in the known issues](https://learn.microsoft.com/en-us/graph/known-issues#some-limitations-apply-to-query-parameters) for limitations for `in` and `eq` operators. |
| Relational operators | - Less than \(`lt`\)<br>- Greater than \(`gt`\)<br>- Less than or equal to \(`le`\)<br>- Greater than or equal to \(`ge`\) |
| Lambda operators | - Any \(`any`\)<br>- All \(`all`\) |
| Conditional operators | - And \(`and`\)<br>- Or \(`or`\) |
| Functions | - Starts with \(`startswith`\)<br>- Ends with \(`endswith`\)<br>- Contains \(`contains`\) |

## Filter using lambda operators

OData defines the `any` and `all` operators to evaluate matches on multi-valued properties, that is, either collection of primitive values such as String types or collection of resources.

### `any` operator

The `any` operator iteratively applies a Boolean expression to each item of a collection and returns `true` if the expression is `true` for *at least one item* of the collection, otherwise it returns `false`. The following query string shows the syntax for the `any` operator:

```http
$filter=collection/any(property:property/subProperty eq 'value-to-match')
```

Where

- *collection* is the property that contains a collection of values or a collection of complex properties.
- *property:property* is the range variable that holds the current element of the collection during iteration. This variable can be named almost anything, for example, *p:p*.
- *subProperty* is required when the query applies to a collection of entities. It represents the property of the complex type whose value you're matching against.
- *value-to-match* represents the member of the collection against which you're matching.

The equivalent syntax in `C#` and `LINQ` is as follows:

```csharp
collection.Any(property => property.subProperty == "value-to-match")
```

For example, the **imAddresses** property of the `user` resource contains a collection of String primitive types. The following query retrieves only users with at least one imAddress of `admin@contoso.com`.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$filter=imAddresses/any(i:i eq 'admin@contoso.com')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "imAddresses/any(i:i eq 'admin@contoso.com')";
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


requestFilter := "imAddresses/any(i:i eq 'admin@contoso.com')"

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
	requestConfiguration.queryParameters.filter = "imAddresses/any(i:i eq 'admin@contoso.com')";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.filter('imAddresses/any(i:i eq \'admin@contoso.com\')')
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
$queryParameters->filter = "imAddresses/any(i:i eq 'admin@contoso.com')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -Filter "imAddresses/any(i:i eq 'admin@contoso.com')" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		filter = "imAddresses/any(i:i eq 'admin@contoso.com')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The **assignedLicenses** property of the `user` resource contains a collection of **assignedLicense** objects, a complex type with two properties, **skuId** and **disabledPlans**. The following query retrieves only users with at least one assigned license identified by the **skuId** `184efa21-98c3-4e5d-95ab-d07053a96e67`.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$filter=assignedLicenses/any(s:s/skuId eq 184efa21-98c3-4e5d-95ab-d07053a96e67)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "assignedLicenses/any(s:s/skuId eq 184efa21-98c3-4e5d-95ab-d07053a96e67)";
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


requestFilter := "assignedLicenses/any(s:s/skuId eq 184efa21-98c3-4e5d-95ab-d07053a96e67)"

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
	requestConfiguration.queryParameters.filter = "assignedLicenses/any(s:s/skuId eq 184efa21-98c3-4e5d-95ab-d07053a96e67)";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.filter('assignedLicenses/any(s:s/skuId eq 184efa21-98c3-4e5d-95ab-d07053a96e67)')
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
$queryParameters->filter = "assignedLicenses/any(s:s/skuId eq 184efa21-98c3-4e5d-95ab-d07053a96e67)";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -Filter "assignedLicenses/any(s:s/skuId eq 184efa21-98c3-4e5d-95ab-d07053a96e67)" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		filter = "assignedLicenses/any(s:s/skuId eq 184efa21-98c3-4e5d-95ab-d07053a96e67)",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

To negate the result of the expression inside the `any` clause, use the `not` operator, not the `ne` operator. For example, the following query retrieves only users who aren't assigned the **imAddress** of `admin@contoso.com`.

> **Note:** For directory objects like users, the `not` and `ne` operators are supported only in [advanced queries](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$filter=NOT(imAddresses/any(i:i eq 'admin@contoso.com'))&$count=true
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "NOT(imAddresses/any(i:i eq 'admin@contoso.com'))";
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


requestFilter := "NOT(imAddresses/any(i:i eq 'admin@contoso.com'))"
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
	requestConfiguration.queryParameters.filter = "NOT(imAddresses/any(i:i eq 'admin@contoso.com'))";
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
	.filter('NOT(imAddresses/any(i:i eq \'admin@contoso.com\'))')
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
$queryParameters->filter = "NOT(imAddresses/any(i:i eq 'admin@contoso.com'))";
$queryParameters->count = true;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -Filter "NOT(imAddresses/any(i:i eq 'admin@contoso.com'))" -CountVariable CountVar  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		filter = "NOT(imAddresses/any(i:i eq 'admin@contoso.com'))",
		count = True,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### `all` operator

The `all` operator applies a Boolean expression to each member of a collection and returns `true` if the expression is `true` for *all the items* of the collection, otherwise it returns `false`. Currently, it isn't supported in Microsoft Graph.

## Examples using the filter query operator

The following table shows some examples that use the `$filter` query parameter. For more information, see the [OData protocol](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part2-url-conventions/odata-v4.0-errata03-os-part2-url-conventions-complete.html#_Toc453752358).

Note

- Examples marked with <sup>\*\*</sup> are only supported with [advanced query capabilities](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).
- Click the HTTP method to try the examples in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

| Description | Example |
| :--- | :--- |
| Get all users with the name Mary across multiple properties. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users?$filter=startswith\(displayName,%27mary%27\)+or+startswith\(givenName,%27mary%27\)+or+startswith\(surname,%27mary%27\)+or+startswith\(mail,%27mary%27\)+or+startswith\(userPrincipalName,%27mary%27\)&method=GET&version=v1.0) `~/users?$filter=startswith(displayName,'mary') or startswith(givenName,'mary') or startswith(surname,'mary') or startswith(mail,'mary') or startswith(userPrincipalName,'mary')` |
| Get all users with mail domain equal to 'hotmail.com' | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24count%3Dtrue%26%24filter%3Dendswith\(mail%2C%27%40hotmail.com%27\)%26%24select%3Did%2CdisplayName%2Cmail&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$count=true&$filter=endswith(mail,'@hotmail.com')`<sup>[\*\*](#**)</sup> |
| Get all users without assigned licenses | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24filter%3DassignedLicenses%2F%24count%2Bne%2B0%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$filter=assignedLicenses/$count eq 0&$count=true`<sup>[\*\*](#**)</sup> |
| Get all the signed-in user's events that start after 7/1/2017. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/events?$filter=start/dateTime+ge+%272017-07-01T08:00%27&method=GET&version=v1.0) `~/me/events?$filter=start/dateTime ge '2017-07-01T08:00'`.  <br>**NOTE:** The **dateTime** property of the event entity is a String type. |
| Get all emails from a specific address received by the signed-in user. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/messages?$filter=from/emailAddress/address+eq+%27someuser@.com%27&method=GET&version=v1.0) `~/me/messages?$filter=from/emailAddress/address eq 'someuser@example.com'` |
| Get all emails received by the signed-in user in April 2017. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/mailFolders/inbox/messages?$filter=ReceivedDateTime+ge+2017-04-01+and+receivedDateTime+lt+2017-05-01&method=GET&version=v1.0) `~/me/mailFolders/inbox/messages?$filter=ReceivedDateTime ge 2017-04-01 and receivedDateTime lt 2017-05-01` |
| Get all unread mail in the signed-in user's Inbox. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me/mailFolders/inbox/messages?$filter=isRead+eq+false&method=GET&version=v1.0) `~/me/mailFolders/inbox/messages?$filter=isRead eq false` |
| Get all users in the Retail and Sales departments. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24filter%3Ddepartment%20in%20\(%27Retail%27%2C%20%27Sales%27\)&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) `~/users?$filter=department in ('Retail', 'Sales')` |
| List users with a particular service plan that is in a suspended state. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24filter%3DassignedPlans%2Fany\(a%3Aa%2FservicePlanId%20eq%202e2ddb96-6af9-4b1d-a3f0-d6ecfd22edb2%20and%20a%2FcapabilityStatus%20eq%20%27Suspended%27\)%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$filter=assignedPlans/any(a:a/servicePlanId eq 2e2ddb96-6af9-4b1d-a3f0-d6ecfd22edb2 and a/capabilityStatus eq 'Suspended')&$count=true`<sup>[\*\*](#**)</sup> |
| List all non-Microsoft 365 groups in an organization. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=groups%3F%24filter%3DNOT%20groupTypes%2Fany\(c%3Ac%20eq%20%27Unified%27\)%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/groups?$filter=NOT groupTypes/any(c:c eq 'Unified')&$count=true`<sup>[\*\*](#**)</sup> |
| List all users whose company name isn't undefined \(that is, not a `null` value\) or Microsoft. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24filter%3DcompanyName%20ne%20null%20and%20NOT\(companyName%20eq%20%27Microsoft%27\)%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$filter=companyName ne null and NOT(companyName eq 'Microsoft')&$count=true`<sup>[\*\*](#**)</sup> |
| List all users whose company name is either undefined or Microsoft. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=users%3F%24filter%3DcompanyName%20in%20\(null%2C%20%27Microsoft%27\)%26%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/users?$filter=companyName in (null, 'Microsoft')&$count=true`<sup>[\*\*](#**)</sup> |
| Use OData cast to get transitive membership in groups with a display name that starts with 'a' including a count of returned objects. | [GET](https://developer.microsoft.com/graph/graph-explorer?request=me%2FtransitiveMemberOf%2Fmicrosoft.graph.group%3F%24count%3Dtrue&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com&headers=W3sibmFtZSI6IkNvbnNpc3RlbmN5TGV2ZWwiLCJ2YWx1ZSI6ImV2ZW50dWFsIn1d) `~/me/transitiveMemberOf/microsoft.graph.group?$count=true&$filter=startswith(displayName, 'a')`<sup>[\*\*](#**)</sup> |

## Syntax for using the filter OData query parameter

The following article demonstrates the syntax for using the `$filter` OData query parameter and its associated operators. The examples are provided for guidance only and don't reflect a comprehensive list for the application of `$filter`.

Note

- GUID and DateTimeOffset values aren't enclosed in quotes in `$filter` expressions.

<sup>\*\*</sup> : This example is only supported with [advanced query capabilities](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

### For single primitive types like String, Int, and dates

| Operator | Syntax |
| --- | --- |
| `eq` | `~/users?$filter=userType eq 'Member'`  <br>  <br>`~/groups?$filter=isAssignableToRole eq true` |
| `not` | `~/users?$filter=not(userType eq 'Member')`<sup>[\*\*](#**)</sup> |
| `ne` | `~/users?$filter=companyName ne null`<sup>[\*\*](#**)</sup>  <br>  <br>`~/groups?$filter=isAssignableToRole ne true`<sup>[\*\*](#**)</sup> |
| `startswith` | `~/users?$filter=startswith(userPrincipalName, 'admin')` |
| `endswith` | `~/users?$filter=endswith(mail,'@outlook.com')`<sup>[\*\*](#**)</sup> |
| `in` | `~/users?$filter=mail in ('mail1@domain.com', 'mail2@domain.com')`  <br>  <br>**Note:** See [query parameter limitations in the known issues](https://learn.microsoft.com/en-us/graph/known-issues?search=13635) for limitations for `in` and `eq` operators. |
| `le` | `~/devices?$filter=registrationDateTime le 2021-01-02T12:00:00Z`<sup>[\*\*](#**)</sup> |
| `ge` | `~/devices?$filter=registrationDateTime ge 2021-01-02T12:00:00Z`<sup>[\*\*](#**)</sup> |
| `not` and `endswith` | `~/users?$filter=not(endswith(mail, 'contoso.com'))`<sup>[\*\*](#**)</sup> |
| `not` and `startswith` | `~/users?$filter=not(startswith(mail, 'A'))`<sup>[\*\*](#**)</sup> |
| `not` and `eq` | `~/users?$filter=not(companyName eq 'Contoso E.A.')`<sup>[\*\*](#**)</sup> |
| `not` and `in` | `~/users?$filter=not(userType in ('Member'))`<sup>[\*\*](#**)</sup> |
| `contains` | `~/identityGovernance/accessReviews/definitions?$filter=contains(scope/microsoft.graph.accessReviewQueryScope/query, './members')` |
| `has` | `~/identity/conditionalAccess/templates?$filter=scenarios has 'secureFoundation'` |

### For a collection of primitive types

| Operator \(s\) | Syntax |
| --- | --- |
| `eq` | `~/groups?$filter=groupTypes/any(c:c eq 'Unified')` |
| `not` | `~/groups?$filter=not(groupTypes/any(c:c eq 'Unified'))`<sup>[\*\*](#**)</sup> |
| `ne` | `~/users?$filter=companyName ne null`<sup>[\*\*](#**)</sup> |
| `startswith` | `~/users?$filter=businessPhones/any(p:startswith(p, '44'))`<sup>[\*\*](#**)</sup> |
| `endswith` | `~/users?$filter=endswith(mail,'@outlook.com')`<sup>[\*\*](#**)</sup> |
| `not` and `endswith` | `~/groups?$filter=not(endswith(mail,'contoso.com'))`<sup>[\*\*](#**)</sup> |
| `not` and `startswith` | `~/groups?$filter=not(startswith(mail,'Pineview'))`<sup>[\*\*](#**)</sup> |
| `not` and `eq` | `~/groups?$filter=not(mail eq 'PineviewSchoolStaff@Contoso.com')`<sup>[\*\*](#**)</sup> |
| `eq` and `$count` for empty collections | `~/users?$filter=assignedLicenses/$count eq 0`<sup>[\*\*](#**)</sup> |
| `ne` and `$count` for empty collections | `~/users?$filter=assignedLicenses/$count ne 0`<sup>[\*\*](#**)</sup> |
| `not` and `$count` for empty collections | `~/users?$filter=not(assignedLicenses/$count eq 0)`<sup>[\*\*](#**)</sup> |
| `$count` for collections with one object | `~/servicePrincipals?$filter=owners/$count eq 1`<sup>[\*\*](#**)</sup> |

### For GUID types

| Operator \(s\) | Syntax |
| --- | --- |
| `eq` | `~/servicePrincipals?$filter=appOwnerOrganizationId eq 72f988bf-86f1-41af-91ab-2d7cd011db47`<sup>[\*\*](#**)</sup> |
| `not` | `~/servicePrincipals?$filter=not(appOwnerOrganizationId eq 72f988bf-86f1-41af-91ab-2d7cd011db47)`<sup>[\*\*](#**)</sup> |

### For a collection of GUID types

| Operator \(s\) | Syntax |
| --- | --- |
| `eq` | `~/devices?$filter=alternativeSecurityIds/any(a:a/type eq 2)`<sup>[\*\*](#**)</sup> |
| `le` | `~/devices?$filter=alternativeSecurityIds/any(a:a/type le 2)`<sup>[\*\*](#**)</sup> |
| `ge` | `~/devices?$filter=alternativeSecurityIds/any(a:a/type ge 2)`<sup>[\*\*](#**)</sup> |

### For a collection of complex types

| Operator \(s\) | Syntax |
| --- | --- |
| `eq` | `~/users?$filter=certificateUserIds/any(x:x eq '9876543210@mil')`<sup>[\*\*](#**)</sup> |
| `not` and `eq` | `~/users?$filter=not(certificateUserIds/any(x:x eq '9876543210@mil'))`<sup>[\*\*](#**)</sup> |
| `startswith` | `~/users?$filter=certificateUserIds/any(x:startswith(x,'987654321'))`<sup>[\*\*](#**)</sup> |
| `endswith` | `~/users?$filter=proxyAddresses/any(p:endswith(p,'contoso.com'))`<sup>[\*\*](#**)</sup> |

## Related content

- [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries)
