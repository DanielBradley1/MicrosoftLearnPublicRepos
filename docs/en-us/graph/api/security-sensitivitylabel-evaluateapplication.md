<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateapplication?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# sensitivityLabel: evaluateApplication

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Compute the [sensitivity label](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) that should be applied and return the set of actions that must be taken to correctly label the information. This API is useful when a label should be set manually or explicitly by a user or service, rather than automatically based on file contents.

Given [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-contentinfo?view=graph-rest-beta), which includes existing content metadata [key-value pairs](https://learn.microsoft.com/en-us/graph/api/resources/security-keyvaluepair?view=graph-rest-beta), and [labelingOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-labelingoptions?view=graph-rest-beta) as an input, the API returns an [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) object that contains one of more of the following:

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
POST /users/{usersId}/security/informationProtection/sensitivityLabels/evaluateApplication
POST /me/security/informationProtection/sensitivityLabels/evaluateApplication
```

To evaluate as a service principal \(application permission\):

```http
POST /security/informationProtection/sensitivityLabels/evaluateApplication
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| User-Agent | Describes the name of the calling application. Details will surface in Azure Information Protection Analytics. Suggested format is `ApplicationName/Version`. Optional. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentInfo | [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-contentinfo?view=graph-rest-beta) | Provides details on the content format, content state, and existing [metadata](https://learn.microsoft.com/en-us/graph/api/resources/security-keyvaluepair?view=graph-rest-beta) as key-value pairs. |
| labelingOptions | [labelingOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-labelingoptions?view=graph-rest-beta) | Provides details about the desired state of the content. |

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
POST https://graph.microsoft.com/beta/users/bob@contoso.com/security/informationProtection/sensitivityLabels/evaluateApplication
Content-Type: application/json
Content-length: 181
User-agent: ContosoLobApp/1.0

{
    "contentInfo": {
        "@odata.type": "#microsoft.graph.security.contentInfo",
        "format@odata.type": "#microsoft.graph.security.contentFormat",
        "contentFormat": "File",
        "format": "default",
        "identifier": null,
        "state@odata.type": "#microsoft.graph.security.contentState",
        "state": "rest",
        "metadata@odata.type": "#Collection(microsoft.graph.security.keyValuePair)",
        "metadata": [
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Enabled",
                "value": "True"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Method",
                "value": "Standard"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SetDate",
                "value": "1/1/0001 12:00:00 AM"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SiteId",
                "value": "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Name",
                "value": "LabelScopedToBob_Tests"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ContentBits",
                "value": "0"
            },
            {
                "@odata.type": "#microsoft.graph.security.keyValuePair",
                "name": "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ActionId",
                "value": "00000000-0000-0000-0000-000000000000"
            }
        ]
    },
    "labelingOptions": {
        "@odata.type": "#microsoft.graph.security.labelingOptions",
        "assignmentMethod@odata.type": "#microsoft.graph.security.assignmentMethod",
        "assignmentMethod": "standard",
        "labelId@odata.type": "#Guid",
        "labelId": "836ff34f-b604-4a62-a68c-d6be4205d569",
        "downgradeJustification": {
            "justificationMessage": "Justified",
            "isDowngradeJustified": true
        },
        "extendedProperties@odata.type": "#Collection(microsoft.graph.security.keyValuePair)",
        "extendedProperties": []
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.Security.InformationProtection.SensitivityLabels.MicrosoftGraphSecurityEvaluateApplication;
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new EvaluateApplicationPostRequestBody
{
	ContentInfo = new ContentInfo
	{
		OdataType = "#microsoft.graph.security.contentInfo",
		ContentFormat = "File",
		Identifier = null,
		State = ContentState.Rest,
		Metadata = new List<KeyValuePair>
		{
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Enabled",
				Value = "True",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Method",
				Value = "Standard",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SetDate",
				Value = "1/1/0001 12:00:00 AM",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SiteId",
				Value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Name",
				Value = "LabelScopedToBob_Tests",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ContentBits",
				Value = "0",
			},
			new KeyValuePair
			{
				OdataType = "#microsoft.graph.security.keyValuePair",
				Name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ActionId",
				Value = "00000000-0000-0000-0000-000000000000",
			},
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
			{
				"metadata@odata.type" , "#Collection(microsoft.graph.security.keyValuePair)"
			},
		},
	},
	LabelingOptions = new LabelingOptions
	{
		OdataType = "#microsoft.graph.security.labelingOptions",
		AssignmentMethod = AssignmentMethod.Standard,
		LabelId = "836ff34f-b604-4a62-a68c-d6be4205d569",
		DowngradeJustification = new DowngradeJustification
		{
			JustificationMessage = "Justified",
			IsDowngradeJustified = true,
		},
		ExtendedProperties = new List<KeyValuePair>
		{
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"assignmentMethod@odata.type" , "#microsoft.graph.security.assignmentMethod"
			},
			{
				"labelId@odata.type" , "#Guid"
			},
			{
				"extendedProperties@odata.type" , "#Collection(microsoft.graph.security.keyValuePair)"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Security.InformationProtection.SensitivityLabels.MicrosoftGraphSecurityEvaluateApplication.PostAsEvaluateApplicationPostResponseAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("User-Agent", "ContosoLobApp/1.0");
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
headers.Add("User-Agent", "ContosoLobApp/1.0")

configuration := &graphusers.ItemSecurityInformationProtectionSensitivityLabelsMicrosoft.graph.security.evaluateApplicationRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewEvaluateApplicationPostRequestBody()
contentInfo := graphmodelssecurity.NewContentInfo()
contentFormat := "File"
contentInfo.SetContentFormat(&contentFormat) 
identifier := null
contentInfo.SetIdentifier(&identifier) 
state := graphmodels.REST_CONTENTSTATE 
contentInfo.SetState(&state) 


keyValuePair := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Enabled"
keyValuePair.SetName(&name) 
value := "True"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Method"
keyValuePair1.SetName(&name) 
value := "Standard"
keyValuePair1.SetValue(&value) 
keyValuePair2 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SetDate"
keyValuePair2.SetName(&name) 
value := "1/1/0001 12:00:00 AM"
keyValuePair2.SetValue(&value) 
keyValuePair3 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SiteId"
keyValuePair3.SetName(&name) 
value := "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
keyValuePair3.SetValue(&value) 
keyValuePair4 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Name"
keyValuePair4.SetName(&name) 
value := "LabelScopedToBob_Tests"
keyValuePair4.SetValue(&value) 
keyValuePair5 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ContentBits"
keyValuePair5.SetName(&name) 
value := "0"
keyValuePair5.SetValue(&value) 
keyValuePair6 := graphmodelssecurity.NewKeyValuePair()
name := "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ActionId"
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
	"format@odata.type" : "#microsoft.graph.security.contentFormat", 
	"format" : "default", 
	"state@odata.type" : "#microsoft.graph.security.contentState", 
	"metadata@odata.type" : "#Collection(microsoft.graph.security.keyValuePair)", 
}
contentInfo.SetAdditionalData(additionalData)
requestBody.SetContentInfo(contentInfo)
labelingOptions := graphmodelssecurity.NewLabelingOptions()
assignmentMethod := graphmodels.STANDARD_ASSIGNMENTMETHOD 
labelingOptions.SetAssignmentMethod(&assignmentMethod) 
labelId := "836ff34f-b604-4a62-a68c-d6be4205d569"
labelingOptions.SetLabelId(&labelId) 
downgradeJustification := graphmodelssecurity.NewDowngradeJustification()
justificationMessage := "Justified"
downgradeJustification.SetJustificationMessage(&justificationMessage) 
isDowngradeJustified := true
downgradeJustification.SetIsDowngradeJustified(&isDowngradeJustified) 
labelingOptions.SetDowngradeJustification(downgradeJustification)
extendedProperties := []graphmodelssecurity.KeyValuePairable {

}
labelingOptions.SetExtendedProperties(extendedProperties)
additionalData := map[string]interface{}{
	"assignmentMethod@odata.type" : "#microsoft.graph.security.assignmentMethod", 
	"labelId@odata.type" : "#Guid", 
	"extendedProperties@odata.type" : "#Collection(microsoft.graph.security.keyValuePair)", 
}
labelingOptions.SetAdditionalData(additionalData)
requestBody.SetLabelingOptions(labelingOptions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityEvaluateApplication, err := graphClient.Users().ByUserId("user-id").Security().InformationProtection().SensitivityLabels().MicrosoftGraphSecurityEvaluateApplication().PostAsEvaluateApplicationPostResponse(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.security.informationprotection.sensitivitylabels.microsoftgraphsecurityevaluateapplication.EvaluateApplicationPostRequestBody evaluateApplicationPostRequestBody = new com.microsoft.graph.beta.users.item.security.informationprotection.sensitivitylabels.microsoftgraphsecurityevaluateapplication.EvaluateApplicationPostRequestBody();
com.microsoft.graph.beta.models.security.ContentInfo contentInfo = new com.microsoft.graph.beta.models.security.ContentInfo();
contentInfo.setOdataType("#microsoft.graph.security.contentInfo");
contentInfo.setContentFormat("File");
contentInfo.setIdentifier(null);
contentInfo.setState(com.microsoft.graph.beta.models.security.ContentState.Rest);
LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair> metadata = new LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair>();
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair.setName("MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Enabled");
keyValuePair.setValue("True");
metadata.add(keyValuePair);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair1 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair1.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair1.setName("MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Method");
keyValuePair1.setValue("Standard");
metadata.add(keyValuePair1);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair2 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair2.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair2.setName("MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SetDate");
keyValuePair2.setValue("1/1/0001 12:00:00 AM");
metadata.add(keyValuePair2);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair3 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair3.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair3.setName("MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SiteId");
keyValuePair3.setValue("cfa4cf1d-a337-4481-aa99-19d8f3d63f7c");
metadata.add(keyValuePair3);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair4 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair4.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair4.setName("MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Name");
keyValuePair4.setValue("LabelScopedToBob_Tests");
metadata.add(keyValuePair4);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair5 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair5.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair5.setName("MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ContentBits");
keyValuePair5.setValue("0");
metadata.add(keyValuePair5);
com.microsoft.graph.beta.models.security.KeyValuePair keyValuePair6 = new com.microsoft.graph.beta.models.security.KeyValuePair();
keyValuePair6.setOdataType("#microsoft.graph.security.keyValuePair");
keyValuePair6.setName("MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ActionId");
keyValuePair6.setValue("00000000-0000-0000-0000-000000000000");
metadata.add(keyValuePair6);
contentInfo.setMetadata(metadata);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("format@odata.type", "#microsoft.graph.security.contentFormat");
additionalData.put("format", "default");
additionalData.put("state@odata.type", "#microsoft.graph.security.contentState");
additionalData.put("metadata@odata.type", "#Collection(microsoft.graph.security.keyValuePair)");
contentInfo.setAdditionalData(additionalData);
evaluateApplicationPostRequestBody.setContentInfo(contentInfo);
com.microsoft.graph.beta.models.security.LabelingOptions labelingOptions = new com.microsoft.graph.beta.models.security.LabelingOptions();
labelingOptions.setOdataType("#microsoft.graph.security.labelingOptions");
labelingOptions.setAssignmentMethod(com.microsoft.graph.beta.models.security.AssignmentMethod.Standard);
labelingOptions.setLabelId("836ff34f-b604-4a62-a68c-d6be4205d569");
com.microsoft.graph.beta.models.security.DowngradeJustification downgradeJustification = new com.microsoft.graph.beta.models.security.DowngradeJustification();
downgradeJustification.setJustificationMessage("Justified");
downgradeJustification.setIsDowngradeJustified(true);
labelingOptions.setDowngradeJustification(downgradeJustification);
LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair> extendedProperties = new LinkedList<com.microsoft.graph.beta.models.security.KeyValuePair>();
labelingOptions.setExtendedProperties(extendedProperties);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("assignmentMethod@odata.type", "#microsoft.graph.security.assignmentMethod");
additionalData1.put("labelId@odata.type", "#Guid");
additionalData1.put("extendedProperties@odata.type", "#Collection(microsoft.graph.security.keyValuePair)");
labelingOptions.setAdditionalData(additionalData1);
evaluateApplicationPostRequestBody.setLabelingOptions(labelingOptions);
var result = graphClient.users().byUserId("{user-id}").security().informationProtection().sensitivityLabels().microsoftGraphSecurityEvaluateApplication().post(evaluateApplicationPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("User-Agent", "ContosoLobApp/1.0");
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
        contentFormat: 'File',
        format: 'default',
        identifier: null,
        'state@odata.type': '#microsoft.graph.security.contentState',
        state: 'rest',
        'metadata@odata.type': '#Collection(microsoft.graph.security.keyValuePair)',
        metadata: [
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Enabled',
                value: 'True'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Method',
                value: 'Standard'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SetDate',
                value: '1/1/0001 12:00:00 AM'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SiteId',
                value: 'cfa4cf1d-a337-4481-aa99-19d8f3d63f7c'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Name',
                value: 'LabelScopedToBob_Tests'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ContentBits',
                value: '0'
            },
            {
                '@odata.type': '#microsoft.graph.security.keyValuePair',
                name: 'MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ActionId',
                value: '00000000-0000-0000-0000-000000000000'
            }
        ]
    },
    labelingOptions: {
        '@odata.type': '#microsoft.graph.security.labelingOptions',
        'assignmentMethod@odata.type': '#microsoft.graph.security.assignmentMethod',
        assignmentMethod: 'standard',
        'labelId@odata.type': '#Guid',
        labelId: '836ff34f-b604-4a62-a68c-d6be4205d569',
        downgradeJustification: {
            justificationMessage: 'Justified',
            isDowngradeJustified: true
        },
        'extendedProperties@odata.type': '#Collection(microsoft.graph.security.keyValuePair)',
        extendedProperties: []
    }
};

await client.api('/users/bob@contoso.com/security/informationProtection/sensitivityLabels/evaluateApplication')
	.version('beta')
	.post(informationProtectionAction);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Security\InformationProtection\SensitivityLabels\Microsoft\Graph\Security\EvaluateApplication\EvaluateApplicationRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Users\Item\Security\InformationProtection\SensitivityLabels\MicrosoftGraphSecurityEvaluateApplication\EvaluateApplicationPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Security\ContentInfo;
use Microsoft\Graph\Beta\Generated\Models\Security\ContentState;
use Microsoft\Graph\Beta\Generated\Models\Security\KeyValuePair;
use Microsoft\Graph\Beta\Generated\Models\Security\LabelingOptions;
use Microsoft\Graph\Beta\Generated\Models\Security\AssignmentMethod;
use Microsoft\Graph\Beta\Generated\Models\Security\DowngradeJustification;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluateApplicationPostRequestBody();
$contentInfo = new ContentInfo();
$contentInfo->setOdataType('#microsoft.graph.security.contentInfo');
$contentInfo->setContentFormat('File');
$contentInfo->setIdentifier(null);
$contentInfo->setState(new ContentState('rest'));
$metadataKeyValuePair1 = new KeyValuePair();
$metadataKeyValuePair1->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair1->setName('MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Enabled');
$metadataKeyValuePair1->setValue('True');
$metadataArray []= $metadataKeyValuePair1;
$metadataKeyValuePair2 = new KeyValuePair();
$metadataKeyValuePair2->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair2->setName('MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Method');
$metadataKeyValuePair2->setValue('Standard');
$metadataArray []= $metadataKeyValuePair2;
$metadataKeyValuePair3 = new KeyValuePair();
$metadataKeyValuePair3->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair3->setName('MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SetDate');
$metadataKeyValuePair3->setValue('1/1/0001 12:00:00 AM');
$metadataArray []= $metadataKeyValuePair3;
$metadataKeyValuePair4 = new KeyValuePair();
$metadataKeyValuePair4->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair4->setName('MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SiteId');
$metadataKeyValuePair4->setValue('cfa4cf1d-a337-4481-aa99-19d8f3d63f7c');
$metadataArray []= $metadataKeyValuePair4;
$metadataKeyValuePair5 = new KeyValuePair();
$metadataKeyValuePair5->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair5->setName('MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Name');
$metadataKeyValuePair5->setValue('LabelScopedToBob_Tests');
$metadataArray []= $metadataKeyValuePair5;
$metadataKeyValuePair6 = new KeyValuePair();
$metadataKeyValuePair6->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair6->setName('MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ContentBits');
$metadataKeyValuePair6->setValue('0');
$metadataArray []= $metadataKeyValuePair6;
$metadataKeyValuePair7 = new KeyValuePair();
$metadataKeyValuePair7->setOdataType('#microsoft.graph.security.keyValuePair');
$metadataKeyValuePair7->setName('MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ActionId');
$metadataKeyValuePair7->setValue('00000000-0000-0000-0000-000000000000');
$metadataArray []= $metadataKeyValuePair7;
$contentInfo->setMetadata($metadataArray);

$additionalData = [
'format@odata.type' => '#microsoft.graph.security.contentFormat',
'format' => 'default',
'state@odata.type' => '#microsoft.graph.security.contentState',
'metadata@odata.type' => '#Collection(microsoft.graph.security.keyValuePair)',
];
$contentInfo->setAdditionalData($additionalData);
$requestBody->setContentInfo($contentInfo);
$labelingOptions = new LabelingOptions();
$labelingOptions->setOdataType('#microsoft.graph.security.labelingOptions');
$labelingOptions->setAssignmentMethod(new AssignmentMethod('standard'));
$labelingOptions->setLabelId('836ff34f-b604-4a62-a68c-d6be4205d569');
$labelingOptionsDowngradeJustification = new DowngradeJustification();
$labelingOptionsDowngradeJustification->setJustificationMessage('Justified');
$labelingOptionsDowngradeJustification->setIsDowngradeJustified(true);
$labelingOptions->setDowngradeJustification($labelingOptionsDowngradeJustification);
$labelingOptions->setExtendedProperties([]);
$additionalData = [
'assignmentMethod@odata.type' => '#microsoft.graph.security.assignmentMethod',
'labelId@odata.type' => '#Guid',
'extendedProperties@odata.type' => '#Collection(microsoft.graph.security.keyValuePair)',
];
$labelingOptions->setAdditionalData($additionalData);
$requestBody->setLabelingOptions($labelingOptions);
$requestConfiguration = new MicrosoftEvaluateApplicationRequestBuilderPostRequestConfiguration();
$headers = [
	'User-Agent' => 'ContosoLobApp/1.0',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->security()->informationProtection()->sensitivityLabels()->microsoftGraphSecurityEvaluateApplication()->post($requestBody, $requestConfiguration)->wait();
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
		contentFormat = "File"
		format = "default"
		identifier = $null
		"state@odata.type" = "#microsoft.graph.security.contentState"
		state = "rest"
		"metadata@odata.type" = "#Collection(microsoft.graph.security.keyValuePair)"
		metadata = @(
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Enabled"
				value = "True"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Method"
				value = "Standard"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SetDate"
				value = "1/1/0001 12:00:00 AM"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SiteId"
				value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Name"
				value = "LabelScopedToBob_Tests"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ContentBits"
				value = "0"
			}
			@{
				"@odata.type" = "#microsoft.graph.security.keyValuePair"
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ActionId"
				value = "00000000-0000-0000-0000-000000000000"
			}
		)
	}
	labelingOptions = @{
		"@odata.type" = "#microsoft.graph.security.labelingOptions"
		"assignmentMethod@odata.type" = "#microsoft.graph.security.assignmentMethod"
		assignmentMethod = "standard"
		"labelId@odata.type" = "#Guid"
		labelId = "836ff34f-b604-4a62-a68c-d6be4205d569"
		downgradeJustification = @{
			justificationMessage = "Justified"
			isDowngradeJustified = $true
		}
		"extendedProperties@odata.type" = "#Collection(microsoft.graph.security.keyValuePair)"
		extendedProperties = @(
		)
	}
}

Test-MgBetaUserSecurityInformationProtectionSensitivityLabelApplication -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.security.information_protection.sensitivity_labels.microsoft.graph.security.evaluate_application.evaluate_application_request_builder import EvaluateApplicationRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.users.item.security.informationprotection.sensitivitylabels.microsoft_graph_security_evaluate_application.evaluate_application_post_request_body import EvaluateApplicationPostRequestBody
from msgraph_beta.generated.models.security.content_info import ContentInfo
from msgraph_beta.generated.models.content_state import ContentState
from msgraph_beta.generated.models.security.key_value_pair import KeyValuePair
from msgraph_beta.generated.models.security.labeling_options import LabelingOptions
from msgraph_beta.generated.models.assignment_method import AssignmentMethod
from msgraph_beta.generated.models.security.downgrade_justification import DowngradeJustification
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluateApplicationPostRequestBody(
	content_info = ContentInfo(
		odata_type = "#microsoft.graph.security.contentInfo",
		content_format = "File",
		identifier = None,
		state = ContentState.Rest,
		metadata = [
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Enabled",
				value = "True",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Method",
				value = "Standard",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SetDate",
				value = "1/1/0001 12:00:00 AM",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_SiteId",
				value = "cfa4cf1d-a337-4481-aa99-19d8f3d63f7c",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_Name",
				value = "LabelScopedToBob_Tests",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ContentBits",
				value = "0",
			),
			KeyValuePair(
				odata_type = "#microsoft.graph.security.keyValuePair",
				name = "MSIP_Label_3a80e051-487c-40d4-b491-73ad25d997e6_ActionId",
				value = "00000000-0000-0000-0000-000000000000",
			),
		],
		additional_data = {
				"format@odata_type" : "#microsoft.graph.security.contentFormat",
				"format" : "default",
				"state@odata_type" : "#microsoft.graph.security.contentState",
				"metadata@odata_type" : "#Collection(microsoft.graph.security.keyValuePair)",
		}
	),
	labeling_options = LabelingOptions(
		odata_type = "#microsoft.graph.security.labelingOptions",
		assignment_method = AssignmentMethod.Standard,
		label_id = "836ff34f-b604-4a62-a68c-d6be4205d569",
		downgrade_justification = DowngradeJustification(
			justification_message = "Justified",
			is_downgrade_justified = True,
		),
		extended_properties = [
		],
		additional_data = {
				"assignment_method@odata_type" : "#microsoft.graph.security.assignmentMethod",
				"label_id@odata_type" : "#Guid",
				"extended_properties@odata_type" : "#Collection(microsoft.graph.security.keyValuePair)",
		}
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("User-Agent", "ContosoLobApp/1.0")


result = await graph_client.users.by_user_id('user-id').security.information_protection.sensitivity_labels.microsoft_graph_security_evaluate_application.post(request_body, request_configuration = request_configuration)
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
            "@odata.type": "#microsoft.graph.security.addContentHeaderAction",
            "uiElementName": "MSIPCM_v1_header",
            "text": "HIGHLY CONFIDENTIAL",
            "fontName": "Calibri",
            "fontSize": 12,
            "fontColor": "#000000",
            "alignment": "left",
            "margin": 5
        },
        {
            "@odata.type": "#microsoft.graph.security.addWatermarkAction",
            "uiElementName": "MSIPWM_v1_main",
            "layout": "diagonal",
            "text": "HIGHLY CONFIDENTIAL",
            "fontName": "Calibri",
            "fontSize": 72,
            "fontColor": "#000000"
        },
        {
            "@odata.type": "#microsoft.graph.security.addContentFooterAction",
            "uiElementName": "MSIPCM_v1_footer",
            "text": "HIGHLY CONFIDENTIAL",
            "fontName": "Calibri",
            "fontSize": 12,
            "fontColor": "#000000",
            "alignment": "left",
            "margin": 5
        },
        {
            "@odata.type": "#microsoft.graph.security.protectByTemplateAction",
            "templateId": "684d0d40-83d4-4ce6-a5e7-0efb9fffb2dc"
        },
        {
            "@odata.type": "#microsoft.graph.security.metadataAction",
            "metadataToRemove": [],
            "metadataToAdd": [
                {
                    "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Enabled",
                    "value": "true"
                },
                {
                    "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SetDate",
                    "value": "2022-03-04T22:48:13Z"
                },
                {
                    "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Method",
                    "value": "Standard"
                },
                {
                    "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_Name",
                    "value": "FTEs_HC"
                },
                {
                    "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_SiteId",
                    "value": "29375103-6ce7-4dba-81ec-8e33884c6f0f"
                },
                {
                    "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ActionId",
                    "value": "14368e92-2e6a-46c4-9a48-5117de375b66"
                },
                {
                    "name": "MSIP_Label_836ff34f-b604-4a62-a68c-d6be4205d569_ContentBits",
                    "value": "15"
                }
            ]
        }
    ]
}
```
