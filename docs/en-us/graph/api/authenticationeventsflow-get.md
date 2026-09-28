<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationeventsflow-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get authenticationEventsFlow

Namespace: microsoft.graph

Retrieve the properties and relationships of a specific [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object by ID. The **@odata.type** property in the response object indicates the type of the object, which can be one of the following derived subtypes:

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
GET /identity/authenticationEventsFlows/{authenticationEventsFlow-id}
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request to retrieve a specific External Identities user flow.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/identity/authenticationEventsFlows/0313cc37-d421-421d-857b-87804d61e33e
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventsFlows["{authenticationEventsFlow-id}"].GetAsync();
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
authenticationEventsFlows, err := graphClient.Identity().AuthenticationEventsFlows().ByAuthenticationEventsFlowId("authenticationEventsFlow-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationEventsFlow result = graphClient.identity().authenticationEventsFlows().byAuthenticationEventsFlowId("{authenticationEventsFlow-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authenticationEventsFlow = await client.api('/identity/authenticationEventsFlows/0313cc37-d421-421d-857b-87804d61e33e')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identity()->authenticationEventsFlows()->byAuthenticationEventsFlowId('authenticationEventsFlow-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityAuthenticationEventFlow -AuthenticationEventsFlowId $authenticationEventsFlowId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity.authentication_events_flows.by_authentication_events_flow_id('authenticationEventsFlow-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response. In this example, the user flow retrieved is named "Woodgrove Drive Users Flow" and is set up to:

- Allow users to create a local email with password account, or sign up with their Google or Facebook identity
- Collect **Display Name** and **Favorite Color**
- Create a "Member" user type.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value": {
        "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
        "id": "0313cc37-d421-421d-857b-87804d61e33e",
        "displayName": "Woodgrove Drive User Flow",
        "description": "For onboarding consumers to the Woodgrove Drive application",
        "conditions": {
            "applications": {
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
            "userTypeToCreate": "member",
            "accessPackages": []
        }
    }
}
```
