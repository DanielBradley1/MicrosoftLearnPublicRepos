<!-- Source: https://learn.microsoft.com/en-us/graph/api/sensitivitylabel-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get sensitivityLabel

Namespace: microsoft.graph

Get a sensitivity label available for the entire tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SensitivityLabel.Read | SensitivityLabels.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SensitivityLabel.Read | SensitivityLabels.Read.All |

When an application calls this API with an application permission \(`SensitivityLabels.Read.All`\), the API returns all labels for the tenant by default.

## HTTP request

Get labels for all tenant labels:

```http
GET /security/dataSecurityAndGovernance/sensitivityLabels/{labelId}
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

If successful, this method returns a `200 OK` response code and a collection of [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-1.0) objects in the response body.

## Examples

The following example shows a request to get a label available in the tenant.

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
GET https://graph.microsoft.com/v1.0/security/dataSecurityAndGovernance/sensitivityLabels/4e4234dd-377b-42a3-935b-0e42f138fa23
Authorization: Bearer {token}
Client-Request-Id: a0b9c8d7-e6f5-a4b3-c2d1-e0f9a8b7c6d5
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.DataSecurityAndGovernance.SensitivityLabels["{sensitivityLabel-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Authorization", "Bearer {token}");
	requestConfiguration.Headers.Add("Client-Request-Id", "a0b9c8d7-e6f5-a4b3-c2d1-e0f9a8b7c6d5");
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
headers.Add("Client-Request-Id", "a0b9c8d7-e6f5-a4b3-c2d1-e0f9a8b7c6d5")

configuration := &graphsecurity.DataSecurityAndGovernanceSensitivityLabelsItemRequestBuilderGetRequestConfiguration{
	Headers: headers,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sensitivityLabels, err := graphClient.Security().DataSecurityAndGovernance().SensitivityLabels().BySensitivityLabelId("sensitivityLabel-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SensitivityLabel result = graphClient.security().dataSecurityAndGovernance().sensitivityLabels().bySensitivityLabelId("{sensitivityLabel-id}").get(requestConfiguration -> {
	requestConfiguration.headers.add("Authorization", "Bearer {token}");
	requestConfiguration.headers.add("Client-Request-Id", "a0b9c8d7-e6f5-a4b3-c2d1-e0f9a8b7c6d5");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sensitivityLabel = await client.api('/security/dataSecurityAndGovernance/sensitivityLabels/4e4234dd-377b-42a3-935b-0e42f138fa23')
	.header('Authorization','Bearer {token}')
	.header('Client-Request-Id','a0b9c8d7-e6f5-a4b3-c2d1-e0f9a8b7c6d5')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\DataSecurityAndGovernance\SensitivityLabels\Item\SensitivityLabelItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new SensitivityLabelItemRequestBuilderGetRequestConfiguration();
$headers = [
		'Authorization' => 'Bearer {token}',
		'Client-Request-Id' => 'a0b9c8d7-e6f5-a4b3-c2d1-e0f9a8b7c6d5',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->security()->dataSecurityAndGovernance()->sensitivityLabels()->bySensitivityLabelId('sensitivityLabel-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityDataSecurityAndGovernanceSensitivityLabel -SensitivityLabelId $sensitivityLabelId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.data_security_and_governance.sensitivity_labels.item.sensitivity_label_item_request_builder import SensitivityLabelItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

request_configuration = RequestConfiguration()
request_configuration.headers.add("Authorization", "Bearer {token}")
request_configuration.headers.add("Client-Request-Id", "a0b9c8d7-e6f5-a4b3-c2d1-e0f9a8b7c6d5")


result = await graph_client.security.data_security_and_governance.sensitivity_labels.by_sensitivity_label_id('sensitivityLabel-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response containing only the labels matching the filters.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/dataSecurityAndGovernance/sensitivityLabel",
  "value": [
    {
      "id": "4e4234dd-377b-42a3-935b-0e42f138fa23",
      "name": "General",
      "description": "General data, not for public use.",
      "color": "#000000",
      "priority": 10,
      "toolTip": "Apply this label to general non-public data.",
      "isEnabled": true,
      "isEndpointProtectionEnabled": true,
      "autoTooltip": "",
      "actionSource": "manual",
      "applicableTo": "email,teamwork,file",
      "sublabels": []
    }
  ]
}
```
