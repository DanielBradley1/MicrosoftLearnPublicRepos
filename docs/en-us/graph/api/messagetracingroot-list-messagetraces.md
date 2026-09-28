<!-- Source: https://learn.microsoft.com/en-us/graph/api/messagetracingroot-list-messagetraces?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List messageTraces

Namespace: microsoft.graph

Get a list of [exchangeMessageTrace](https://learn.microsoft.com/en-us/graph/api/resources/exchangemessagetrace?view=graph-rest-1.0) objects.

Note

- Before you can use this API, ensure that the [Prerequisites](https://learn.microsoft.com/en-us/graph/api/resources/exchangemessagetrace?view=graph-rest-1.0#prerequisites) are met.
- This API has a throttling limit of 100 requests per 5 minutes. For more information, see [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ExchangeMessageTrace.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ExchangeMessageTrace.Read.All | Not available. |

## HTTP request

```http
GET /admin/exchange/tracing/messageTraces
```

## Optional query parameters

This method supports the `$filter`, `$top` and `$skiptoken` OData query parameters of the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

The default page size for this API is 1000 **exchangeMessageTrace** objects. Use `$top` to customize the page size, within the range of 1 and 5000. To get the next page of message traces, simply apply the entire URL returned in `@odata.nextLink` to the next get-messagetraces request. This URL includes any query parameters you may have specified in the initial request. For more information, see [Paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).

To retrieve message traces for a specific time period, filter on `receivedDateTime` by specifying both bounds: `$filter=receivedDateTime ge {startDateTime} and receivedDateTime le {endDateTime}`. The time interval must not exceed 10 days, `{startDateTime}` must not be more than 90 days before the current date, and `{endDateTime}` must not be later than the current date. Specify `{startDateTime}` and `{endDateTime}` as ISO 8601 format \(`YYYY-MM-DDThh:mm:ssZ`\).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [exchangeMessageTrace](https://learn.microsoft.com/en-us/graph/api/resources/exchangemessagetrace?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: List message traces

The following example shows how to retrieve the default top 1,000 message-trace information for the previous 48 hours, which is the default time period.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/admin/exchange/tracing/messageTraces
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Tracing.MessageTraces.GetAsync();
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
messageTraces, err := graphClient.Admin().Exchange().Tracing().MessageTraces().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeMessageTraceCollectionResponse result = graphClient.admin().exchange().tracing().messageTraces().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let messageTraces = await client.api('/admin/exchange/tracing/messageTraces')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->exchange()->tracing()->messageTraces()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.exchange.tracing.message_traces.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK        
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/exchange/tracing/messageTraces",
  "value": [
    {
      "id": "4451a062-48cb-e80d-e8c0-196330437ae6",
      "senderAddress": "sender@contoso.com",
      "recipientAddress": "recipient@contoso.com",
      "messageId": "<d9683b4c-127b-413a-ae2e-fa7dfb32c69d@contoso.com>",
      "receivedDateTime": "2025-06-13T10:30:00Z",
      "subject": "Quarterly Report",
      "size": 45678,
      "fromIP": "192.168.1.100",
      "toIP": "",
      "status": "delivered"
    }
  ]
}
```

### Example 2: Get message trace by message trace ID

The following example returns the message trace that matches the specified message trace ID \(the `id` property\).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/admin/exchange/tracing/messageTraces?$filter=id eq 'a3f6d2c1-5c3b-4f7a-9d1e-2c8f1b0a6e45'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Tracing.MessageTraces.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "id eq 'a3f6d2c1-5c3b-4f7a-9d1e-2c8f1b0a6e45'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)


requestFilter := "id eq 'a3f6d2c1-5c3b-4f7a-9d1e-2c8f1b0a6e45'"

requestParameters := &graphadmin.ExchangeTracingMessageTracesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphadmin.ExchangeTracingMessageTracesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messageTraces, err := graphClient.Admin().Exchange().Tracing().MessageTraces().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeMessageTraceCollectionResponse result = graphClient.admin().exchange().tracing().messageTraces().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "id eq 'a3f6d2c1-5c3b-4f7a-9d1e-2c8f1b0a6e45'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let messageTraces = await client.api('/admin/exchange/tracing/messageTraces')
	.filter('id eq \'a3f6d2c1-5c3b-4f7a-9d1e-2c8f1b0a6e45\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Exchange\Tracing\MessageTraces\MessageTracesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new MessageTracesRequestBuilderGetRequestConfiguration();
$queryParameters = MessageTracesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "id eq 'a3f6d2c1-5c3b-4f7a-9d1e-2c8f1b0a6e45'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->admin()->exchange()->tracing()->messageTraces()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.exchange.tracing.message_traces.message_traces_request_builder import MessageTracesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = MessageTracesRequestBuilder.MessageTracesRequestBuilderGetQueryParameters(
		filter = "id eq 'a3f6d2c1-5c3b-4f7a-9d1e-2c8f1b0a6e45'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.admin.exchange.tracing.message_traces.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK        
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/exchange/tracing/messageTraces",
  "value": [
    {
      "id": "a3f6d2c1-5c3b-4f7a-9d1e-2c8f1b0a6e45",
      "senderAddress": "sender@contoso.com",
      "recipientAddress": "recipient@contoso.com",
      "messageId": "<0d7f3a2b-6c1e-4f9a-9b9a-3c0a2b1c4d5e@contoso.com>",
      "receivedDateTime": "2026-01-18T10:30:00Z",
      "subject": "Daily report",
      "size": 45678,
      "fromIP": "203.0.113.10",
      "toIP": "",
      "status": "delivered"
    }
  ]
}
```

### Example 3: Retrieve message traces for a specific time period

The following example shows how to retrieve message trace information for messages between `2026-01-20T00:00:00Z` and `2026-01-23T00:00:00Z` \(UTC\) by filtering on `receivedDateTime`.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
GET https://graph.microsoft.com/v1.0/admin/exchange/tracing/messageTraces?$filter=receivedDateTime ge 2026-01-20T00:00:00Z and receivedDateTime le 2026-01-23T00:00:00Z
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Tracing.MessageTraces.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "receivedDateTime ge 2026-01-20T00:00:00Z and receivedDateTime le 2026-01-23T00:00:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)


requestFilter := "receivedDateTime ge 2026-01-20T00:00:00Z and receivedDateTime le 2026-01-23T00:00:00Z"

requestParameters := &graphadmin.ExchangeTracingMessageTracesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphadmin.ExchangeTracingMessageTracesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messageTraces, err := graphClient.Admin().Exchange().Tracing().MessageTraces().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeMessageTraceCollectionResponse result = graphClient.admin().exchange().tracing().messageTraces().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "receivedDateTime ge 2026-01-20T00:00:00Z and receivedDateTime le 2026-01-23T00:00:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let messageTraces = await client.api('/admin/exchange/tracing/messageTraces')
	.filter('receivedDateTime ge 2026-01-20T00:00:00Z and receivedDateTime le 2026-01-23T00:00:00Z')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Exchange\Tracing\MessageTraces\MessageTracesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new MessageTracesRequestBuilderGetRequestConfiguration();
$queryParameters = MessageTracesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "receivedDateTime ge 2026-01-20T00:00:00Z and receivedDateTime le 2026-01-23T00:00:00Z";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->admin()->exchange()->tracing()->messageTraces()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.exchange.tracing.message_traces.message_traces_request_builder import MessageTracesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = MessageTracesRequestBuilder.MessageTracesRequestBuilderGetQueryParameters(
		filter = "receivedDateTime ge 2026-01-20T00:00:00Z and receivedDateTime le 2026-01-23T00:00:00Z",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.admin.exchange.tracing.message_traces.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK        
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/exchange/tracing/messageTraces",
  "value": [
    {
      "id": "b7c1f4d2-9a6e-4c3b-8f2d-1e0a6c5b4d3f",
      "senderAddress": "sender@contoso.com",
      "recipientAddress": "recipient@contoso.com",
      "messageId": "<1f2e3d4c-5b6a-7980-9a0b-1c2d3e4f5a6b@contoso.com>",
      "receivedDateTime": "2026-01-21T14:12:34Z",
      "subject": "Monthly report",
      "size": 51234,
      "fromIP": "203.0.113.25",
      "toIP": "",
      "status": "delivered"
    }
  ]
}
```

### Example 4: List message traces by subject and recipient

The following example lists message traces for messages where the subject contains `Weekly digest` and the recipient address is `test@contoso.com`.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [Python](#tabpanel_4_python)

```http
GET https://graph.microsoft.com/v1.0/admin/exchange/tracing/messageTraces?$filter=contains(subject, 'Weekly digest') and recipientAddress eq 'test@contoso.com'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Tracing.MessageTraces.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "contains(subject, 'Weekly digest') and recipientAddress eq 'test@contoso.com'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)


requestFilter := "contains(subject, 'Weekly digest') and recipientAddress eq 'test@contoso.com'"

requestParameters := &graphadmin.ExchangeTracingMessageTracesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphadmin.ExchangeTracingMessageTracesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messageTraces, err := graphClient.Admin().Exchange().Tracing().MessageTraces().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExchangeMessageTraceCollectionResponse result = graphClient.admin().exchange().tracing().messageTraces().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "contains(subject, 'Weekly digest') and recipientAddress eq 'test@contoso.com'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let messageTraces = await client.api('/admin/exchange/tracing/messageTraces')
	.filter('contains(subject, \'Weekly digest\') and recipientAddress eq \'test@contoso.com\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Exchange\Tracing\MessageTraces\MessageTracesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new MessageTracesRequestBuilderGetRequestConfiguration();
$queryParameters = MessageTracesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "contains(subject, 'Weekly digest') and recipientAddress eq 'test@contoso.com'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->admin()->exchange()->tracing()->messageTraces()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.exchange.tracing.message_traces.message_traces_request_builder import MessageTracesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = MessageTracesRequestBuilder.MessageTracesRequestBuilderGetQueryParameters(
		filter = "contains(subject, 'Weekly digest') and recipientAddress eq 'test@contoso.com'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.admin.exchange.tracing.message_traces.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK        
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/exchange/tracing/messageTraces",
  "value": [
    {
      "id": "c1d2e3f4-5678-49ab-9cde-0123456789ab",
      "senderAddress": "sender@contoso.com",
      "recipientAddress": "test@contoso.com",
      "messageId": "<2a3b4c5d-6e7f-8091-a2b3-c4d5e6f78901@contoso.com>",
      "receivedDateTime": "2026-01-22T09:15:00Z",
      "subject": "Weekly digest: updates for your team",
      "size": 28765,
      "fromIP": "203.0.113.25",
      "toIP": "",
      "status": "delivered"
    }
  ]
}
```
