<!-- Source: https://learn.microsoft.com/en-us/graph/api/applicationtemplate-instantiate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# applicationTemplate: instantiate

Namespace: microsoft.graph

Add an instance of an application from the [Microsoft Entra application gallery](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) into your directory.

For [non-gallery apps](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal), use an application template with one of the following IDs to configure different single sign-on \(SSO\) modes like SAML SSO and password-based SSO.

- Global service: `8adf8e6e-67b2-4cf2-a259-e3dc5476c621`
- US government: `4602d0b4-76bb-404b-bca9-2652e1a39c6d`
- China operated by 21Vianet: `5a532e38-1581-4918-9658-008dc27c1d68`

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | Application.ReadWrite.All, Directory.ReadWrite.All |

## HTTP request

```http
POST /applicationTemplates/{applicationTemplate-id}/instantiate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Custom name of the application |

## Response

If successful, this method returns a `201 Created` response code and a new [applicationServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/applicationserviceprincipal?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/applicationTemplates/229946b9-a9fb-45b8-9531-efa47453ac9e/instantiate
Content-type: application/json

{
    "displayName": "Azure AD SAML Toolkit"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.ApplicationTemplates.Item.Instantiate;

var requestBody = new InstantiatePostRequestBody
{
	DisplayName = "Azure AD SAML Toolkit",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ApplicationTemplates["{applicationTemplate-id}"].Instantiate.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphapplicationtemplates "github.com/microsoftgraph/msgraph-sdk-go/applicationtemplates"
	  //other-imports
)

requestBody := graphapplicationtemplates.NewInstantiatePostRequestBody()
displayName := "Azure AD SAML Toolkit"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
instantiate, err := graphClient.ApplicationTemplates().ByApplicationTemplateId("applicationTemplate-id").Instantiate().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.applicationtemplates.item.instantiate.InstantiatePostRequestBody instantiatePostRequestBody = new com.microsoft.graph.applicationtemplates.item.instantiate.InstantiatePostRequestBody();
instantiatePostRequestBody.setDisplayName("Azure AD SAML Toolkit");
var result = graphClient.applicationTemplates().byApplicationTemplateId("{applicationTemplate-id}").instantiate().post(instantiatePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const applicationServicePrincipal = {
    displayName: 'Azure AD SAML Toolkit'
};

await client.api('/applicationTemplates/229946b9-a9fb-45b8-9531-efa47453ac9e/instantiate')
	.post(applicationServicePrincipal);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ApplicationTemplates\Item\Instantiate\InstantiatePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InstantiatePostRequestBody();
$requestBody->setDisplayName('Azure AD SAML Toolkit');

$result = $graphServiceClient->applicationTemplates()->byApplicationTemplateId('applicationTemplate-id')->instantiate()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	displayName = "Azure AD SAML Toolkit"
}

Invoke-MgInstantiateApplicationTemplate -ApplicationTemplateId $applicationTemplateId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.applicationtemplates.item.instantiate.instantiate_post_request_body import InstantiatePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InstantiatePostRequestBody(
	display_name = "Azure AD SAML Toolkit",
)

result = await graph_client.application_templates.by_application_template_id('applicationTemplate-id').instantiate.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.applicationServicePrincipal",
    "application": {
        "id": "20845737-a145-446f-aa3c-77d432903957",
        "appId": "3c653ec4-4e4c-4820-8127-49e3889cad99",
        "applicationTemplateId": "229946b9-a9fb-45b8-9531-efa47453ac9e",
        "createdDateTime": "2022-04-25T16:48:24Z",
        "deletedDateTime": null,
        "displayName": "Azure AD SAML Toolkit",
        "groupMembershipClaims": null,
        "identifierUris": [],
        "isFallbackPublicClient": false,
        "signInAudience": "AzureADMyOrg",
        "tags": [],
        "tokenEncryptionKeyId": null,
        "defaultRedirectUri": null,
        "optionalClaims": null,
        "addIns": [],
        "api": {
            "acceptMappedClaims": null,
            "knownClientApplications": [],
            "requestedAccessTokenVersion": null,
            "oauth2PermissionScopes": [
                {
                    "adminConsentDescription": "Allow the application to access Azure AD SAML Toolkit on behalf of the signed-in user.",
                    "adminConsentDisplayName": "Access Azure AD SAML Toolkit",
                    "id": "00e7ef81-4deb-41d7-9ee3-90d4eba1e991",
                    "isEnabled": true,
                    "type": "User",
                    "userConsentDescription": "Allow the application to access Azure AD SAML Toolkit on your behalf.",
                    "userConsentDisplayName": "Access Azure AD SAML Toolkit",
                    "value": "user_impersonation"
                }
            ],
            "preAuthorizedApplications": []
        },
        "appRoles": [
            {
                "allowedMemberTypes": [
                    "User"
                ],
                "displayName": "msiam_access",
                "id": "8b292bda-39b6-4b77-849e-887565235bb0",
                "isEnabled": true,
                "description": "msiam_access",
                "value": null,
                "origin": "Application"
            }
        ],
        "info": {
            "logoUrl": null,
            "marketingUrl": null,
            "privacyStatementUrl": null,
            "supportUrl": null,
            "termsOfServiceUrl": null
        },
        "keyCredentials": [],
        "parentalControlSettings": {
            "countriesBlockedForMinors": [],
            "legalAgeGroupRule": "Allow"
        },
        "passwordCredentials": [],
        "publicClient": {
            "redirectUris": []
        },
        "requiredResourceAccess": [],
        "verifiedPublisher": {
            "displayName": null,
            "verifiedPublisherId": null,
            "addedDateTime": null
        },
        "web": {
            "homePageUrl": "https://samltoolkit.azurewebsites.net/SAML/Consume?metadata=samltoolkit|ISV9.2|primary|z",
            "redirectUris": [
                "https://samltoolkit.azurewebsites.net/SAML/Consume"
            ]
        }
    },
    "servicePrincipal": {
        "id": "912729dd-97ae-4ceb-ade4-07bed3046486",
        "deletedDateTime": null,
        "accountEnabled": true,
        "appId": "3c653ec4-4e4c-4820-8127-49e3889cad99",
        "applicationTemplateId": "229946b9-a9fb-45b8-9531-efa47453ac9e",
        "appDisplayName": "Azure AD SAML Toolkit",
        "alternativeNames": [],
        "appOwnerOrganizationId": "29a4f813-9274-4e1b-858d-0afa98ae66d4",
        "displayName": "Azure AD SAML Toolkit",
        "appRoleAssignmentRequired": true,
        "loginUrl": null,
        "logoutUrl": null,
        "homepage": "https://samltoolkit.azurewebsites.net/SAML/Consume?metadata=samltoolkit|ISV9.2|primary|z",
        "notificationEmailAddresses": [],
        "preferredSingleSignOnMode": null,
        "preferredTokenSigningKeyThumbprint": null,
        "replyUrls": [
            "https://samltoolkit.azurewebsites.net/SAML/Consume"
        ],
        "servicePrincipalNames": [
            "3c653ec4-4e4c-4820-8127-49e3889cad99"
        ],
        "servicePrincipalType": "Application",
        "tags": [
            "WindowsAzureActiveDirectoryIntegratedApp"
        ],
        "tokenEncryptionKeyId": null,
        "samlSingleSignOnSettings": null,
        "verifiedPublisher": {
            "displayName": null,
            "verifiedPublisherId": null,
            "addedDateTime": null
        },
        "addIns": [],
        "appRoles": [
            {
                "allowedMemberTypes": [
                    "User"
                ],
                "displayName": "msiam_access",
                "id": "8b292bda-39b6-4b77-849e-887565235bb0",
                "isEnabled": true,
                "description": "msiam_access",
                "value": null,
                "origin": "Application"
            }
        ],
        "info": {
            "logoUrl": null,
            "marketingUrl": null,
            "privacyStatementUrl": null,
            "supportUrl": null,
            "termsOfServiceUrl": null
        },
        "keyCredentials": [],
        "oauth2PermissionScopes": [
            {
                "adminConsentDescription": "Allow the application to access Azure AD SAML Toolkit on behalf of the signed-in user.",
                "adminConsentDisplayName": "Access Azure AD SAML Toolkit",
                "id": "00e7ef81-4deb-41d7-9ee3-90d4eba1e991",
                "isEnabled": true,
                "type": "User",
                "userConsentDescription": "Allow the application to access Azure AD SAML Toolkit on your behalf.",
                "userConsentDisplayName": "Access Azure AD SAML Toolkit",
                "value": "user_impersonation"
            }
        ],
        "passwordCredentials": []
    }
}
```

## Related content

[Quickstart: Add an enterprise application from the Microsoft Entra gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal)
