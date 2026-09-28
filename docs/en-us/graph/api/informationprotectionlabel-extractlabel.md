<!-- Source: https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-extractlabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# informationProtectionLabel: extractLabel \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Using the metadata that exists on an already-labeled piece of information, resolve the metadata to a specific sensitivity label. The [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta) input is resolved to [informationProtectionContentLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectioncontentlabel?view=graph-rest-beta).

Note

The **[informationProtectionContentLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectioncontentlabel?view=graph-rest-beta)** resource represents a sensitivity label that has been applied to a piece of information. [informationProtectionLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionlabel?view=graph-rest-beta) objects are the abstract labels that are part of the organizational labeling policy and can be applied to information.

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
POST /informationprotection/policy/labels/extractLabel
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | Content-type: application/json. Required. |
| User-Agent | Describes the name and version of the calling application. Details will surface in Azure Information Protection Analytics. Suggested format is ApplicationName/Version. Optional. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentInfo | [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta) | Provides details about the content format, content state, and existing [metadata](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) as key/value pairs. |

## Response

If successful, this method returns a `200 OK` response code and a new [informationProtectionContentLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectioncontentlabel?view=graph-rest-beta) object in the response body.

## Examples

The following is an example of how to call this API.

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
POST https://graph.microsoft.com/beta/informationProtection/policy/labels/extractLabel
Content-type: application/json
User-agent: ContosoLOBApp/1.0

