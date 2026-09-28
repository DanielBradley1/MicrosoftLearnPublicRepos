<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataroot-post-outboundprovisioningflowsets?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-11 -->

# Create outboundProvisioningFlowSet

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-OutboundFlow.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /external/industryData/OutboundProvisioningFlowSets
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) object.

## Response

If successful, this method returns a `201 Created` response code and an [outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/external/industryData/OutboundProvisioningFlowSets
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.industryData.outboundProvisioningFlowSet",
    "displayName": "Outbound Provisioning Flow Test",
    "filter": {
        "@odata.type": "#microsoft.graph.industryData.basicFilter",
        "attribute": "orgExternalId",
        "in": [
            "Quarter",
            "Demo"
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new OutboundProvisioningFlowSet
{
	OdataType = "#microsoft.graph.industryData.outboundProvisioningFlowSet",
	DisplayName = "Outbound Provisioning Flow Test",
	Filter = new BasicFilter
	{
		OdataType = "#microsoft.graph.industryData.basicFilter",
		Attribute = FilterOptions.OrgExternalId,
		In = new List<string>
		{
			"Quarter",
			"Demo",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.OutboundProvisioningFlowSets.PostAsync(requestBody);
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
	  graphmodelsindustrydata "github.com/microsoftgraph/msgraph-beta-sdk-go/models/industrydata"
	  //other-imports
)

requestBody := graphmodelsindustrydata.NewOutboundProvisioningFlowSet()
displayName := "Outbound Provisioning Flow Test"
requestBody.SetDisplayName(&displayName) 
filter := graphmodelsindustrydata.NewBasicFilter()
attribute := graphmodels.ORGEXTERNALID_FILTEROPTIONS 
filter.SetAttribute(&attribute) 
in := []string {
	"Quarter",
	"Demo",
}
filter.SetIn(in)
requestBody.SetFilter(filter)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
outboundProvisioningFlowSets, err := graphClient.External().IndustryData().OutboundProvisioningFlowSets().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.OutboundProvisioningFlowSet outboundProvisioningFlowSet = new com.microsoft.graph.beta.models.industrydata.OutboundProvisioningFlowSet();
outboundProvisioningFlowSet.setOdataType("#microsoft.graph.industryData.outboundProvisioningFlowSet");
outboundProvisioningFlowSet.setDisplayName("Outbound Provisioning Flow Test");
com.microsoft.graph.beta.models.industrydata.BasicFilter filter = new com.microsoft.graph.beta.models.industrydata.BasicFilter();
filter.setOdataType("#microsoft.graph.industryData.basicFilter");
filter.setAttribute(com.microsoft.graph.beta.models.industrydata.FilterOptions.OrgExternalId);
LinkedList<String> in = new LinkedList<String>();
in.add("Quarter");
in.add("Demo");
filter.setIn(in);
outboundProvisioningFlowSet.setFilter(filter);
com.microsoft.graph.models.industrydata.OutboundProvisioningFlowSet result = graphClient.external().industryData().outboundProvisioningFlowSets().post(outboundProvisioningFlowSet);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const outboundProvisioningFlowSet = {
    '@odata.type': '#microsoft.graph.industryData.outboundProvisioningFlowSet',
    displayName: 'Outbound Provisioning Flow Test',
    filter: {
        '@odata.type': '#microsoft.graph.industryData.basicFilter',
        attribute: 'orgExternalId',
        in: [
            'Quarter',
            'Demo'
        ]
    }
};

await client.api('/external/industryData/OutboundProvisioningFlowSets')
	.version('beta')
	.post(outboundProvisioningFlowSet);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\OutboundProvisioningFlowSet;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\BasicFilter;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\FilterOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OutboundProvisioningFlowSet();
$requestBody->setOdataType('#microsoft.graph.industryData.outboundProvisioningFlowSet');
$requestBody->setDisplayName('Outbound Provisioning Flow Test');
$filter = new BasicFilter();
$filter->setOdataType('#microsoft.graph.industryData.basicFilter');
$filter->setAttribute(new FilterOptions('orgExternalId'));
$filter->setIn(['Quarter', 'Demo', 	]);
$requestBody->setFilter($filter);

$result = $graphServiceClient->external()->industryData()->outboundProvisioningFlowSets()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.outboundProvisioningFlowSet"
	displayName = "Outbound Provisioning Flow Test"
	filter = @{
		"@odata.type" = "#microsoft.graph.industryData.basicFilter"
		attribute = "orgExternalId"
		in = @(
		"Quarter"
	"Demo"
)
}
}

New-MgBetaExternalIndustryDataOutboundProvisioningFlowSet -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.outbound_provisioning_flow_set import OutboundProvisioningFlowSet
from msgraph_beta.generated.models.industry_data.basic_filter import BasicFilter
from msgraph_beta.generated.models.filter_options import FilterOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OutboundProvisioningFlowSet(
	odata_type = "#microsoft.graph.industryData.outboundProvisioningFlowSet",
	display_name = "Outbound Provisioning Flow Test",
	filter = BasicFilter(
		odata_type = "#microsoft.graph.industryData.basicFilter",
		attribute = FilterOptions.OrgExternalId,
		in = [
			"Quarter",
			"Demo",
		],
	),
)

result = await graph_client.external.industry_data.outbound_provisioning_flow_sets.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#external/industryData/outboundProvisioningFlowSets/$entity",
    "id": "8ac3c08f-6f93-465b-4bd9-08dc4ac773d0",
    "createdDateTime": "2024-03-25T21:55:03.495336Z",
    "lastModifiedDateTime": "2024-03-25T21:55:03.495336Z",
    "displayName": "Outbound Provisioning Flow Test",
    "filter": {
        "@odata.type": "#microsoft.graph.industryData.basicFilter",
        "attribute": "orgExternalId",
        "in": [
            "Quarter",
            "Demo"
        ]
    }
}
```
