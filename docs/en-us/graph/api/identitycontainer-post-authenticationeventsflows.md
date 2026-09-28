<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-authenticationeventsflows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create authenticationEventsFlow

Namespace: microsoft.graph

Create a new [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object that is of the type specified in the request body. The following derived subtypes are supported:

- [externalUsersSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) object type.

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
POST /identity/authenticationEventsFlows
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object.

You can specify the following properties when creating an **authenticationEventsFlow**. You must include the **@odata.type** property with a value of the specific user flow type in the body. For example, `"@odata.type": "#microsoft.graph.externalUsersSelfServiceSignupEventsFlow"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Required. The display name for the events policy. Must be unique. |
| description | String | Optional. The description of the events policy. |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | Optional. The conditions representing the context of the authentication request which is used to decide whether the events policy is invoked. |
| priority | Int32 | Optional. The priority to use for each individual event of the events policy. If multiple competing listeners for an event have the same priority, one is chosen and an error is silently logged. Default is 500. |
| onInteractiveAuthFlowStart | [onInteractiveAuthFlowStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstarthandler?view=graph-rest-1.0) | Required. The configuration for what to invoke when an authentication flow is ready to be initiated. |
| onAuthenticationMethodLoadStart | [onAuthenticationMethodLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstarthandler?view=graph-rest-1.0) | Required. The configuration for what to invoke when authentication methods are ready to be presented to the user. Must have at least one identity provider linked. |
| onAttributeCollection | [onAttributeCollectionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionhandler?view=graph-rest-1.0) | Optional. The configuration for what to invoke when attributes are ready to be collected from the user. To configure this property, you must specify both **attributes** and **onAttributeCollectionPage** > **views** objects. |
| onUserCreateStart | [onUserCreateStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestarthandler?view=graph-rest-1.0) | Optional. The configuration for what to invoke during user creation. |

## Response

If successful, this method returns a `201 Created` response code and a JSON representation of an [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) object in the response body. An **@odata.type** property with the value of the specific user flow type created is included in the response body. For example, `"@odata.type": "#microsoft.graph.externalUsersSelfServiceSignupEventsFlow"`.

## Examples

### Example 1: Create a basic External Identities sign-up and sign-in user flow in an external tenant

#### Request

The following example shows a request. In this example, you create a user flow named "Woodgrove User Flow" with the following configuration.

- Allow sign up and sign in.
- Allow users to create a local email with password account.
- Collect the **Display Name** built-in attribute from the user.
- Defines how the attributes to be collected will be displayed to the user.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
    "displayName": "Woodgrove Drive User Flow",
    "onAuthenticationMethodLoadStart": {
        "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
        "identityProviders": [
            {
                "id": "EmailPassword-OAUTH"
            }
        ]
    },  
    "onInteractiveAuthFlowStart": {
        "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
        "isSignUpAllowed": true
    },
    "onAttributeCollection": {
        "@odata.type": "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
        "attributes": [
            {
                "id": "email",
                "displayName": "Email Address",
                "description": "Email address of the user",
                "userFlowAttributeType": "builtIn",
                "dataType": "string"
            },
            {
                "id": "displayName",
                "displayName": "Display Name",
                "description": "Display Name of the User.",
                "userFlowAttributeType": "builtIn",
                "dataType": "string"
            }
        ],
        "attributeCollectionPage": {
            "views": [
                {
                    "inputs": [
                        {
                            "attribute": "email",
                            "label": "Email Address",
                            "inputType": "Text",
                            "hidden": true,
                            "editable": false,
                            "writeToDirectory": true,
                            "required": true,
                            "validationRegEx": "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$"
                        },
                        {
                            "attribute": "displayName",
                            "label": "Display Name",
                            "inputType": "text",
                            "hidden": false,
                            "editable": true,
                            "writeToDirectory": true,
                            "required": false,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
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
	DisplayName = "Woodgrove Drive User Flow",
	OnAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
		IdentityProviders = new List<IdentityProviderBase>
		{
			new IdentityProviderBase
			{
				Id = "EmailPassword-OAUTH",
			},
		},
	},
	OnInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
		IsSignUpAllowed = true,
	},
	OnAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
		Attributes = new List<IdentityUserFlowAttribute>
		{
			new IdentityUserFlowAttribute
			{
				Id = "email",
				DisplayName = "Email Address",
				Description = "Email address of the user",
				UserFlowAttributeType = IdentityUserFlowAttributeType.BuiltIn,
				DataType = IdentityUserFlowAttributeDataType.String,
			},
			new IdentityUserFlowAttribute
			{
				Id = "displayName",
				DisplayName = "Display Name",
				Description = "Display Name of the User.",
				UserFlowAttributeType = IdentityUserFlowAttributeType.BuiltIn,
				DataType = IdentityUserFlowAttributeDataType.String,
			},
		},
		AttributeCollectionPage = new AuthenticationAttributeCollectionPage
		{
			Views = new List<AuthenticationAttributeCollectionPageViewConfiguration>
			{
				new AuthenticationAttributeCollectionPageViewConfiguration
				{
					Inputs = new List<AuthenticationAttributeCollectionInputConfiguration>
					{
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "email",
							Label = "Email Address",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							Hidden = true,
							Editable = false,
							WriteToDirectory = true,
							Required = true,
							ValidationRegEx = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
						},
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "displayName",
							Label = "Display Name",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							Hidden = false,
							Editable = true,
							WriteToDirectory = true,
							Required = false,
							ValidationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows.PostAsync(requestBody);
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
displayName := "Woodgrove Drive User Flow"
requestBody.SetDisplayName(&displayName) 
onAuthenticationMethodLoadStart := graphmodels.NewOnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp()


identityProviderBase := graphmodels.NewIdentityProviderBase()
id := "EmailPassword-OAUTH"
identityProviderBase.SetId(&id) 

identityProviders := []graphmodels.IdentityProviderBaseable {
	identityProviderBase,
}
onAuthenticationMethodLoadStart.SetIdentityProviders(identityProviders)
requestBody.SetOnAuthenticationMethodLoadStart(onAuthenticationMethodLoadStart)
onInteractiveAuthFlowStart := graphmodels.NewOnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp()
isSignUpAllowed := true
onInteractiveAuthFlowStart.SetIsSignUpAllowed(&isSignUpAllowed) 
requestBody.SetOnInteractiveAuthFlowStart(onInteractiveAuthFlowStart)
onAttributeCollection := graphmodels.NewOnAttributeCollectionExternalUsersSelfServiceSignUp()


identityUserFlowAttribute := graphmodels.NewIdentityUserFlowAttribute()
id := "email"
identityUserFlowAttribute.SetId(&id) 
displayName := "Email Address"
identityUserFlowAttribute.SetDisplayName(&displayName) 
description := "Email address of the user"
identityUserFlowAttribute.SetDescription(&description) 
userFlowAttributeType := graphmodels.BUILTIN_IDENTITYUSERFLOWATTRIBUTETYPE 
identityUserFlowAttribute.SetUserFlowAttributeType(&userFlowAttributeType) 
dataType := graphmodels.STRING_IDENTITYUSERFLOWATTRIBUTEDATATYPE 
identityUserFlowAttribute.SetDataType(&dataType) 
identityUserFlowAttribute1 := graphmodels.NewIdentityUserFlowAttribute()
id := "displayName"
identityUserFlowAttribute1.SetId(&id) 
displayName := "Display Name"
identityUserFlowAttribute1.SetDisplayName(&displayName) 
description := "Display Name of the User."
identityUserFlowAttribute1.SetDescription(&description) 
userFlowAttributeType := graphmodels.BUILTIN_IDENTITYUSERFLOWATTRIBUTETYPE 
identityUserFlowAttribute1.SetUserFlowAttributeType(&userFlowAttributeType) 
dataType := graphmodels.STRING_IDENTITYUSERFLOWATTRIBUTEDATATYPE 
identityUserFlowAttribute1.SetDataType(&dataType) 

attributes := []graphmodels.IdentityUserFlowAttributeable {
	identityUserFlowAttribute,
	identityUserFlowAttribute1,
}
onAttributeCollection.SetAttributes(attributes)
attributeCollectionPage := graphmodels.NewAuthenticationAttributeCollectionPage()


authenticationAttributeCollectionPageViewConfiguration := graphmodels.NewAuthenticationAttributeCollectionPageViewConfiguration()


authenticationAttributeCollectionInputConfiguration := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "email"
authenticationAttributeCollectionInputConfiguration.SetAttribute(&attribute) 
label := "Email Address"
authenticationAttributeCollectionInputConfiguration.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration.SetInputType(&inputType) 
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
authenticationAttributeCollectionInputConfiguration1 := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "displayName"
authenticationAttributeCollectionInputConfiguration1.SetAttribute(&attribute) 
label := "Display Name"
authenticationAttributeCollectionInputConfiguration1.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration1.SetInputType(&inputType) 
hidden := false
authenticationAttributeCollectionInputConfiguration1.SetHidden(&hidden) 
editable := true
authenticationAttributeCollectionInputConfiguration1.SetEditable(&editable) 
writeToDirectory := true
authenticationAttributeCollectionInputConfiguration1.SetWriteToDirectory(&writeToDirectory) 
required := false
authenticationAttributeCollectionInputConfiguration1.SetRequired(&required) 
validationRegEx := "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
authenticationAttributeCollectionInputConfiguration1.SetValidationRegEx(&validationRegEx) 

inputs := []graphmodels.AuthenticationAttributeCollectionInputConfigurationable {
	authenticationAttributeCollectionInputConfiguration,
	authenticationAttributeCollectionInputConfiguration1,
}
authenticationAttributeCollectionPageViewConfiguration.SetInputs(inputs)

views := []graphmodels.AuthenticationAttributeCollectionPageViewConfigurationable {
	authenticationAttributeCollectionPageViewConfiguration,
}
attributeCollectionPage.SetViews(views)
onAttributeCollection.SetAttributeCollectionPage(attributeCollectionPage)
requestBody.SetOnAttributeCollection(onAttributeCollection)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalUsersSelfServiceSignUpEventsFlow authenticationEventsFlow = new ExternalUsersSelfServiceSignUpEventsFlow();
authenticationEventsFlow.setOdataType("#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow");
authenticationEventsFlow.setDisplayName("Woodgrove Drive User Flow");
OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp onAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp();
onAuthenticationMethodLoadStart.setOdataType("#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp");
LinkedList<IdentityProviderBase> identityProviders = new LinkedList<IdentityProviderBase>();
IdentityProviderBase identityProviderBase = new IdentityProviderBase();
identityProviderBase.setId("EmailPassword-OAUTH");
identityProviders.add(identityProviderBase);
onAuthenticationMethodLoadStart.setIdentityProviders(identityProviders);
authenticationEventsFlow.setOnAuthenticationMethodLoadStart(onAuthenticationMethodLoadStart);
OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp onInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp();
onInteractiveAuthFlowStart.setOdataType("#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp");
onInteractiveAuthFlowStart.setIsSignUpAllowed(true);
authenticationEventsFlow.setOnInteractiveAuthFlowStart(onInteractiveAuthFlowStart);
OnAttributeCollectionExternalUsersSelfServiceSignUp onAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp();
onAttributeCollection.setOdataType("#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp");
LinkedList<IdentityUserFlowAttribute> attributes = new LinkedList<IdentityUserFlowAttribute>();
IdentityUserFlowAttribute identityUserFlowAttribute = new IdentityUserFlowAttribute();
identityUserFlowAttribute.setId("email");
identityUserFlowAttribute.setDisplayName("Email Address");
identityUserFlowAttribute.setDescription("Email address of the user");
identityUserFlowAttribute.setUserFlowAttributeType(IdentityUserFlowAttributeType.BuiltIn);
identityUserFlowAttribute.setDataType(IdentityUserFlowAttributeDataType.String);
attributes.add(identityUserFlowAttribute);
IdentityUserFlowAttribute identityUserFlowAttribute1 = new IdentityUserFlowAttribute();
identityUserFlowAttribute1.setId("displayName");
identityUserFlowAttribute1.setDisplayName("Display Name");
identityUserFlowAttribute1.setDescription("Display Name of the User.");
identityUserFlowAttribute1.setUserFlowAttributeType(IdentityUserFlowAttributeType.BuiltIn);
identityUserFlowAttribute1.setDataType(IdentityUserFlowAttributeDataType.String);
attributes.add(identityUserFlowAttribute1);
onAttributeCollection.setAttributes(attributes);
AuthenticationAttributeCollectionPage attributeCollectionPage = new AuthenticationAttributeCollectionPage();
LinkedList<AuthenticationAttributeCollectionPageViewConfiguration> views = new LinkedList<AuthenticationAttributeCollectionPageViewConfiguration>();
AuthenticationAttributeCollectionPageViewConfiguration authenticationAttributeCollectionPageViewConfiguration = new AuthenticationAttributeCollectionPageViewConfiguration();
LinkedList<AuthenticationAttributeCollectionInputConfiguration> inputs = new LinkedList<AuthenticationAttributeCollectionInputConfiguration>();
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration.setAttribute("email");
authenticationAttributeCollectionInputConfiguration.setLabel("Email Address");
authenticationAttributeCollectionInputConfiguration.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration.setHidden(true);
authenticationAttributeCollectionInputConfiguration.setEditable(false);
authenticationAttributeCollectionInputConfiguration.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration.setRequired(true);
authenticationAttributeCollectionInputConfiguration.setValidationRegEx("^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$");
inputs.add(authenticationAttributeCollectionInputConfiguration);
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration1 = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration1.setAttribute("displayName");
authenticationAttributeCollectionInputConfiguration1.setLabel("Display Name");
authenticationAttributeCollectionInputConfiguration1.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration1.setHidden(false);
authenticationAttributeCollectionInputConfiguration1.setEditable(true);
authenticationAttributeCollectionInputConfiguration1.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration1.setRequired(false);
authenticationAttributeCollectionInputConfiguration1.setValidationRegEx("^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$");
inputs.add(authenticationAttributeCollectionInputConfiguration1);
authenticationAttributeCollectionPageViewConfiguration.setInputs(inputs);
views.add(authenticationAttributeCollectionPageViewConfiguration);
attributeCollectionPage.setViews(views);
onAttributeCollection.setAttributeCollectionPage(attributeCollectionPage);
authenticationEventsFlow.setOnAttributeCollection(onAttributeCollection);
AuthenticationEventsFlow result = graphClient.identity().authenticationEventsFlows().post(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventsFlow = {
    '@odata.type': '#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow',
    displayName: 'Woodgrove Drive User Flow',
    onAuthenticationMethodLoadStart: {
        '@odata.type': '#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp',
        identityProviders: [
            {
                id: 'EmailPassword-OAUTH'
            }
        ]
    },  
    onInteractiveAuthFlowStart: {
        '@odata.type': '#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp',
        isSignUpAllowed: true
    },
    onAttributeCollection: {
        '@odata.type': '#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp',
        attributes: [
            {
                id: 'email',
                displayName: 'Email Address',
                description: 'Email address of the user',
                userFlowAttributeType: 'builtIn',
                dataType: 'string'
            },
            {
                id: 'displayName',
                displayName: 'Display Name',
                description: 'Display Name of the User.',
                userFlowAttributeType: 'builtIn',
                dataType: 'string'
            }
        ],
        attributeCollectionPage: {
            views: [
                {
                    inputs: [
                        {
                            attribute: 'email',
                            label: 'Email Address',
                            inputType: 'Text',
                            hidden: true,
                            editable: false,
                            writeToDirectory: true,
                            required: true,
                            validationRegEx: '^[a-zA-Z0-9.!#$%&amp;&#8217;\'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$'
                        },
                        {
                            attribute: 'displayName',
                            label: 'Display Name',
                            inputType: 'text',
                            hidden: false,
                            editable: true,
                            writeToDirectory: true,
                            required: false,
                            validationRegEx: '^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$'
                        }
                    ]
                }
            ]
        }
    }
};

await client.api('/identity/authenticationEventsFlows')
	.post(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalUsersSelfServiceSignUpEventsFlow;
use Microsoft\Graph\Generated\Models\OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\IdentityProviderBase;
use Microsoft\Graph\Generated\Models\OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\OnAttributeCollectionExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttribute;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttributeType;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttributeDataType;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionPage;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionPageViewConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionInputConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionInputType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalUsersSelfServiceSignUpEventsFlow();
$requestBody->setOdataType('#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow');
$requestBody->setDisplayName('Woodgrove Drive User Flow');
$onAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp();
$onAuthenticationMethodLoadStart->setOdataType('#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp');
$identityProvidersIdentityProviderBase1 = new IdentityProviderBase();
$identityProvidersIdentityProviderBase1->setId('EmailPassword-OAUTH');
$identityProvidersArray []= $identityProvidersIdentityProviderBase1;
$onAuthenticationMethodLoadStart->setIdentityProviders($identityProvidersArray);

$requestBody->setOnAuthenticationMethodLoadStart($onAuthenticationMethodLoadStart);
$onInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp();
$onInteractiveAuthFlowStart->setOdataType('#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp');
$onInteractiveAuthFlowStart->setIsSignUpAllowed(true);
$requestBody->setOnInteractiveAuthFlowStart($onInteractiveAuthFlowStart);
$onAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp();
$onAttributeCollection->setOdataType('#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp');
$attributesIdentityUserFlowAttribute1 = new IdentityUserFlowAttribute();
$attributesIdentityUserFlowAttribute1->setId('email');
$attributesIdentityUserFlowAttribute1->setDisplayName('Email Address');
$attributesIdentityUserFlowAttribute1->setDescription('Email address of the user');
$attributesIdentityUserFlowAttribute1->setUserFlowAttributeType(new IdentityUserFlowAttributeType('builtIn'));
$attributesIdentityUserFlowAttribute1->setDataType(new IdentityUserFlowAttributeDataType('string'));
$attributesArray []= $attributesIdentityUserFlowAttribute1;
$attributesIdentityUserFlowAttribute2 = new IdentityUserFlowAttribute();
$attributesIdentityUserFlowAttribute2->setId('displayName');
$attributesIdentityUserFlowAttribute2->setDisplayName('Display Name');
$attributesIdentityUserFlowAttribute2->setDescription('Display Name of the User.');
$attributesIdentityUserFlowAttribute2->setUserFlowAttributeType(new IdentityUserFlowAttributeType('builtIn'));
$attributesIdentityUserFlowAttribute2->setDataType(new IdentityUserFlowAttributeDataType('string'));
$attributesArray []= $attributesIdentityUserFlowAttribute2;
$onAttributeCollection->setAttributes($attributesArray);

$onAttributeCollectionAttributeCollectionPage = new AuthenticationAttributeCollectionPage();
$viewsAuthenticationAttributeCollectionPageViewConfiguration1 = new AuthenticationAttributeCollectionPageViewConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration1 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration1->setAttribute('email');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setLabel('Email Address');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration1->setHidden(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setEditable(false);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setRequired(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setValidationRegEx('^[a-zA-Z0-9.!#$%&amp;&#8217;\'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$');
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration1;
$inputsAuthenticationAttributeCollectionInputConfiguration2 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration2->setAttribute('displayName');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setLabel('Display Name');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration2->setHidden(false);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setEditable(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setRequired(false);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setValidationRegEx('^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$');
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration2;
$viewsAuthenticationAttributeCollectionPageViewConfiguration1->setInputs($inputsArray);

$viewsArray []= $viewsAuthenticationAttributeCollectionPageViewConfiguration1;
$onAttributeCollectionAttributeCollectionPage->setViews($viewsArray);

$onAttributeCollection->setAttributeCollectionPage($onAttributeCollectionAttributeCollectionPage);
$requestBody->setOnAttributeCollection($onAttributeCollection);

$result = $graphServiceClient->identity()->authenticationEventsFlows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow"
	displayName = "Woodgrove Drive User Flow"
	onAuthenticationMethodLoadStart = @{
		"@odata.type" = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp"
		identityProviders = @(
			@{
				id = "EmailPassword-OAUTH"
			}
		)
	}
	onInteractiveAuthFlowStart = @{
		"@odata.type" = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp"
		isSignUpAllowed = $true
	}
	onAttributeCollection = @{
		"@odata.type" = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp"
		attributes = @(
			@{
				id = "email"
				displayName = "Email Address"
				description = "Email address of the user"
				userFlowAttributeType = "builtIn"
				dataType = "string"
			}
			@{
				id = "displayName"
				displayName = "Display Name"
				description = "Display Name of the User."
				userFlowAttributeType = "builtIn"
				dataType = "string"
			}
		)
		attributeCollectionPage = @{
			views = @(
				@{
					inputs = @(
						@{
							attribute = "email"
							label = "Email Address"
							inputType = "Text"
							hidden = $true
							editable = $false
							writeToDirectory = $true
							required = $true
							validationRegEx = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$"
						}
						@{
							attribute = "displayName"
							label = "Display Name"
							inputType = "text"
							hidden = $false
							editable = $true
							writeToDirectory = $true
							required = $false
							validationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
						}
					)
				}
			)
		}
	}
}

New-MgIdentityAuthenticationEventFlow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_users_self_service_sign_up_events_flow import ExternalUsersSelfServiceSignUpEventsFlow
from msgraph.generated.models.on_authentication_method_load_start_external_users_self_service_sign_up import OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp
from msgraph.generated.models.identity_provider_base import IdentityProviderBase
from msgraph.generated.models.on_interactive_auth_flow_start_external_users_self_service_sign_up import OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp
from msgraph.generated.models.on_attribute_collection_external_users_self_service_sign_up import OnAttributeCollectionExternalUsersSelfServiceSignUp
from msgraph.generated.models.identity_user_flow_attribute import IdentityUserFlowAttribute
from msgraph.generated.models.identity_user_flow_attribute_type import IdentityUserFlowAttributeType
from msgraph.generated.models.identity_user_flow_attribute_data_type import IdentityUserFlowAttributeDataType
from msgraph.generated.models.authentication_attribute_collection_page import AuthenticationAttributeCollectionPage
from msgraph.generated.models.authentication_attribute_collection_page_view_configuration import AuthenticationAttributeCollectionPageViewConfiguration
from msgraph.generated.models.authentication_attribute_collection_input_configuration import AuthenticationAttributeCollectionInputConfiguration
from msgraph.generated.models.authentication_attribute_collection_input_type import AuthenticationAttributeCollectionInputType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalUsersSelfServiceSignUpEventsFlow(
	odata_type = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
	display_name = "Woodgrove Drive User Flow",
	on_authentication_method_load_start = OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
		identity_providers = [
			IdentityProviderBase(
				id = "EmailPassword-OAUTH",
			),
		],
	),
	on_interactive_auth_flow_start = OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
		is_sign_up_allowed = True,
	),
	on_attribute_collection = OnAttributeCollectionExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
		attributes = [
			IdentityUserFlowAttribute(
				id = "email",
				display_name = "Email Address",
				description = "Email address of the user",
				user_flow_attribute_type = IdentityUserFlowAttributeType.BuiltIn,
				data_type = IdentityUserFlowAttributeDataType.String,
			),
			IdentityUserFlowAttribute(
				id = "displayName",
				display_name = "Display Name",
				description = "Display Name of the User.",
				user_flow_attribute_type = IdentityUserFlowAttributeType.BuiltIn,
				data_type = IdentityUserFlowAttributeDataType.String,
			),
		],
		attribute_collection_page = AuthenticationAttributeCollectionPage(
			views = [
				AuthenticationAttributeCollectionPageViewConfiguration(
					inputs = [
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "email",
							label = "Email Address",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							hidden = True,
							editable = False,
							write_to_directory = True,
							required = True,
							validation_reg_ex = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
						),
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "displayName",
							label = "Display Name",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							hidden = False,
							editable = True,
							write_to_directory = True,
							required = False,
							validation_reg_ex = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
						),
					],
				),
			],
		),
	),
)

result = await graph_client.identity.authentication_events_flows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows/$entity",
    "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
    "id": "0313cc37-d421-421d-857b-87804d61e33e",
    "displayName": "Woodgrove Drive User Flow",
    "conditions": {
        "applications": {
            "includeAllApplications": false
        }
    },
    "onInteractiveAuthFlowStart": {
        "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
        "isSignUpAllowed": true
    },
    "onAuthenticationMethodLoadStart": {
        "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp"
    },
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
                            "required": false,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
                            "options": []
                        }
                    ]
                }
            ]
        }
    }
}
```

### Example 2: Create a basic external identities sign-up and sign-in user flow with an attached application in an external tenant

#### Request

The following example shows a request. In this example, you create a user flow named "Woodgrove User Flow" with the following configuration.

- Allow sign up and sign in.
- Allow users to create a local email with password account.
- Collect the **Display Name** built-in attribute from the user.
- Defines how the attributes to be collected will be displayed to the user.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
    "displayName": "Woodgrove Drive User Flow",
    "conditions": {
        "applications": {
            "includeApplications": [
                {
                    "appId": "63856651-13d9-4784-9abf-20758d509e19"
                }
            ]
        }
    },
    "onAuthenticationMethodLoadStart": {
        "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
        "identityProviders": [
            {
                "id": "EmailPassword-OAUTH"
            }
        ]
    },  
    "onInteractiveAuthFlowStart": {
        "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
        "isSignUpAllowed": true
    },
    "onAttributeCollection": {
        "@odata.type": "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
        "attributes": [
            {
                "id": "email",
                "displayName": "Email Address",
                "description": "Email address of the user",
                "userFlowAttributeType": "builtIn",
                "dataType": "string"
            },
            {
                "id": "displayName",
                "displayName": "Display Name",
                "description": "Display Name of the User.",
                "userFlowAttributeType": "builtIn",
                "dataType": "string"
            }
        ],
        "attributeCollectionPage": {
            "views": [
                {
                    "inputs": [
                        {
                            "attribute": "email",
                            "label": "Email Address",
                            "inputType": "Text",
                            "hidden": true,
                            "editable": false,
                            "writeToDirectory": true,
                            "required": true,
                            "validationRegEx": "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$"
                        },
                        {
                            "attribute": "displayName",
                            "label": "Display Name",
                            "inputType": "text",
                            "hidden": false,
                            "editable": true,
                            "writeToDirectory": true,
                            "required": false,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
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
	DisplayName = "Woodgrove Drive User Flow",
	Conditions = new AuthenticationConditions
	{
		Applications = new AuthenticationConditionsApplications
		{
			IncludeApplications = new List<AuthenticationConditionApplication>
			{
				new AuthenticationConditionApplication
				{
					AppId = "63856651-13d9-4784-9abf-20758d509e19",
				},
			},
		},
	},
	OnAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
		IdentityProviders = new List<IdentityProviderBase>
		{
			new IdentityProviderBase
			{
				Id = "EmailPassword-OAUTH",
			},
		},
	},
	OnInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
		IsSignUpAllowed = true,
	},
	OnAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
		Attributes = new List<IdentityUserFlowAttribute>
		{
			new IdentityUserFlowAttribute
			{
				Id = "email",
				DisplayName = "Email Address",
				Description = "Email address of the user",
				UserFlowAttributeType = IdentityUserFlowAttributeType.BuiltIn,
				DataType = IdentityUserFlowAttributeDataType.String,
			},
			new IdentityUserFlowAttribute
			{
				Id = "displayName",
				DisplayName = "Display Name",
				Description = "Display Name of the User.",
				UserFlowAttributeType = IdentityUserFlowAttributeType.BuiltIn,
				DataType = IdentityUserFlowAttributeDataType.String,
			},
		},
		AttributeCollectionPage = new AuthenticationAttributeCollectionPage
		{
			Views = new List<AuthenticationAttributeCollectionPageViewConfiguration>
			{
				new AuthenticationAttributeCollectionPageViewConfiguration
				{
					Inputs = new List<AuthenticationAttributeCollectionInputConfiguration>
					{
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "email",
							Label = "Email Address",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							Hidden = true,
							Editable = false,
							WriteToDirectory = true,
							Required = true,
							ValidationRegEx = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
						},
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "displayName",
							Label = "Display Name",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							Hidden = false,
							Editable = true,
							WriteToDirectory = true,
							Required = false,
							ValidationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows.PostAsync(requestBody);
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
displayName := "Woodgrove Drive User Flow"
requestBody.SetDisplayName(&displayName) 
conditions := graphmodels.NewAuthenticationConditions()
applications := graphmodels.NewAuthenticationConditionsApplications()


authenticationConditionApplication := graphmodels.NewAuthenticationConditionApplication()
appId := "63856651-13d9-4784-9abf-20758d509e19"
authenticationConditionApplication.SetAppId(&appId) 

includeApplications := []graphmodels.AuthenticationConditionApplicationable {
	authenticationConditionApplication,
}
applications.SetIncludeApplications(includeApplications)
conditions.SetApplications(applications)
requestBody.SetConditions(conditions)
onAuthenticationMethodLoadStart := graphmodels.NewOnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp()


identityProviderBase := graphmodels.NewIdentityProviderBase()
id := "EmailPassword-OAUTH"
identityProviderBase.SetId(&id) 

identityProviders := []graphmodels.IdentityProviderBaseable {
	identityProviderBase,
}
onAuthenticationMethodLoadStart.SetIdentityProviders(identityProviders)
requestBody.SetOnAuthenticationMethodLoadStart(onAuthenticationMethodLoadStart)
onInteractiveAuthFlowStart := graphmodels.NewOnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp()
isSignUpAllowed := true
onInteractiveAuthFlowStart.SetIsSignUpAllowed(&isSignUpAllowed) 
requestBody.SetOnInteractiveAuthFlowStart(onInteractiveAuthFlowStart)
onAttributeCollection := graphmodels.NewOnAttributeCollectionExternalUsersSelfServiceSignUp()


identityUserFlowAttribute := graphmodels.NewIdentityUserFlowAttribute()
id := "email"
identityUserFlowAttribute.SetId(&id) 
displayName := "Email Address"
identityUserFlowAttribute.SetDisplayName(&displayName) 
description := "Email address of the user"
identityUserFlowAttribute.SetDescription(&description) 
userFlowAttributeType := graphmodels.BUILTIN_IDENTITYUSERFLOWATTRIBUTETYPE 
identityUserFlowAttribute.SetUserFlowAttributeType(&userFlowAttributeType) 
dataType := graphmodels.STRING_IDENTITYUSERFLOWATTRIBUTEDATATYPE 
identityUserFlowAttribute.SetDataType(&dataType) 
identityUserFlowAttribute1 := graphmodels.NewIdentityUserFlowAttribute()
id := "displayName"
identityUserFlowAttribute1.SetId(&id) 
displayName := "Display Name"
identityUserFlowAttribute1.SetDisplayName(&displayName) 
description := "Display Name of the User."
identityUserFlowAttribute1.SetDescription(&description) 
userFlowAttributeType := graphmodels.BUILTIN_IDENTITYUSERFLOWATTRIBUTETYPE 
identityUserFlowAttribute1.SetUserFlowAttributeType(&userFlowAttributeType) 
dataType := graphmodels.STRING_IDENTITYUSERFLOWATTRIBUTEDATATYPE 
identityUserFlowAttribute1.SetDataType(&dataType) 

attributes := []graphmodels.IdentityUserFlowAttributeable {
	identityUserFlowAttribute,
	identityUserFlowAttribute1,
}
onAttributeCollection.SetAttributes(attributes)
attributeCollectionPage := graphmodels.NewAuthenticationAttributeCollectionPage()


authenticationAttributeCollectionPageViewConfiguration := graphmodels.NewAuthenticationAttributeCollectionPageViewConfiguration()


authenticationAttributeCollectionInputConfiguration := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "email"
authenticationAttributeCollectionInputConfiguration.SetAttribute(&attribute) 
label := "Email Address"
authenticationAttributeCollectionInputConfiguration.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration.SetInputType(&inputType) 
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
authenticationAttributeCollectionInputConfiguration1 := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "displayName"
authenticationAttributeCollectionInputConfiguration1.SetAttribute(&attribute) 
label := "Display Name"
authenticationAttributeCollectionInputConfiguration1.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration1.SetInputType(&inputType) 
hidden := false
authenticationAttributeCollectionInputConfiguration1.SetHidden(&hidden) 
editable := true
authenticationAttributeCollectionInputConfiguration1.SetEditable(&editable) 
writeToDirectory := true
authenticationAttributeCollectionInputConfiguration1.SetWriteToDirectory(&writeToDirectory) 
required := false
authenticationAttributeCollectionInputConfiguration1.SetRequired(&required) 
validationRegEx := "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
authenticationAttributeCollectionInputConfiguration1.SetValidationRegEx(&validationRegEx) 

inputs := []graphmodels.AuthenticationAttributeCollectionInputConfigurationable {
	authenticationAttributeCollectionInputConfiguration,
	authenticationAttributeCollectionInputConfiguration1,
}
authenticationAttributeCollectionPageViewConfiguration.SetInputs(inputs)

views := []graphmodels.AuthenticationAttributeCollectionPageViewConfigurationable {
	authenticationAttributeCollectionPageViewConfiguration,
}
attributeCollectionPage.SetViews(views)
onAttributeCollection.SetAttributeCollectionPage(attributeCollectionPage)
requestBody.SetOnAttributeCollection(onAttributeCollection)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalUsersSelfServiceSignUpEventsFlow authenticationEventsFlow = new ExternalUsersSelfServiceSignUpEventsFlow();
authenticationEventsFlow.setOdataType("#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow");
authenticationEventsFlow.setDisplayName("Woodgrove Drive User Flow");
AuthenticationConditions conditions = new AuthenticationConditions();
AuthenticationConditionsApplications applications = new AuthenticationConditionsApplications();
LinkedList<AuthenticationConditionApplication> includeApplications = new LinkedList<AuthenticationConditionApplication>();
AuthenticationConditionApplication authenticationConditionApplication = new AuthenticationConditionApplication();
authenticationConditionApplication.setAppId("63856651-13d9-4784-9abf-20758d509e19");
includeApplications.add(authenticationConditionApplication);
applications.setIncludeApplications(includeApplications);
conditions.setApplications(applications);
authenticationEventsFlow.setConditions(conditions);
OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp onAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp();
onAuthenticationMethodLoadStart.setOdataType("#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp");
LinkedList<IdentityProviderBase> identityProviders = new LinkedList<IdentityProviderBase>();
IdentityProviderBase identityProviderBase = new IdentityProviderBase();
identityProviderBase.setId("EmailPassword-OAUTH");
identityProviders.add(identityProviderBase);
onAuthenticationMethodLoadStart.setIdentityProviders(identityProviders);
authenticationEventsFlow.setOnAuthenticationMethodLoadStart(onAuthenticationMethodLoadStart);
OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp onInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp();
onInteractiveAuthFlowStart.setOdataType("#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp");
onInteractiveAuthFlowStart.setIsSignUpAllowed(true);
authenticationEventsFlow.setOnInteractiveAuthFlowStart(onInteractiveAuthFlowStart);
OnAttributeCollectionExternalUsersSelfServiceSignUp onAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp();
onAttributeCollection.setOdataType("#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp");
LinkedList<IdentityUserFlowAttribute> attributes = new LinkedList<IdentityUserFlowAttribute>();
IdentityUserFlowAttribute identityUserFlowAttribute = new IdentityUserFlowAttribute();
identityUserFlowAttribute.setId("email");
identityUserFlowAttribute.setDisplayName("Email Address");
identityUserFlowAttribute.setDescription("Email address of the user");
identityUserFlowAttribute.setUserFlowAttributeType(IdentityUserFlowAttributeType.BuiltIn);
identityUserFlowAttribute.setDataType(IdentityUserFlowAttributeDataType.String);
attributes.add(identityUserFlowAttribute);
IdentityUserFlowAttribute identityUserFlowAttribute1 = new IdentityUserFlowAttribute();
identityUserFlowAttribute1.setId("displayName");
identityUserFlowAttribute1.setDisplayName("Display Name");
identityUserFlowAttribute1.setDescription("Display Name of the User.");
identityUserFlowAttribute1.setUserFlowAttributeType(IdentityUserFlowAttributeType.BuiltIn);
identityUserFlowAttribute1.setDataType(IdentityUserFlowAttributeDataType.String);
attributes.add(identityUserFlowAttribute1);
onAttributeCollection.setAttributes(attributes);
AuthenticationAttributeCollectionPage attributeCollectionPage = new AuthenticationAttributeCollectionPage();
LinkedList<AuthenticationAttributeCollectionPageViewConfiguration> views = new LinkedList<AuthenticationAttributeCollectionPageViewConfiguration>();
AuthenticationAttributeCollectionPageViewConfiguration authenticationAttributeCollectionPageViewConfiguration = new AuthenticationAttributeCollectionPageViewConfiguration();
LinkedList<AuthenticationAttributeCollectionInputConfiguration> inputs = new LinkedList<AuthenticationAttributeCollectionInputConfiguration>();
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration.setAttribute("email");
authenticationAttributeCollectionInputConfiguration.setLabel("Email Address");
authenticationAttributeCollectionInputConfiguration.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration.setHidden(true);
authenticationAttributeCollectionInputConfiguration.setEditable(false);
authenticationAttributeCollectionInputConfiguration.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration.setRequired(true);
authenticationAttributeCollectionInputConfiguration.setValidationRegEx("^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$");
inputs.add(authenticationAttributeCollectionInputConfiguration);
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration1 = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration1.setAttribute("displayName");
authenticationAttributeCollectionInputConfiguration1.setLabel("Display Name");
authenticationAttributeCollectionInputConfiguration1.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration1.setHidden(false);
authenticationAttributeCollectionInputConfiguration1.setEditable(true);
authenticationAttributeCollectionInputConfiguration1.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration1.setRequired(false);
authenticationAttributeCollectionInputConfiguration1.setValidationRegEx("^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$");
inputs.add(authenticationAttributeCollectionInputConfiguration1);
authenticationAttributeCollectionPageViewConfiguration.setInputs(inputs);
views.add(authenticationAttributeCollectionPageViewConfiguration);
attributeCollectionPage.setViews(views);
onAttributeCollection.setAttributeCollectionPage(attributeCollectionPage);
authenticationEventsFlow.setOnAttributeCollection(onAttributeCollection);
AuthenticationEventsFlow result = graphClient.identity().authenticationEventsFlows().post(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventsFlow = {
    '@odata.type': '#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow',
    displayName: 'Woodgrove Drive User Flow',
    conditions: {
        applications: {
            includeApplications: [
                {
                    appId: '63856651-13d9-4784-9abf-20758d509e19'
                }
            ]
        }
    },
    onAuthenticationMethodLoadStart: {
        '@odata.type': '#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp',
        identityProviders: [
            {
                id: 'EmailPassword-OAUTH'
            }
        ]
    },  
    onInteractiveAuthFlowStart: {
        '@odata.type': '#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp',
        isSignUpAllowed: true
    },
    onAttributeCollection: {
        '@odata.type': '#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp',
        attributes: [
            {
                id: 'email',
                displayName: 'Email Address',
                description: 'Email address of the user',
                userFlowAttributeType: 'builtIn',
                dataType: 'string'
            },
            {
                id: 'displayName',
                displayName: 'Display Name',
                description: 'Display Name of the User.',
                userFlowAttributeType: 'builtIn',
                dataType: 'string'
            }
        ],
        attributeCollectionPage: {
            views: [
                {
                    inputs: [
                        {
                            attribute: 'email',
                            label: 'Email Address',
                            inputType: 'Text',
                            hidden: true,
                            editable: false,
                            writeToDirectory: true,
                            required: true,
                            validationRegEx: '^[a-zA-Z0-9.!#$%&amp;&#8217;\'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$'
                        },
                        {
                            attribute: 'displayName',
                            label: 'Display Name',
                            inputType: 'text',
                            hidden: false,
                            editable: true,
                            writeToDirectory: true,
                            required: false,
                            validationRegEx: '^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$'
                        }
                    ]
                }
            ]
        }
    }
};

await client.api('/identity/authenticationEventsFlows')
	.post(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalUsersSelfServiceSignUpEventsFlow;
use Microsoft\Graph\Generated\Models\AuthenticationConditions;
use Microsoft\Graph\Generated\Models\AuthenticationConditionsApplications;
use Microsoft\Graph\Generated\Models\AuthenticationConditionApplication;
use Microsoft\Graph\Generated\Models\OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\IdentityProviderBase;
use Microsoft\Graph\Generated\Models\OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\OnAttributeCollectionExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttribute;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttributeType;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttributeDataType;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionPage;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionPageViewConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionInputConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionInputType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalUsersSelfServiceSignUpEventsFlow();
$requestBody->setOdataType('#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow');
$requestBody->setDisplayName('Woodgrove Drive User Flow');
$conditions = new AuthenticationConditions();
$conditionsApplications = new AuthenticationConditionsApplications();
$includeApplicationsAuthenticationConditionApplication1 = new AuthenticationConditionApplication();
$includeApplicationsAuthenticationConditionApplication1->setAppId('63856651-13d9-4784-9abf-20758d509e19');
$includeApplicationsArray []= $includeApplicationsAuthenticationConditionApplication1;
$conditionsApplications->setIncludeApplications($includeApplicationsArray);

$conditions->setApplications($conditionsApplications);
$requestBody->setConditions($conditions);
$onAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp();
$onAuthenticationMethodLoadStart->setOdataType('#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp');
$identityProvidersIdentityProviderBase1 = new IdentityProviderBase();
$identityProvidersIdentityProviderBase1->setId('EmailPassword-OAUTH');
$identityProvidersArray []= $identityProvidersIdentityProviderBase1;
$onAuthenticationMethodLoadStart->setIdentityProviders($identityProvidersArray);

$requestBody->setOnAuthenticationMethodLoadStart($onAuthenticationMethodLoadStart);
$onInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp();
$onInteractiveAuthFlowStart->setOdataType('#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp');
$onInteractiveAuthFlowStart->setIsSignUpAllowed(true);
$requestBody->setOnInteractiveAuthFlowStart($onInteractiveAuthFlowStart);
$onAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp();
$onAttributeCollection->setOdataType('#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp');
$attributesIdentityUserFlowAttribute1 = new IdentityUserFlowAttribute();
$attributesIdentityUserFlowAttribute1->setId('email');
$attributesIdentityUserFlowAttribute1->setDisplayName('Email Address');
$attributesIdentityUserFlowAttribute1->setDescription('Email address of the user');
$attributesIdentityUserFlowAttribute1->setUserFlowAttributeType(new IdentityUserFlowAttributeType('builtIn'));
$attributesIdentityUserFlowAttribute1->setDataType(new IdentityUserFlowAttributeDataType('string'));
$attributesArray []= $attributesIdentityUserFlowAttribute1;
$attributesIdentityUserFlowAttribute2 = new IdentityUserFlowAttribute();
$attributesIdentityUserFlowAttribute2->setId('displayName');
$attributesIdentityUserFlowAttribute2->setDisplayName('Display Name');
$attributesIdentityUserFlowAttribute2->setDescription('Display Name of the User.');
$attributesIdentityUserFlowAttribute2->setUserFlowAttributeType(new IdentityUserFlowAttributeType('builtIn'));
$attributesIdentityUserFlowAttribute2->setDataType(new IdentityUserFlowAttributeDataType('string'));
$attributesArray []= $attributesIdentityUserFlowAttribute2;
$onAttributeCollection->setAttributes($attributesArray);

$onAttributeCollectionAttributeCollectionPage = new AuthenticationAttributeCollectionPage();
$viewsAuthenticationAttributeCollectionPageViewConfiguration1 = new AuthenticationAttributeCollectionPageViewConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration1 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration1->setAttribute('email');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setLabel('Email Address');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration1->setHidden(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setEditable(false);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setRequired(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setValidationRegEx('^[a-zA-Z0-9.!#$%&amp;&#8217;\'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$');
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration1;
$inputsAuthenticationAttributeCollectionInputConfiguration2 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration2->setAttribute('displayName');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setLabel('Display Name');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration2->setHidden(false);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setEditable(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setRequired(false);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setValidationRegEx('^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$');
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration2;
$viewsAuthenticationAttributeCollectionPageViewConfiguration1->setInputs($inputsArray);

$viewsArray []= $viewsAuthenticationAttributeCollectionPageViewConfiguration1;
$onAttributeCollectionAttributeCollectionPage->setViews($viewsArray);

$onAttributeCollection->setAttributeCollectionPage($onAttributeCollectionAttributeCollectionPage);
$requestBody->setOnAttributeCollection($onAttributeCollection);

$result = $graphServiceClient->identity()->authenticationEventsFlows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow"
	displayName = "Woodgrove Drive User Flow"
	conditions = @{
		applications = @{
			includeApplications = @(
				@{
					appId = "63856651-13d9-4784-9abf-20758d509e19"
				}
			)
		}
	}
	onAuthenticationMethodLoadStart = @{
		"@odata.type" = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp"
		identityProviders = @(
			@{
				id = "EmailPassword-OAUTH"
			}
		)
	}
	onInteractiveAuthFlowStart = @{
		"@odata.type" = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp"
		isSignUpAllowed = $true
	}
	onAttributeCollection = @{
		"@odata.type" = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp"
		attributes = @(
			@{
				id = "email"
				displayName = "Email Address"
				description = "Email address of the user"
				userFlowAttributeType = "builtIn"
				dataType = "string"
			}
			@{
				id = "displayName"
				displayName = "Display Name"
				description = "Display Name of the User."
				userFlowAttributeType = "builtIn"
				dataType = "string"
			}
		)
		attributeCollectionPage = @{
			views = @(
				@{
					inputs = @(
						@{
							attribute = "email"
							label = "Email Address"
							inputType = "Text"
							hidden = $true
							editable = $false
							writeToDirectory = $true
							required = $true
							validationRegEx = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$"
						}
						@{
							attribute = "displayName"
							label = "Display Name"
							inputType = "text"
							hidden = $false
							editable = $true
							writeToDirectory = $true
							required = $false
							validationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
						}
					)
				}
			)
		}
	}
}

New-MgIdentityAuthenticationEventFlow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_users_self_service_sign_up_events_flow import ExternalUsersSelfServiceSignUpEventsFlow
from msgraph.generated.models.authentication_conditions import AuthenticationConditions
from msgraph.generated.models.authentication_conditions_applications import AuthenticationConditionsApplications
from msgraph.generated.models.authentication_condition_application import AuthenticationConditionApplication
from msgraph.generated.models.on_authentication_method_load_start_external_users_self_service_sign_up import OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp
from msgraph.generated.models.identity_provider_base import IdentityProviderBase
from msgraph.generated.models.on_interactive_auth_flow_start_external_users_self_service_sign_up import OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp
from msgraph.generated.models.on_attribute_collection_external_users_self_service_sign_up import OnAttributeCollectionExternalUsersSelfServiceSignUp
from msgraph.generated.models.identity_user_flow_attribute import IdentityUserFlowAttribute
from msgraph.generated.models.identity_user_flow_attribute_type import IdentityUserFlowAttributeType
from msgraph.generated.models.identity_user_flow_attribute_data_type import IdentityUserFlowAttributeDataType
from msgraph.generated.models.authentication_attribute_collection_page import AuthenticationAttributeCollectionPage
from msgraph.generated.models.authentication_attribute_collection_page_view_configuration import AuthenticationAttributeCollectionPageViewConfiguration
from msgraph.generated.models.authentication_attribute_collection_input_configuration import AuthenticationAttributeCollectionInputConfiguration
from msgraph.generated.models.authentication_attribute_collection_input_type import AuthenticationAttributeCollectionInputType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalUsersSelfServiceSignUpEventsFlow(
	odata_type = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
	display_name = "Woodgrove Drive User Flow",
	conditions = AuthenticationConditions(
		applications = AuthenticationConditionsApplications(
			include_applications = [
				AuthenticationConditionApplication(
					app_id = "63856651-13d9-4784-9abf-20758d509e19",
				),
			],
		),
	),
	on_authentication_method_load_start = OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
		identity_providers = [
			IdentityProviderBase(
				id = "EmailPassword-OAUTH",
			),
		],
	),
	on_interactive_auth_flow_start = OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
		is_sign_up_allowed = True,
	),
	on_attribute_collection = OnAttributeCollectionExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
		attributes = [
			IdentityUserFlowAttribute(
				id = "email",
				display_name = "Email Address",
				description = "Email address of the user",
				user_flow_attribute_type = IdentityUserFlowAttributeType.BuiltIn,
				data_type = IdentityUserFlowAttributeDataType.String,
			),
			IdentityUserFlowAttribute(
				id = "displayName",
				display_name = "Display Name",
				description = "Display Name of the User.",
				user_flow_attribute_type = IdentityUserFlowAttributeType.BuiltIn,
				data_type = IdentityUserFlowAttributeDataType.String,
			),
		],
		attribute_collection_page = AuthenticationAttributeCollectionPage(
			views = [
				AuthenticationAttributeCollectionPageViewConfiguration(
					inputs = [
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "email",
							label = "Email Address",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							hidden = True,
							editable = False,
							write_to_directory = True,
							required = True,
							validation_reg_ex = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
						),
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "displayName",
							label = "Display Name",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							hidden = False,
							editable = True,
							write_to_directory = True,
							required = False,
							validation_reg_ex = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
						),
					],
				),
			],
		),
	),
)

result = await graph_client.identity.authentication_events_flows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows/$entity",
    "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
    "id": "1d51b447-eb52-4ec8-ae4e-0a35ebc148ea",
    "displayName": "Woodgrove Drive User Flow",
    "description": null,
    "onUserCreateStart": null,
    "conditions": {
        "applications": {
            "includeAllApplications": false
        }
    },
    "onInteractiveAuthFlowStart": {
        "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
        "isSignUpAllowed": true
    },
    "onAuthenticationMethodLoadStart": {
        "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp"
    },
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
                            "required": false,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
                            "options": []
                        }
                    ]
                }
            ]
        }
    }
}
```

### Example 3: Create an External Identities sign-up and sign-in user flow with social providers and a custom attribute

#### Request

The following example shows a request. In this example, you create a user flow named "Woodgrove Drive User Flow" with the following configuration

- Allow sign up and sign in.
- Allow users to create a local email with password account, or authenticate with Google or Facebook
- Collect the **Display Name** built-in attribute and a **Favorite Color** custom attribute.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
    "displayName": "Woodgrove User Flow 2",
    "onAuthenticationMethodLoadStart": {
        "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
        "identityProviders": [
            {
                "id": "EmailPassword-OAUTH"
            },
            {
                "id": "Google-OAUTH"
            },
            {
                "id": "Facebook-OAUTH"
            }
        ]
    },  
    "onInteractiveAuthFlowStart": {
        "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
        "isSignUpAllowed": true
    },
    "onAttributeCollection": {
        "@odata.type": "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
        "attributes": [
            {
                "id": "email",
                "displayName": "Email Address",
                "description": "Email address of the user",
                "userFlowAttributeType": "builtIn",
                "dataType": "string"
            },
            {
                "id": "displayName",
                "displayName": "Display Name",
                "description": "Display Name of the User.",
                "userFlowAttributeType": "builtIn",
                "dataType": "string"
            },
            {
                "id": "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor",
                "displayName": "Favorite color",
                "description": "what is your favorite color",
                "userFlowAttributeType": "custom",
                "dataType": "string"
            }
        ],
        "attributeCollectionPage": {
            "views": [
                {
                    "inputs": [
                        {
                            "attribute": "email",
                            "label": "Email Address",
                            "inputType": "Text",
                            "hidden": true,
                            "editable": false,
                            "writeToDirectory": true,
                            "required": true,
                            "validationRegEx": "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$"
                        },
                        {
                            "attribute": "displayName",
                            "label": "Display Name",
                            "inputType": "text",
                            "hidden": false,
                            "editable": true,
                            "writeToDirectory": true,
                            "required": false,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
                        },
                        {
                            "attribute": "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor",
                            "label": "Favorite color",
                            "inputType": "text",
                            "hidden": false,
                            "editable": true,
                            "writeToDirectory": true,
                            "required": false,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
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
	DisplayName = "Woodgrove User Flow 2",
	OnAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
		IdentityProviders = new List<IdentityProviderBase>
		{
			new IdentityProviderBase
			{
				Id = "EmailPassword-OAUTH",
			},
			new IdentityProviderBase
			{
				Id = "Google-OAUTH",
			},
			new IdentityProviderBase
			{
				Id = "Facebook-OAUTH",
			},
		},
	},
	OnInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
		IsSignUpAllowed = true,
	},
	OnAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp
	{
		OdataType = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
		Attributes = new List<IdentityUserFlowAttribute>
		{
			new IdentityUserFlowAttribute
			{
				Id = "email",
				DisplayName = "Email Address",
				Description = "Email address of the user",
				UserFlowAttributeType = IdentityUserFlowAttributeType.BuiltIn,
				DataType = IdentityUserFlowAttributeDataType.String,
			},
			new IdentityUserFlowAttribute
			{
				Id = "displayName",
				DisplayName = "Display Name",
				Description = "Display Name of the User.",
				UserFlowAttributeType = IdentityUserFlowAttributeType.BuiltIn,
				DataType = IdentityUserFlowAttributeDataType.String,
			},
			new IdentityUserFlowAttribute
			{
				Id = "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor",
				DisplayName = "Favorite color",
				Description = "what is your favorite color",
				UserFlowAttributeType = IdentityUserFlowAttributeType.Custom,
				DataType = IdentityUserFlowAttributeDataType.String,
			},
		},
		AttributeCollectionPage = new AuthenticationAttributeCollectionPage
		{
			Views = new List<AuthenticationAttributeCollectionPageViewConfiguration>
			{
				new AuthenticationAttributeCollectionPageViewConfiguration
				{
					Inputs = new List<AuthenticationAttributeCollectionInputConfiguration>
					{
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "email",
							Label = "Email Address",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							Hidden = true,
							Editable = false,
							WriteToDirectory = true,
							Required = true,
							ValidationRegEx = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
						},
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "displayName",
							Label = "Display Name",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							Hidden = false,
							Editable = true,
							WriteToDirectory = true,
							Required = false,
							ValidationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
						},
						new AuthenticationAttributeCollectionInputConfiguration
						{
							Attribute = "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor",
							Label = "Favorite color",
							InputType = AuthenticationAttributeCollectionInputType.Text,
							Hidden = false,
							Editable = true,
							WriteToDirectory = true,
							Required = false,
							ValidationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows.PostAsync(requestBody);
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
displayName := "Woodgrove User Flow 2"
requestBody.SetDisplayName(&displayName) 
onAuthenticationMethodLoadStart := graphmodels.NewOnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp()


identityProviderBase := graphmodels.NewIdentityProviderBase()
id := "EmailPassword-OAUTH"
identityProviderBase.SetId(&id) 
identityProviderBase1 := graphmodels.NewIdentityProviderBase()
id := "Google-OAUTH"
identityProviderBase1.SetId(&id) 
identityProviderBase2 := graphmodels.NewIdentityProviderBase()
id := "Facebook-OAUTH"
identityProviderBase2.SetId(&id) 

identityProviders := []graphmodels.IdentityProviderBaseable {
	identityProviderBase,
	identityProviderBase1,
	identityProviderBase2,
}
onAuthenticationMethodLoadStart.SetIdentityProviders(identityProviders)
requestBody.SetOnAuthenticationMethodLoadStart(onAuthenticationMethodLoadStart)
onInteractiveAuthFlowStart := graphmodels.NewOnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp()
isSignUpAllowed := true
onInteractiveAuthFlowStart.SetIsSignUpAllowed(&isSignUpAllowed) 
requestBody.SetOnInteractiveAuthFlowStart(onInteractiveAuthFlowStart)
onAttributeCollection := graphmodels.NewOnAttributeCollectionExternalUsersSelfServiceSignUp()


identityUserFlowAttribute := graphmodels.NewIdentityUserFlowAttribute()
id := "email"
identityUserFlowAttribute.SetId(&id) 
displayName := "Email Address"
identityUserFlowAttribute.SetDisplayName(&displayName) 
description := "Email address of the user"
identityUserFlowAttribute.SetDescription(&description) 
userFlowAttributeType := graphmodels.BUILTIN_IDENTITYUSERFLOWATTRIBUTETYPE 
identityUserFlowAttribute.SetUserFlowAttributeType(&userFlowAttributeType) 
dataType := graphmodels.STRING_IDENTITYUSERFLOWATTRIBUTEDATATYPE 
identityUserFlowAttribute.SetDataType(&dataType) 
identityUserFlowAttribute1 := graphmodels.NewIdentityUserFlowAttribute()
id := "displayName"
identityUserFlowAttribute1.SetId(&id) 
displayName := "Display Name"
identityUserFlowAttribute1.SetDisplayName(&displayName) 
description := "Display Name of the User."
identityUserFlowAttribute1.SetDescription(&description) 
userFlowAttributeType := graphmodels.BUILTIN_IDENTITYUSERFLOWATTRIBUTETYPE 
identityUserFlowAttribute1.SetUserFlowAttributeType(&userFlowAttributeType) 
dataType := graphmodels.STRING_IDENTITYUSERFLOWATTRIBUTEDATATYPE 
identityUserFlowAttribute1.SetDataType(&dataType) 
identityUserFlowAttribute2 := graphmodels.NewIdentityUserFlowAttribute()
id := "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor"
identityUserFlowAttribute2.SetId(&id) 
displayName := "Favorite color"
identityUserFlowAttribute2.SetDisplayName(&displayName) 
description := "what is your favorite color"
identityUserFlowAttribute2.SetDescription(&description) 
userFlowAttributeType := graphmodels.CUSTOM_IDENTITYUSERFLOWATTRIBUTETYPE 
identityUserFlowAttribute2.SetUserFlowAttributeType(&userFlowAttributeType) 
dataType := graphmodels.STRING_IDENTITYUSERFLOWATTRIBUTEDATATYPE 
identityUserFlowAttribute2.SetDataType(&dataType) 

attributes := []graphmodels.IdentityUserFlowAttributeable {
	identityUserFlowAttribute,
	identityUserFlowAttribute1,
	identityUserFlowAttribute2,
}
onAttributeCollection.SetAttributes(attributes)
attributeCollectionPage := graphmodels.NewAuthenticationAttributeCollectionPage()


authenticationAttributeCollectionPageViewConfiguration := graphmodels.NewAuthenticationAttributeCollectionPageViewConfiguration()


authenticationAttributeCollectionInputConfiguration := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "email"
authenticationAttributeCollectionInputConfiguration.SetAttribute(&attribute) 
label := "Email Address"
authenticationAttributeCollectionInputConfiguration.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration.SetInputType(&inputType) 
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
authenticationAttributeCollectionInputConfiguration1 := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "displayName"
authenticationAttributeCollectionInputConfiguration1.SetAttribute(&attribute) 
label := "Display Name"
authenticationAttributeCollectionInputConfiguration1.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration1.SetInputType(&inputType) 
hidden := false
authenticationAttributeCollectionInputConfiguration1.SetHidden(&hidden) 
editable := true
authenticationAttributeCollectionInputConfiguration1.SetEditable(&editable) 
writeToDirectory := true
authenticationAttributeCollectionInputConfiguration1.SetWriteToDirectory(&writeToDirectory) 
required := false
authenticationAttributeCollectionInputConfiguration1.SetRequired(&required) 
validationRegEx := "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
authenticationAttributeCollectionInputConfiguration1.SetValidationRegEx(&validationRegEx) 
authenticationAttributeCollectionInputConfiguration2 := graphmodels.NewAuthenticationAttributeCollectionInputConfiguration()
attribute := "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor"
authenticationAttributeCollectionInputConfiguration2.SetAttribute(&attribute) 
label := "Favorite color"
authenticationAttributeCollectionInputConfiguration2.SetLabel(&label) 
inputType := graphmodels.TEXT_AUTHENTICATIONATTRIBUTECOLLECTIONINPUTTYPE 
authenticationAttributeCollectionInputConfiguration2.SetInputType(&inputType) 
hidden := false
authenticationAttributeCollectionInputConfiguration2.SetHidden(&hidden) 
editable := true
authenticationAttributeCollectionInputConfiguration2.SetEditable(&editable) 
writeToDirectory := true
authenticationAttributeCollectionInputConfiguration2.SetWriteToDirectory(&writeToDirectory) 
required := false
authenticationAttributeCollectionInputConfiguration2.SetRequired(&required) 
validationRegEx := "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
authenticationAttributeCollectionInputConfiguration2.SetValidationRegEx(&validationRegEx) 

inputs := []graphmodels.AuthenticationAttributeCollectionInputConfigurationable {
	authenticationAttributeCollectionInputConfiguration,
	authenticationAttributeCollectionInputConfiguration1,
	authenticationAttributeCollectionInputConfiguration2,
}
authenticationAttributeCollectionPageViewConfiguration.SetInputs(inputs)

views := []graphmodels.AuthenticationAttributeCollectionPageViewConfigurationable {
	authenticationAttributeCollectionPageViewConfiguration,
}
attributeCollectionPage.SetViews(views)
onAttributeCollection.SetAttributeCollectionPage(attributeCollectionPage)
requestBody.SetOnAttributeCollection(onAttributeCollection)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalUsersSelfServiceSignUpEventsFlow authenticationEventsFlow = new ExternalUsersSelfServiceSignUpEventsFlow();
authenticationEventsFlow.setOdataType("#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow");
authenticationEventsFlow.setDisplayName("Woodgrove User Flow 2");
OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp onAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp();
onAuthenticationMethodLoadStart.setOdataType("#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp");
LinkedList<IdentityProviderBase> identityProviders = new LinkedList<IdentityProviderBase>();
IdentityProviderBase identityProviderBase = new IdentityProviderBase();
identityProviderBase.setId("EmailPassword-OAUTH");
identityProviders.add(identityProviderBase);
IdentityProviderBase identityProviderBase1 = new IdentityProviderBase();
identityProviderBase1.setId("Google-OAUTH");
identityProviders.add(identityProviderBase1);
IdentityProviderBase identityProviderBase2 = new IdentityProviderBase();
identityProviderBase2.setId("Facebook-OAUTH");
identityProviders.add(identityProviderBase2);
onAuthenticationMethodLoadStart.setIdentityProviders(identityProviders);
authenticationEventsFlow.setOnAuthenticationMethodLoadStart(onAuthenticationMethodLoadStart);
OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp onInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp();
onInteractiveAuthFlowStart.setOdataType("#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp");
onInteractiveAuthFlowStart.setIsSignUpAllowed(true);
authenticationEventsFlow.setOnInteractiveAuthFlowStart(onInteractiveAuthFlowStart);
OnAttributeCollectionExternalUsersSelfServiceSignUp onAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp();
onAttributeCollection.setOdataType("#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp");
LinkedList<IdentityUserFlowAttribute> attributes = new LinkedList<IdentityUserFlowAttribute>();
IdentityUserFlowAttribute identityUserFlowAttribute = new IdentityUserFlowAttribute();
identityUserFlowAttribute.setId("email");
identityUserFlowAttribute.setDisplayName("Email Address");
identityUserFlowAttribute.setDescription("Email address of the user");
identityUserFlowAttribute.setUserFlowAttributeType(IdentityUserFlowAttributeType.BuiltIn);
identityUserFlowAttribute.setDataType(IdentityUserFlowAttributeDataType.String);
attributes.add(identityUserFlowAttribute);
IdentityUserFlowAttribute identityUserFlowAttribute1 = new IdentityUserFlowAttribute();
identityUserFlowAttribute1.setId("displayName");
identityUserFlowAttribute1.setDisplayName("Display Name");
identityUserFlowAttribute1.setDescription("Display Name of the User.");
identityUserFlowAttribute1.setUserFlowAttributeType(IdentityUserFlowAttributeType.BuiltIn);
identityUserFlowAttribute1.setDataType(IdentityUserFlowAttributeDataType.String);
attributes.add(identityUserFlowAttribute1);
IdentityUserFlowAttribute identityUserFlowAttribute2 = new IdentityUserFlowAttribute();
identityUserFlowAttribute2.setId("extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor");
identityUserFlowAttribute2.setDisplayName("Favorite color");
identityUserFlowAttribute2.setDescription("what is your favorite color");
identityUserFlowAttribute2.setUserFlowAttributeType(IdentityUserFlowAttributeType.Custom);
identityUserFlowAttribute2.setDataType(IdentityUserFlowAttributeDataType.String);
attributes.add(identityUserFlowAttribute2);
onAttributeCollection.setAttributes(attributes);
AuthenticationAttributeCollectionPage attributeCollectionPage = new AuthenticationAttributeCollectionPage();
LinkedList<AuthenticationAttributeCollectionPageViewConfiguration> views = new LinkedList<AuthenticationAttributeCollectionPageViewConfiguration>();
AuthenticationAttributeCollectionPageViewConfiguration authenticationAttributeCollectionPageViewConfiguration = new AuthenticationAttributeCollectionPageViewConfiguration();
LinkedList<AuthenticationAttributeCollectionInputConfiguration> inputs = new LinkedList<AuthenticationAttributeCollectionInputConfiguration>();
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration.setAttribute("email");
authenticationAttributeCollectionInputConfiguration.setLabel("Email Address");
authenticationAttributeCollectionInputConfiguration.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration.setHidden(true);
authenticationAttributeCollectionInputConfiguration.setEditable(false);
authenticationAttributeCollectionInputConfiguration.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration.setRequired(true);
authenticationAttributeCollectionInputConfiguration.setValidationRegEx("^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$");
inputs.add(authenticationAttributeCollectionInputConfiguration);
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration1 = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration1.setAttribute("displayName");
authenticationAttributeCollectionInputConfiguration1.setLabel("Display Name");
authenticationAttributeCollectionInputConfiguration1.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration1.setHidden(false);
authenticationAttributeCollectionInputConfiguration1.setEditable(true);
authenticationAttributeCollectionInputConfiguration1.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration1.setRequired(false);
authenticationAttributeCollectionInputConfiguration1.setValidationRegEx("^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$");
inputs.add(authenticationAttributeCollectionInputConfiguration1);
AuthenticationAttributeCollectionInputConfiguration authenticationAttributeCollectionInputConfiguration2 = new AuthenticationAttributeCollectionInputConfiguration();
authenticationAttributeCollectionInputConfiguration2.setAttribute("extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor");
authenticationAttributeCollectionInputConfiguration2.setLabel("Favorite color");
authenticationAttributeCollectionInputConfiguration2.setInputType(AuthenticationAttributeCollectionInputType.Text);
authenticationAttributeCollectionInputConfiguration2.setHidden(false);
authenticationAttributeCollectionInputConfiguration2.setEditable(true);
authenticationAttributeCollectionInputConfiguration2.setWriteToDirectory(true);
authenticationAttributeCollectionInputConfiguration2.setRequired(false);
authenticationAttributeCollectionInputConfiguration2.setValidationRegEx("^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$");
inputs.add(authenticationAttributeCollectionInputConfiguration2);
authenticationAttributeCollectionPageViewConfiguration.setInputs(inputs);
views.add(authenticationAttributeCollectionPageViewConfiguration);
attributeCollectionPage.setViews(views);
onAttributeCollection.setAttributeCollectionPage(attributeCollectionPage);
authenticationEventsFlow.setOnAttributeCollection(onAttributeCollection);
AuthenticationEventsFlow result = graphClient.identity().authenticationEventsFlows().post(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventsFlow = {
    '@odata.type': '#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow',
    displayName: 'Woodgrove User Flow 2',
    onAuthenticationMethodLoadStart: {
        '@odata.type': '#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp',
        identityProviders: [
            {
                id: 'EmailPassword-OAUTH'
            },
            {
                id: 'Google-OAUTH'
            },
            {
                id: 'Facebook-OAUTH'
            }
        ]
    },  
    onInteractiveAuthFlowStart: {
        '@odata.type': '#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp',
        isSignUpAllowed: true
    },
    onAttributeCollection: {
        '@odata.type': '#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp',
        attributes: [
            {
                id: 'email',
                displayName: 'Email Address',
                description: 'Email address of the user',
                userFlowAttributeType: 'builtIn',
                dataType: 'string'
            },
            {
                id: 'displayName',
                displayName: 'Display Name',
                description: 'Display Name of the User.',
                userFlowAttributeType: 'builtIn',
                dataType: 'string'
            },
            {
                id: 'extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor',
                displayName: 'Favorite color',
                description: 'what is your favorite color',
                userFlowAttributeType: 'custom',
                dataType: 'string'
            }
        ],
        attributeCollectionPage: {
            views: [
                {
                    inputs: [
                        {
                            attribute: 'email',
                            label: 'Email Address',
                            inputType: 'Text',
                            hidden: true,
                            editable: false,
                            writeToDirectory: true,
                            required: true,
                            validationRegEx: '^[a-zA-Z0-9.!#$%&amp;&#8217;\'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$'
                        },
                        {
                            attribute: 'displayName',
                            label: 'Display Name',
                            inputType: 'text',
                            hidden: false,
                            editable: true,
                            writeToDirectory: true,
                            required: false,
                            validationRegEx: '^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$'
                        },
                        {
                            attribute: 'extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor',
                            label: 'Favorite color',
                            inputType: 'text',
                            hidden: false,
                            editable: true,
                            writeToDirectory: true,
                            required: false,
                            validationRegEx: '^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$'
                        }
                    ]
                }
            ]
        }
    }
};

await client.api('/identity/authenticationEventsFlows')
	.post(authenticationEventsFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalUsersSelfServiceSignUpEventsFlow;
use Microsoft\Graph\Generated\Models\OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\IdentityProviderBase;
use Microsoft\Graph\Generated\Models\OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\OnAttributeCollectionExternalUsersSelfServiceSignUp;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttribute;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttributeType;
use Microsoft\Graph\Generated\Models\IdentityUserFlowAttributeDataType;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionPage;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionPageViewConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionInputConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationAttributeCollectionInputType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalUsersSelfServiceSignUpEventsFlow();
$requestBody->setOdataType('#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow');
$requestBody->setDisplayName('Woodgrove User Flow 2');
$onAuthenticationMethodLoadStart = new OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp();
$onAuthenticationMethodLoadStart->setOdataType('#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp');
$identityProvidersIdentityProviderBase1 = new IdentityProviderBase();
$identityProvidersIdentityProviderBase1->setId('EmailPassword-OAUTH');
$identityProvidersArray []= $identityProvidersIdentityProviderBase1;
$identityProvidersIdentityProviderBase2 = new IdentityProviderBase();
$identityProvidersIdentityProviderBase2->setId('Google-OAUTH');
$identityProvidersArray []= $identityProvidersIdentityProviderBase2;
$identityProvidersIdentityProviderBase3 = new IdentityProviderBase();
$identityProvidersIdentityProviderBase3->setId('Facebook-OAUTH');
$identityProvidersArray []= $identityProvidersIdentityProviderBase3;
$onAuthenticationMethodLoadStart->setIdentityProviders($identityProvidersArray);

$requestBody->setOnAuthenticationMethodLoadStart($onAuthenticationMethodLoadStart);
$onInteractiveAuthFlowStart = new OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp();
$onInteractiveAuthFlowStart->setOdataType('#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp');
$onInteractiveAuthFlowStart->setIsSignUpAllowed(true);
$requestBody->setOnInteractiveAuthFlowStart($onInteractiveAuthFlowStart);
$onAttributeCollection = new OnAttributeCollectionExternalUsersSelfServiceSignUp();
$onAttributeCollection->setOdataType('#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp');
$attributesIdentityUserFlowAttribute1 = new IdentityUserFlowAttribute();
$attributesIdentityUserFlowAttribute1->setId('email');
$attributesIdentityUserFlowAttribute1->setDisplayName('Email Address');
$attributesIdentityUserFlowAttribute1->setDescription('Email address of the user');
$attributesIdentityUserFlowAttribute1->setUserFlowAttributeType(new IdentityUserFlowAttributeType('builtIn'));
$attributesIdentityUserFlowAttribute1->setDataType(new IdentityUserFlowAttributeDataType('string'));
$attributesArray []= $attributesIdentityUserFlowAttribute1;
$attributesIdentityUserFlowAttribute2 = new IdentityUserFlowAttribute();
$attributesIdentityUserFlowAttribute2->setId('displayName');
$attributesIdentityUserFlowAttribute2->setDisplayName('Display Name');
$attributesIdentityUserFlowAttribute2->setDescription('Display Name of the User.');
$attributesIdentityUserFlowAttribute2->setUserFlowAttributeType(new IdentityUserFlowAttributeType('builtIn'));
$attributesIdentityUserFlowAttribute2->setDataType(new IdentityUserFlowAttributeDataType('string'));
$attributesArray []= $attributesIdentityUserFlowAttribute2;
$attributesIdentityUserFlowAttribute3 = new IdentityUserFlowAttribute();
$attributesIdentityUserFlowAttribute3->setId('extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor');
$attributesIdentityUserFlowAttribute3->setDisplayName('Favorite color');
$attributesIdentityUserFlowAttribute3->setDescription('what is your favorite color');
$attributesIdentityUserFlowAttribute3->setUserFlowAttributeType(new IdentityUserFlowAttributeType('custom'));
$attributesIdentityUserFlowAttribute3->setDataType(new IdentityUserFlowAttributeDataType('string'));
$attributesArray []= $attributesIdentityUserFlowAttribute3;
$onAttributeCollection->setAttributes($attributesArray);

$onAttributeCollectionAttributeCollectionPage = new AuthenticationAttributeCollectionPage();
$viewsAuthenticationAttributeCollectionPageViewConfiguration1 = new AuthenticationAttributeCollectionPageViewConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration1 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration1->setAttribute('email');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setLabel('Email Address');
$inputsAuthenticationAttributeCollectionInputConfiguration1->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration1->setHidden(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setEditable(false);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setRequired(true);
$inputsAuthenticationAttributeCollectionInputConfiguration1->setValidationRegEx('^[a-zA-Z0-9.!#$%&amp;&#8217;\'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$');
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration1;
$inputsAuthenticationAttributeCollectionInputConfiguration2 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration2->setAttribute('displayName');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setLabel('Display Name');
$inputsAuthenticationAttributeCollectionInputConfiguration2->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration2->setHidden(false);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setEditable(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setRequired(false);
$inputsAuthenticationAttributeCollectionInputConfiguration2->setValidationRegEx('^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$');
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration2;
$inputsAuthenticationAttributeCollectionInputConfiguration3 = new AuthenticationAttributeCollectionInputConfiguration();
$inputsAuthenticationAttributeCollectionInputConfiguration3->setAttribute('extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor');
$inputsAuthenticationAttributeCollectionInputConfiguration3->setLabel('Favorite color');
$inputsAuthenticationAttributeCollectionInputConfiguration3->setInputType(new AuthenticationAttributeCollectionInputType('text'));
$inputsAuthenticationAttributeCollectionInputConfiguration3->setHidden(false);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setEditable(true);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setWriteToDirectory(true);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setRequired(false);
$inputsAuthenticationAttributeCollectionInputConfiguration3->setValidationRegEx('^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$');
$inputsArray []= $inputsAuthenticationAttributeCollectionInputConfiguration3;
$viewsAuthenticationAttributeCollectionPageViewConfiguration1->setInputs($inputsArray);

$viewsArray []= $viewsAuthenticationAttributeCollectionPageViewConfiguration1;
$onAttributeCollectionAttributeCollectionPage->setViews($viewsArray);

$onAttributeCollection->setAttributeCollectionPage($onAttributeCollectionAttributeCollectionPage);
$requestBody->setOnAttributeCollection($onAttributeCollection);

$result = $graphServiceClient->identity()->authenticationEventsFlows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow"
	displayName = "Woodgrove User Flow 2"
	onAuthenticationMethodLoadStart = @{
		"@odata.type" = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp"
		identityProviders = @(
			@{
				id = "EmailPassword-OAUTH"
			}
			@{
				id = "Google-OAUTH"
			}
			@{
				id = "Facebook-OAUTH"
			}
		)
	}
	onInteractiveAuthFlowStart = @{
		"@odata.type" = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp"
		isSignUpAllowed = $true
	}
	onAttributeCollection = @{
		"@odata.type" = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp"
		attributes = @(
			@{
				id = "email"
				displayName = "Email Address"
				description = "Email address of the user"
				userFlowAttributeType = "builtIn"
				dataType = "string"
			}
			@{
				id = "displayName"
				displayName = "Display Name"
				description = "Display Name of the User."
				userFlowAttributeType = "builtIn"
				dataType = "string"
			}
			@{
				id = "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor"
				displayName = "Favorite color"
				description = "what is your favorite color"
				userFlowAttributeType = "custom"
				dataType = "string"
			}
		)
		attributeCollectionPage = @{
			views = @(
				@{
					inputs = @(
						@{
							attribute = "email"
							label = "Email Address"
							inputType = "Text"
							hidden = $true
							editable = $false
							writeToDirectory = $true
							required = $true
							validationRegEx = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$"
						}
						@{
							attribute = "displayName"
							label = "Display Name"
							inputType = "text"
							hidden = $false
							editable = $true
							writeToDirectory = $true
							required = $false
							validationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
						}
						@{
							attribute = "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor"
							label = "Favorite color"
							inputType = "text"
							hidden = $false
							editable = $true
							writeToDirectory = $true
							required = $false
							validationRegEx = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$"
						}
					)
				}
			)
		}
	}
}

New-MgIdentityAuthenticationEventFlow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_users_self_service_sign_up_events_flow import ExternalUsersSelfServiceSignUpEventsFlow
from msgraph.generated.models.on_authentication_method_load_start_external_users_self_service_sign_up import OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp
from msgraph.generated.models.identity_provider_base import IdentityProviderBase
from msgraph.generated.models.on_interactive_auth_flow_start_external_users_self_service_sign_up import OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp
from msgraph.generated.models.on_attribute_collection_external_users_self_service_sign_up import OnAttributeCollectionExternalUsersSelfServiceSignUp
from msgraph.generated.models.identity_user_flow_attribute import IdentityUserFlowAttribute
from msgraph.generated.models.identity_user_flow_attribute_type import IdentityUserFlowAttributeType
from msgraph.generated.models.identity_user_flow_attribute_data_type import IdentityUserFlowAttributeDataType
from msgraph.generated.models.authentication_attribute_collection_page import AuthenticationAttributeCollectionPage
from msgraph.generated.models.authentication_attribute_collection_page_view_configuration import AuthenticationAttributeCollectionPageViewConfiguration
from msgraph.generated.models.authentication_attribute_collection_input_configuration import AuthenticationAttributeCollectionInputConfiguration
from msgraph.generated.models.authentication_attribute_collection_input_type import AuthenticationAttributeCollectionInputType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalUsersSelfServiceSignUpEventsFlow(
	odata_type = "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
	display_name = "Woodgrove User Flow 2",
	on_authentication_method_load_start = OnAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
		identity_providers = [
			IdentityProviderBase(
				id = "EmailPassword-OAUTH",
			),
			IdentityProviderBase(
				id = "Google-OAUTH",
			),
			IdentityProviderBase(
				id = "Facebook-OAUTH",
			),
		],
	),
	on_interactive_auth_flow_start = OnInteractiveAuthFlowStartExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
		is_sign_up_allowed = True,
	),
	on_attribute_collection = OnAttributeCollectionExternalUsersSelfServiceSignUp(
		odata_type = "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
		attributes = [
			IdentityUserFlowAttribute(
				id = "email",
				display_name = "Email Address",
				description = "Email address of the user",
				user_flow_attribute_type = IdentityUserFlowAttributeType.BuiltIn,
				data_type = IdentityUserFlowAttributeDataType.String,
			),
			IdentityUserFlowAttribute(
				id = "displayName",
				display_name = "Display Name",
				description = "Display Name of the User.",
				user_flow_attribute_type = IdentityUserFlowAttributeType.BuiltIn,
				data_type = IdentityUserFlowAttributeDataType.String,
			),
			IdentityUserFlowAttribute(
				id = "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor",
				display_name = "Favorite color",
				description = "what is your favorite color",
				user_flow_attribute_type = IdentityUserFlowAttributeType.Custom,
				data_type = IdentityUserFlowAttributeDataType.String,
			),
		],
		attribute_collection_page = AuthenticationAttributeCollectionPage(
			views = [
				AuthenticationAttributeCollectionPageViewConfiguration(
					inputs = [
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "email",
							label = "Email Address",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							hidden = True,
							editable = False,
							write_to_directory = True,
							required = True,
							validation_reg_ex = "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$",
						),
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "displayName",
							label = "Display Name",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							hidden = False,
							editable = True,
							write_to_directory = True,
							required = False,
							validation_reg_ex = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
						),
						AuthenticationAttributeCollectionInputConfiguration(
							attribute = "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor",
							label = "Favorite color",
							input_type = AuthenticationAttributeCollectionInputType.Text,
							hidden = False,
							editable = True,
							write_to_directory = True,
							required = False,
							validation_reg_ex = "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
						),
					],
				),
			],
		),
	),
)

result = await graph_client.identity.authentication_events_flows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows/$entity",
    "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
    "id": "{authentictionEventsFlow-id}",
    "displayName": "Woodgrove User Flow 2",
    "description": null,
    "onUserCreateStart": null,
    "conditions": {
        "applications": {
            "includeAllApplications": false
        }
    },
    "onInteractiveAuthFlowStart": {
        "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
        "isSignUpAllowed": true
    },
    "onAuthenticationMethodLoadStart": {
        "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp"
    },
    "onAttributeCollection": {
        "@odata.type": "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
        "attributeCollectionPage": {
            "customStringsFileId": null,
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
                            "required": false,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
                            "options": []
                        },
                        {
                            "attribute": "extension_6ea3bc85aec24b1c92ff4a117afb6621_Favoritecolor",
                            "label": "Favorite color",
                            "inputType": "text",
                            "defaultValue": null,
                            "hidden": false,
                            "editable": true,
                            "writeToDirectory": true,
                            "required": false,
                            "validationRegEx": "^[a-zA-Z_][0-9a-zA-Z_ ]*[0-9a-zA-Z_]+$",
                            "options": []
                        }
                    ]
                }
            ]
        }
    }
}
```
