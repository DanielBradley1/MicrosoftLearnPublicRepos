<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-onerosterapidataconnector-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-18 -->

# Update oneRosterApiDataConnector

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [oneRosterApiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IndustryData-DataConnector.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IndustryData-DataConnector.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /external/industryData/dataConnectors/{industryDataConnectorId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the data connector. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta). Required. |
| apiFormat | microsoft.graph.industryData.apiFormat | The API format of the external system being connected to. Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta). The possible values are: `oneRoster`, `unknownFutureValue`. Required. |
| baseUrl | String | The base URI including the scheme, host, and path for the API \(with or without a trailing '/'\). Example: `https://example.com/ims/oneRoster/v1p1`. Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta). Required. |
| credential | [microsoft.graph.industryData.credential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-credential?view=graph-rest-beta) | The base type for all supported credentials. Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta). Required. |
| apiVersion | String | The API version of the OneRoster source. Required. |
| isDemographicsEnabled | Boolean | Indicates whether the user specified to import optional demographics data. Required. |
| isFlagsEnabled | Boolean | Indicates whether the user specified to import optional flags data. Required. |
| isContactsEnabled | Boolean | Indicates whether the user specified to import optional contacts data. Required. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/beta/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271
Content-type: application/json

{
  "@odata.type": "microsoft.graph.industryData.oneRosterApiDataConnector",
  "displayName": "One Roster Connector"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new OneRosterApiDataConnector
{
	OdataType = "microsoft.graph.industryData.oneRosterApiDataConnector",
	DisplayName = "One Roster Connector",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.DataConnectors["{industryDataConnector-id}"].PatchAsync(requestBody);
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

requestBody := graphmodelsindustrydata.NewIndustryDataConnector()
displayName := "One Roster Connector"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
dataConnectors, err := graphClient.External().IndustryData().DataConnectors().ByIndustryDataConnectorId("industryDataConnector-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.OneRosterApiDataConnector industryDataConnector = new com.microsoft.graph.beta.models.industrydata.OneRosterApiDataConnector();
industryDataConnector.setOdataType("microsoft.graph.industryData.oneRosterApiDataConnector");
industryDataConnector.setDisplayName("One Roster Connector");
com.microsoft.graph.models.industrydata.IndustryDataConnector result = graphClient.external().industryData().dataConnectors().byIndustryDataConnectorId("{industryDataConnector-id}").patch(industryDataConnector);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const industryDataConnector = {
  '@odata.type': 'microsoft.graph.industryData.oneRosterApiDataConnector',
  displayName: 'One Roster Connector'
};

await client.api('/external/industryData/dataConnectors/51dca0a0-85f6-4478-f526-08daddab2271')
	.version('beta')
	.update(industryDataConnector);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\OneRosterApiDataConnector;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneRosterApiDataConnector();
$requestBody->setOdataType('microsoft.graph.industryData.oneRosterApiDataConnector');
$requestBody->setDisplayName('One Roster Connector');

$result = $graphServiceClient->external()->industryData()->dataConnectors()->byIndustryDataConnectorId('industryDataConnector-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "microsoft.graph.industryData.oneRosterApiDataConnector"
	displayName = "One Roster Connector"
}

Update-MgBetaExternalIndustryDataConnector -IndustryDataConnectorId $industryDataConnectorId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.one_roster_api_data_connector import OneRosterApiDataConnector
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneRosterApiDataConnector(
	odata_type = "microsoft.graph.industryData.oneRosterApiDataConnector",
	display_name = "One Roster Connector",
)

result = await graph_client.external.industry_data.data_connectors.by_industry_data_connector_id('industryDataConnector-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
