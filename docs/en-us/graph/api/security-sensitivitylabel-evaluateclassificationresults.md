<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# sensitivityLabel: evaluateClassificationResults

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Use the [classification results](https://learn.microsoft.com/en-us/graph/api/resources/security-classificationresult?view=graph-rest-beta) to compute the [sensitivity label](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) that should be applied and return the set of actions that must be taken to correctly label the information. This API is useful when a label should be set automatically based on classification of the file contents, rather than labeled directly by a user or service.

To evaluate based on classification results, provide the [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-contentinfo?view=graph-rest-beta), which includes existing content metadata [key-value pairs](https://learn.microsoft.com/en-us/graph/api/resources/security-keyvaluepair?view=graph-rest-beta), and [classification results](https://learn.microsoft.com/en-us/graph/api/resources/security-classificationresult?view=graph-rest-beta). The API returns an [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) that contains one of more of the following:

- [addContentFooterAction](https://learn.microsoft.com/en-us/graph/api/resources/security-addcontentfooteraction?view=graph-rest-beta)
- [addContentHeaderAction](https://learn.microsoft.com/en-us/graph/api/resources/security-addcontentheaderaction?view=graph-rest-beta)
- [addWatermarkAction](https://learn.microsoft.com/en-us/graph/api/resources/security-addwatermarkaction?view=graph-rest-beta)
- [applyLabelAction](https://learn.microsoft.com/en-us/graph/api/resources/security-applylabelaction?view=graph-rest-beta)
- [customAction](https://learn.microsoft.com/en-us/graph/api/resources/security-customaction?view=graph-rest-beta)
- [justifyAction](https://learn.microsoft.com/en-us/graph/api/resources/security-justifyaction?view=graph-rest-beta)
- [metadataAction](https://learn.microsoft.com/en-us/graph/api/resources/security-metadataaction?view=graph-rest-beta)
- [protectAdhocAction](https://learn.microsoft.com/en-us/graph/api/resources/security-protectadhocaction?view=graph-rest-beta)
- [protectByTemplateAction](https://learn.microsoft.com/en-us/graph/api/resources/security-protectbytemplateaction?view=graph-rest-beta)
- [protectionDoNotForwardAction](https://learn.microsoft.com/en-us/graph/api/resources/security-protectdonotforwardaction?view=graph-rest-beta)
- [recommendLabelAction](https://learn.microsoft.com/en-us/graph/api/resources/security-recommendlabelaction?view=graph-rest-beta)
- [removeContentFooterAction](https://learn.microsoft.com/en-us/graph/api/resources/security-removecontentfooteraction?view=graph-rest-beta)
- [removeContentHeaderAction](https://learn.microsoft.com/en-us/graph/api/resources/security-removecontentheaderaction?view=graph-rest-beta)
- [removeProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-removeprotectionaction?view=graph-rest-beta)
- [removeWatermarkAction](https://learn.microsoft.com/en-us/graph/api/resources/security-removewatermarkaction?view=graph-rest-beta)

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

To evaluate as the signed-in user \(delegated permission\) or a specified user \(application permission\):

```http
POST /users/{usersId}/security/informationProtection/sensitivityLabels/evaluateClassificationResults
POST /me/security/informationProtection/sensitivityLabels/evaluateClassificationResults
```

To evaluate as a service principal \(application permission\):

```http
POST /users/security/informationProtection/sensitivityLabels/evaluateClassificationResults
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| User-Agent | Describes the name and version of the calling application. Details will surface in Azure Information Protection Analytics. Suggested format is `ApplicationName/Version`. Optional. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentInfo | [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-contentinfo?view=graph-rest-beta) | Provides details about the content format, content state, and existing [metadata](https://learn.microsoft.com/en-us/graph/api/resources/security-keyvaluepair?view=graph-rest-beta) as key-value pairs. |
| classificationResults | [classificationResult](https://learn.microsoft.com/en-us/graph/api/resources/security-classificationresult?view=graph-rest-beta) collection | Contains the set of classification results returned by the data classification endpoint. Classification information is used to determine the appropriate label based on the Microsoft Purview Information Protection policy label configuration in Microsoft 365 Security and Compliance Center. |

## Response

If successful, this action returns a `200 OK` response code and an [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) collection in the response body.

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
POST https://graph.microsoft.com/beta/users/bob@contoso.com/security/informationProtection/sensitivityLabels/evaluateClassificationResults
Content-type: application/json
User-agent: ContosoLOBApp/1.0

{
    "contentInfo": {
        "@odata.type": "#microsoft.graph.security.contentInfo",
        "format@odata.type": "#microsoft.graph.security.contentFormat",
        "format": "default",
        "contentFormat": "File",
        "identifier": "c:\\user\\new.docx",
        "state@odata.type": "#microsoft.graph.security.contentState",
        "state": "rest",
        "metadata": []
    },
    "classificationResults": [
        {
            "sensitiveTypeId": "50842eb7-edc8-4019-85dd-5a5c1f2bb085", //Credit Card 
            "count": 7,
            "confidenceLevel": 99
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.Security.InformationProtection.SensitivityLabels.MicrosoftGraphSecurityEvaluateClassificationResults;
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new EvaluateClassificationResultsPostRequestBody
{
	ContentInfo = new ContentInfo
	{
		OdataType = "#microsoft.graph.security.contentInfo",
		ContentFormat = "File",
		Identifier = "c:\user\new.docx",
		State = ContentState.Rest,
		Metadata = new List<KeyValuePair>
		{
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"format@odata.type" , "#microsoft.graph.security.contentFormat"
			},
			{
				"format" , "default"
			},
			{
				"state@odata.type" , "#microsoft.graph.security.contentState"
			},
		},
	},
	ClassificationResults = new List<ClassificationResult>
	{
		new ClassificationResult
		{
			SensitiveTypeId = "50842eb7-edc8-4019-85dd-5a5c1f2bb085",
			Count = 7,
			ConfidenceLevel = 99,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Security.InformationProtection.SensitivityLabels.MicrosoftGraphSecurityEvaluateClassificationResults.PostAsEvaluateClassificationResultsPostResponseAsync(requestBody, (requestConfiguration) =>
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
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("User-Agent", "ContosoLOBApp/1.0")

configuration := &graphusers.ItemSecurityInformationProtectionSensitivityLabelsMicrosoft.graph.security.evaluateClassificationResultsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewEvaluateClassificationResultsPostRequestBody()
contentInfo := graphmodelssecurity.NewContentInfo()
contentFormat := "File"
contentInfo.SetContentFormat(&contentFormat) 
identifier := "c:\user\new.docx"
contentInfo.SetIdentifier(&identifier) 
state := graphmodels.REST_CONTENTSTATE 
contentInfo.SetState(&state) 
metadata := []graphmodelssecurity.KeyValuePairable {

}
contentInfo.SetMetadata(metadata)
additionalData := map[string]interface{}{
	"format@odata.type" : "#microsoft.graph.security.contentFormat", 
	"format" : "default", 
	"state@odata.type" : "#microsoft.graph.security.contentState", 
}
contentInfo.SetAdditionalData(additionalData)
requestBody.SetContentInfo(contentInfo)


classificationResult := graphmodelssecurity.NewClassificationResult()
sensitiveTypeId := "50842eb7-edc8-4019-85dd-5a5c1f2bb085"
classificationResult.SetSensitiveTypeId(&sensitiveTypeId) 
count := int32(7)
classificationResult.SetCount(&count) 
confidenceLevel := int32(99)
classificationResult.SetConfidenceLevel(&confidenceLevel) 

classificationResults := []graphmodelssecurity.ClassificationResultable {
	classificationResult,
}
requestBody.SetClassificationResults(classificationResults)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityEvaluateClassificationResults, err := graphClient.Users().ByUserId("user-id").Security().InformationProtection().SensitivityLabels().MicrosoftGraphSecurityEvaluateClassificationResults().PostAsEvaluateClassificationResultsPostResponse(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.security.informationprotection.sensitivitylabels.microsoftgraphsecurityevaluateclassificationresults.EvaluateClassificationResultsPostRequestBody evaluateClassificationResultsPostRequestBody = new com.microsoft.graph.beta.users.item.security.informationprotection.sensitivitylabels.microsoftgraphsecurityevaluateclassificationresults.EvaluateClassificationResultsPostRequestBody();
com.microsoft.graph.beta.models.security.ContentInfo contentInfo = new com.microsoft.graph.beta.models.security.ContentInfo();
contentInfo.setOdataType("#microsoft.graph.security.contentInfo");
contentInfo.setContentFormat("File");
contentInfo.setIdentifier("c:\user\new.docx");
contentInfo.setState(com.microsoft.graph.beta.models.security.ContentState.Rest);
LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair> metadata = new LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair>();
contentInfo.setMetadata(metadata);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("format@odata.type", "#microsoft.graph.security.contentFormat");
additionalData.put("format", "default");
additionalData.put("state@odata.type", "#microsoft.graph.security.contentState");
contentInfo.setAdditionalData(additionalData);
evaluateClassificationResultsPostRequestBody.setContentInfo(contentInfo);
LinkedList<com.microsoft.graph.beta.models.security.ClassificationResult> classificationResults = new LinkedList<com.microsoft.graph.beta.models.security.ClassificationResult>();
com.microsoft.graph.beta.models.security.ClassificationResult classificationResult = new com.microsoft.graph.beta.models.security.ClassificationResult();
classificationResult.setSensitiveTypeId("50842eb7-edc8-4019-85dd-5a5c1f2bb085");
classificationResult.setCount(7);
classificationResult.setConfidenceLevel(99);
classificationResults.add(classificationResult);
evaluateClassificationResultsPostRequestBody.setClassificationResults(classificationResults);
var result = graphClient.users().byUserId("{user-id}").security().informationProtection().sensitivityLabels().microsoftGraphSecurityEvaluateClassificationResults().post(evaluateClassificationResultsPostRequestBody, requestConfiguration -> {
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
        '@odata.type': '#microsoft.graph.security.contentInfo',
        'format@odata.type': '#microsoft.graph.security.contentFormat',
        format: 'default',
        contentFormat: 'File',
        identifier: 'c:\\user\\new.docx',
        'state@odata.type': '#microsoft.graph.security.contentState',
        state: 'rest',
        metadata: []
    },
    classificationResults: [
        {
            sensitiveTypeId: '50842eb7-edc8-4019-85dd-5a5c1f2bb085', //Credit Card 
            count: 7,
            confidenceLevel: 99
        }
    ]
};

await client.api('/users/bob@contoso.com/security/informationProtection/sensitivityLabels/evaluateClassificationResults')
	.version('beta')
	.post(informationProtectionAction);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Security\InformationProtection\SensitivityLabels\Microsoft\Graph\Security\EvaluateClassificationResults\EvaluateClassificationResultsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Users\Item\Security\InformationProtection\SensitivityLabels\MicrosoftGraphSecurityEvaluateClassificationResults\EvaluateClassificationResultsPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Security\ContentInfo;
use Microsoft\Graph\Beta\Generated\Models\Security\ContentState;
use Microsoft\Graph\Beta\Generated\Models\Security\KeyValuePair;
use Microsoft\Graph\Beta\Generated\Models\Security\ClassificationResult;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluateClassificationResultsPostRequestBody();
$contentInfo = new ContentInfo();
$contentInfo->setOdataType('#microsoft.graph.security.contentInfo');
$contentInfo->setContentFormat('File');
$contentInfo->setIdentifier('c:\user\new.docx');
$contentInfo->setState(new ContentState('rest'));
$contentInfo->setMetadata([	]);
$additionalData = [
	'format@odata.type' => '#microsoft.graph.security.contentFormat',
	'format' => 'default',
	'state@odata.type' => '#microsoft.graph.security.contentState',
];
$contentInfo->setAdditionalData($additionalData);
$requestBody->setContentInfo($contentInfo);
$classificationResultsClassificationResult1 = new ClassificationResult();
$classificationResultsClassificationResult1->setSensitiveTypeId('50842eb7-edc8-4019-85dd-5a5c1f2bb085');
$classificationResultsClassificationResult1->setCount(7);
$classificationResultsClassificationResult1->setConfidenceLevel(99);
$classificationResultsArray []= $classificationResultsClassificationResult1;
$requestBody->setClassificationResults($classificationResultsArray);

$requestConfiguration = new MicrosoftEvaluateClassificationResultsRequestBuilderPostRequestConfiguration();
$headers = [
	'User-Agent' => 'ContosoLOBApp/1.0',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->security()->informationProtection()->sensitivityLabels()->microsoftGraphSecurityEvaluateClassificationResults()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	contentInfo = @{
		"@odata.type" = "#microsoft.graph.security.contentInfo"
		"format@odata.type" = "#microsoft.graph.security.contentFormat"
		format = "default"
		contentFormat = "File"
		identifier = "c:\user\new.docx"
		"state@odata.type" = "#microsoft.graph.security.contentState"
		state = "rest"
		metadata = @(
		)
	}
	classificationResults = @(
		@{
			sensitiveTypeId = "50842eb7-edc8-4019-85dd-5a5c1f2bb085"
			count = 7
			confidenceLevel = 99
		}
	)
}

Test-MgBetaUserSecurityInformationProtectionSensitivityLabelClassificationResult -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.security.information_protection.sensitivity_labels.microsoft.graph.security.evaluate_classification_results.evaluate_classification_results_request_builder import EvaluateClassificationResultsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.users.item.security.informationprotection.sensitivitylabels.microsoft_graph_security_evaluate_classification_results.evaluate_classification_results_post_request_body import EvaluateClassificationResultsPostRequestBody
from msgraph_beta.generated.models.security.content_info import ContentInfo
from msgraph_beta.generated.models.content_state import ContentState
from msgraph_beta.generated.models.security.key_value_pair import KeyValuePair
from msgraph_beta.generated.models.security.classification_result import ClassificationResult
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluateClassificationResultsPostRequestBody(
	content_info = ContentInfo(
		odata_type = "#microsoft.graph.security.contentInfo",
		content_format = "File",
		identifier = "c:\user\new.docx",
		state = ContentState.Rest,
		metadata = [
		],
		additional_data = {
				"format@odata_type" : "#microsoft.graph.security.contentFormat",
				"format" : "default",
				"state@odata_type" : "#microsoft.graph.security.contentState",
		}
	),
	classification_results = [
		ClassificationResult(
			sensitive_type_id = "50842eb7-edc8-4019-85dd-5a5c1f2bb085",
			count = 7,
			confidence_level = 99,
		),
	],
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("User-Agent", "ContosoLOBApp/1.0")


result = await graph_client.users.by_user_id('user-id').security.information_protection.sensitivity_labels.microsoft_graph_security_evaluate_classification_results.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.security.informationProtectionAction)",
  "value": [
    {
      "@odata.type": "#microsoft.graph.security.applyLabelAction",
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
          "@odata.type": "#microsoft.graphsecurity..protectByTemplateAction",
          "templateId": "0e7fea72-7bba-4438-a070-95c292cd6f8c"
        },
        {
          "@odata.type": "#microsoft.graph.security.metadataAction",
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
