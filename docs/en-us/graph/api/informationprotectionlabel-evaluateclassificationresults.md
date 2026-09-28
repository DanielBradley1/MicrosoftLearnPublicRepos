<!-- Source: https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# informationProtectionLabel: evaluateClassificationResults \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Using [classification results](https://learn.microsoft.com/en-us/graph/api/resources/classificationresult?view=graph-rest-beta), compute the [information protection label](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionlabel?view=graph-rest-beta) that should be applied and return the set of actions that must be taken to correctly label the information. This API is useful when a label should be set automatically based on classification of the file contents, rather than labeled directly by a user or service.

To evaluate based on classification results, provide [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta), which includes existing content metadata [key/value pairs](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta), and [classification results](https://learn.microsoft.com/en-us/graph/api/resources/classificationresult?view=graph-rest-beta). The API returns an [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) that contains one of more of the following:

- [addContentFooterAction](https://learn.microsoft.com/en-us/graph/api/resources/addcontentfooteraction?view=graph-rest-beta)
- [addContentHeaderAction](https://learn.microsoft.com/en-us/graph/api/resources/addcontentheaderaction?view=graph-rest-beta)
- [addWatermarkAction](https://learn.microsoft.com/en-us/graph/api/resources/addwatermarkaction?view=graph-rest-beta)
- [applyLabelAction](https://learn.microsoft.com/en-us/graph/api/resources/applylabelaction?view=graph-rest-beta)
- [customAction](https://learn.microsoft.com/en-us/graph/api/resources/customaction?view=graph-rest-beta)
- [justifyAction](https://learn.microsoft.com/en-us/graph/api/resources/justifyaction?view=graph-rest-beta)
- [metadataAction](https://learn.microsoft.com/en-us/graph/api/resources/metadataaction?view=graph-rest-beta)
- [protectAdhocAction](https://learn.microsoft.com/en-us/graph/api/resources/protectadhocaction?view=graph-rest-beta)
- [protectByTemplateAction](https://learn.microsoft.com/en-us/graph/api/resources/protectbytemplateaction?view=graph-rest-beta)
- [protectionDoNotForwardAction](https://learn.microsoft.com/en-us/graph/api/resources/protectdonotforwardaction?view=graph-rest-beta)
- [recommendLabelAction](https://learn.microsoft.com/en-us/graph/api/resources/recommendlabelaction?view=graph-rest-beta)
- [removeContentFooterAction](https://learn.microsoft.com/en-us/graph/api/resources/removecontentfooteraction?view=graph-rest-beta)
- [removeContentHeaderAction](https://learn.microsoft.com/en-us/graph/api/resources/removecontentheaderaction?view=graph-rest-beta)
- [removeProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/removeprotectionaction?view=graph-rest-beta)
- [removeWatermarkAction](https://learn.microsoft.com/en-us/graph/api/resources/removewatermarkaction?view=graph-rest-beta)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | InformationProtectionPolicy.Read | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | InformationProtectionPolicy.Read.All | Not available. |

## HTTP request

```http
POST /informationProtection/policy/labels/evaluateClassificationResults
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| User-Agent | Describes the name and version of the calling application. Details will surface in Azure Information Protection Analytics. Suggested format is ApplicationName/Version. Optional. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentInfo | [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta) | Provides details about the content format, content state, and existing [metadata](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) as key/value pairs. |
| classificationResults | [classificationResult](https://learn.microsoft.com/en-us/graph/api/resources/classificationresult?view=graph-rest-beta) collection | Contains the set of classification results returned by the data classification endpoint. Classification information is used to determine the appropriate label based on the Microsoft Purview Information Protection policy label configuration in Microsoft 365 Security and Compliance Center. |

## Response

If successful, this method returns a `200 OK` response code and a new [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) collection object in the response body.

## Examples

The following example shows how to call this API.

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
POST https://graph.microsoft.com/beta/informationProtection/policy/labels/evaluateClassificationResults
Content-type: application/json
User-agent: ContosoLOBApp/1.0

{
  "contentInfo": {
    "@odata.type": "#microsoft.graph.contentInfo",
    "format@odata.type": "#microsoft.graph.contentFormat",
    "format": "default",
    "identifier": null,
    "state@odata.type": "#microsoft.graph.contentState",
    "state": "rest"
  },
  "classificationResults": [
    {
      "sensitiveTypeId": "cb353f78-2b72-4c3c-8827-92ebe4f69fdf",
      "count": 4,
      "confidenceLevel": 75
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.InformationProtection.Policy.Labels.EvaluateClassificationResults;
using Microsoft.Graph.Beta.Models;

var requestBody = new EvaluateClassificationResultsPostRequestBody
{
	ContentInfo = new ContentInfo
	{
		OdataType = "#microsoft.graph.contentInfo",
		Format = ContentFormat.Default,
		Identifier = null,
		State = ContentState.Rest,
		AdditionalData = new Dictionary<string, object>
		{
			{
				"format@odata.type" , "#microsoft.graph.contentFormat"
			},
			{
				"state@odata.type" , "#microsoft.graph.contentState"
			},
		},
	},
	ClassificationResults = new List<ClassificationResult>
	{
		new ClassificationResult
		{
			SensitiveTypeId = "cb353f78-2b72-4c3c-8827-92ebe4f69fdf",
			Count = 4,
			ConfidenceLevel = 75,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.InformationProtection.Policy.Labels.EvaluateClassificationResults.PostAsEvaluateClassificationResultsPostResponseAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("User-Agent", "ContosoLOBApp/1.0");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphinformationprotection "github.com/microsoftgraph/msgraph-beta-sdk-go/informationprotection"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("User-Agent", "ContosoLOBApp/1.0")

configuration := &graphinformationprotection.PolicyLabelsEvaluateClassificationResultsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphinformationprotection.NewEvaluateClassificationResultsPostRequestBody()
contentInfo := graphmodels.NewContentInfo()
format := graphmodels.DEFAULT_CONTENTFORMAT 
contentInfo.SetFormat(&format) 
identifier := null
contentInfo.SetIdentifier(&identifier) 
state := graphmodels.REST_CONTENTSTATE 
contentInfo.SetState(&state) 
additionalData := map[string]interface{}{
	"format@odata.type" : "#microsoft.graph.contentFormat", 
	"state@odata.type" : "#microsoft.graph.contentState", 
}
contentInfo.SetAdditionalData(additionalData)
requestBody.SetContentInfo(contentInfo)


classificationResult := graphmodels.NewClassificationResult()
sensitiveTypeId := "cb353f78-2b72-4c3c-8827-92ebe4f69fdf"
classificationResult.SetSensitiveTypeId(&sensitiveTypeId) 
count := int32(4)
classificationResult.SetCount(&count) 
confidenceLevel := int32(75)
classificationResult.SetConfidenceLevel(&confidenceLevel) 

classificationResults := []graphmodels.ClassificationResultable {
	classificationResult,
}
requestBody.SetClassificationResults(classificationResults)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
evaluateClassificationResults, err := graphClient.InformationProtection().Policy().Labels().EvaluateClassificationResults().PostAsEvaluateClassificationResultsPostResponse(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.informationprotection.policy.labels.evaluateclassificationresults.EvaluateClassificationResultsPostRequestBody evaluateClassificationResultsPostRequestBody = new com.microsoft.graph.beta.informationprotection.policy.labels.evaluateclassificationresults.EvaluateClassificationResultsPostRequestBody();
ContentInfo contentInfo = new ContentInfo();
contentInfo.setOdataType("#microsoft.graph.contentInfo");
contentInfo.setFormat(ContentFormat.Default);
contentInfo.setIdentifier(null);
contentInfo.setState(ContentState.Rest);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("format@odata.type", "#microsoft.graph.contentFormat");
additionalData.put("state@odata.type", "#microsoft.graph.contentState");
contentInfo.setAdditionalData(additionalData);
evaluateClassificationResultsPostRequestBody.setContentInfo(contentInfo);
LinkedList<ClassificationResult> classificationResults = new LinkedList<ClassificationResult>();
ClassificationResult classificationResult = new ClassificationResult();
classificationResult.setSensitiveTypeId("cb353f78-2b72-4c3c-8827-92ebe4f69fdf");
classificationResult.setCount(4);
classificationResult.setConfidenceLevel(75);
classificationResults.add(classificationResult);
evaluateClassificationResultsPostRequestBody.setClassificationResults(classificationResults);
var result = graphClient.informationProtection().policy().labels().evaluateClassificationResults().post(evaluateClassificationResultsPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("User-Agent", "ContosoLOBApp/1.0");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const informationProtectionAction = {
  contentInfo: {
    '@odata.type': '#microsoft.graph.contentInfo',
    'format@odata.type': '#microsoft.graph.contentFormat',
    format: 'default',
    identifier: null,
    'state@odata.type': '#microsoft.graph.contentState',
    state: 'rest'
  },
  classificationResults: [
    {
      sensitiveTypeId: 'cb353f78-2b72-4c3c-8827-92ebe4f69fdf',
      count: 4,
      confidenceLevel: 75
    }
  ]
};

await client.api('/informationProtection/policy/labels/evaluateClassificationResults')
	.version('beta')
	.post(informationProtectionAction);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\InformationProtection\Policy\Labels\EvaluateClassificationResults\EvaluateClassificationResultsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\InformationProtection\Policy\Labels\EvaluateClassificationResults\EvaluateClassificationResultsPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\ContentInfo;
use Microsoft\Graph\Beta\Generated\Models\ContentFormat;
use Microsoft\Graph\Beta\Generated\Models\ContentState;
use Microsoft\Graph\Beta\Generated\Models\ClassificationResult;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluateClassificationResultsPostRequestBody();
$contentInfo = new ContentInfo();
$contentInfo->setOdataType('#microsoft.graph.contentInfo');
$contentInfo->setFormat(new ContentFormat('default'));
$contentInfo->setIdentifier(null);
$contentInfo->setState(new ContentState('rest'));
$additionalData = [
	'format@odata.type' => '#microsoft.graph.contentFormat',
	'state@odata.type' => '#microsoft.graph.contentState',
];
$contentInfo->setAdditionalData($additionalData);
$requestBody->setContentInfo($contentInfo);
$classificationResultsClassificationResult1 = new ClassificationResult();
$classificationResultsClassificationResult1->setSensitiveTypeId('cb353f78-2b72-4c3c-8827-92ebe4f69fdf');
$classificationResultsClassificationResult1->setCount(4);
$classificationResultsClassificationResult1->setConfidenceLevel(75);
$classificationResultsArray []= $classificationResultsClassificationResult1;
$requestBody->setClassificationResults($classificationResultsArray);

$requestConfiguration = new EvaluateClassificationResultsRequestBuilderPostRequestConfiguration();
$headers = [
	'User-Agent' => 'ContosoLOBApp/1.0',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->informationProtection()->policy()->labels()->evaluateClassificationResults()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	contentInfo = @{
		"@odata.type" = "#microsoft.graph.contentInfo"
		"format@odata.type" = "#microsoft.graph.contentFormat"
		format = "default"
		identifier = $null
		"state@odata.type" = "#microsoft.graph.contentState"
		state = "rest"
	}
	classificationResults = @(
		@{
			sensitiveTypeId = "cb353f78-2b72-4c3c-8827-92ebe4f69fdf"
			count = 4
			confidenceLevel = 75
		}
	)
}

Test-MgBetaInformationProtectionPolicyLabelClassificationResult -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.information_protection.policy.labels.evaluate_classification_results.evaluate_classification_results_request_builder import EvaluateClassificationResultsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.informationprotection.policy.labels.evaluate_classification_results.evaluate_classification_results_post_request_body import EvaluateClassificationResultsPostRequestBody
from msgraph_beta.generated.models.content_info import ContentInfo
from msgraph_beta.generated.models.content_format import ContentFormat
from msgraph_beta.generated.models.content_state import ContentState
from msgraph_beta.generated.models.classification_result import ClassificationResult
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluateClassificationResultsPostRequestBody(
	content_info = ContentInfo(
		odata_type = "#microsoft.graph.contentInfo",
		format = ContentFormat.Default,
		identifier = None,
		state = ContentState.Rest,
		additional_data = {
				"format@odata_type" : "#microsoft.graph.contentFormat",
				"state@odata_type" : "#microsoft.graph.contentState",
		}
	),
	classification_results = [
		ClassificationResult(
			sensitive_type_id = "cb353f78-2b72-4c3c-8827-92ebe4f69fdf",
			count = 4,
			confidence_level = 75,
		),
	],
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("User-Agent", "ContosoLOBApp/1.0")


result = await graph_client.information_protection.policy.labels.evaluate_classification_results.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.informationProtectionAction)",
  "value": [
    {
      "@odata.type": "#microsoft.graph.applyLabelAction",
      "responsibleSensitiveTypeIds": [
        "cb353f78-2b72-4c3c-8827-92ebe4f69fdf"
      ],
      "actionSource": "automatic",
      "label": {
        "id": "722a5300-ac39-4c9a-88e3-f54c46676417",
        "name": "Top Secret",
        "description": "",
        "color": "#000000",
        "sensitivity": 13,
        "tooltip": "This information is Top Secret.",
        "isActive": true
      },
      "actions": [
        {
          "@odata.type": "#microsoft.graph.protectByTemplateAction",
          "templateId": "0e7fea72-7bba-4438-a070-95c292cd6f8c"
        },
        {
          "@odata.type": "#microsoft.graph.metadataAction",
          "metadataToRemove": [],
          "metadataToAdd": [
            {
              "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled",
              "value": "true"
            },
            {
              "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate",
              "value": "2019-10-03T21:50:20Z"
            },
            {
              "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method",
              "value": "Standard"
            },
            {
              "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name",
              "value": "Top Secret"
            },
            {
              "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId",
              "value": "cb46c030-1825-4e81-a295-151c039dbf02"
            },
            {
              "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId",
              "value": "76dc494e-6c59-43e6-88a1-0000edd58fca"
            },
            {
              "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits",
              "value": "8"
            }
          ]
        }
      ]
    }
  ]
}
```
