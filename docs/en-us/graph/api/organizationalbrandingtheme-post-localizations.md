<!-- Source: https://learn.microsoft.com/en-us/graph/api/organizationalbrandingtheme-post-localizations?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create organizationalBrandingThemeLocalization

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OrganizationalBranding.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OrganizationalBranding.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Organizational Branding Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /organization/{organizationId}/branding/themes/{organizationalBrandingThemeId}/localizations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) object.

You can specify the following properties when creating an **organizationalBrandingThemeLocalization**.

| Property | Type | Description |
| :--- | :--- | :--- |
| accountResetCredentials | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Can't access your account?" and "Reset it now" hyperlinks of self-service password reset \(SSPR\) that can be customized on the sign-in page for a theme. A destination URL can be updated. Optional. |
| bannerLogoRelativeUrl | String | A relative url for the bannerLogo property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| cannotAccessYourAccount | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Can't access your account?" hyperlink of self-service password reset \(SSPR\) that can be customized on the sign-in page for a theme. A display text can be updated. Optional. |
| cdnHosts | String collection | A list of available CDN base urls that are serving the assets of the current resource. There are several CDNs used to provide redundancy hence eliminating Single Point of Failure for blob properties of this resource. Read-only. Optional. |
| contentCustomization | [contentCustomization](https://learn.microsoft.com/en-us/graph/api/resources/contentcustomization?view=graph-rest-beta) | Represents the various content options to be customized throughout the authentication flow for a tenant.  <br>  <br>**NOTE:** Supported by Microsoft Entra ID for customers tenants only. Optional. |
| customCSSRelativeUrl | String | A relative url for the customCSS property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| BackgroundImageRelativeUrl | String | A relative url for the backgroundImage property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| faviconRelativeUrl | String | A relative url for the favicon property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| forgotMyPassword | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Forgot my password" hyperlink of self-service password reset \(SSPR\) that can be customized on the sign-in page for a theme. A display text can be updated. Optional. |
| headerBackgroundColor | String | The RGB color to apply to customize the color of the header. Optional. |
| headerLogoRelativeUrl | String | A relative url for the headerLogo property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| locale | String | An identifier that represents the locale specified using culture names. Culture names follow the RFC 1766 standard in the format "languagecode2-country/regioncode2". The portion "languagecode2" is a lowercase two-letter code derived from ISO 639-1 and "country/regioncode2" is an uppercase two-letter code derived from ISO 3166. For example, U.S. English is `en-US`. You can't create the default branding by setting the value of **locale** to the String types `0` or `default`.  <br>  <br>**NOTE:** Multiple branding for a single locale are currently not supported. Required. |
| loginPageLayoutConfiguration | [loginPageLayoutConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/loginpagelayoutconfiguration?view=graph-rest-beta) | Represents the layout configuration to be displayed on the login page for a tenant. Optional. |
| pageBackgroundColor | String | Color that appears in place of the background image in low-bandwidth connections. We recommend that you use the primary color of your banner logo or your organization color. Specify this in hexadecimal format, for example, white is `#FFFFFF`. Optional. |
| privacyAndCookies | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Privacy & cookies" hyperlink in the footer of sign-in page that can be customized for a theme. A destination URL and a display text can be updated. Optional. |
| resetItNow | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Reset it now" hyperlink of self-service password reset \(SSPR\) that can be customized on the sign-in page for a theme. A display text can be updated. Optional. |
| signInPageText | String | Text that appears at the bottom of the sign-in box. Use this to communicate additional information, such as the phone number to your help desk or a legal statement. This text must be in Unicode format and not exceed 1024 characters. Optional. |
| squareLogoRelativeUrl | String | A relative url for the squareLogo property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| squareLogoDarkRelativeUrl | String | A relative url for the squareLogoDark property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| termsOfUse | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents the Term of Use hyperlink that can be customized in the footer of login page for a theme. A destination URL and a display text can be updated. Optional. |
| usernameHintText | String | A string that shows as the hint in the username textbox on the sign-in screen. This text must be a Unicode, without links or code, and can't exceed 64 characters. Optional. |

## Response

If successful, this method returns a `201 Created` response code and an [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/organization/aaaabbbb-0000-cccc-1111-dddd2222eeee/branding/themes/931cc1bb-5395-4fd7-aa54-406d793a4b05/localizations
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.organizationalBrandingThemeLocalization",
      "locale": "fr-FR",
      "headerBackgroundColor": "#3377ffff",
      "pageBackgroundColor": "#FFFF33",
      "signInPageText": "Welcome to Contoso",
      "usernameHintText": "ContosoUsername "
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new OrganizationalBrandingThemeLocalization
{
	OdataType = "#microsoft.graph.organizationalBrandingThemeLocalization",
	Locale = "fr-FR",
	HeaderBackgroundColor = "#3377ffff",
	PageBackgroundColor = "#FFFF33",
	SignInPageText = "Welcome to Contoso",
	UsernameHintText = "ContosoUsername ",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Organization["{organization-id}"].Branding.Themes["{organizationalBrandingTheme-id}"].Localizations.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewOrganizationalBrandingThemeLocalization()
locale := "fr-FR"
requestBody.SetLocale(&locale) 
headerBackgroundColor := "#3377ffff"
requestBody.SetHeaderBackgroundColor(&headerBackgroundColor) 
pageBackgroundColor := "#FFFF33"
requestBody.SetPageBackgroundColor(&pageBackgroundColor) 
signInPageText := "Welcome to Contoso"
requestBody.SetSignInPageText(&signInPageText) 
usernameHintText := "ContosoUsername "
requestBody.SetUsernameHintText(&usernameHintText) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
localizations, err := graphClient.Organization().ByOrganizationId("organization-id").Branding().Themes().ByOrganizationalBrandingThemeId("organizationalBrandingTheme-id").Localizations().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OrganizationalBrandingThemeLocalization organizationalBrandingThemeLocalization = new OrganizationalBrandingThemeLocalization();
organizationalBrandingThemeLocalization.setOdataType("#microsoft.graph.organizationalBrandingThemeLocalization");
organizationalBrandingThemeLocalization.setLocale("fr-FR");
organizationalBrandingThemeLocalization.setHeaderBackgroundColor("#3377ffff");
organizationalBrandingThemeLocalization.setPageBackgroundColor("#FFFF33");
organizationalBrandingThemeLocalization.setSignInPageText("Welcome to Contoso");
organizationalBrandingThemeLocalization.setUsernameHintText("ContosoUsername ");
OrganizationalBrandingThemeLocalization result = graphClient.organization().byOrganizationId("{organization-id}").branding().themes().byOrganizationalBrandingThemeId("{organizationalBrandingTheme-id}").localizations().post(organizationalBrandingThemeLocalization);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const organizationalBrandingThemeLocalization = {
  '@odata.type': '#microsoft.graph.organizationalBrandingThemeLocalization',
      locale: 'fr-FR',
      headerBackgroundColor: '#3377ffff',
      pageBackgroundColor: '#FFFF33',
      signInPageText: 'Welcome to Contoso',
      usernameHintText: 'ContosoUsername '
};

await client.api('/organization/aaaabbbb-0000-cccc-1111-dddd2222eeee/branding/themes/931cc1bb-5395-4fd7-aa54-406d793a4b05/localizations')
	.version('beta')
	.post(organizationalBrandingThemeLocalization);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\OrganizationalBrandingThemeLocalization;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OrganizationalBrandingThemeLocalization();
$requestBody->setOdataType('#microsoft.graph.organizationalBrandingThemeLocalization');
$requestBody->setLocale('fr-FR');
$requestBody->setHeaderBackgroundColor('#3377ffff');
$requestBody->setPageBackgroundColor('#FFFF33');
$requestBody->setSignInPageText('Welcome to Contoso');
$requestBody->setUsernameHintText('ContosoUsername ');

$result = $graphServiceClient->organization()->byOrganizationId('organization-id')->branding()->themes()->byOrganizationalBrandingThemeId('organizationalBrandingTheme-id')->localizations()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	"@odata.type" = "#microsoft.graph.organizationalBrandingThemeLocalization"
	locale = "fr-FR"
	headerBackgroundColor = "#3377ffff"
	pageBackgroundColor = "#FFFF33"
	signInPageText = "Welcome to Contoso"
	usernameHintText = "ContosoUsername "
}

New-MgBetaOrganizationBrandingThemeLocalization -OrganizationId $organizationId -OrganizationalBrandingThemeId $organizationalBrandingThemeId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.organizational_branding_theme_localization import OrganizationalBrandingThemeLocalization
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OrganizationalBrandingThemeLocalization(
	odata_type = "#microsoft.graph.organizationalBrandingThemeLocalization",
	locale = "fr-FR",
	header_background_color = "#3377ffff",
	page_background_color = "#FFFF33",
	sign_in_page_text = "Welcome to Contoso",
	username_hint_text = "ContosoUsername ",
)

result = await graph_client.organization.by_organization_id('organization-id').branding.themes.by_organizational_branding_theme_id('organizationalBrandingTheme-id').localizations.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.organizationalBrandingThemeLocalization",
  "locale": "fr-FR",
    "accountResetCredentials": {
      "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
    },
    "backgroundImage": null,
    "backgroundImageRelativeUrl": null,
    "bannerLogo": null,
    "bannerLogoRelativeUrl": null,
    "cannotAccessYourAccount": {
      "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
    },
    "cdnHosts": [],
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
    "headerLogoRelativeUrl": "/images/headerLogo.png",
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
```
