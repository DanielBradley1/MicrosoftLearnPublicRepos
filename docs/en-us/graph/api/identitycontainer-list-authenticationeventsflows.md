<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitycontainer-list-authenticationeventsflows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List authenticationEventsFlows

Namespace: microsoft.graph

Get a collection of authentication events policies that are derived from [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0). The following derived subtypes are supported:

- [externalUsersSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EventListener.Read.All | EventListener.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EventListener.Read.All | EventListener.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- External ID User Flow Administrator
- External Identity Provider Administrator

## HTTP request

```http
GET /identity/authenticationEventsFlows
```

## Optional query parameters

This method supports the `$filter`, `$expand`, `$orderby`, and `$top` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: List all user flows

#### Request

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
GET https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationEventsFlowCollectionResponse result = graphClient.identity().authenticationEventsFlows().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authenticationEventsFlows = await client.api('/identity/authenticationEventsFlows')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identity()->authenticationEventsFlows()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityAuthenticationEventFlow
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity.authentication_events_flows.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following is an example of a response that returns two user flows: "Test User Flow 1" and "Woodgrove Drive User Flow" with the following configurations:

- "Test User Flow 1" is set up to allow email+password accounts, collect email address and country/region, and create a "Member" user type.
- "Woodgrove Drive User Flow" is set up to allow email+password accounts or social \(Google or Facebook\) sign in, collect email address, display name, and favorite color, and create "Member" user type.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value": [
        {
            "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
            "id": "79a67c51-c86d-4a48-8313-1e14ac821e16",
            "displayName": "TestUserFlow1",
            "description": null,
            "onAttributeCollectionStart": null,
            "onAttributeCollectionSubmit": null,
            "conditions": {
                "applications": {
                    "includeAllApplications": false,
                    "includeApplications@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows('79a67c51-c86d-4a48-8313-1e14ac821e16')/microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications",
                    "includeApplications": []
                }
            },
            "onInteractiveAuthFlowStart": {
                "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
                "isSignUpAllowed": true
            },
            "onAuthenticationMethodLoadStart": {
                "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
                "identityProviders": [
                    {
                        "@odata.type": "#microsoft.graph.builtInIdentityProvider",
                        "id": "EmailPassword-OAUTH",
                        "displayName": "Email with password",
                        "identityProviderType": "EmailPassword"                    }
                ]
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
                                    "attribute": "country",
                                    "label": "Country/Region",
                                    "inputType": "text",
                                    "defaultValue": null,
                                    "hidden": false,
                                    "editable": true,
                                    "writeToDirectory": true,
                                    "required": false,
                                    "validationRegEx": "^.*",
                                    "options": []
                                }
                            ]
                        }
                    ]
                },
                "attributes": [
                    {
                        "id": "email",
                        "displayName": "Email Address",
                        "description": "Email address of the user",
                        "userFlowAttributeType": "builtIn",
                        "dataType": "string"
                    },
                    {
                        "id": "country",
                        "displayName": "Country/Region",
                        "description": "The country/region in which the user is located.",
                        "userFlowAttributeType": "builtIn",
                        "dataType": "string"
                    }
                ]
            },
            "onUserCreateStart": {
                "@odata.type": "#microsoft.graph.onUserCreateStartExternalUsersSelfServiceSignUp",
                "userTypeToCreate": "member"
            }
        },
        {
            "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
            "id": "0313cc37-d421-421d-857b-87804d61e33e",
            "displayName": "Woodgrove Drive User Flow",
            "description": "For onboarding consumers to the Woodgrove Drive application",
            "onAttributeCollectionStart": null,
            "onAttributeCollectionSubmit": null,
            "conditions": {
                "applications": {
                    "includeAllApplications": false,
                    "includeApplications@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows('0313cc37-d421-421d-857b-87804d61e33e')/microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications",
                    "includeApplications": []
                }
            },
            "onInteractiveAuthFlowStart": {
                "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
                "isSignUpAllowed": true
            },
            "onAuthenticationMethodLoadStart": {
                "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
                "identityProviders": [
                    {
                        "@odata.type": "#microsoft.graph.builtInIdentityProvider",
                        "id": "EmailPassword-OAUTH",
                        "displayName": "Email with password",
                        "identityProviderType": "EmailPassword"
                    },
                    {
                        "@odata.type": "#microsoft.graph.socialIdentityProvider",
                        "id": "Google-OAUTH",
                        "displayName": "Google",
                        "identityProviderType": "Google",
                        "clientId": "137004260525-q8j2cp9hqceqa6hpvaa346e04g92tn8m.apps.googleusercontent.com",
                        "clientSecret": "******"
                    },
                    {
                        "@odata.type": "#microsoft.graph.socialIdentityProvider",
                        "id": "Facebook-OAUTH",
                        "displayName": "Facebook",
                        "identityProviderType": "Facebook",
                        "clientId": "236028191057849",
                        "clientSecret": "******"
                    }
                ]
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
                                    "validationRegEx": "^.*",
                                    "options": []
                                }
                            ]
                        }
                    ]
                },
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
                ]
            },
            "onUserCreateStart": {
                "@odata.type": "#microsoft.graph.onUserCreateStartExternalUsersSelfServiceSignUp",
                "userTypeToCreate": "member"
            }
        }
    ]
}
```

### Example 2: List all user flows that include Google as an identity provider

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows?$filter=microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq 'Google-OAUTH')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq 'Google-OAUTH')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentity "github.com/microsoftgraph/msgraph-sdk-go/identity"
	  //other-imports
)


requestFilter := "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq 'Google-OAUTH')"

requestParameters := &graphidentity.IdentityAuthenticationEventsFlowsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentity.IdentityAuthenticationEventsFlowsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationEventsFlowCollectionResponse result = graphClient.identity().authenticationEventsFlows().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq 'Google-OAUTH')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authenticationEventsFlows = await client.api('/identity/authenticationEventsFlows')
	.filter('microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq \'Google-OAUTH\')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\AuthenticationEventsFlows\AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq 'Google-OAUTH')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identity()->authenticationEventsFlows()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityAuthenticationEventFlow -Filter "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq 'Google-OAUTH')" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.authentication_events_flows.authentication_events_flows_request_builder import AuthenticationEventsFlowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthenticationEventsFlowsRequestBuilder.AuthenticationEventsFlowsRequestBuilderGetQueryParameters(
		filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq 'Google-OAUTH')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity.authentication_events_flows.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows",
    "value": [
        {
            "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
            "id": "0313cc37-d421-421d-857b-87804d61e33e",
            "displayName": "Woodgrove Drive User Flow",
            "description": "For onboarding consumers to the Woodgrove Drive application",
            "onAttributeCollectionStart": null,
            "onAttributeCollectionSubmit": null,
            "conditions": {
                "applications": {
                    "includeAllApplications": false,
                    "includeApplications@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows('0313cc37-d421-421d-857b-87804d61e33e')/microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications",
                    "includeApplications": []
                }
            },
            "onInteractiveAuthFlowStart": {
                "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
                "isSignUpAllowed": true
            },
            "onAuthenticationMethodLoadStart": {
                "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
                "identityProviders": [
                    {
                        "@odata.type": "#microsoft.graph.builtInIdentityProvider",
                        "id": "EmailPassword-OAUTH",
                        "displayName": "Email with password",
                        "identityProviderType": "EmailPassword"
                    },
                    {
                        "@odata.type": "#microsoft.graph.socialIdentityProvider",
                        "id": "Google-OAUTH",
                        "displayName": "Google",
                        "identityProviderType": "Google",
                        "clientId": "############-q8j2cp9hqceqa6hpvaa346e04g92tn8m.apps.googleusercontent.com",
                        "clientSecret": "******"
                    },
                    {
                        "@odata.type": "#microsoft.graph.socialIdentityProvider",
                        "id": "Facebook-OAUTH",
                        "displayName": "Facebook",
                        "identityProviderType": "Facebook",
                        "clientId": "###############",
                        "clientSecret": "******"
                    }
                ]
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
                                    "validationRegEx": "^.*",
                                    "options": []
                                }
                            ]
                        }
                    ]
                },
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
                ]
            },
            "onUserCreateStart": {
                "@odata.type": "#microsoft.graph.onUserCreateStartExternalUsersSelfServiceSignUp",
                "userTypeToCreate": "member"
            }
        }
    ]
}
```

