<!-- Source: https://learn.microsoft.com/en-us/graph/api/ediscovery-casesettings-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# Update caseSettings

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Update the properties of a an eDiscovery [caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /compliance/ediscovery/cases/{caseId}/settings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) object.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/compliance/ediscovery/cases/{caseId}/settings
Content-Type: application/json

{
    "redundancyDetection": {
        "isEnabled": false,
        "similarityThreshold": 70,
        "minWords": 12,
        "maxWords": 400000
    },
    "topicModeling": {
        "isEnabled": false,
        "ignoreNumbers": false,
        "topicCount": 50,
        "dynamicallyAdjustTopicCount": false
    },
    "ocr": {
        "isEnabled": true,
        "maxImageSize": 12000
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Ediscovery;

var requestBody = new CaseSettings
{
	RedundancyDetection = new RedundancyDetectionSettings
	{
		IsEnabled = false,
		SimilarityThreshold = 70,
		MinWords = 12,
		MaxWords = 400000,
	},
	TopicModeling = new TopicModelingSettings
	{
		IsEnabled = false,
		IgnoreNumbers = false,
		TopicCount = 50,
		DynamicallyAdjustTopicCount = false,
	},
	Ocr = new OcrSettings
	{
		IsEnabled = true,
		MaxImageSize = 12000,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Compliance.Ediscovery.Cases["{case-id}"].Settings.PatchAsync(requestBody);
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
	  graphmodelsediscovery "github.com/microsoftgraph/msgraph-beta-sdk-go/models/ediscovery"
	  //other-imports
)

requestBody := graphmodelsediscovery.NewCaseSettings()
redundancyDetection := graphmodelsediscovery.NewRedundancyDetectionSettings()
isEnabled := false
redundancyDetection.SetIsEnabled(&isEnabled) 
similarityThreshold := int32(70)
redundancyDetection.SetSimilarityThreshold(&similarityThreshold) 
minWords := int32(12)
redundancyDetection.SetMinWords(&minWords) 
maxWords := int32(400000)
redundancyDetection.SetMaxWords(&maxWords) 
requestBody.SetRedundancyDetection(redundancyDetection)
topicModeling := graphmodelsediscovery.NewTopicModelingSettings()
isEnabled := false
topicModeling.SetIsEnabled(&isEnabled) 
ignoreNumbers := false
topicModeling.SetIgnoreNumbers(&ignoreNumbers) 
topicCount := int32(50)
topicModeling.SetTopicCount(&topicCount) 
dynamicallyAdjustTopicCount := false
topicModeling.SetDynamicallyAdjustTopicCount(&dynamicallyAdjustTopicCount) 
requestBody.SetTopicModeling(topicModeling)
ocr := graphmodelsediscovery.NewOcrSettings()
isEnabled := true
ocr.SetIsEnabled(&isEnabled) 
maxImageSize := int32(12000)
ocr.SetMaxImageSize(&maxImageSize) 
requestBody.SetOcr(ocr)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
settings, err := graphClient.Compliance().Ediscovery().Cases().ByCaseId("case-id").Settings().Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.ediscovery.CaseSettings caseSettings = new com.microsoft.graph.beta.models.ediscovery.CaseSettings();
com.microsoft.graph.beta.models.ediscovery.RedundancyDetectionSettings redundancyDetection = new com.microsoft.graph.beta.models.ediscovery.RedundancyDetectionSettings();
redundancyDetection.setIsEnabled(false);
redundancyDetection.setSimilarityThreshold(70);
redundancyDetection.setMinWords(12);
redundancyDetection.setMaxWords(400000);
caseSettings.setRedundancyDetection(redundancyDetection);
com.microsoft.graph.beta.models.ediscovery.TopicModelingSettings topicModeling = new com.microsoft.graph.beta.models.ediscovery.TopicModelingSettings();
topicModeling.setIsEnabled(false);
topicModeling.setIgnoreNumbers(false);
topicModeling.setTopicCount(50);
topicModeling.setDynamicallyAdjustTopicCount(false);
caseSettings.setTopicModeling(topicModeling);
com.microsoft.graph.beta.models.ediscovery.OcrSettings ocr = new com.microsoft.graph.beta.models.ediscovery.OcrSettings();
ocr.setIsEnabled(true);
ocr.setMaxImageSize(12000);
caseSettings.setOcr(ocr);
com.microsoft.graph.models.ediscovery.CaseSettings result = graphClient.compliance().ediscovery().cases().byCaseId("{case-id}").settings().patch(caseSettings);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const caseSettings = {
    redundancyDetection: {
        isEnabled: false,
        similarityThreshold: 70,
        minWords: 12,
        maxWords: 400000
    },
    topicModeling: {
        isEnabled: false,
        ignoreNumbers: false,
        topicCount: 50,
        dynamicallyAdjustTopicCount: false
    },
    ocr: {
        isEnabled: true,
        maxImageSize: 12000
    }
};

await client.api('/compliance/ediscovery/cases/{caseId}/settings')
	.version('beta')
	.update(caseSettings);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\CaseSettings;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\RedundancyDetectionSettings;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\TopicModelingSettings;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\OcrSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CaseSettings();
$redundancyDetection = new RedundancyDetectionSettings();
$redundancyDetection->setIsEnabled(false);
$redundancyDetection->setSimilarityThreshold(70);
$redundancyDetection->setMinWords(12);
$redundancyDetection->setMaxWords(400000);
$requestBody->setRedundancyDetection($redundancyDetection);
$topicModeling = new TopicModelingSettings();
$topicModeling->setIsEnabled(false);
$topicModeling->setIgnoreNumbers(false);
$topicModeling->setTopicCount(50);
$topicModeling->setDynamicallyAdjustTopicCount(false);
$requestBody->setTopicModeling($topicModeling);
$ocr = new OcrSettings();
$ocr->setIsEnabled(true);
$ocr->setMaxImageSize(12000);
$requestBody->setOcr($ocr);

$result = $graphServiceClient->compliance()->ediscovery()->cases()->byCaseId('case-id')->settings()->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Compliance

$params = @{
	redundancyDetection = @{
		isEnabled = $false
		similarityThreshold = 70
		minWords = 12
		maxWords = 400000
	}
	topicModeling = @{
		isEnabled = $false
		ignoreNumbers = $false
		topicCount = 50
		dynamicallyAdjustTopicCount = $false
	}
	ocr = @{
		isEnabled = $true
		maxImageSize = 12000
	}
}

Update-MgBetaComplianceEdiscoveryCaseSetting -CaseId $caseId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.ediscovery.case_settings import CaseSettings
from msgraph_beta.generated.models.ediscovery.redundancy_detection_settings import RedundancyDetectionSettings
from msgraph_beta.generated.models.ediscovery.topic_modeling_settings import TopicModelingSettings
from msgraph_beta.generated.models.ediscovery.ocr_settings import OcrSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CaseSettings(
	redundancy_detection = RedundancyDetectionSettings(
		is_enabled = False,
		similarity_threshold = 70,
		min_words = 12,
		max_words = 400000,
	),
	topic_modeling = TopicModelingSettings(
		is_enabled = False,
		ignore_numbers = False,
		topic_count = 50,
		dynamically_adjust_topic_count = False,
	),
	ocr = OcrSettings(
		is_enabled = True,
		max_image_size = 12000,
	),
)

result = await graph_client.compliance.ediscovery.cases.by_case_id('case-id').settings.patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
cache-control: no-cache
client-request-id: e9fc7554-ca5e-0928-fc09-9c5825820c88
content-length: 0
request-id: 1f53bd55-f099-46cb-91df-8f5d466aba3a
```
