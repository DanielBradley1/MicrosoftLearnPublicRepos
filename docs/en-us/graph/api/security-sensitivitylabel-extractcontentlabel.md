<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-extractcontentlabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# sensitivityLabel: extractContentLabel

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Use the metadata that exists on an already-labeled piece of information to resolve the metadata to a specific sensitivity label. The [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-contentinfo?view=graph-rest-beta) input is resolved to [informationProtectionContentLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-contentlabel?view=graph-rest-beta).

Note

The [contentLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-contentlabel?view=graph-rest-beta) resource represents a sensitivity label that has been applied to a piece of information. [sensitivityLabels](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) objects are the abstract labels that are part of the organizational labeling policy and can be applied to the information.

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

To extract the content label as the signed-in user \(delegated permission\) or a specified user \(application permission\):

```http
POST /users/{usersId}/security/informationProtection/sensitivityLabels/extractContentLabel
POST /me/security/informationProtection/sensitivityLabels/extractContentLabel
```

To extract the content label as a service principal \(application permission\):

```http
POST /users/security/informationProtection/sensitivityLabels/extractContentLabel
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | Content-type: application/json. Required. |
| User-Agent | Describes the name and version of the calling application. Details will surface in Azure Information Protection Analytics. Suggested format is `ApplicationName/Version`. Optional. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameter that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentInfo | [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-contentinfo?view=graph-rest-beta) | Provides details about the content format, content state, and existing [metadata](https://learn.microsoft.com/en-us/graph/api/resources/security-keyvaluepair?view=graph-rest-beta) as key-value pairs. |

## Response

If successful, this action returns a `200 OK` response code and a [contentLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-contentlabel?view=graph-rest-beta) object in the response body.

## Examples

### Response

The following example shows the response.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/users/bob@contoso.com/security/informationProtection/sensitivityLabels/extractContentLabel
Content-type: application/json
User-agent: ContosoLOBApp/1.0

{
    "contentInfo": {
        "format": "default",
        "identifier": "MyDoc.docx",
        "state": "rest",
        "metadata": [
            {
                "name": "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Enabled",
                "value": "True"
            },
            {
                "name": "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Method",
                "value": "Standard"
            },
            {
                "name": "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SetDate",
                "value": "1/1/0001 12:00:00 AM"
            },
            {
                "name": "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SiteId",
                "value": "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
            },
            {
                "name": "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Name",
                "value": "LabelScopedToBob_Tests"
            },
            {
                "name": "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ContentBits",
                "value": "0"
            },
            {
                "name": "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ActionId",
                "value": "00000000-0000-0000-0000-000000000000"
            }
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.Security.InformationProtection.SensitivityLabels.MicrosoftGraphSecurityExtractContentLabel;
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new ExtractContentLabelPostRequestBody
{
	ContentInfo = new ContentInfo
	{
		Identifier = "MyDoc.docx",
		State = ContentState.Rest,
		Metadata = new List<KeyValuePair>
		{
			new KeyValuePair
			{
				Name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Enabled",
				Value = "True",
			},
			new KeyValuePair
			{
				Name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Method",
				Value = "Standard",
			},
			new KeyValuePair
			{
				Name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SetDate",
				Value = "1/1/0001 12:00:00 AM",
			},
			new KeyValuePair
			{
				Name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SiteId",
				Value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c",
			},
			new KeyValuePair
			{
				Name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Name",
				Value = "LabelScopedToBob_Tests",
			},
			new KeyValuePair
			{
				Name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ContentBits",
				Value = "0",
			},
			new KeyValuePair
			{
				Name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ActionId",
				Value = "00000000-0000-0000-0000-000000000000",
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"format" , "default"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Security.InformationProtection.SensitivityLabels.MicrosoftGraphSecurityExtractContentLabel.PostAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphusers.ItemSecurityInformationProtectionSensitivityLabelsMicrosoft.graph.security.extractContentLabelRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewExtractContentLabelPostRequestBody()
contentInfo := graphmodelssecurity.NewContentInfo()
identifier := "MyDoc.docx"
contentInfo.SetIdentifier(&identifier) 
state := graphmodels.REST_CONTENTSTATE 
contentInfo.SetState(&state) 


keyValuePair := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Enabled"
keyValuePair.SetName(&name) 
value := "True"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Method"
keyValuePair1.SetName(&name) 
value := "Standard"
keyValuePair1.SetValue(&value) 
keyValuePair2 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SetDate"
keyValuePair2.SetName(&name) 
value := "1/1/0001 12:00:00 AM"
keyValuePair2.SetValue(&value) 
keyValuePair3 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SiteId"
keyValuePair3.SetName(&name) 
value := "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
keyValuePair3.SetValue(&value) 
keyValuePair4 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Name"
keyValuePair4.SetName(&name) 
value := "LabelScopedToBob_Tests"
keyValuePair4.SetValue(&value) 
keyValuePair5 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ContentBits"
keyValuePair5.SetName(&name) 
value := "0"
keyValuePair5.SetValue(&value) 
keyValuePair6 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ActionId"
keyValuePair6.SetName(&name) 
value := "00000000-0000-0000-0000-000000000000"
keyValuePair6.SetValue(&value) 

metadata := []graphmodelssecurity.KeyValuePairable {
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
	"format" : "default", 
}
contentInfo.SetAdditionalData(additionalData)
requestBody.SetContentInfo(contentInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityExtractContentLabel, err := graphClient.Users().ByUserId("user-id").Security().InformationProtection().SensitivityLabels().MicrosoftGraphSecurityExtractContentLabel().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.security.informationprotection.sensitivitylabels.microsoftgraphsecurityextractcontentlabel.ExtractContentLabelPostRequestBody extractContentLabelPostRequestBody = new com.microsoft.graph.beta.users.item.security.informationprotection.sensitivitylabels.microsoftgraphsecurityextractcontentlabel.ExtractContentLabelPostRequestBody();
com.microsoft.graph.beta.models.security.ContentInfo contentInfo = new com.microsoft.graph.beta.models.security.ContentInfo();
contentInfo.setIdentifier("MyDoc.docx");
contentInfo.setState(com.microsoft.graph.beta.models.security.ContentState.Rest);
LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair> metadata = new LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair>();
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair.setName("MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Enabled");
keyValuePair.setValue("True");
metadata.add(keyValuePair);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair1 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair1.setName("MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Method");
keyValuePair1.setValue("Standard");
metadata.add(keyValuePair1);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair2 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair2.setName("MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SetDate");
keyValuePair2.setValue("1/1/0001 12:00:00 AM");
metadata.add(keyValuePair2);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair3 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair3.setName("MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SiteId");
keyValuePair3.setValue("cfa4cf1d-a337-4481-aa99-19d8f3d63f7c");
metadata.add(keyValuePair3);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair4 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair4.setName("MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Name");
keyValuePair4.setValue("LabelScopedToBob_Tests");
metadata.add(keyValuePair4);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair5 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair5.setName("MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ContentBits");
keyValuePair5.setValue("0");
metadata.add(keyValuePair5);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair6 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair6.setName("MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ActionId");
keyValuePair6.setValue("00000000-0000-0000-0000-000000000000");
metadata.add(keyValuePair6);
contentInfo.setMetadata(metadata);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("format", "default");
contentInfo.setAdditionalData(additionalData);
extractContentLabelPostRequestBody.setContentInfo(contentInfo);
var result = graphClient.users().byUserId("{user-id}").security().informationProtection().sensitivityLabels().microsoftGraphSecurityExtractContentLabel().post(extractContentLabelPostRequestBody, requestConfiguration -> {
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

const contentLabel = {
    contentInfo: {
        format: 'default',
        identifier: 'MyDoc.docx',
        state: 'rest',
        metadata: [
            {
                name: 'MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Enabled',
                value: 'True'
            },
            {
                name: 'MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Method',
                value: 'Standard'
            },
            {
                name: 'MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SetDate',
                value: '1/1/0001 12:00:00 AM'
            },
            {
                name: 'MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SiteId',
                value: 'cfa4cf1d-a337-4481-aa99-19d8f3d63f7c'
            },
            {
                name: 'MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Name',
                value: 'LabelScopedToBob_Tests'
            },
            {
                name: 'MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ContentBits',
                value: '0'
            },
            {
                name: 'MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ActionId',
                value: '00000000-0000-0000-0000-000000000000'
            }
        ]
    }
};

await client.api('/users/bob@contoso.com/security/informationProtection/sensitivityLabels/extractContentLabel')
	.version('beta')
	.post(contentLabel);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Security\InformationProtection\SensitivityLabels\Microsoft\Graph\Security\ExtractContentLabel\ExtractContentLabelRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Users\Item\Security\InformationProtection\SensitivityLabels\MicrosoftGraphSecurityExtractContentLabel\ExtractContentLabelPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Security\ContentInfo;
use Microsoft\Graph\Beta\Generated\Models\Security\ContentState;
use Microsoft\Graph\Beta\Generated\Models\Security\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExtractContentLabelPostRequestBody();
$contentInfo = new ContentInfo();
$contentInfo->setIdentifier('MyDoc.docx');
$contentInfo->setState(new ContentState('rest'));
$metadataKeyValuePair1 = new KeyValuePair();
$metadataKeyValuePair1->setName('MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Enabled');
$metadataKeyValuePair1->setValue('True');
$metadataArray []= $metadataKeyValuePair1;
$metadataKeyValuePair2 = new KeyValuePair();
$metadataKeyValuePair2->setName('MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Method');
$metadataKeyValuePair2->setValue('Standard');
$metadataArray []= $metadataKeyValuePair2;
$metadataKeyValuePair3 = new KeyValuePair();
$metadataKeyValuePair3->setName('MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SetDate');
$metadataKeyValuePair3->setValue('1/1/0001 12:00:00 AM');
$metadataArray []= $metadataKeyValuePair3;
$metadataKeyValuePair4 = new KeyValuePair();
$metadataKeyValuePair4->setName('MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SiteId');
$metadataKeyValuePair4->setValue('cfa4cf1d-a337-4481-aa99-19d8f3d63f7c');
$metadataArray []= $metadataKeyValuePair4;
$metadataKeyValuePair5 = new KeyValuePair();
$metadataKeyValuePair5->setName('MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Name');
$metadataKeyValuePair5->setValue('LabelScopedToBob_Tests');
$metadataArray []= $metadataKeyValuePair5;
$metadataKeyValuePair6 = new KeyValuePair();
$metadataKeyValuePair6->setName('MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ContentBits');
$metadataKeyValuePair6->setValue('0');
$metadataArray []= $metadataKeyValuePair6;
$metadataKeyValuePair7 = new KeyValuePair();
$metadataKeyValuePair7->setName('MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ActionId');
$metadataKeyValuePair7->setValue('00000000-0000-0000-0000-000000000000');
$metadataArray []= $metadataKeyValuePair7;
$contentInfo->setMetadata($metadataArray);

$additionalData = [
'format' => 'default',
];
$contentInfo->setAdditionalData($additionalData);
$requestBody->setContentInfo($contentInfo);
$requestConfiguration = new MicrosoftExtractContentLabelRequestBuilderPostRequestConfiguration();
$headers = [
	'User-Agent' => 'ContosoLOBApp/1.0',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->security()->informationProtection()->sensitivityLabels()->microsoftGraphSecurityExtractContentLabel()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	contentInfo = @{
		format = "default"
		identifier = "MyDoc.docx"
		state = "rest"
		metadata = @(
			@{
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Enabled"
				value = "True"
			}
			@{
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Method"
				value = "Standard"
			}
			@{
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SetDate"
				value = "1/1/0001 12:00:00 AM"
			}
			@{
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SiteId"
				value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
			}
			@{
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Name"
				value = "LabelScopedToBob_Tests"
			}
			@{
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ContentBits"
				value = "0"
			}
			@{
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ActionId"
				value = "00000000-0000-0000-0000-000000000000"
			}
		)
	}
}

Invoke-MgBetaExtractUserSecurityInformationProtectionSensitivityLabelContentLabel -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.security.information_protection.sensitivity_labels.microsoft.graph.security.extract_content_label.extract_content_label_request_builder import ExtractContentLabelRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.users.item.security.informationprotection.sensitivitylabels.microsoft_graph_security_extract_content_label.extract_content_label_post_request_body import ExtractContentLabelPostRequestBody
from msgraph_beta.generated.models.security.content_info import ContentInfo
from msgraph_beta.generated.models.content_state import ContentState
from msgraph_beta.generated.models.security.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExtractContentLabelPostRequestBody(
	content_info = ContentInfo(
		identifier = "MyDoc.docx",
		state = ContentState.Rest,
		metadata = [
			KeyValuePair(
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Enabled",
				value = "True",
			),
			KeyValuePair(
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Method",
				value = "Standard",
			),
			KeyValuePair(
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SetDate",
				value = "1/1/0001 12:00:00 AM",
			),
			KeyValuePair(
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_SiteId",
				value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c",
			),
			KeyValuePair(
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_Name",
				value = "LabelScopedToBob_Tests",
			),
			KeyValuePair(
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ContentBits",
				value = "0",
			),
			KeyValuePair(
				name = "MSIP_Label_0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3_ActionId",
				value = "00000000-0000-0000-0000-000000000000",
			),
		],
		additional_data = {
				"format" : "default",
		}
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("User-Agent", "ContosoLOBApp/1.0")


result = await graph_client.users.by_user_id('user-id').security.information_protection.sensitivity_labels.microsoft_graph_security_extract_content_label.post(request_body, request_configuration = request_configuration)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.security.contentLabel",
    "createdDateTime": "2001-01-01T12:00:00Z",
    "assignmentMethod": "standard",
    "sensitivityLabelId": "0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3"
}
```