{
    "contentInfo": {
        "@odata.type": "#microsoft.graph.contentInfo",
        "format@odata.type": "#microsoft.graph.contentFormat",
        "format": "default",
        "identifier": null,
        "state@odata.type": "#microsoft.graph.contentState",
        "state": "rest",
        "metadata@odata.type": "#Collection(microsoft.graph.keyValuePair)",
        "metadata": [
            {
                "@odata.type": "#microsoft.graph.keyValuePair",
                "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled",
                "value": "True"
            },
            {
                "@odata.type": "#microsoft.graph.keyValuePair",
                "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method",
                "value": "Standard"
            },
            {
                "@odata.type": "#microsoft.graph.keyValuePair",
                "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate",
                "value": "1/1/0001 12:00:00 AM"
            },
            {
                "@odata.type": "#microsoft.graph.keyValuePair",
                "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId",
                "value": "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
            },
            {
                "@odata.type": "#microsoft.graph.keyValuePair",
                "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name",
                "value": "Top Secret"
            },
            {
                "@odata.type": "#microsoft.graph.keyValuePair",
                "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits",
                "value": "0"
            },
            {
                "@odata.type": "#microsoft.graph.keyValuePair",
                "name": "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId",
                "value": "00000000-0000-0000-0000-000000000000"
            }
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.InformationProtection.Policy.Labels.ExtractLabel;
using Microsoft.Graph.Beta.Models;

var requestBody = new ExtractLabelPostRequestBody
{
	ContentInfo = new ContentInfo
	{
		OdataType = "#microsoft.graph.contentInfo",
		Format = ContentFormat.Default,
		Identifier = null,
		State = ContentState.Rest,
		Metadata = new List<KeyValuePair>
		{
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.keyValuePair",
				Name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled",
				Value = "True",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.keyValuePair",
				Name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method",
				Value = "Standard",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.keyValuePair",
				Name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate",
				Value = "1/1/0001 12:00:00 AM",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.keyValuePair",
				Name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId",
				Value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.keyValuePair",
				Name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name",
				Value = "Top Secret",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.keyValuePair",
				Name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits",
				Value = "0",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.keyValuePair",
				Name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId",
				Value = "00000000-0000-0000-0000-000000000000",
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"format@odata.type" , "#microsoft.graph.contentFormat"
			},
			{
				"state@odata.type" , "#microsoft.graph.contentState"
			},
			{
				"metadata@odata.type" , "#Collection(microsoft.graph.keyValuePair)"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.InformationProtection.Policy.Labels.ExtractLabel.PostAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphinformationprotection.PolicyLabelsExtractLabelRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphinformationprotection.NewExtractLabelPostRequestBody()
contentInfo := graphmodels.NewContentInfo()
format := graphmodels.DEFAULT_CONTENTFORMAT 
contentInfo.SetFormat(&format) 
identifier := null
contentInfo.SetIdentifier(&identifier) 
state := graphmodels.REST_CONTENTSTATE 
contentInfo.SetState(&state) 


keyValuePair := graphmodels.NewKeyValuePair()
name := "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled"
keyValuePair.SetName(&name) 
value := "True"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodels.NewKeyValuePair()
name := "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method"
keyValuePair1.SetName(&name) 
value := "Standard"
keyValuePair1.SetValue(&value) 
keyValuePair2 := graphmodels.NewKeyValuePair()
name := "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate"
keyValuePair2.SetName(&name) 
value := "1/1/0001 12:00:00 AM"
keyValuePair2.SetValue(&value) 
keyValuePair3 := graphmodels.NewKeyValuePair()
name := "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId"
keyValuePair3.SetName(&name) 
value := "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
keyValuePair3.SetValue(&value) 
keyValuePair4 := graphmodels.NewKeyValuePair()
name := "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name"
keyValuePair4.SetName(&name) 
value := "Top Secret"
keyValuePair4.SetValue(&value) 
keyValuePair5 := graphmodels.NewKeyValuePair()
name := "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits"
keyValuePair5.SetName(&name) 
value := "0"
keyValuePair5.SetValue(&value) 
keyValuePair6 := graphmodels.NewKeyValuePair()
name := "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId"
keyValuePair6.SetName(&name) 
value := "00000000-0000-0000-0000-000000000000"
keyValuePair6.SetValue(&value) 

metadata := []graphmodels.KeyValuePairable {
	keyValuePair,
	keyValuePair1,
	keyValuePair2,
	keyValuePair3,
	keyValuePair4,
	keyValuePair5,
	keyValuePair6,
}
contentInfo.SetMetadata(metadata)
additionalData := map[string]interface{}{
	"format@odata.type" : "#microsoft.graph.contentFormat", 
	"state@odata.type" : "#microsoft.graph.contentState", 
	"metadata@odata.type" : "#Collection(microsoft.graph.keyValuePair)", 
}
contentInfo.SetAdditionalData(additionalData)
requestBody.SetContentInfo(contentInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
extractLabel, err := graphClient.InformationProtection().Policy().Labels().ExtractLabel().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.informationprotection.policy.labels.extractlabel.ExtractLabelPostRequestBody extractLabelPostRequestBody = new com.microsoft.graph.beta.informationprotection.policy.labels.extractlabel.ExtractLabelPostRequestBody();
ContentInfo contentInfo = new ContentInfo();
contentInfo.setOdataType("#microsoft.graph.contentInfo");
contentInfo.setFormat(ContentFormat.Default);
contentInfo.setIdentifier(null);
contentInfo.setState(ContentState.Rest);
LinkedList<KeyValuePair> metadata = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setOdataType("#microsoft.graph.keyValuePair");
keyValuePair.setName("MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled");
keyValuePair.setValue("True");
metadata.add(keyValuePair);
KeyValuePair keyValuePair1 = new KeyValuePair();
keyValuePair1.setOdataType("#microsoft.graph.keyValuePair");
keyValuePair1.setName("MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method");
keyValuePair1.setValue("Standard");
metadata.add(keyValuePair1);
KeyValuePair keyValuePair2 = new KeyValuePair();
keyValuePair2.setOdataType("#microsoft.graph.keyValuePair");
keyValuePair2.setName("MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate");
keyValuePair2.setValue("1/1/0001 12:00:00 AM");
metadata.add(keyValuePair2);
KeyValuePair keyValuePair3 = new KeyValuePair();
keyValuePair3.setOdataType("#microsoft.graph.keyValuePair");
keyValuePair3.setName("MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId");
keyValuePair3.setValue("cfa4cf1d-a337-4481-aa99-19d8f3d63f7c");
metadata.add(keyValuePair3);
KeyValuePair keyValuePair4 = new KeyValuePair();
keyValuePair4.setOdataType("#microsoft.graph.keyValuePair");
keyValuePair4.setName("MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name");
keyValuePair4.setValue("Top Secret");
metadata.add(keyValuePair4);
KeyValuePair keyValuePair5 = new KeyValuePair();
keyValuePair5.setOdataType("#microsoft.graph.keyValuePair");
keyValuePair5.setName("MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits");
keyValuePair5.setValue("0");
metadata.add(keyValuePair5);
KeyValuePair keyValuePair6 = new KeyValuePair();
keyValuePair6.setOdataType("#microsoft.graph.keyValuePair");
keyValuePair6.setName("MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId");
keyValuePair6.setValue("00000000-0000-0000-0000-000000000000");
metadata.add(keyValuePair6);
contentInfo.setMetadata(metadata);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("format@odata.type", "#microsoft.graph.contentFormat");
additionalData.put("state@odata.type", "#microsoft.graph.contentState");
additionalData.put("metadata@odata.type", "#Collection(microsoft.graph.keyValuePair)");
contentInfo.setAdditionalData(additionalData);
extractLabelPostRequestBody.setContentInfo(contentInfo);
var result = graphClient.informationProtection().policy().labels().extractLabel().post(extractLabelPostRequestBody, requestConfiguration -> {
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

const informationProtectionContentLabel = {
    contentInfo: {
        '@odata.type': '#microsoft.graph.contentInfo',
        'format@odata.type': '#microsoft.graph.contentFormat',
        format: 'default',
        identifier: null,
        'state@odata.type': '#microsoft.graph.contentState',
        state: 'rest',
        'metadata@odata.type': '#Collection(microsoft.graph.keyValuePair)',
        metadata: [
            {
                '@odata.type': '#microsoft.graph.keyValuePair',
                name: 'MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled',
                value: 'True'
            },
            {
                '@odata.type': '#microsoft.graph.keyValuePair',
                name: 'MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method',
                value: 'Standard'
            },
            {
                '@odata.type': '#microsoft.graph.keyValuePair',
                name: 'MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate',
                value: '1/1/0001 12:00:00 AM'
            },
            {
                '@odata.type': '#microsoft.graph.keyValuePair',
                name: 'MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId',
                value: 'cfa4cf1d-a337-4481-aa99-19d8f3d63f7c'
            },
            {
                '@odata.type': '#microsoft.graph.keyValuePair',
                name: 'MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name',
                value: 'Top Secret'
            },
            {
                '@odata.type': '#microsoft.graph.keyValuePair',
                name: 'MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits',
                value: '0'
            },
            {
                '@odata.type': '#microsoft.graph.keyValuePair',
                name: 'MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId',
                value: '00000000-0000-0000-0000-000000000000'
            }
        ]
    }
};

await client.api('/informationProtection/policy/labels/extractLabel')
	.version('beta')
	.post(informationProtectionContentLabel);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\InformationProtection\Policy\Labels\ExtractLabel\ExtractLabelRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\InformationProtection\Policy\Labels\ExtractLabel\ExtractLabelPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\ContentInfo;
use Microsoft\Graph\Beta\Generated\Models\ContentFormat;
use Microsoft\Graph\Beta\Generated\Models\ContentState;
use Microsoft\Graph\Beta\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExtractLabelPostRequestBody();
$contentInfo = new ContentInfo();
$contentInfo->setOdataType('#microsoft.graph.contentInfo');
$contentInfo->setFormat(new ContentFormat('default'));
$contentInfo->setIdentifier(null);
$contentInfo->setState(new ContentState('rest'));
$metadataKeyValuePair1 = new KeyValuePair();
$metadataKeyValuePair1->setOdataType('#microsoft.graph.keyValuePair');
$metadataKeyValuePair1->setName('MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled');
$metadataKeyValuePair1->setValue('True');
$metadataArray []= $metadataKeyValuePair1;
$metadataKeyValuePair2 = new KeyValuePair();
$metadataKeyValuePair2->setOdataType('#microsoft.graph.keyValuePair');
$metadataKeyValuePair2->setName('MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method');
$metadataKeyValuePair2->setValue('Standard');
$metadataArray []= $metadataKeyValuePair2;
$metadataKeyValuePair3 = new KeyValuePair();
$metadataKeyValuePair3->setOdataType('#microsoft.graph.keyValuePair');
$metadataKeyValuePair3->setName('MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate');
$metadataKeyValuePair3->setValue('1/1/0001 12:00:00 AM');
$metadataArray []= $metadataKeyValuePair3;
$metadataKeyValuePair4 = new KeyValuePair();
$metadataKeyValuePair4->setOdataType('#microsoft.graph.keyValuePair');
$metadataKeyValuePair4->setName('MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId');
$metadataKeyValuePair4->setValue('cfa4cf1d-a337-4481-aa99-19d8f3d63f7c');
$metadataArray []= $metadataKeyValuePair4;
$metadataKeyValuePair5 = new KeyValuePair();
$metadataKeyValuePair5->setOdataType('#microsoft.graph.keyValuePair');
$metadataKeyValuePair5->setName('MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name');
$metadataKeyValuePair5->setValue('Top Secret');
$metadataArray []= $metadataKeyValuePair5;
$metadataKeyValuePair6 = new KeyValuePair();
$metadataKeyValuePair6->setOdataType('#microsoft.graph.keyValuePair');
$metadataKeyValuePair6->setName('MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits');
$metadataKeyValuePair6->setValue('0');
$metadataArray []= $metadataKeyValuePair6;
$metadataKeyValuePair7 = new KeyValuePair();
$metadataKeyValuePair7->setOdataType('#microsoft.graph.keyValuePair');
$metadataKeyValuePair7->setName('MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId');
$metadataKeyValuePair7->setValue('00000000-0000-0000-0000-000000000000');
$metadataArray []= $metadataKeyValuePair7;
$contentInfo->setMetadata($metadataArray);

$additionalData = [
'format@odata.type' => '#microsoft.graph.contentFormat',
'state@odata.type' => '#microsoft.graph.contentState',
'metadata@odata.type' => '#Collection(microsoft.graph.keyValuePair)',
];
$contentInfo->setAdditionalData($additionalData);
$requestBody->setContentInfo($contentInfo);
$requestConfiguration = new ExtractLabelRequestBuilderPostRequestConfiguration();
$headers = [
	'User-Agent' => 'ContosoLOBApp/1.0',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->informationProtection()->policy()->labels()->extractLabel()->post($requestBody, $requestConfiguration)->wait();
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
		"metadata@odata.type" = "#Collection(microsoft.graph.keyValuePair)"
		metadata = @(
			@{
				"@odata.type" = "#microsoft.graph.keyValuePair"
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled"
				value = "True"
			}
			@{
				"@odata.type" = "#microsoft.graph.keyValuePair"
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method"
				value = "Standard"
			}
			@{
				"@odata.type" = "#microsoft.graph.keyValuePair"
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate"
				value = "1/1/0001 12:00:00 AM"
			}
			@{
				"@odata.type" = "#microsoft.graph.keyValuePair"
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId"
				value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
			}
			@{
				"@odata.type" = "#microsoft.graph.keyValuePair"
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name"
				value = "Top Secret"
			}
			@{
				"@odata.type" = "#microsoft.graph.keyValuePair"
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits"
				value = "0"
			}
			@{
				"@odata.type" = "#microsoft.graph.keyValuePair"
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId"
				value = "00000000-0000-0000-0000-000000000000"
			}
		)
	}
}

Invoke-MgBetaExtractInformationProtectionPolicyLabel -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.information_protection.policy.labels.extract_label.extract_label_request_builder import ExtractLabelRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.informationprotection.policy.labels.extract_label.extract_label_post_request_body import ExtractLabelPostRequestBody
from msgraph_beta.generated.models.content_info import ContentInfo
from msgraph_beta.generated.models.content_format import ContentFormat
from msgraph_beta.generated.models.content_state import ContentState
from msgraph_beta.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExtractLabelPostRequestBody(
	content_info = ContentInfo(
		odata_type = "#microsoft.graph.contentInfo",
		format = ContentFormat.Default,
		identifier = None,
		state = ContentState.Rest,
		metadata = [
			KeyValuePair(
				odata_type = "#microsoft.graph.keyValuePair",
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Enabled",
				value = "True",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.keyValuePair",
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Method",
				value = "Standard",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.keyValuePair",
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SetDate",
				value = "1/1/0001 12:00:00 AM",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.keyValuePair",
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_SiteId",
				value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.keyValuePair",
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_Name",
				value = "Top Secret",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.keyValuePair",
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ContentBits",
				value = "0",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.keyValuePair",
				name = "MSIP_Label_722a5300-ac39-4c9a-88e3-f54c46676417_ActionId",
				value = "00000000-0000-0000-0000-000000000000",
			),
		],
		additional_data = {
				"format@odata_type" : "#microsoft.graph.contentFormat",
				"state@odata_type" : "#microsoft.graph.contentState",
				"metadata@odata_type" : "#Collection(microsoft.graph.keyValuePair)",
		}
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("User-Agent", "ContosoLOBApp/1.0")


result = await graph_client.information_protection.policy.labels.extract_label.post(request_body, request_configuration = request_configuration)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.informationProtectionContentLabel",
    "creationDateTime": "1970-01-01T00:00:00Z",
    "assignmentMethod": "standard",
    "label": {
        "id": "722a5300-ac39-4c9a-88e3-f54c46676417",
        "name": "Top Secret",
        "description": "",
        "color": "#000000",
        "sensitivity": 13,
        "tooltip": "This information is top secret.",
        "isActive": true,
        "parent" : null
    }
}
```
