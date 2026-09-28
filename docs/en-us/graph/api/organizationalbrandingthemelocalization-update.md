<!-- Source: https://learn.microsoft.com/en-us/graph/api/organizationalbrandingthemelocalization-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update organizationalBrandingThemeLocalization

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update an [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) object.

To update String data types, such as **signInPageText** and **usernameHintText**, use the PATCH method. To update Stream data types, such as **bannerLogo** and **pageBackgroundImage**, use the PUT method. You can't update Stream types with other data types in the same request.

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

To update String data types, such as **signInPageText** and **usernameHintText**:

```http
PATCH /organization/{organizationId}/branding/themes/{organizationalBrandingThemeId}/localizations/{organizationalBrandingThemeLocalizationId}
```

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| accountResetCredentials | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Can't access your account?" and "Reset it now" hyperlinks of self-service password reset \(SSPR\) that can be customized on the sign-in page for a theme. A destination URL can be updated. Optional. |
| bannerLogo | Stream | A banner version of your company logo that appears on the sign-in page. The allowed types are PNG or JPEG not larger than 245 x 36 pixels. We recommend using a transparent image with no padding around the logo. Optional. |
| bannerLogoRelativeUrl | String | A relative url for the bannerLogo property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| cannotAccessYourAccount | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Can't access your account?" hyperlink of self-service password reset \(SSPR\) that can be customized on the sign-in page for a theme. A display text can be updated. Optional. |
| cdnHosts | String collection | A list of available CDN base urls that are serving the assets of the current resource. There are several CDNs used to provide redundancy hence eliminating Single Point of Failure for blob properties of this resource. Read-only. Optional. |
| contentCustomization | [contentCustomization](https://learn.microsoft.com/en-us/graph/api/resources/contentcustomization?view=graph-rest-beta) | Represents the various content options to be customized throughout the authentication flow for a tenant.  <br>  <br>**NOTE:** Supported by Microsoft Entra ID for customers tenants only. Optional. |
| customCSS | Stream | CSS styling that appears on the sign-in page. The allowed format is .css format only and not larger than 25KB. Optional. |
| customCSSRelativeUrl | String | A relative url for the customCSS property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| BackgroundImage | Stream | Image that appears as the background of the sign-in page. The allowed types are PNG or JPEG not smaller than 300 KB and not larger than 1920 × 1080 pixels. A smaller image will reduce bandwidth requirements and make the page load faster. Optional. |
| BackgroundImageRelativeUrl | String | A relative url for the backgroundImage property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| favicon | Stream | A custom icon \(favicon\) to replace a default Microsoft product favicon on a Microsoft Entra tenant. Optional. |
| faviconRelativeUrl | String | A relative url for the favicon property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| forgotMyPassword | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Forgot my password" hyperlink of self-service password reset \(SSPR\) that can be customized on the sign-in page for a theme. A display text can be updated. Optional. |
| headerBackgroundColor | String | The RGB color to apply to customize the color of the header. Optional. |
| headerLogo | Stream | A company logo that appears in the header of the sign-in page. The allowed types are PNG or JPEG not larger than 245 x 36 pixels. We recommend using a transparent image with no padding around the logo. Optional. |
| headerLogoRelativeUrl | String | A relative url for the headerLogo property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| locale | String | An identifier that represents the locale specified using culture names. Culture names follow the RFC 1766 standard in the format "languagecode2-country/regioncode2". The portion "languagecode2" is a lowercase two-letter code derived from ISO 639-1 and "country/regioncode2" is an uppercase two-letter code derived from ISO 3166. For example, U.S. English is `en-US`. You can't create the default branding by setting the value of **locale** to the String types `0` or `default`.  <br>  <br>**NOTE:** Multiple branding for a single locale are currently not supported. |
| loginPageLayoutConfiguration | [loginPageLayoutConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/loginpagelayoutconfiguration?view=graph-rest-beta) | Represents the layout configuration to be displayed on the login page for a tenant. Optional. |
| pageBackgroundColor | String | Color that appears in place of the background image in low-bandwidth connections. We recommend that you use the primary color of your banner logo or your organization color. Specify this in hexadecimal format, for example, white is `#FFFFFF`. Optional. |
| privacyAndCookies | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Privacy & cookies" hyperlink in the footer of sign-in page that can be customized for a theme. A destination URL and a display text can be updated. Optional. |
| resetItNow | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents "Reset it now" hyperlink of self-service password reset \(SSPR\) that can be customized on the sign-in page for a theme. A display text can be updated. Optional. |
| signInPageText | String | Text that appears at the bottom of the sign-in box. Use this to communicate additional information, such as the phone number to your help desk or a legal statement. This text must be in Unicode format and not exceed 1024 characters. Optional. |
| squareLogo | Stream | A square version of your company logo that appears in Windows 10 out-of-box experiences \(OOBE\) and when Windows Autopilot is enabled for deployment. Allowed types are PNG or JPEG not larger than 240 x 240 pixels and not more than 10 KB in size. We recommend using a transparent image with no padding around the logo. Optional. |
| squareLogoRelativeUrl | String | A relative url for the squareLogo property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| squareLogoDark | Stream | A square dark version of your company logo that appears in Windows 10 out-of-box experiences \(OOBE\) and when Windows Autopilot is enabled for deployment. Allowed types are PNG or JPEG not larger than 240 x 240 pixels and not more than 10 KB in size. We recommend using a transparent image with no padding around the logo. Optional. |
| squareLogoDarkRelativeUrl | String | A relative url for the squareLogoDark property that is combined with a CDN base URL from the cdnList to provide the version served by a CDN. Read-only. Optional. |
| termsOfUse | [loginPageBrandingVisualElement](https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta) | Represents the Term of Use hyperlink that can be customized in the footer of login page for a theme. A destination URL and a display text can be updated. Optional. |
| usernameHintText | String | A string that shows as the hint in the username textbox on the sign-in screen. This text must be a Unicode, without links or code, and can't exceed 64 characters. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Update string properties for the localized branding theme of the specific locale \(fr-FR\)

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
PATCH https://graph.microsoft.com/beta/organization/84841066-274d-4ec0-a5c1-276be684bdd3/branding/themes/931cc1bb-5395-4fd7-aa54-406d793a4b05/localizations/fr-FR
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.organizationalBrandingThemeLocalization",
  "locale": "en-US",
  "accountResetCredentials": {
    "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
  },
  "backgroundImageRelativeUrl": null,
  "bannerLogoRelativeUrl": null,
  "cannotAccessYourAccount": {
    "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
  },
  "cdnHosts": [],
  "contentCustomization": {
    "@odata.type": "microsoft.graph.contentCustomization"
  },
  "customCSSRelativeUrl": null,
  "faviconRelativeUrl": null,
  "forgotMyPassword": {
    "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
  },
  "headerBackgroundColor": "#3377ffff",
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
  "squareLogoRelativeUrl": null,
  "squareLogoDarkRelativeUrl": null,
  "termsOfUse": {
    "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
  },
  "usernameHintText": "ContosoUsername"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new OrganizationalBrandingThemeLocalization
{
	OdataType = "#microsoft.graph.organizationalBrandingThemeLocalization",
	Locale = "en-US",
	AccountResetCredentials = new LoginPageBrandingVisualElement
	{
		OdataType = "microsoft.graph.loginPageBrandingVisualElement",
	},
	BackgroundImageRelativeUrl = null,
	BannerLogoRelativeUrl = null,
	CannotAccessYourAccount = new LoginPageBrandingVisualElement
	{
		OdataType = "microsoft.graph.loginPageBrandingVisualElement",
	},
	CdnHosts = new List<string>
	{
	},
	ContentCustomization = new ContentCustomization
	{
		OdataType = "microsoft.graph.contentCustomization",
	},
	CustomCSSRelativeUrl = null,
	FaviconRelativeUrl = null,
	ForgotMyPassword = new LoginPageBrandingVisualElement
	{
		OdataType = "microsoft.graph.loginPageBrandingVisualElement",
	},
	HeaderBackgroundColor = "#3377ffff",
	HeaderLogoRelativeUrl = null,
	LoginPageLayoutConfiguration = new LoginPageLayoutConfiguration
	{
		OdataType = "microsoft.graph.loginPageLayoutConfiguration",
	},
	PageBackgroundColor = "#FFFF33",
	PrivacyAndCookies = new LoginPageBrandingVisualElement
	{
		OdataType = "microsoft.graph.loginPageBrandingVisualElement",
	},
	ResetItNow = new LoginPageBrandingVisualElement
	{
		OdataType = "microsoft.graph.loginPageBrandingVisualElement",
	},
	SignInPageText = "Welcome to Contoso",
	SquareLogoRelativeUrl = null,
	SquareLogoDarkRelativeUrl = null,
	TermsOfUse = new LoginPageBrandingVisualElement
	{
		OdataType = "microsoft.graph.loginPageBrandingVisualElement",
	},
	UsernameHintText = "ContosoUsername",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Organization["{organization-id}"].Branding.Themes["{organizationalBrandingTheme-id}"].Localizations["{organizationalBrandingThemeLocalization-locale}"].PatchAsync(requestBody);
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
locale := "en-US"
requestBody.SetLocale(&locale) 
accountResetCredentials := graphmodels.NewLoginPageBrandingVisualElement()
requestBody.SetAccountResetCredentials(accountResetCredentials)
backgroundImageRelativeUrl := null
requestBody.SetBackgroundImageRelativeUrl(&backgroundImageRelativeUrl) 
bannerLogoRelativeUrl := null
requestBody.SetBannerLogoRelativeUrl(&bannerLogoRelativeUrl) 
cannotAccessYourAccount := graphmodels.NewLoginPageBrandingVisualElement()
requestBody.SetCannotAccessYourAccount(cannotAccessYourAccount)
cdnHosts := []string {

}
requestBody.SetCdnHosts(cdnHosts)
contentCustomization := graphmodels.NewContentCustomization()
requestBody.SetContentCustomization(contentCustomization)
customCSSRelativeUrl := null
requestBody.SetCustomCSSRelativeUrl(&customCSSRelativeUrl) 
faviconRelativeUrl := null
requestBody.SetFaviconRelativeUrl(&faviconRelativeUrl) 
forgotMyPassword := graphmodels.NewLoginPageBrandingVisualElement()
requestBody.SetForgotMyPassword(forgotMyPassword)
headerBackgroundColor := "#3377ffff"
requestBody.SetHeaderBackgroundColor(&headerBackgroundColor) 
headerLogoRelativeUrl := null
requestBody.SetHeaderLogoRelativeUrl(&headerLogoRelativeUrl) 
loginPageLayoutConfiguration := graphmodels.NewLoginPageLayoutConfiguration()
requestBody.SetLoginPageLayoutConfiguration(loginPageLayoutConfiguration)
pageBackgroundColor := "#FFFF33"
requestBody.SetPageBackgroundColor(&pageBackgroundColor) 
privacyAndCookies := graphmodels.NewLoginPageBrandingVisualElement()
requestBody.SetPrivacyAndCookies(privacyAndCookies)
resetItNow := graphmodels.NewLoginPageBrandingVisualElement()
requestBody.SetResetItNow(resetItNow)
signInPageText := "Welcome to Contoso"
requestBody.SetSignInPageText(&signInPageText) 
squareLogoRelativeUrl := null
requestBody.SetSquareLogoRelativeUrl(&squareLogoRelativeUrl) 
squareLogoDarkRelativeUrl := null
requestBody.SetSquareLogoDarkRelativeUrl(&squareLogoDarkRelativeUrl) 
termsOfUse := graphmodels.NewLoginPageBrandingVisualElement()
requestBody.SetTermsOfUse(termsOfUse)
usernameHintText := "ContosoUsername"
requestBody.SetUsernameHintText(&usernameHintText) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
localizations, err := graphClient.Organization().ByOrganizationId("organization-id").Branding().Themes().ByOrganizationalBrandingThemeId("organizationalBrandingTheme-id").Localizations().ByOrganizationalBrandingThemeLocalizationLocale("organizationalBrandingThemeLocalization-locale").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OrganizationalBrandingThemeLocalization organizationalBrandingThemeLocalization = new OrganizationalBrandingThemeLocalization();
organizationalBrandingThemeLocalization.setOdataType("#microsoft.graph.organizationalBrandingThemeLocalization");
organizationalBrandingThemeLocalization.setLocale("en-US");
LoginPageBrandingVisualElement accountResetCredentials = new LoginPageBrandingVisualElement();
accountResetCredentials.setOdataType("microsoft.graph.loginPageBrandingVisualElement");
organizationalBrandingThemeLocalization.setAccountResetCredentials(accountResetCredentials);
organizationalBrandingThemeLocalization.setBackgroundImageRelativeUrl(null);
organizationalBrandingThemeLocalization.setBannerLogoRelativeUrl(null);
LoginPageBrandingVisualElement cannotAccessYourAccount = new LoginPageBrandingVisualElement();
cannotAccessYourAccount.setOdataType("microsoft.graph.loginPageBrandingVisualElement");
organizationalBrandingThemeLocalization.setCannotAccessYourAccount(cannotAccessYourAccount);
LinkedList<String> cdnHosts = new LinkedList<String>();
organizationalBrandingThemeLocalization.setCdnHosts(cdnHosts);
ContentCustomization contentCustomization = new ContentCustomization();
contentCustomization.setOdataType("microsoft.graph.contentCustomization");
organizationalBrandingThemeLocalization.setContentCustomization(contentCustomization);
organizationalBrandingThemeLocalization.setCustomCSSRelativeUrl(null);
organizationalBrandingThemeLocalization.setFaviconRelativeUrl(null);
LoginPageBrandingVisualElement forgotMyPassword = new LoginPageBrandingVisualElement();
forgotMyPassword.setOdataType("microsoft.graph.loginPageBrandingVisualElement");
organizationalBrandingThemeLocalization.setForgotMyPassword(forgotMyPassword);
organizationalBrandingThemeLocalization.setHeaderBackgroundColor("#3377ffff");
organizationalBrandingThemeLocalization.setHeaderLogoRelativeUrl(null);
LoginPageLayoutConfiguration loginPageLayoutConfiguration = new LoginPageLayoutConfiguration();
loginPageLayoutConfiguration.setOdataType("microsoft.graph.loginPageLayoutConfiguration");
organizationalBrandingThemeLocalization.setLoginPageLayoutConfiguration(loginPageLayoutConfiguration);
organizationalBrandingThemeLocalization.setPageBackgroundColor("#FFFF33");
LoginPageBrandingVisualElement privacyAndCookies = new LoginPageBrandingVisualElement();
privacyAndCookies.setOdataType("microsoft.graph.loginPageBrandingVisualElement");
organizationalBrandingThemeLocalization.setPrivacyAndCookies(privacyAndCookies);
LoginPageBrandingVisualElement resetItNow = new LoginPageBrandingVisualElement();
resetItNow.setOdataType("microsoft.graph.loginPageBrandingVisualElement");
organizationalBrandingThemeLocalization.setResetItNow(resetItNow);
organizationalBrandingThemeLocalization.setSignInPageText("Welcome to Contoso");
organizationalBrandingThemeLocalization.setSquareLogoRelativeUrl(null);
organizationalBrandingThemeLocalization.setSquareLogoDarkRelativeUrl(null);
LoginPageBrandingVisualElement termsOfUse = new LoginPageBrandingVisualElement();
termsOfUse.setOdataType("microsoft.graph.loginPageBrandingVisualElement");
organizationalBrandingThemeLocalization.setTermsOfUse(termsOfUse);
organizationalBrandingThemeLocalization.setUsernameHintText("ContosoUsername");
OrganizationalBrandingThemeLocalization result = graphClient.organization().byOrganizationId("{organization-id}").branding().themes().byOrganizationalBrandingThemeId("{organizationalBrandingTheme-id}").localizations().byOrganizationalBrandingThemeLocalizationLocale("{organizationalBrandingThemeLocalization-locale}").patch(organizationalBrandingThemeLocalization);
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
  locale: 'en-US',
  accountResetCredentials: {
    '@odata.type': 'microsoft.graph.loginPageBrandingVisualElement'
  },
  backgroundImageRelativeUrl: null,
  bannerLogoRelativeUrl: null,
  cannotAccessYourAccount: {
    '@odata.type': 'microsoft.graph.loginPageBrandingVisualElement'
  },
  cdnHosts: [],
  contentCustomization: {
    '@odata.type': 'microsoft.graph.contentCustomization'
  },
  customCSSRelativeUrl: null,
  faviconRelativeUrl: null,
  forgotMyPassword: {
    '@odata.type': 'microsoft.graph.loginPageBrandingVisualElement'
  },
  headerBackgroundColor: '#3377ffff',
  headerLogoRelativeUrl: null,
  loginPageLayoutConfiguration: {
    '@odata.type': 'microsoft.graph.loginPageLayoutConfiguration'
  },
  pageBackgroundColor: '#FFFF33',
  privacyAndCookies: {
    '@odata.type': 'microsoft.graph.loginPageBrandingVisualElement'
  },
  resetItNow: {
    '@odata.type': 'microsoft.graph.loginPageBrandingVisualElement'
  },
  signInPageText: 'Welcome to Contoso',
  squareLogoRelativeUrl: null,
  squareLogoDarkRelativeUrl: null,
  termsOfUse: {
    '@odata.type': 'microsoft.graph.loginPageBrandingVisualElement'
  },
  usernameHintText: 'ContosoUsername'
};

await client.api('/organization/84841066-274d-4ec0-a5c1-276be684bdd3/branding/themes/931cc1bb-5395-4fd7-aa54-406d793a4b05/localizations/fr-FR')
	.version('beta')
	.update(organizationalBrandingThemeLocalization);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\OrganizationalBrandingThemeLocalization;
use Microsoft\Graph\Beta\Generated\Models\LoginPageBrandingVisualElement;
use Microsoft\Graph\Beta\Generated\Models\ContentCustomization;
use Microsoft\Graph\Beta\Generated\Models\LoginPageLayoutConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OrganizationalBrandingThemeLocalization();
$requestBody->setOdataType('#microsoft.graph.organizationalBrandingThemeLocalization');
$requestBody->setLocale('en-US');
$accountResetCredentials = new LoginPageBrandingVisualElement();
$accountResetCredentials->setOdataType('microsoft.graph.loginPageBrandingVisualElement');
$requestBody->setAccountResetCredentials($accountResetCredentials);
$requestBody->setBackgroundImageRelativeUrl(null);
$requestBody->setBannerLogoRelativeUrl(null);
$cannotAccessYourAccount = new LoginPageBrandingVisualElement();
$cannotAccessYourAccount->setOdataType('microsoft.graph.loginPageBrandingVisualElement');
$requestBody->setCannotAccessYourAccount($cannotAccessYourAccount);
$requestBody->setCdnHosts([	]);
$contentCustomization = new ContentCustomization();
$contentCustomization->setOdataType('microsoft.graph.contentCustomization');
$requestBody->setContentCustomization($contentCustomization);
$requestBody->setCustomCSSRelativeUrl(null);
$requestBody->setFaviconRelativeUrl(null);
$forgotMyPassword = new LoginPageBrandingVisualElement();
$forgotMyPassword->setOdataType('microsoft.graph.loginPageBrandingVisualElement');
$requestBody->setForgotMyPassword($forgotMyPassword);
$requestBody->setHeaderBackgroundColor('#3377ffff');
$requestBody->setHeaderLogoRelativeUrl(null);
$loginPageLayoutConfiguration = new LoginPageLayoutConfiguration();
$loginPageLayoutConfiguration->setOdataType('microsoft.graph.loginPageLayoutConfiguration');
$requestBody->setLoginPageLayoutConfiguration($loginPageLayoutConfiguration);
$requestBody->setPageBackgroundColor('#FFFF33');
$privacyAndCookies = new LoginPageBrandingVisualElement();
$privacyAndCookies->setOdataType('microsoft.graph.loginPageBrandingVisualElement');
$requestBody->setPrivacyAndCookies($privacyAndCookies);
$resetItNow = new LoginPageBrandingVisualElement();
$resetItNow->setOdataType('microsoft.graph.loginPageBrandingVisualElement');
$requestBody->setResetItNow($resetItNow);
$requestBody->setSignInPageText('Welcome to Contoso');
$requestBody->setSquareLogoRelativeUrl(null);
$requestBody->setSquareLogoDarkRelativeUrl(null);
$termsOfUse = new LoginPageBrandingVisualElement();
$termsOfUse->setOdataType('microsoft.graph.loginPageBrandingVisualElement');
$requestBody->setTermsOfUse($termsOfUse);
$requestBody->setUsernameHintText('ContosoUsername');

$result = $graphServiceClient->organization()->byOrganizationId('organization-id')->branding()->themes()->byOrganizationalBrandingThemeId('organizationalBrandingTheme-id')->localizations()->byOrganizationalBrandingThemeLocalizationLocale('organizationalBrandingThemeLocalization-locale')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	"@odata.type" = "#microsoft.graph.organizationalBrandingThemeLocalization"
	locale = "en-US"
	accountResetCredentials = @{
		"@odata.type" = "microsoft.graph.loginPageBrandingVisualElement"
	}
	backgroundImageRelativeUrl = $null
	bannerLogoRelativeUrl = $null
	cannotAccessYourAccount = @{
		"@odata.type" = "microsoft.graph.loginPageBrandingVisualElement"
	}
	cdnHosts = @(
	)
	contentCustomization = @{
		"@odata.type" = "microsoft.graph.contentCustomization"
	}
	customCSSRelativeUrl = $null
	faviconRelativeUrl = $null
	forgotMyPassword = @{
		"@odata.type" = "microsoft.graph.loginPageBrandingVisualElement"
	}
	headerBackgroundColor = "#3377ffff"
	headerLogoRelativeUrl = $null
	loginPageLayoutConfiguration = @{
		"@odata.type" = "microsoft.graph.loginPageLayoutConfiguration"
	}
	pageBackgroundColor = "#FFFF33"
	privacyAndCookies = @{
		"@odata.type" = "microsoft.graph.loginPageBrandingVisualElement"
	}
	resetItNow = @{
		"@odata.type" = "microsoft.graph.loginPageBrandingVisualElement"
	}
	signInPageText = "Welcome to Contoso"
	squareLogoRelativeUrl = $null
	squareLogoDarkRelativeUrl = $null
	termsOfUse = @{
		"@odata.type" = "microsoft.graph.loginPageBrandingVisualElement"
	}
	usernameHintText = "ContosoUsername"
}

