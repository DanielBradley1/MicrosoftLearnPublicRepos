<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# security: runHuntingQuery

Namespace: microsoft.graph.security

Queries a specified set of event, activity, or entity data supported by Microsoft 365 Defender to proactively look for specific threats in your environment.

This method is for advanced hunting in Microsoft 365 Defender. This method includes a query in Kusto Query Language \(KQL\). It specifies a data table in the [advanced hunting schema](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-schema-tables?view=o365-worldwide&preserve-view=true) and a piped sequence of operators to filter or search that data, and format the query output in specific ways.

Find out more about [hunting for threats across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-query-emails-devices?view=o365-worldwide&preserve-view=true). Learn about [KQL](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/).

For information on using advanced hunting in the [Microsoft 365 Defender portal](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-365-defender-portal?view=o365-worldwide&preserve-view=true), see [Proactively hunt for threats with advanced hunting in Microsoft 365 Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-overview?view=o365-worldwide&preserve-view=true).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ThreatHunting.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ThreatHunting.Read.All | Not available. |

## HTTP request

```http
POST /security/runHuntingQuery
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

Note

If you're using non-ANSI characters in your query, for example to query email subjects with malformed or lookalike characters, use `application/json; charset=utf-8` for the Content-Type header.

## Request body

In the request body, provide a JSON object with the `Query` property, and optionally include the `Timespan` and `workspaceId` properties.

| Parameter | Type | Description | Example |
| :--- | :--- | :--- | :--- |
| Query | String | Required. The hunting query in Kusto Query Language \(KQL\). For more information, see [KQL quick reference](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference). |  |
| Timespan | String | Optional. The interval of time over which to query data, in ISO 8601 format. The default value is 30 days, meaning if no startTime is specified, the query looks back 30 days from now. If a time filter is specified in both the query and the startTime parameter, the shorter time span is applied. For example, if the query has a filter for the last seven days and the startTime is 10 days ago, the query only looks back seven days. |  |
| workspaceId | Guid | Optional. The GUID of a specific Log Analytics workspace to target. If omitted, the service uses the caller's primary workspace. If the workspace isn't found or not accessible, the service falls back to the caller's primary workspace. | `00000000-0000-0000-0000-000000000001` |

The following examples show the possible formats for the `Timespan` parameter:

- **Date/Date**: "2024-02-01T08:00:00Z/2024-02-15T08:00:00Z" - Start and end dates.
- **Duration/endDate**: "P30D/2024-02-15T08:00:00Z" - A period before the end date.
- **Start/duration**: "2024-02-01T08:00:00Z/P30D" - Start date and duration.
- **ISO8601 duration**: "P30D" - Duration from now backwards.
- **Single date/time**: "2024-02-01T08:00:00Z" - Start time with end time defaulted to the current time.

## Response

If successful, this action returns a `200 OK` response code and a [huntingQueryResults](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingqueryresults?view=graph-rest-1.0) in the response body.

## Examples

### Example 1: Query with default timespan

#### Request

The following example specifies a KQL query and does the following:

- Looks into the [DeviceProcessEvents](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-deviceprocessevents-table?view=o365-worldwide&preserve-view=true) table in the advanced hunting schema.
- Filters on the condition that the powershell.exe process initiates the event.
- Specifies the output of three columns from the same table for each row: `Timestamp`, `FileName`, `InitiatingProcessFileName`.
- Sorts the output by the `Timestamp` value.
- Limits the output to two records \(two rows\).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/security/runHuntingQuery

{
    "Query": "DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.MicrosoftGraphSecurityRunHuntingQuery;

var requestBody = new RunHuntingQueryPostRequestBody
{
	Query = "DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.MicrosoftGraphSecurityRunHuntingQuery.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)

requestBody := graphsecurity.NewRunHuntingQueryPostRequestBody()
query := "DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
requestBody.SetQuery(&query) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityRunHuntingQuery, err := graphClient.Security().MicrosoftGraphSecurityRunHuntingQuery().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.microsoftgraphsecurityrunhuntingquery.RunHuntingQueryPostRequestBody runHuntingQueryPostRequestBody = new com.microsoft.graph.security.microsoftgraphsecurityrunhuntingquery.RunHuntingQueryPostRequestBody();
runHuntingQueryPostRequestBody.setQuery("DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2");
var result = graphClient.security().microsoftGraphSecurityRunHuntingQuery().post(runHuntingQueryPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const huntingQueryResults = {
    Query: 'DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2'
};

await client.api('/security/runHuntingQuery')
	.post(huntingQueryResults);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\MicrosoftGraphSecurityRunHuntingQuery\RunHuntingQueryPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RunHuntingQueryPostRequestBody();
$requestBody->setQuery('DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2');

$result = $graphServiceClient->security()->microsoftGraphSecurityRunHuntingQuery()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	Query = "DeviceProcessEvents | where InitiatingProcessFileName =~ "powershell.exe" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

Start-MgSecurityHuntingQuery -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.microsoft_graph_security_run_hunting_query.run_hunting_query_post_request_body import RunHuntingQueryPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RunHuntingQueryPostRequestBody(
	query = "DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2",
)

result = await graph_client.security.microsoft_graph_security_run_hunting_query.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.security.huntingQueryResults",
    "schema": [
        {
            "name": "Timestamp",
            "type": "DateTime"
        },
        {
            "name": "FileName",
            "type": "String"
        },
        {
            "name": "InitiatingProcessFileName",
            "type": "String"
        }
    ],
    "results": [
        {
            "Timestamp": "2024-03-26T09:39:50.7688641Z",
            "FileName": "cmd.exe",
            "InitiatingProcessFileName": "powershell.exe"
        },
        {
            "Timestamp": "2024-03-26T09:39:49.4353788Z",
            "FileName": "cmd.exe",
            "InitiatingProcessFileName": "powershell.exe"
        }
    ]
}
```

