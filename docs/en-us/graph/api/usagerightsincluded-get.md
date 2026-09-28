<!-- Source: https://learn.microsoft.com/en-us/graph/api/usagerightsincluded-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-07 -->

# Get usageRightsIncluded

Namespace: microsoft.graph

Get the usage rights granted to the calling user for a specific sensitivity label that has admin-defined permissions.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SensitivityLabel.Read | SensitivityLabels.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SensitivityLabel.Read | SensitivityLabels.Read.All |

## HTTP request

```http
GET /security/dataSecurityAndGovernance/sensitivityLabels/{labelId}/rights
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Client-Request-Id | Optional. A client-generated GUID to trace the request. Recommended for troubleshooting. |

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [usageRights](https://learn.microsoft.com/en-us/graph/api/resources/usagerights?view=graph-rest-1.0) enum values in the response body, representing the rights granted to the user for the specified label.

If the label is not found, doesn't have admin-defined protection, or the user doesn't have the `VIEW` right, the API might return an error response \(for example, `403 Forbidden` or `404 Not Found`\) with details in an [error object](https://learn.microsoft.com/en-us/graph/errors).

## Examples

Request to get the rights for a specific sensitivity label `4e4234dd-377b-42a3-935b-0e42f138fa23` for the user.

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/security/dataSecurityAndGovernance/sensitivityLabels/4e4234dd-377b-42a3-935b-0e42f138fa23/rights?ownerEmail=bob@contoso.com
Authorization: Bearer {token}
Client-Request-Id: 7c9b1b4c-5b5a-4e3e-9f1b-2d9b0b4a9a0a
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.DataSecurityAndGovernance.SensitivityLabels["{sensitivityLabel-id}"].Rights.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.OwnerEmail = "bob@contoso.com";
	requestConfiguration.Headers.Add("Authorization", "Bearer {token}");
	requestConfiguration.Headers.Add("Client-Request-Id", "7c9b1b4c-5b5a-4e3e-9f1b-2d9b0b4a9a0a");
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
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Authorization", "Bearer {token}")
headers.Add("Client-Request-Id", "7c9b1b4c-5b5a-4e3e-9f1b-2d9b0b4a9a0a")


requestOwnerEmail := "bob@contoso.com"

requestParameters := &graphsecurity.DataSecurityAndGovernanceSensitivityLabelsItemRightsRequestBuilderGetQueryParameters{
	OwnerEmail: &requestOwnerEmail,
}
configuration := &graphsecurity.DataSecurityAndGovernanceSensitivityLabelsItemRightsRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rights, err := graphClient.Security().DataSecurityAndGovernance().SensitivityLabels().BySensitivityLabelId("sensitivityLabel-id").Rights().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UsageRightsIncluded result = graphClient.security().dataSecurityAndGovernance().sensitivityLabels().bySensitivityLabelId("{sensitivityLabel-id}").rights().get(requestConfiguration -> {
	requestConfiguration.queryParameters.ownerEmail = "bob@contoso.com";
	requestConfiguration.headers.add("Authorization", "Bearer {token}");
	requestConfiguration.headers.add("Client-Request-Id", "7c9b1b4c-5b5a-4e3e-9f1b-2d9b0b4a9a0a");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let usageRightsIncluded = await client.api('/security/dataSecurityAndGovernance/sensitivityLabels/4e4234dd-377b-42a3-935b-0e42f138fa23/rights?ownerEmail=bob@contoso.com')
	.header('Authorization','Bearer {token}')
	.header('Client-Request-Id','7c9b1b4c-5b5a-4e3e-9f1b-2d9b0b4a9a0a')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\DataSecurityAndGovernance\SensitivityLabels\Item\Rights\RightsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RightsRequestBuilderGetRequestConfiguration();
$headers = [
		'Authorization' => 'Bearer {token}',
		'Client-Request-Id' => '7c9b1b4c-5b5a-4e3e-9f1b-2d9b0b4a9a0a',
	];
$requestConfiguration->headers = $headers;

$queryParameters = RightsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->ownerEmail = "bob@contoso.com";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->dataSecurityAndGovernance()->sensitivityLabels()->bySensitivityLabelId('sensitivityLabel-id')->rights()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityDataSecurityAndGovernanceSensitivityLabelRight -SensitivityLabelId $sensitivityLabelId -Owneremail "bob@contoso.com" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.data_security_and_governance.sensitivity_labels.item.rights.rights_request_builder import RightsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = RightsRequestBuilder.RightsRequestBuilderGetQueryParameters(
		owner_email = "bob@contoso.com",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("Authorization", "Bearer {token}")
request_configuration.headers.add("Client-Request-Id", "7c9b1b4c-5b5a-4e3e-9f1b-2d9b0b4a9a0a")


result = await graph_client.security.data_security_and_governance.sensitivity_labels.by_sensitivity_label_id('sensitivityLabel-id').rights.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response containing the usage rights granted to the user.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.usageRights)",
  "id": "f306e677-4c14-4136-b2c3-d9c7dd448cc1",
  "ownerEmail": "bob@contoso.com",
  "value": "docEdit, edit, forward, print, reply, replyAll, view, extract, viewRightsData, objModel"
}
```
