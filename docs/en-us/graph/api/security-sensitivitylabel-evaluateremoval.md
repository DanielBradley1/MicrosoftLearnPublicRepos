<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateremoval?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# sensitivityLabel: evaluateRemoval

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicate to the consuming application what actions it should take to remove the label information.

Given [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta) as an input, which includes existing content metadata [key-value pairs](https://learn.microsoft.com/en-us/graph/api/resources/security-keyvaluepair?view=graph-rest-beta), the API returns an [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) that contains some combination of one or more of the following:

- [justifyAction](https://learn.microsoft.com/en-us/graph/api/resources/security-justifyaction?view=graph-rest-beta)
- [metadataAction](https://learn.microsoft.com/en-us/graph/api/resources/security-metadataaction?view=graph-rest-beta)
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

To evaluate removal as the signed-in user \(delegated permission\) or a specified user \(application permission\):

```http
POST /users/{usersId}/security/informationProtection/sensitivityLabels/evaluateRemoval
POST /me/security/informationProtection/sensitivityLabels/evaluateRemoval
```

To evaluate removal as a service principal \(application permission\):

```http
POST /users/security/informationProtection/sensitivityLabels/evaluateRemoval
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
| downgradeJustification | [downgradeJustification](https://learn.microsoft.com/en-us/graph/api/resources/security-downgradejustification?view=graph-rest-beta) | Justification that must be provided by the user or application logic. |

## Response

If successful, this action returns a `200 OK` response code and an [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) collection in the response body. The [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) object will contain a [metadataAction](https://learn.microsoft.com/en-us/graph/api/resources/security-metadataaction?view=graph-rest-beta) object that informs the application which metadata to remove.

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
POST https://graph.microsoft.com/beta/users/bob@contoso.com/security/informationProtection/sensitivityLabels/evaluateRemoval
Content-type: application/json
User-agent: ContosoLOBApp/1.0

{
    "contentInfo": {
        "@odata.type": "#microsoft.graph.security.contentInfo",
        "identifier": null,
        "state": "rest",
        "metadata": [
            {
                "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled",
                "value": "True"
            },
            {
                "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method",
                "value": "Standard"
            },
            {
                "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate",
                "value": "1/1/0001 12:00:00 AM"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId",
                "value": "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name",
                "value": "LabelScopedToBob_Tests"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits",
                "value": "0"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId",
                "value": "00000000-0000-0000-0000-000000000000"
            }
        ]
    },
    "downgradeJustification": {
        "justificationMessage": "The information has been declassified.",
        "isDowngradeJustified": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.Security.InformationProtection.SensitivityLabels.MicrosoftGraphSecurityEvaluateRemoval;
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new EvaluateRemovalPostRequestBody
{
	ContentInfo = new ContentInfo
	{
		OdataType = "#microsoft.graph.security.contentInfo",
		Identifier = null,
		State = ContentState.Rest,
		Metadata = new List<KeyValuePair>
		{
			new KeyValuePair
			{
				Name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled",
				Value = "True",
			},
			new KeyValuePair
			{
				Name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method",
				Value = "Standard",
			},
			new KeyValuePair
			{
				Name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate",
				Value = "1/1/0001 12:00:00 AM",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId",
				Value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name",
				Value = "LabelScopedToBob_Tests",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits",
				Value = "0",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId",
				Value = "00000000-0000-0000-0000-000000000000",
			},
		},
	},
	DowngradeJustification = new DowngradeJustification
	{
		JustificationMessage = "The information has been declassified.",
		IsDowngradeJustified = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Security.InformationProtection.SensitivityLabels.MicrosoftGraphSecurityEvaluateRemoval.PostAsEvaluateRemovalPostResponseAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphusers.ItemSecurityInformationProtectionSensitivityLabelsMicrosoft.graph.security.evaluateRemovalRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewEvaluateRemovalPostRequestBody()
contentInfo := graphmodelssecurity.NewContentInfo()
identifier := null
contentInfo.SetIdentifier(&identifier) 
state := graphmodels.REST_CONTENTSTATE 
contentInfo.SetState(&state) 


keyValuePair := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled"
keyValuePair.SetName(&name) 
value := "True"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method"
keyValuePair1.SetName(&name) 
value := "Standard"
keyValuePair1.SetValue(&value) 
keyValuePair2 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate"
keyValuePair2.SetName(&name) 
value := "1/1/0001 12:00:00 AM"
keyValuePair2.SetValue(&value) 
keyValuePair3 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId"
keyValuePair3.SetName(&name) 
value := "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
keyValuePair3.SetValue(&value) 
keyValuePair4 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name"
keyValuePair4.SetName(&name) 
value := "LabelScopedToBob_Tests"
keyValuePair4.SetValue(&value) 
keyValuePair5 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits"
keyValuePair5.SetName(&name) 
value := "0"
keyValuePair5.SetValue(&value) 
keyValuePair6 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId"
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
requestBody.SetContentInfo(contentInfo)
downgradeJustification := graphmodelssecurity.NewDowngradeJustification()
justificationMessage := "The information has been declassified."
downgradeJustification.SetJustificationMessage(&justificationMessage) 
isDowngradeJustified := true
downgradeJustification.SetIsDowngradeJustified(&isDowngradeJustified) 
requestBody.SetDowngradeJustification(downgradeJustification)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityEvaluateRemoval, err := graphClient.Users().ByUserId("user-id").Security().InformationProtection().SensitivityLabels().MicrosoftGraphSecurityEvaluateRemoval().PostAsEvaluateRemovalPostResponse(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.security.informationprotection.sensitivitylabels.microsoftgraphsecurityevaluateremoval.EvaluateRemovalPostRequestBody evaluateRemovalPostRequestBody = new com.microsoft.graph.beta.users.item.security.informationprotection.sensitivitylabels.microsoftgraphsecurityevaluateremoval.EvaluateRemovalPostRequestBody();
com.microsoft.graph.beta.models.security.ContentInfo contentInfo = new com.microsoft.graph.beta.models.security.ContentInfo();
contentInfo.setOdataType("#microsoft.graph.security.contentInfo");
contentInfo.setIdentifier(null);
contentInfo.setState(com.microsoft.graph.beta.models.security.ContentState.Rest);
LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair> metadata = new LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair>();
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair.setName("MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled");
keyValuePair.setValue("True");
metadata.add(keyValuePair);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair1 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair1.setName("MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method");
keyValuePair1.setValue("Standard");
metadata.add(keyValuePair1);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair2 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair2.setName("MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate");
keyValuePair2.setValue("1/1/0001 12:00:00 AM");
metadata.add(keyValuePair2);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair3 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair3.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair3.setName("MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId");
keyValuePair3.setValue("cfa4cf1d-a337-4481-aa99-19d8f3d63f7c");
metadata.add(keyValuePair3);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair4 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair4.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair4.setName("MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name");
keyValuePair4.setValue("LabelScopedToBob_Tests");
metadata.add(keyValuePair4);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair5 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair5.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair5.setName("MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits");
keyValuePair5.setValue("0");
metadata.add(keyValuePair5);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair6 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair6.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair6.setName("MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId");
keyValuePair6.setValue("00000000-0000-0000-0000-000000000000");
metadata.add(keyValuePair6);
contentInfo.setMetadata(metadata);
evaluateRemovalPostRequestBody.setContentInfo(contentInfo);
com.microsoft.graph.beta.models.security.DowngradeJustification downgradeJustification = new com.microsoft.graph.beta.models.security.DowngradeJustification();
downgradeJustification.setJustificationMessage("The information has been declassified.");
downgradeJustification.setIsDowngradeJustified(true);
evaluateRemovalPostRequestBody.setDowngradeJustification(downgradeJustification);
var result = graphClient.users().byUserId("{user-id}").security().informationProtection().sensitivityLabels().microsoftGraphSecurityEvaluateRemoval().post(evaluateRemovalPostRequestBody, requestConfiguration -> {
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
        identifier: null,
        state: 'rest',
        metadata: [
            {
                name: 'MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled',
                value: 'True'
            },
            {
                name: 'MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method',
                value: 'Standard'
            },
            {
                name: 'MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate',
                value: '1/1/0001 12:00:00 AM'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId',
                value: 'cfa4cf1d-a337-4481-aa99-19d8f3d63f7c'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name',
                value: 'LabelScopedToBob_Tests'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits',
                value: '0'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId',
                value: '00000000-0000-0000-0000-000000000000'
            }
        ]
    },
    downgradeJustification: {
        justificationMessage: 'The information has been declassified.',
        isDowngradeJustified: true
    }
};

await client.api('/users/bob@contoso.com/security/informationProtection/sensitivityLabels/evaluateRemoval')
	.version('beta')
	.post(informationProtectionAction);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Security\InformationProtection\SensitivityLabels\Microsoft\Graph\Security\EvaluateRemoval\EvaluateRemovalRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Users\Item\Security\InformationProtection\SensitivityLabels\MicrosoftGraphSecurityEvaluateRemoval\EvaluateRemovalPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Security\ContentInfo;
use Microsoft\Graph\Beta\Generated\Models\Security\ContentState;
use Microsoft\Graph\Beta\Generated\Models\Security\KeyValuePair;
use Microsoft\Graph\Beta\Generated\Models\Security\DowngradeJustification;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluateRemovalPostRequestBody();
$contentInfo = new ContentInfo();
$contentInfo->setOdataType('#microsoft.graph.security.contentInfo');
$contentInfo->setIdentifier(null);
$contentInfo->setState(new ContentState('rest'));
$metadataKeyValuePair1 = new KeyValuePair();
$metadataKeyValuePair1->setName('MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled');
$metadataKeyValuePair1->setValue('True');
$metadataArray []= $metadataKeyValuePair1;
$metadataKeyValuePair2 = new KeyValuePair();
$metadataKeyValuePair2->setName('MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method');
$metadataKeyValuePair2->setValue('Standard');
$metadataArray []= $metadataKeyValuePair2;
$metadataKeyValuePair3 = new KeyValuePair();
$metadataKeyValuePair3->setName('MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate');
$metadataKeyValuePair3->setValue('1/1/0001 12:00:00 AM');
$metadataArray []= $metadataKeyValuePair3;
$metadataKeyValuePair4 = new KeyValuePair();
$metadataKeyValuePair4->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair4->setName('MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId');
$metadataKeyValuePair4->setValue('cfa4cf1d-a337-4481-aa99-19d8f3d63f7c');
$metadataArray []= $metadataKeyValuePair4;
$metadataKeyValuePair5 = new KeyValuePair();
$metadataKeyValuePair5->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair5->setName('MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name');
$metadataKeyValuePair5->setValue('LabelScopedToBob_Tests');
$metadataArray []= $metadataKeyValuePair5;
$metadataKeyValuePair6 = new KeyValuePair();
$metadataKeyValuePair6->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair6->setName('MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits');
$metadataKeyValuePair6->setValue('0');
$metadataArray []= $metadataKeyValuePair6;
$metadataKeyValuePair7 = new KeyValuePair();
$metadataKeyValuePair7->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair7->setName('MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId');
$metadataKeyValuePair7->setValue('00000000-0000-0000-0000-000000000000');
$metadataArray []= $metadataKeyValuePair7;
$contentInfo->setMetadata($metadataArray);

$requestBody->setContentInfo($contentInfo);
$downgradeJustification = new DowngradeJustification();
$downgradeJustification->setJustificationMessage('The information has been declassified.');
$downgradeJustification->setIsDowngradeJustified(true);
$requestBody->setDowngradeJustification($downgradeJustification);
$requestConfiguration = new MicrosoftEvaluateRemovalRequestBuilderPostRequestConfiguration();
$headers = [
	'User-Agent' => 'ContosoLOBApp/1.0',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->security()->informationProtection()->sensitivityLabels()->microsoftGraphSecurityEvaluateRemoval()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	contentInfo = @{
		"@odata.type" = "#microsoft.graph.security.contentInfo"
		identifier = $null
		state = "rest"
		metadata = @(
			@{
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled"
				value = "True"
			}
			@{
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method"
				value = "Standard"
			}
			@{
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate"
				value = "1/1/0001 12:00:00 AM"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId"
				value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name"
				value = "LabelScopedToBob_Tests"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits"
				value = "0"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId"
				value = "00000000-0000-0000-0000-000000000000"
			}
		)
	}
	downgradeJustification = @{
		justificationMessage = "The information has been declassified."
		isDowngradeJustified = $true
	}
}

Test-MgBetaUserSecurityInformationProtectionSensitivityLabelRemoval -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.security.information_protection.sensitivity_labels.microsoft.graph.security.evaluate_removal.evaluate_removal_request_builder import EvaluateRemovalRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.users.item.security.informationprotection.sensitivitylabels.microsoft_graph_security_evaluate_removal.evaluate_removal_post_request_body import EvaluateRemovalPostRequestBody
from msgraph_beta.generated.models.security.content_info import ContentInfo
from msgraph_beta.generated.models.content_state import ContentState
from msgraph_beta.generated.models.security.key_value_pair import KeyValuePair
from msgraph_beta.generated.models.security.downgrade_justification import DowngradeJustification
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluateRemovalPostRequestBody(
	content_info = ContentInfo(
		odata_type = "#microsoft.graph.security.contentInfo",
		identifier = None,
		state = ContentState.Rest,
		metadata = [
			KeyValuePair(
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled",
				value = "True",
			),
			KeyValuePair(
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method",
				value = "Standard",
			),
			KeyValuePair(
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate",
				value = "1/1/0001 12:00:00 AM",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId",
				value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name",
				value = "LabelScopedToBob_Tests",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits",
				value = "0",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId",
				value = "00000000-0000-0000-0000-000000000000",
			),
		],
	),
	downgrade_justification = DowngradeJustification(
		justification_message = "The information has been declassified.",
		is_downgrade_justified = True,
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("User-Agent", "ContosoLOBApp/1.0")


result = await graph_client.users.by_user_id('user-id').security.information_protection.sensitivity_labels.microsoft_graph_security_evaluate_removal.post(request_body, request_configuration = request_configuration)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.security.informationProtectionAction)",
    "value": [
        {
            "@odata.type": "#microsoft.graph.security.metadataAction",
            "metadataToRemove": [
                "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled",
                "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method",
                "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate",
                "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId",
                "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name",
                "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits",
                "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId"
            ],
            "metadataToAdd": []
        }
    ]
}
```
