<!-- Source: https://learn.microsoft.com/en-us/graph/api/industrydata-azuredatalakeconnector-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-05 -->

# Create azureDataLakeConnector

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [azureDataLakeConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-azuredatalakeconnector?view=graph-rest-beta) object.

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
POST /external/industryData/dataConnectors
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [azureDataLakeConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-azuredatalakeconnector?view=graph-rest-beta) object.

You can specify the following properties when you create an **azureDataLakeConnector**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the data connector. Required. |
| fileFormat | [microsoft.graph.industryData.fileFormatReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-fileformatreferencevalue?view=graph-rest-beta) | A reference to a file format entry in the [referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) collection. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.industryData.azureDataLakeConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-azuredatalakeconnector?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/external/industryData/dataConnectors
Content-Type: application/json
Content-length: 104

{
    "@odata.type": "#microsoft.graph.industryData.azureDataLakeConnector",
    "displayName": "CSV connector",
    "sourceSystem@odata.bind": "https://graph.microsoft.com/beta/external/industryData/sourceSystems('aa050107-5784-4a8e-1876-08daddab21bc')",
    "fileFormat": {
      "@odata.type": "microsoft.graph.industryData.fileFormatReferenceValue",
      "code": "schoolDataSyncV1"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.IndustryData;

var requestBody = new AzureDataLakeConnector
{
	OdataType = "#microsoft.graph.industryData.azureDataLakeConnector",
	DisplayName = "CSV connector",
	FileFormat = new FileFormatReferenceValue
	{
		OdataType = "microsoft.graph.industryData.fileFormatReferenceValue",
		Code = "schoolDataSyncV1",
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"sourceSystem@odata.bind" , "https://graph.microsoft.com/beta/external/industryData/sourceSystems('aa050107-5784-4a8e-1876-08daddab21bc')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.IndustryData.DataConnectors.PostAsync(requestBody);
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
displayName := "CSV connector"
requestBody.SetDisplayName(&displayName) 
fileFormat := graphmodelsindustrydata.NewFileFormatReferenceValue()
code := "schoolDataSyncV1"
fileFormat.SetCode(&code) 
requestBody.SetFileFormat(fileFormat)
additionalData := map[string]interface{}{
	"sourceSystem@odata.bind" : "https://graph.microsoft.com/beta/external/industryData/sourceSystems('aa050107-5784-4a8e-1876-08daddab21bc')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
dataConnectors, err := graphClient.External().IndustryData().DataConnectors().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.industrydata.AzureDataLakeConnector industryDataConnector = new com.microsoft.graph.beta.models.industrydata.AzureDataLakeConnector();
industryDataConnector.setOdataType("#microsoft.graph.industryData.azureDataLakeConnector");
industryDataConnector.setDisplayName("CSV connector");
com.microsoft.graph.beta.models.industrydata.FileFormatReferenceValue fileFormat = new com.microsoft.graph.beta.models.industrydata.FileFormatReferenceValue();
fileFormat.setOdataType("microsoft.graph.industryData.fileFormatReferenceValue");
fileFormat.setCode("schoolDataSyncV1");
industryDataConnector.setFileFormat(fileFormat);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("sourceSystem@odata.bind", "https://graph.microsoft.com/beta/external/industryData/sourceSystems('aa050107-5784-4a8e-1876-08daddab21bc')");
industryDataConnector.setAdditionalData(additionalData);
com.microsoft.graph.models.industrydata.IndustryDataConnector result = graphClient.external().industryData().dataConnectors().post(industryDataConnector);
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
    '@odata.type': '#microsoft.graph.industryData.azureDataLakeConnector',
    displayName: 'CSV connector',
    'sourceSystem@odata.bind': 'https://graph.microsoft.com/beta/external/industryData/sourceSystems(\'aa050107-5784-4a8e-1876-08daddab21bc\')',
    fileFormat: {
      '@odata.type': 'microsoft.graph.industryData.fileFormatReferenceValue',
      code: 'schoolDataSyncV1'
    }
};

await client.api('/external/industryData/dataConnectors')
	.version('beta')
	.post(industryDataConnector);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\AzureDataLakeConnector;
use Microsoft\Graph\Beta\Generated\Models\IndustryData\FileFormatReferenceValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AzureDataLakeConnector();
$requestBody->setOdataType('#microsoft.graph.industryData.azureDataLakeConnector');
$requestBody->setDisplayName('CSV connector');
$fileFormat = new FileFormatReferenceValue();
$fileFormat->setOdataType('microsoft.graph.industryData.fileFormatReferenceValue');
$fileFormat->setCode('schoolDataSyncV1');
$requestBody->setFileFormat($fileFormat);
$additionalData = [
	'sourceSystem@odata.bind' => 'https://graph.microsoft.com/beta/external/industryData/sourceSystems(\'aa050107-5784-4a8e-1876-08daddab21bc\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->external()->industryData()->dataConnectors()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	"@odata.type" = "#microsoft.graph.industryData.azureDataLakeConnector"
	displayName = "CSV connector"
	"sourceSystem@odata.bind" = "https://graph.microsoft.com/beta/external/industryData/sourceSystems('aa050107-5784-4a8e-1876-08daddab21bc')"
	fileFormat = @{
		"@odata.type" = "microsoft.graph.industryData.fileFormatReferenceValue"
		code = "schoolDataSyncV1"
	}
}

New-MgBetaExternalIndustryDataConnector -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.industry_data.azure_data_lake_connector import AzureDataLakeConnector
from msgraph_beta.generated.models.industry_data.file_format_reference_value import FileFormatReferenceValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AzureDataLakeConnector(
	odata_type = "#microsoft.graph.industryData.azureDataLakeConnector",
	display_name = "CSV connector",
	file_format = FileFormatReferenceValue(
		odata_type = "microsoft.graph.industryData.fileFormatReferenceValue",
		code = "schoolDataSyncV1",
	),
	additional_data = {
			"source_system@odata_bind" : "https://graph.microsoft.com/beta/external/industryData/sourceSystems('aa050107-5784-4a8e-1876-08daddab21bc')",
	}
)

result = await graph_client.external.industry_data.data_connectors.post(request_body)
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
  "@odata.type": "#microsoft.graph.industryData.azureDataLakeConnector",
  "displayName": "CSV connector",
  "id": "51dca0a0-85f6-4478-f526-08daddab2271",
  "fileFormat": {
    "@odata.type": "microsoft.graph.industryData.fileFormatReferenceValue",
    "code": "schoolDataSyncV1"
  }
}
```