### Example 3: List all user flows that collect 'city' during attribute collection at account creation

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
GET https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows?$filter=microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq 'city')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq 'city')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentity "github.com/microsoftgraph/msgraph-sdk-go/identity"
	  //other-imports
)


requestFilter := "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq 'city')"

requestParameters := &graphidentity.IdentityAuthenticationEventsFlowsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentity.IdentityAuthenticationEventsFlowsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationEventsFlowCollectionResponse result = graphClient.identity().authenticationEventsFlows().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq 'city')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authenticationEventsFlows = await client.api('/identity/authenticationEventsFlows')
	.filter('microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq \'city\')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\AuthenticationEventsFlows\AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq 'city')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identity()->authenticationEventsFlows()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityAuthenticationEventFlow -Filter "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq 'city')" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.authentication_events_flows.authentication_events_flows_request_builder import AuthenticationEventsFlowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthenticationEventsFlowsRequestBuilder.AuthenticationEventsFlowsRequestBuilderGetQueryParameters(
		filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq 'city')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity.authentication_events_flows.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows",
    "value": [
        {
            "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
            "id": "0313cc37-d421-421d-857b-87804d61e33e",
            "displayName": "TestUserFlow3",
            "description": "my user flow description newestXXX",
            "onAttributeCollectionStart": null,
            "onAttributeCollectionSubmit": null,
            "conditions": {
                "applications": {
                    "includeAllApplications": false,
                    "includeApplications@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows('0313cc37-d421-421d-857b-87804d61e33e')/microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications",
                    "includeApplications": []
                }
            },
            "onInteractiveAuthFlowStart": {
                "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
                "isSignUpAllowed": true
            },
            "onAuthenticationMethodLoadStart": {
                "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
                "identityProviders": [
                    {
                        "@odata.type": "#microsoft.graph.builtInIdentityProvider",
                        "id": "AADSignup-OAUTH",
                        "displayName": "Azure Active Directory Sign up",
                        "identityProviderType": "AADSignup"
                    },
                    {
                        "@odata.type": "#microsoft.graph.builtInIdentityProvider",
                        "id": "EmailPassword-OAUTH",
                        "displayName": "Email with password",
                        "identityProviderType": "EmailPassword"
                    },
                    {
                        "@odata.type": "#microsoft.graph.socialIdentityProvider",
                        "id": "Google-OAUTH",
                        "displayName": "Google",
                        "identityProviderType": "Google",
                        "clientId": "137004260525-q8j2cp9hqceqa6hpvaa346e04g92tn8m.apps.googleusercontent.com",
                        "clientSecret": "******"
                    },
                    {
                        "@odata.type": "#microsoft.graph.socialIdentityProvider",
                        "id": "Facebook-OAUTH",
                        "displayName": "Facebook",
                        "identityProviderType": "Facebook",
                        "clientId": "236028191057849",
                        "clientSecret": "******"
                    }
                ]
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
                                    "attribute": "city",
                                    "label": "City",
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
                },
                "attributes": [
                    {
                        "id": "email",
                        "displayName": "Email Address",
                        "description": "Email address of the user",
                        "userFlowAttributeType": "builtIn",
                        "dataType": "string"
                    },
                    {
                        "id": "city",
                        "displayName": "City",
                        "description": "The city in which the user is located.",
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
                ]
            },
            "onUserCreateStart": {
                "@odata.type": "#microsoft.graph.onUserCreateStartExternalUsersSelfServiceSignUp",
                "userTypeToCreate": "member"
            }
        },
        {
            "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
            "id": "f5b9b311-cb87-445b-a655-e6e6a4d3e582",
            "displayName": "TestUserFlow4",
            "description": null,
            "onAttributeCollectionStart": null,
            "onAttributeCollectionSubmit": null,
            "conditions": {
                "applications": {
                    "includeAllApplications": false,
                    "includeApplications@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows('f5b9b311-cb87-445b-a655-e6e6a4d3e582')/microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications",
                    "includeApplications": []
                }
            },
            "onInteractiveAuthFlowStart": {
                "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
                "isSignUpAllowed": true
            },
            "onAuthenticationMethodLoadStart": {
                "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
                "identityProviders": [
                    {
                        "@odata.type": "#microsoft.graph.builtInIdentityProvider",
                        "id": "EmailPassword-OAUTH",
                        "displayName": "Email with password",
                        "identityProviderType": "EmailPassword"
                    }
                ]
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
                                    "attribute": "city",
                                    "label": "City",
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
                                    "attribute": "country",
                                    "label": "Country/Region",
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
                },
                "attributes": [
                    {
                        "id": "email",
                        "displayName": "Email Address",
                        "description": "Email address of the user",
                        "userFlowAttributeType": "builtIn",
                        "dataType": "string"
                    },
                    {
                        "id": "city",
                        "displayName": "City",
                        "description": "The city in which the user is located.",
                        "userFlowAttributeType": "builtIn",
                        "dataType": "string"
                    },
                    {
                        "id": "country",
                        "displayName": "Country/Region",
                        "description": "The country/region in which the user is located.",
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
                ]
            },
            "onUserCreateStart": {
                "@odata.type": "#microsoft.graph.onUserCreateStartExternalUsersSelfServiceSignUp",
                "userTypeToCreate": "member"
            }
        }
    ]
}
```

### Example 4: List user flow associated with specific application ID

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
GET https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows?$filter=microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq '63856651-13d9-4784-9abf-20758d509e19')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq '63856651-13d9-4784-9abf-20758d509e19')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentity "github.com/microsoftgraph/msgraph-sdk-go/identity"
	  //other-imports
)


requestFilter := "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq '63856651-13d9-4784-9abf-20758d509e19')"

requestParameters := &graphidentity.IdentityAuthenticationEventsFlowsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentity.IdentityAuthenticationEventsFlowsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationEventsFlowCollectionResponse result = graphClient.identity().authenticationEventsFlows().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq '63856651-13d9-4784-9abf-20758d509e19')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authenticationEventsFlows = await client.api('/identity/authenticationEventsFlows')
	.filter('microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq \'63856651-13d9-4784-9abf-20758d509e19\')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\AuthenticationEventsFlows\AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthenticationEventsFlowsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq '63856651-13d9-4784-9abf-20758d509e19')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identity()->authenticationEventsFlows()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityAuthenticationEventFlow -Filter "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq '63856651-13d9-4784-9abf-20758d509e19')" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.authentication_events_flows.authentication_events_flows_request_builder import AuthenticationEventsFlowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthenticationEventsFlowsRequestBuilder.AuthenticationEventsFlowsRequestBuilderGetQueryParameters(
		filter = "microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq '63856651-13d9-4784-9abf-20758d509e19')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity.authentication_events_flows.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows",
    "value": [
        {
            "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
            "id": "b5ca7ddb-f5e4-4dea-8ee5-282116ddc71d",
            "displayName": "Test User Flow",
            "description": null,
            "onAttributeCollectionStart": null,
            "onAttributeCollectionSubmit": null,
            "conditions": {
                "applications": {
                    "includeAllApplications": false,
                    "includeApplications@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventsFlows('b5ca7ddb-f5e4-4dea-8ee5-282116ddc71d')/microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications",
                    "includeApplications": [
                        {
                            "appId": "63856651-13d9-4784-9abf-20758d509e19"
                        }
                    ]
                }
            },
            "onInteractiveAuthFlowStart": {
                "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
                "isSignUpAllowed": true
            },
            "onAuthenticationMethodLoadStart": {
                "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp",
                "identityProviders": [
                    {
                        "@odata.type": "#microsoft.graph.builtInIdentityProvider",
                        "id": "EmailPassword-OAUTH",
                        "displayName": "Email with password",
                        "identityProviderType": "EmailPassword"
                    }
                ]
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
                                    "validationRegEx": "^[a-zA-Z0-9.!#$%&amp;&#8217;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\\.[a-zA-Z0-9-]+)*$",
                                    "options": []
                                },
                                {
                                    "attribute": "extension_6ea3bc85aec24b1c92ff4a117afb6621_RewardsNumber",
                                    "label": "Rewards number",
                                    "inputType": "text",
                                    "defaultValue": null,
                                    "hidden": false,
                                    "editable": true,
                                    "writeToDirectory": true,
                                    "required": false,
                                    "validationRegEx": "^.*",
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
                                    "validationRegEx": "^.*",
                                    "options": []
                                }
                            ]
                        }
                    ]
                },
                "attributes": [
                    {
                        "id": "email",
                        "displayName": "Email Address",
                        "description": "Email address of the user",
                        "userFlowAttributeType": "builtIn",
                        "dataType": "string"
                    },
                    {
                        "id": "extension_6ea3bc85aec24b1c92ff4a117afb6621_RewardsNumber",
                        "displayName": "RewardsNumber",
                        "description": null,
                        "userFlowAttributeType": "custom",
                        "dataType": "string"
                    },
                    {
                        "id": "displayName",
                        "displayName": "Display Name",
                        "description": "Display Name of the User.",
                        "userFlowAttributeType": "builtIn",
                        "dataType": "string"
                    }
                ]
            },
            "onUserCreateStart": {
                "@odata.type": "#microsoft.graph.onUserCreateStartExternalUsersSelfServiceSignUp",
                "userTypeToCreate": "member"
            }
        }
    ]
}
```