### Example 2: Query with optional the timespan parameter specified

#### Request

This example specifies a KQL query and looks into the [deviceProcessEvents](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-deviceprocessevents-table?view=o365-worldwide&preserve-view=true) table in the advanced hunting schema 60 days back.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/security/runHuntingQuery

{
    "Query": "DeviceProcessEvents",
    "Timespan": "P90D"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.MicrosoftGraphSecurityRunHuntingQuery;

var requestBody = new RunHuntingQueryPostRequestBody
{
	Query = "DeviceProcessEvents",
	Timespan = "P90D",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.MicrosoftGraphSecurityRunHuntingQuery.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)

requestBody := graphsecurity.NewRunHuntingQueryPostRequestBody()
query := "DeviceProcessEvents"
requestBody.SetQuery(&query) 
timespan := "P90D"
requestBody.SetTimespan(&timespan) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityRunHuntingQuery, err := graphClient.Security().MicrosoftGraphSecurityRunHuntingQuery().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.microsoftgraphsecurityrunhuntingquery.RunHuntingQueryPostRequestBody runHuntingQueryPostRequestBody = new com.microsoft.graph.security.microsoftgraphsecurityrunhuntingquery.RunHuntingQueryPostRequestBody();
runHuntingQueryPostRequestBody.setQuery("DeviceProcessEvents");
runHuntingQueryPostRequestBody.setTimespan("P90D");
var result = graphClient.security().microsoftGraphSecurityRunHuntingQuery().post(runHuntingQueryPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const huntingQueryResults = {
    Query: 'DeviceProcessEvents',
    Timespan: 'P90D'
};

await client.api('/security/runHuntingQuery')
	.post(huntingQueryResults);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\MicrosoftGraphSecurityRunHuntingQuery\RunHuntingQueryPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RunHuntingQueryPostRequestBody();
$requestBody->setQuery('DeviceProcessEvents');
$requestBody->setTimespan('P90D');

$result = $graphServiceClient->security()->microsoftGraphSecurityRunHuntingQuery()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	Query = "DeviceProcessEvents"
	Timespan = "P90D"
}

Start-MgSecurityHuntingQuery -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.microsoft_graph_security_run_hunting_query.run_hunting_query_post_request_body import RunHuntingQueryPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RunHuntingQueryPostRequestBody(
	query = "DeviceProcessEvents",
	timespan = "P90D",
)

result = await graph_client.security.microsoft_graph_security_run_hunting_query.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "schema": [
        {
            "name": "Timestamp",
            "type": "DateTime"
        },
        {
            "name": "FileName",
            "type": "String"
        },
        {
            "name": "InitiatingProcessFileName",
            "type": "String"
        }
    ],
    "results": [
        {
            "timestamp": "2020-08-30T06:38:35.7664356Z",
            "fileName": "conhost.exe",
            "initiatingProcessFileName": "powershell.exe"
        },
        {
            "timestamp": "2020-08-30T06:38:30.5163363Z",
            "fileName": "conhost.exe",
            "initiatingProcessFileName": "powershell.exe"
        }
    ]
}
```