Update-MgBetaOrganizationBrandingThemeLocalization -OrganizationId $organizationId -OrganizationalBrandingThemeId $organizationalBrandingThemeId -OrganizationalBrandingThemeLocalizationLocale $organizationalBrandingThemeLocalizationLocale -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.organizational_branding_theme_localization import OrganizationalBrandingThemeLocalization
from msgraph_beta.generated.models.login_page_branding_visual_element import LoginPageBrandingVisualElement
from msgraph_beta.generated.models.content_customization import ContentCustomization
from msgraph_beta.generated.models.login_page_layout_configuration import LoginPageLayoutConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OrganizationalBrandingThemeLocalization(
	odata_type = "#microsoft.graph.organizationalBrandingThemeLocalization",
	locale = "en-US",
	account_reset_credentials = LoginPageBrandingVisualElement(
		odata_type = "microsoft.graph.loginPageBrandingVisualElement",
	),
	background_image_relative_url = None,
	banner_logo_relative_url = None,
	cannot_access_your_account = LoginPageBrandingVisualElement(
		odata_type = "microsoft.graph.loginPageBrandingVisualElement",
	),
	cdn_hosts = [
	],
	content_customization = ContentCustomization(
		odata_type = "microsoft.graph.contentCustomization",
	),
	custom_c_s_s_relative_url = None,
	favicon_relative_url = None,
	forgot_my_password = LoginPageBrandingVisualElement(
		odata_type = "microsoft.graph.loginPageBrandingVisualElement",
	),
	header_background_color = "#3377ffff",
	header_logo_relative_url = None,
	login_page_layout_configuration = LoginPageLayoutConfiguration(
		odata_type = "microsoft.graph.loginPageLayoutConfiguration",
	),
	page_background_color = "#FFFF33",
	privacy_and_cookies = LoginPageBrandingVisualElement(
		odata_type = "microsoft.graph.loginPageBrandingVisualElement",
	),
	reset_it_now = LoginPageBrandingVisualElement(
		odata_type = "microsoft.graph.loginPageBrandingVisualElement",
	),
	sign_in_page_text = "Welcome to Contoso",
	square_logo_relative_url = None,
	square_logo_dark_relative_url = None,
	terms_of_use = LoginPageBrandingVisualElement(
		odata_type = "microsoft.graph.loginPageBrandingVisualElement",
	),
	username_hint_text = "ContosoUsername",
)

