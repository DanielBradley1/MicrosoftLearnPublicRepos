<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationeventsflow-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update authenticationEventsFlow

Namespace: microsoft.graph

Update the properties of an [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object by ID. You must specify the **@odata.type** property and the value of the [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object type to update. The following derived subtypes are supported:

- [externalUsersSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EventListener.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EventListener.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External ID User Flow Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /identity/authenticationEventsFlows/{authenticationEventsFlow-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must include the **@odata.type** property with a value of the specific user flow type in the body. For example, `"@odata.type": "#microsoft.graph.externalUsersSelfServiceSignupEventsFlow"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the entity. Read-only. |
| displayName | String | The display name for the events policy. |
| description | String | The description of the events policy. |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | The conditions representing the context of the authentication request that is used to decide whether the events policy is invoked. |
| onInteractiveAuthFlowStart | [onInteractiveAuthFlowStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstarthandler?view=graph-rest-1.0) | The configuration for what to invoke for the onInteractiveAuthFlowStart event. |
| onAuthenticationMethodLoadStart | [onAuthenticationMethodLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstarthandler?view=graph-rest-1.0) | The configuration for what to invoke for the onAuthenticationMethodLoadStart event. Must have at least one identity provider linked. |
| onAttributeCollection | [onAttributeCollectionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionhandler?view=graph-rest-1.0) | The configuration for what to invoke for the onAttributeCollection event.  <br>  <br><br><br><li> You can only update this property if it was configured during user flow creation. If it wasn&#39;t, call the <a href="https://learn.microsoft.com/en-us/graph/api/onattributecollectionexternalusersselfservicesignup-post-attributes?view=graph-rest-1.0" data-linktype="relative-path">Add attributes to a user flow</a> API first. </li><br><br><li> You can&#39;t add or remove attributes by updating the <strong>attributeCollectionPage</strong> &gt; <strong>views</strong> &gt; <strong>inputs</strong> and <strong>attributes</strong> objects. Use the <a href="https://learn.microsoft.com/en-us/graph/api/onattributecollectionexternalusersselfservicesignup-post-attributes?view=graph-rest-1.0" data-linktype="relative-path">Add attribute to user flow</a> or <a href="https://learn.microsoft.com/en-us/graph/api/onattributecollectionexternalusersselfservicesignup-post-attributes?view=graph-rest-1.0" data-linktype="relative-path">Remove attribute from user flow</a> APIs instead to update both objects.</li><br><br><li> To update the <strong>attributeCollectionPage</strong> &gt; <strong>views</strong> &gt; <strong>inputs</strong> collection, you must include all objects in the collection, not only the changed objects. </li><br><br><li> The order of objects in the <strong>attributeCollectionPage</strong> &gt; <strong>views</strong> &gt; <strong>inputs</strong> collection corresponds to the order in which the attributes are displayed on the app&#39;s sign-up UI.</li> |
| onUserCreateStart | [onUserCreateStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestarthandler?view=graph-rest-1.0) | The configuration for what to invoke for the onUserCreateStart event. |

## Response

If successful, this method returns a `204 No Content` response code. If unsuccessful, a `4xx` error is returned with specific details.

## Examples

### Example 1: Update the display name of an external identities self-service sign-up user flow

#### Request

The following example shows a request that updates the display name of a specific external identities user flow.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows/0313cc37-d421-421d-857b-87804d61e33e
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
  "displayName": "New user flow description",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExternalUsersSelfServiceSignUpEventsFlow
{
	OdataType = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
	DisplayName = "New user flow description",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows["{authenticationEventsFlow-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAuthenticationEventsFlow()
displayName := "New user flow description"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().ByAuthenticationEventsFlowId("authenticationEventsFlow-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalUsersSelfServiceSignUpEventsFlow authenticationEventsFlow = new ExternalUsersSelfServiceSignUpEventsFlow();
authenticationEventsFlow.setOdataType("#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow");
authenticationEventsFlow.setDisplayName("New user flow description");
AuthenticationEventsFlow result = graphClient.identity().authenticationEventsFlows().byAuthenticationEventsFlowId("{authenticationEventsFlow-id}").patch(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventsFlow = {
  '@odata.type': '#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow',
  displayName: 'New user flow description',
};

await client.api('/identity/authenticationEventsFlows/0313cc37-d421-421d-857b-87804d61e33e')
	.update(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalUsersSelfServiceSignUpEventsFlow;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalUsersSelfServiceSignUpEventsFlow();
$requestBody->setOdataType('#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow');
$requestBody->setDisplayName('New user flow description');

$result = $graphServiceClient->identity()->authenticationEventsFlows()->byAuthenticationEventsFlowId('authenticationEventsFlow-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow"
	displayName = "New user flow description"
}

Update-MgIdentityAuthenticationEventFlow -AuthenticationEventsFlowId $authenticationEventsFlowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_users_self_service_sign_up_events_flow import ExternalUsersSelfServiceSignUpEventsFlow
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalUsersSelfServiceSignUpEventsFlow(
	odata_type = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
	display_name = "New user flow description",
)

result = await graph_client.identity.authentication_events_flows.by_authentication_events_flow_id('authenticationEventsFlow-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Update the page layout of a self-service sign up user flow

The following request updates the configuration of some of the attributes. All the attributes are marked as required; the email attribute is marked as hidden; the input type of the custom attribute is also updated to a radio button with two options.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows/0313cc37-d421-421d-857b-87804d61e33e
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
    "onAttributeCollection": {
        "@odata.type": "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
        "attributeCollectionPage": {
            "views": [
                {
                    "title": null,
                    "description": null,
                    "inputs": [
                        {
                            "attribute": "email",
                            "label": "Email Address",
                            "inputType": "text",
                            "defaultValue": null,
                            "hidden": true,
                            "editable": false,
                            "writeToDirectory": true,
                            "required": true,
                            "validationRegEx": "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
                            "options": []
                        },
                        {
                            "attribute": "displayName",
                            "label": "Display Name",
                            "inputType": "text",
                            "defaultValue": null,
                            "hidden": false,
                            "editable": true,
                            "writeToDirectory": true,
                            "required": true,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
                            "options": []
                        },
                        {
                            "attribute": "city",
                            "label": "City",
                            "inputType": "text",
                            "defaultValue": null,
                            "hidden": false,
                            "editable": true,
                            "writeToDirectory": true,
                            "required": true,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
                            "options": []
                        },
                        {
                            "attribute": "extension_331d514c0c18477583ea7dd5a79feda2_RockorCountry",
                            "label": "Rock music or Country",
                            "inputType": "radioSingleSelect",
                            "defaultValue": null,
                            "hidden": false,
                            "editable": true,
                            "writeToDirectory": true,
                            "required": true,
                            "validationRegEx": "^.*",
                            "options": [
                                {
                                    "label": "Rock music",
                                    "value": "Rock"
                                },
                                {
                                    "label": "Country music",
                                    "value": "Country"
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExternalUsersSelfServiceSignUpEventsFlow
{
	OdataType = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
	OnAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
		AttributeCollectionPage = new AuthenticationAttributeCollectionPage
		{
			Views = new List<AuthenticationAttributeCollectionPageViewConfiguration>
			{
				new AuthenticationAttributeCollectionPageViewConfiguration
				{
					Title = null,
					Description = null,
					Inputs = new List<AuthenticationAttributeCollectionInputConfiguration>
					{
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "email",
							Label = "Email Address",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							DefaultValue = null,
							Hidden = true,
							Editable = false,
							WriteToDirectory = true,
							Required = true,
							ValidationRegEx = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
							Options = new List<AuthenticationAttributeCollectionOptionConfiguration>
							{
							},
						},
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "displayName",
							Label = "Display Name",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							DefaultValue = null,
							Hidden = false,
							Editable = true,
							WriteToDirectory = true,
							Required = true,
							ValidationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
							Options = new List<AuthenticationAttributeCollectionOptionConfiguration>
							{
							},
						},
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "city",
							Label = "City",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							DefaultValue = null,
							Hidden = false,
							Editable = true,
							WriteToDirectory = true,
							Required = true,
							ValidationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
							Options = new List<AuthenticationAttributeCollectionOptionConfiguration>
							{
							},
						},
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "extension_331d514c0c18477583ea7dd5a79feda2_RockorCountry",
							Label = "Rock music or Country",
							InputType = AuthenticationAttributeCollectionInputType.RadioSingleSelect,
							DefaultValue = null,
							Hidden = false,
							Editable = true,
							WriteToDirectory = true,
							Required = true,
							ValidationRegEx = "^.*",
							Options = new List<AuthenticationAttributeCollectionOptionConfiguration>
							{
								new AuthenticationAttributeCollectionOptionConfiguration
								{
									Label = "Rock music",
									Value = "Rock",
								},
								new AuthenticationAttributeCollectionOptionConfiguration
								{
									Label = "Country music",
									Value = "Country",
								},
							},
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows["{authenticationEventsFlow-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAuthenticationEventsFlow()
onAttributeCollection := graphmodels.NewOnAttributeCollectionExternalUsersSelfServiceSignUp()
attributeCollectionPage := graphmodels.NewAuthenticationAttributeCollectionPage()


authenticationAttributeCollectionPageViewConfiguration := graphmodels.NewAuthenticationAttributeCollectionPageViewConfiguration()
title := null
authenticationAttributeCollectionPageViewConfiguration.SetTitle(&title) 
description := null
authenticationAttributeCollectionPageViewConfiguration.SetDescription(&description) 


authenticationAttributeCollectionInputConfiguration := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "email"
authenticationAttributeCollectionInputConfiguration.SetAttribute(&attribute) 
label := "Email Address"
authenticationAttributeCollectionInputConfiguration.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration.SetInputType(&inputType) 
defaultValue := null
authenticationAttributeCollectionInputConfiguration.SetDefaultValue(&defaultValue) 
hidden := true
authenticationAttributeCollectionInputConfiguration.SetHidden(&hidden) 
editable := false
authenticationAttributeCollectionInputConfiguration.SetEditable(&editable) 
writeToDirectory := true
authenticationAttributeCollectionInputConfiguration.SetWriteToDirectory(&writeToDirectory) 
required := true
authenticationAttributeCollectionInputConfiguration.SetRequired(&required) 
validationRegEx := "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$"
authenticationAttributeCollectionInputConfiguration.SetValidationRegEx(&validationRegEx) 
options := []graphmodels.AuthenticationAttributeCollectionOptionConfigurationable {

}
authenticationAttributeCollectionInputConfiguration.SetOptions(options)
authenticationAttributeCollectionInputConfiguration1 := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "displayName"
authenticationAttributeCollectionInputConfiguration1.SetAttribute(&attribute) 
label := "Display Name"
authenticationAttributeCollectionInputConfiguration1.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration1.SetInputType(&inputType) 
defaultValue := null
authenticationAttributeCollectionInputConfiguration1.SetDefaultValue(&defaultValue) 
hidden := false
authenticationAttributeCollectionInputConfiguration1.SetHidden(&hidden) 
editable := true
authenticationAttributeCollectionInputConfiguration1.SetEditable(&editable) 
writeToDirectory := true
authenticationAttributeCollectionInputConfiguration1.SetWriteToDirectory(&writeToDirectory) 
required := true
authenticationAttributeCollectionInputConfiguration1.SetRequired(&required) 
validationRegEx := "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
authenticationAttributeCollectionInputConfiguration1.SetValidationRegEx(&validationRegEx) 
options := []graphmodels.AuthenticationAttributeCollectionOptionConfigurationable {

}
authenticationAttributeCollectionInputConfiguration1.SetOptions(options)
authenticationAttributeCollectionInputConfiguration2 := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "city"
authenticationAttributeCollectionInputConfiguration2.SetAttribute(&attribute) 
label := "City"
authenticationAttributeCollectionInputConfiguration2.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration2.SetInputType(&inputType) 
defaultValue := null
authenticationAttributeCollectionInputConfiguration2.SetDefaultValue(&defaultValue) 
hidden := false
authenticationAttributeCollectionInputConfiguration2.SetHidden(&hidden) 
editable := true
authenticationAttributeCollectionInputConfiguration2.SetEditable(&editable) 
writeToDirectory := true
authenticationAttributeCollectionInputConfiguration2.SetWriteToDirectory(&writeToDirectory) 
required := true
authenticationAttributeCollectionInputConfiguration2.SetRequired(&required) 
validationRegEx := "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
authenticationAttributeCollectionInputConfiguration2.SetValidationRegEx(&validationRegEx) 
options := []graphmodels.AuthenticationAttributeCollectionOptionConfigurationable {

}
authenticationAttributeCollectionInputConfiguration2.SetOptions(options)
authenticationAttributeCollectionInputConfiguration3 := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "extension_331d514c0c18477583ea7dd5a79feda2_RockorCountry"
authenticationAttributeCollectionInputConfiguration3.SetAttribute(&attribute) 
label := "Rock music or Country"
authenticationAttributeCollectionInputConfiguration3.SetLabel(&label) 
inputType := graphmodels.RADIOSINGLESELECT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration3.SetInputType(&inputType) 
defaultValue := null
authenticationAttributeCollectionInputConfiguration3.SetDefaultValue(&defaultValue) 
hidden := false
authenticationAttributeCollectionInputConfiguration3.SetHidden(&hidden) 
editable := true
authenticationAttributeCollectionInputConfiguration3.SetEditable(&editable) 
writeToDirectory := true
authenticationAttributeCollectionInputConfiguration3.SetWriteToDirectory(&writeToDirectory) 
required := true
authenticationAttributeCollectionInputConfiguration3.SetRequired(&required) 
validationRegEx := "^.*"
authenticationAttributeCollectionInputConfiguration3.SetValidationRegEx(&validationRegEx) 


authenticationAttributeCollectionOptionConfiguration := graphmodels.NewAuthenticationAttributeCollectionOptionConfiguration()
label := "Rock music"
authenticationAttributeCollectionOptionConfiguration.SetLabel(&label) 
value := "Rock"
authenticationAttributeCollectionOptionConfiguration.SetValue(&value) 
authenticationAttributeCollectionOptionConfiguration1 := graphmodels.NewAuthenticationAttributeCollectionOptionConfiguration()
label := "Country music"
authenticationAttributeCollectionOptionConfiguration1.SetLabel(&label) 
value := "Country"
authenticationAttributeCollectionOptionConfiguration1.SetValue(&value) 

options := []graphmodels.AuthenticationAttributeCollectionOptionConfigurationable {
	authenticationAttributeCollectionOptionConfiguration,
	authenticationAttributeCollectionOptionConfiguration1,
}
authenticationAttributeCollectionInputConfiguration3.SetOptions(options)

inputs := []graphmodels.AuthenticationAttributeCollectionInputConfigurationable {
	authenticationAttributeCollectionInputConfiguration,
	authenticationAttributeCollectionInputConfiguration1,
	authenticationAttributeCollectionInputConfiguration2,
	authenticationAttributeCollectionInputConfiguration3,
}
authenticationAttributeCollectionPageViewConfiguration.SetInputs(inputs)

views := []graphmodels.AuthenticationAttributeCollectionPageViewConfigurationable {
	authenticationAttributeCollectionPageViewConfiguration,
}
attributeCollectionPage.SetViews(views)
onAttributeCollection.SetAttributeCollectionPage(attributeCollectionPage)
requestBody.SetOnAttributeCollection(onAttributeCollection)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().ByAuthenticationEventsFlowId("authenticationEventsFlow-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalUsersSelfServiceSignUpEventsFlow authenticationEventsFlow = new ExternalUsersSelfServiceSignUpEventsFlow();
authenticationEventsFlow.setOdataType("#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow");
OnAttributeCollectionExternalUsersSelfServiceSignUp onAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp();
onAttributeCollection.setOdataType("#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp");
AuthenticationAttributeCollectionPage attributeCollectionPage = new AuthenticationAttributeCollectionPage();
LinkedList<AuthenticationAttributeCollectionPageViewConfiguration> views = new LinkedList<AuthenticationAttributeCollectionPageViewConfiguration>();
AuthenticationAttributeCollectionPageViewConfiguration authenticationAttributeCollectionPageViewConfiguration = new AuthenticationAttributeCollectionPageViewConfiguration();
authenticationAttributeCollectionPageViewConfiguration.setTitle(null);
authenticationAttributeCollectionPageViewConfiguration.setDescription(null);
LinkedList<AuthenticationAttributeCollectionInputConfiguration> inputs = new LinkedList<AuthenticationAttributeCollectionInputConfiguration>();
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration.setAttribute("email");
authenticationAttributeCollectionInputConfiguration.setLabel("Email Address");
authenticationAttributeCollectionInputConfiguration.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration.setDefaultValue(null);
authenticationAttributeCollectionInputConfiguration.setHidden(true);
authenticationAttributeCollectionInputConfiguration.setEditable(false);
authenticationAttributeCollectionInputConfiguration.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration.setRequired(true);
authenticationAttributeCollectionInputConfiguration.setValidationRegEx("^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$");
LinkedList<AuthenticationAttributeCollectionOptionConfiguration> options = new LinkedList<AuthenticationAttributeCollectionOptionConfiguration>();
authenticationAttributeCollectionInputConfiguration.setOptions(options);
inputs.add(authenticationAttributeCollectionInputConfiguration);
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration1 = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration1.setAttribute("displayName");
authenticationAttributeCollectionInputConfiguration1.setLabel("Display Name");
authenticationAttributeCollectionInputConfiguration1.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration1.setDefaultValue(null);
authenticationAttributeCollectionInputConfiguration1.setHidden(false);
authenticationAttributeCollectionInputConfiguration1.setEditable(true);
authenticationAttributeCollectionInputConfiguration1.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration1.setRequired(true);
authenticationAttributeCollectionInputConfiguration1.setValidationRegEx("^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$");
LinkedList<AuthenticationAttributeCollectionOptionConfiguration> options1 = new LinkedList<AuthenticationAttributeCollectionOptionConfiguration>();
authenticationAttributeCollectionInputConfiguration1.setOptions(options1);
inputs.add(authenticationAttributeCollectionInputConfiguration1);
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration2 = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration2.setAttribute("city");
authenticationAttributeCollectionInputConfiguration2.setLabel("City");
authenticationAttributeCollectionInputConfiguration2.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration2.setDefaultValue(null);
authenticationAttributeCollectionInputConfiguration2.setHidden(false);
authenticationAttributeCollectionInputConfiguration2.setEditable(true);
authenticationAttributeCollectionInputConfiguration2.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration2.setRequired(true);
authenticationAttributeCollectionInputConfiguration2.setValidationRegEx("^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$");
LinkedList<AuthenticationAttributeCollectionOptionConfiguration> options2 = new LinkedList<AuthenticationAttributeCollectionOptionConfiguration>();
authenticationAttributeCollectionInputConfiguration2.setOptions(options2);
inputs.add(authenticationAttributeCollectionInputConfiguration2);
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration3 = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration3.setAttribute("extension_331d514c0c18477583ea7dd5a79feda2_RockorCountry");
authenticationAttributeCollectionInputConfiguration3.setLabel("Rock music or Country");
authenticationAttributeCollectionInputConfiguration3.setInputType(AuthenticationAttributeCollectionInputType.RadioSingleSelect);
authenticationAttributeCollectionInputConfiguration3.setDefaultValue(null);
authenticationAttributeCollectionInputConfiguration3.setHidden(false);
authenticationAttributeCollectionInputConfiguration3.setEditable(true);
authenticationAttributeCollectionInputConfiguration3.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration3.setRequired(true);
authenticationAttributeCollectionInputConfiguration3.setValidationRegEx("^.*");
LinkedList<AuthenticationAttributeCollectionOptionConfiguration> options3 = new LinkedList<AuthenticationAttributeCollectionOptionConfiguration>();
AuthenticationAttributeCollectionOptionConfiguration authenticationAttributeCollectionOptionConfiguration = new AuthenticationAttributeCollectionOptionConfiguration();
authenticationAttributeCollectionOptionConfiguration.setLabel("Rock music");
authenticationAttributeCollectionOptionConfiguration.setValue("Rock");
options3.add(authenticationAttributeCollectionOptionConfiguration);
AuthenticationAttributeCollectionOptionConfiguration authenticationAttributeCollectionOptionConfiguration1 = new AuthenticationAttributeCollectionOptionConfiguration();
authenticationAttributeCollectionOptionConfiguration1.setLabel("Country music");
authenticationAttributeCollectionOptionConfiguration1.setValue("Country");
options3.add(authenticationAttributeCollectionOptionConfiguration1);
authenticationAttributeCollectionInputConfiguration3.setOptions(options3);
inputs.add(authenticationAttributeCollectionInputConfiguration3);
authenticationAttributeCollectionPageViewConfiguration.setInputs(inputs);
views.add(authenticationAttributeCollectionPageViewConfiguration);
attributeCollectionPage.setViews(views);
onAttributeCollection.setAttributeCollectionPage(attributeCollectionPage);
authenticationEventsFlow.setOnAttributeCollection(onAttributeCollection);
AuthenticationEventsFlow result = graphClient.identity().authenticationEventsFlows().byAuthenticationEventsFlowId("{authenticationEventsFlow-id}").patch(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventsFlow = {
    '@odata.type': '#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow',
    onAttributeCollection: {
        '@odata.type': '#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp',
        attributeCollectionPage: {
            views: [
                {
                    title: null,
                    description: null,
                    inputs: [
                        {
                            attribute: 'email',
                            label: 'Email Address',
                            inputType: 'text',
                            defaultValue: null,
                            hidden: true,
                            editable: false,
                            writeToDirectory: true,
                            required: true,
                            validationRegEx: '^[a-zA-Z0-9.!#$%&amp;&#8217;\'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$',
                            options: []
                        },
                        {
                            attribute: 'displayName',
                            label: 'Display Name',
                            inputType: 'text',
                            defaultValue: null,
                            hidden: false,
                            editable: true,
                            writeToDirectory: true,
                            required: true,
                            validationRegEx: '^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$',
                            options: []
                        },
                        {
                            attribute: 'city',
                            label: 'City',
                            inputType: 'text',
                            defaultValue: null,
                            hidden: false,
                            editable: true,
                            writeToDirectory: true,
                            required: true,
                            validationRegEx: '^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$',
                            options: []
                        },
                        {
                            attribute: 'extension_331d514c0c18477583ea7dd5a79feda2_RockorCountry',
                            label: 'Rock music or Country',
                            inputType: 'radioSingleSelect',
                            defaultValue: null,
                            hidden: false,
                            editable: true,
                            writeToDirectory: true,
                            required: true,
                            validationRegEx: '^.*',
                            options: [
                                {
                                    label: 'Rock music',
                                    value: 'Rock'
                                },
                                {
                                    label: 'Country music',
                                    value: 'Country'
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    }
};

await client.api('/identity/authenticationEventsFlows/0313cc37-d421-421d-857b-87804d61e33e')
	.update(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalUsersSelfServiceSignUpEventsFlow;
use Microsoft\Graph\Generated\Models\OnAttributeCollectionExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionPage;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionPageViewConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionInputConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionInputType;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionOptionConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalUsersSelfServiceSignUpEventsFlow();
$requestBody->setOdataType('#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow');
$onAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp();
$onAttributeCollection->setOdataType('#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp');
$onAttributeCollectionAttributeCollectionPage = new AuthenticationAttributeCollectionPage();
$viewsAuthenticationAttributeCollectionPageViewConfiguration1 = new AuthenticationAttributeCollectionPageViewConfiguration();
$viewsAuthenticationAttributeCollectionPageViewConfiguration1->setTitle(null);
$viewsAuthenticationAttributeCollectionPageViewConfiguration1->setDescription(null);
$inputsAuthenticationAttributeCollectionInputConfiguration1 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration1->setAttribute('email');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setLabel('Email Address');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration1->setDefaultValue(null);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setHidden(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setEditable(false);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setRequired(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setValidationRegEx('^[a-zA-Z0-9.!#$%&amp;&#8217;\'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setOptions([	]);
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration1;
$inputsAuthenticationAttributeCollectionInputConfiguration2 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration2->setAttribute('displayName');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setLabel('Display Name');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration2->setDefaultValue(null);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setHidden(false);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setEditable(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setRequired(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setValidationRegEx('^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setOptions([	]);
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration2;
$inputsAuthenticationAttributeCollectionInputConfiguration3 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration3->setAttribute('city');
$inputsAuthenticationAttributeCollectionInputConfiguration3->setLabel('City');
$inputsAuthenticationAttributeCollectionInputConfiguration3->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration3->setDefaultValue(null);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setHidden(false);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setEditable(true);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setRequired(true);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setValidationRegEx('^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$');
$inputsAuthenticationAttributeCollectionInputConfiguration3->setOptions([	]);
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration3;
$inputsAuthenticationAttributeCollectionInputConfiguration4 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration4->setAttribute('extension_331d514c0c18477583ea7dd5a79feda2_RockorCountry');
$inputsAuthenticationAttributeCollectionInputConfiguration4->setLabel('Rock music or Country');
$inputsAuthenticationAttributeCollectionInputConfiguration4->setInputType(new AuthenticationAttributeCollectionInputType('radioSingleSelect'));
$inputsAuthenticationAttributeCollectionInputConfiguration4->setDefaultValue(null);
$inputsAuthenticationAttributeCollectionInputConfiguration4->setHidden(false);
$inputsAuthenticationAttributeCollectionInputConfiguration4->setEditable(true);
$inputsAuthenticationAttributeCollectionInputConfiguration4->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration4->setRequired(true);
$inputsAuthenticationAttributeCollectionInputConfiguration4->setValidationRegEx('^.*');
$optionsAuthenticationAttributeCollectionOptionConfiguration1 = new AuthenticationAttributeCollectionOptionConfiguration();
$optionsAuthenticationAttributeCollectionOptionConfiguration1->setLabel('Rock music');
$optionsAuthenticationAttributeCollectionOptionConfiguration1->setValue('Rock');
$optionsArray []= $optionsAuthenticationAttributeCollectionOptionConfiguration1;
$optionsAuthenticationAttributeCollectionOptionConfiguration2 = new AuthenticationAttributeCollectionOptionConfiguration();
$optionsAuthenticationAttributeCollectionOptionConfiguration2->setLabel('Country music');
$optionsAuthenticationAttributeCollectionOptionConfiguration2->setValue('Country');
$optionsArray []= $optionsAuthenticationAttributeCollectionOptionConfiguration2;
$inputsAuthenticationAttributeCollectionInputConfiguration4->setOptions($optionsArray);

$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration4;
$viewsAuthenticationAttributeCollectionPageViewConfiguration1->setInputs($inputsArray);

$viewsArray []= $viewsAuthenticationAttributeCollectionPageViewConfiguration1;
$onAttributeCollectionAttributeCollectionPage->setViews($viewsArray);

$onAttributeCollection->setAttributeCollectionPage($onAttributeCollectionAttributeCollectionPage);
$requestBody->setOnAttributeCollection($onAttributeCollection);

$result = $graphServiceClient->identity()->authenticationEventsFlows()->byAuthenticationEventsFlowId('authenticationEventsFlow-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow"
	onAttributeCollection = @{
		"@odata.type" = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp"
		attributeCollectionPage = @{
			views = @(
				@{
					title = $null
					description = $null
					inputs = @(
						@{
							attribute = "email"
							label = "Email Address"
							inputType = "text"
							defaultValue = $null
							hidden = $true
							editable = $false
							writeToDirectory = $true
							required = $true
							validationRegEx = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$"
							options = @(
							)
						}
						@{
							attribute = "displayName"
							label = "Display Name"
							inputType = "text"
							defaultValue = $null
							hidden = $false
							editable = $true
							writeToDirectory = $true
							required = $true
							validationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
							options = @(
							)
						}
						@{
							attribute = "city"
							label = "City"
							inputType = "text"
							defaultValue = $null
							hidden = $false
							editable = $true
							writeToDirectory = $true
							required = $true
							validationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
							options = @(
							)
						}
						@{
							attribute = "extension_331d514c0c18477583ea7dd5a79feda2_RockorCountry"
							label = "Rock music or Country"
							inputType = "radioSingleSelect"
							defaultValue = $null
							hidden = $false
							editable = $true
							writeToDirectory = $true
							required = $true
							validationRegEx = "^.*"
							options = @(
								@{
									label = "Rock music"
									value = "Rock"
								}
								@{
									label = "Country music"
									value = "Country"
								}
							)
						}
					)
				}
			)
		}
	}
}

Update-MgIdentityAuthenticationEventFlow -AuthenticationEventsFlowId $authenticationEventsFlowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_users_self_service_sign_up_events_flow import ExternalUsersSelfServiceSignUpEventsFlow
from msgraph.generated.models.on_attribute_collection_external_users_self_service_sign_up import OnAttributeCollectionExternalUsersSelfServiceSignUp
from msgraph.generated.models.authentication_attribute_collection_page import AuthenticationAttributeCollectionPage
from msgraph.generated.models.authentication_attribute_collection_page_view_configuration import AuthenticationAttributeCollectionPageViewConfiguration
from msgraph.generated.models.authentication_attribute_collection_input_configuration import AuthenticationAttributeCollectionInputConfiguration
from msgraph.generated.models.authentication_attribute_collection_input_type import AuthenticationAttributeCollectionInputType
from msgraph.generated.models.authentication_attribute_collection_option_configuration import AuthenticationAttributeCollectionOptionConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalUsersSelfServiceSignUpEventsFlow(
	odata_type = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
	on_attribute_collection = OnAttributeCollectionExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
		attribute_collection_page = AuthenticationAttributeCollectionPage(
			views = [
				AuthenticationAttributeCollectionPageViewConfiguration(
					title = None,
					description = None,
					inputs = [
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "email",
							label = "Email Address",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							default_value = None,
							hidden = True,
							editable = False,
							write_to_directory = True,
							required = True,
							validation_reg_ex = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
							options = [
							],
						),
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "displayName",
							label = "Display Name",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							default_value = None,
							hidden = False,
							editable = True,
							write_to_directory = True,
							required = True,
							validation_reg_ex = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
							options = [
							],
						),
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "city",
							label = "City",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							default_value = None,
							hidden = False,
							editable = True,
							write_to_directory = True,
							required = True,
							validation_reg_ex = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
							options = [
							],
						),
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "extension_331d514c0c18477583ea7dd5a79feda2_RockorCountry",
							label = "Rock music or Country",
							input_type = AuthenticationAttributeCollectionInputType.RadioSingleSelect,
							default_value = None,
							hidden = False,
							editable = True,
							write_to_directory = True,
							required = True,
							validation_reg_ex = "^.*",
							options = [
								AuthenticationAttributeCollectionOptionConfiguration(
									label = "Rock music",
									value = "Rock",
								),
								AuthenticationAttributeCollectionOptionConfiguration(
									label = "Country music",
									value = "Country",
								),
							],
						),
					],
				),
			],
		),
	),
)

result = await graph_client.identity.authentication_events_flows.by_authentication_events_flow_id('authenticationEventsFlow-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
