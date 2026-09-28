<!-- Source: https://learn.microsoft.com/en-us/graph/api/organizationalbrandingtheme-list-localizations?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List organizationalBrandingThemeLocalization objects

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OrganizationalBranding.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OrganizationalBranding.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Reader* or *Organizational Branding Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /organization/{organizationId}/branding/themes/{organizationalBrandingThemeId}/localizations
```

## Optional query parameters

This method supports only the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) objects in the response body.

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
GET https://graph.microsoft.com/beta/organization/aaaabbbb-0000-cccc-1111-dddd2222eeee/branding/themes/931cc1bb-5395-4fd7-aa54-406d793a4b05/localizations
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Organization["{organization-id}"].Branding.Themes["{organizationalBrandingTheme-id}"].Localizations.GetAsync();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
localizations, err := graphClient.Organization().ByOrganizationId("organization-id").Branding().Themes().ByOrganizationalBrandingThemeId("organizationalBrandingTheme-id").Localizations().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OrganizationalBrandingThemeLocalizationCollectionResponse result = graphClient.organization().byOrganizationId("{organization-id}").branding().themes().byOrganizationalBrandingThemeId("{organizationalBrandingTheme-id}").localizations().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let localizations = await client.api('/organization/aaaabbbb-0000-cccc-1111-dddd2222eeee/branding/themes/931cc1bb-5395-4fd7-aa54-406d793a4b05/localizations')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->organization()->byOrganizationId('organization-id')->branding()->themes()->byOrganizationalBrandingThemeId('organizationalBrandingTheme-id')->localizations()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

Get-MgBetaOrganizationBrandingThemeLocalization -OrganizationId $organizationId -OrganizationalBrandingThemeId $organizationalBrandingThemeId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.organization.by_organization_id('organization-id').branding.themes.by_organizational_branding_theme_id('organizationalBrandingTheme-id').localizations.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.organizationalBrandingThemeLocalization",
      "locale": "fr-FR",
      "accountResetCredentials": {
        "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
      },
      "backgroundImage": "contosobackground.jpg",
      "backgroundImageRelativeUrl": "c1c6b6c8-urr-dzbkz44n5kuo9kzl1kziuujjcdqonoe2owyacso/logintenantbranding/fr-FR/illustration?ts=637535563816027796",
      "bannerLogo": "contosoLogo.jpg",
      "bannerLogoRelativeUrl": "c1c6b6c8-urr-dzbkz44n5kuo9kzl1kziuujjcdqonoe2owyacso/logintenantbranding/fr-FR/bannerlogo?ts=637535563824629275",
      "cannotAccessYourAccount": {
        "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
      },
      "cdnHosts": [
        "secure.aadcdn.microsoftonline-p.com",
        "aadcdn.msftauthimages.net",
        "aadcdn.msauthimages.net"
      ],
      "contentCustomization": {
        "@odata.type": "microsoft.graph.contentCustomization"
      },
      "customCSS": null,
      "customCSSRelativeUrl": null,
      "favicon": null,
      "faviconRelativeUrl": null,
      "forgotMyPassword": {
        "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
      },
      "headerBackgroundColor": "#3377ffff",
      "headerLogo": null,
      "headerLogoRelativeUrl": null,
      "loginPageLayoutConfiguration": {
        "@odata.type": "microsoft.graph.loginPageLayoutConfiguration"
      },
      "pageBackgroundColor": "#FFFF33",
      "privacyAndCookies": {
        "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
      },
      "resetItNow": {
        "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
      },
      "signInPageText": "Welcome to Contoso",
      "squareLogo": null,
      "squareLogoRelativeUrl": null,
      "squareLogoDark": null,
      "squareLogoDarkRelativeUrl": null,
      "termsOfUse": {
        "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
      },
      "usernameHintText": "ContosoUsername"
    }
  ]
}
```