result = await graph_client.organization.by_organization_id('organization-id').branding.themes.by_organizational_branding_theme_id('organizationalBrandingTheme-id').localizations.by_organizational_branding_theme_localization_locale('organizationalBrandingThemeLocalization-locale').patch(request_body)
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
  "@odata.type": "#microsoft.graph.organizationalBrandingThemeLocalization",
  "locale": "en-US",
  "accountResetCredentials": {
    "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
  },
  "backgroundImageRelativeUrl": null,
  "bannerLogoRelativeUrl": null,
  "cannotAccessYourAccount": {
    "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
  },
  "cdnHosts": [],
  "contentCustomization": {
    "@odata.type": "microsoft.graph.contentCustomization"
  },
  "customCSSRelativeUrl": null,
  "faviconRelativeUrl": null,
  "forgotMyPassword": {
    "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
  },
  "headerBackgroundColor": "#3377ffff",
  "headerLogoRelativeUrl": "/branding/logo-header.png",
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
  "squareLogoRelativeUrl": null,
  "squareLogoDarkRelativeUrl": null,
  "termsOfUse": {
    "@odata.type": "microsoft.graph.loginPageBrandingVisualElement"
  },
  "usernameHintText": "ContosoUsername"
}
```

### Example 2: Update a stream property for the localized branding theme of the specific locale \(fr-FR\)

#### Request

The following example shows a request.

```http
PUT https://graph.microsoft.com/beta/organization/84841066-274d-4ec0-a5c1-276be684bdd3/branding/themes/931cc1bb-5395-4fd7-aa54-406d793a4b05/localizations/fr-FR/bannerLogo
Content-Type: image/jpeg

<Image>
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: image/*

<Image>
```
