<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-01 -->

# organizationalBrandingLocalization resource type

Namespace: microsoft.graph

Resource that supports managing language-specific branding. While you can't change your original configuration's language, this resource allows you to create a new configuration for a different language.

Inherits from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/organizationalbranding-list-localizations?view=graph-rest-1.0) | [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) collection | Get a list of the [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/organizationalbranding-post-localizations?view=graph-rest-1.0) | [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) | Create a new [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/organizationalbrandinglocalization-get?view=graph-rest-1.0) | [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) | Read the properties and relationships of an [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/organizationalbrandinglocalization-update?view=graph-rest-1.0) | None | Update the properties of an [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/organizationalbrandinglocalization-delete?view=graph-rest-1.0) | None | Deletes an [organizationalBrandingLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| backgroundColor | String | Color that appears in place of the background image in low-bandwidth connections. We recommend that you use the primary color of your banner logo or your organization color. Specify this in hexadecimal format, for example, white is `#FFFFFF`. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| backgroundImage | Stream | Image that appears as the background of the sign-in page. The allowed types are PNG or JPEG not smaller than 300 KB and not larger than 1920 × 1080 pixels. A smaller image will reduce bandwidth requirements and make the page load faster. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| backgroundImageRelativeUrl | String | A relative URL for the **backgroundImage** property that is combined with a CDN base URL from the **cdnList** to provide the version served by a CDN. Read-only. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| bannerLogo | Stream | A banner version of your company logo that appears on the sign-in page. The allowed types are PNG or JPEG not larger than 36 × 245 pixels. We recommend using a transparent image with no padding around the logo. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| bannerLogoRelativeUrl | String | A relative URL for the **bannerLogo** property that is combined with a CDN base URL from the **cdnList** to provide the read-only version served by a CDN. Read-only. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| cdnList | String collection | A list of base URLs for all available CDN providers that are serving the assets of the current resource. Several CDN providers are used at the same time for high availability of read requests. Read-only. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| contentCustomization | [contentCustomization](https://learn.microsoft.com/en-us/graph/api/resources/contentcustomization?view=graph-rest-1.0) | Represents the content options to be customized throughout the authentication flow for a tenant.  <br>  <br>**NOTE:** Supported by Microsoft Entra External ID in external tenants only. |
| customAccountResetCredentialsUrl | String | A custom URL for resetting account credentials. This URL must be in ASCII format or non-ASCII characters must be URL encoded, and not exceed 128 characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customCannotAccessYourAccountText | String | A string to replace the default "Can't access your account?" self-service password reset \(SSPR\) hyperlink text on the sign-in page. This text must be in Unicode format and not exceed 256 characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customCannotAccessYourAccountUrl | String | A custom URL to replace the default URL of the self-service password reset \(SSPR\) "Can't access your account?" hyperlink on the sign-in page. This URL must be in ASCII format or non-ASCII characters must be URL encoded, and not exceed 128 characters.  <br>  <br>**DO NOT USE.** Use **customAccountResetCredentialsUrl** instead. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customCSS | Stream | CSS styling that appears on the sign-in page. The allowed format is .css format only and not larger than 25KB. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customCSSRelativeUrl | String | A relative URL for the **customCSS** property that is combined with a CDN base URL from the **cdnList** to provide the version served by a CDN. Read-only. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customForgotMyPasswordText | String | A string to replace the default "Forgot my password" hyperlink text on the sign-in form. This text must be in Unicode format and not exceed 256 characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customPrivacyAndCookiesText | String | A string to replace the default "Privacy and Cookies" hyperlink text in the footer. This text must be in Unicode format and not exceed 256 characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customPrivacyAndCookiesUrl | String | A custom URL to replace the default URL of the "Privacy and Cookies" hyperlink in the footer. This URL must be in ASCII format or non-ASCII characters must be URL encoded, and not exceed 128 characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customResetItNowText | String | A string to replace the default "reset it now" hyperlink text on the sign-in form. This text must be in Unicode format and not exceed 256 characters.  <br>  <br>**DO NOT USE:** Customization of the "reset it now" hyperlink text is currently not supported. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customTermsOfUseText | String | A string to replace the the default "Terms of Use" hyperlink text in the footer. This text must be in Unicode format and not exceed 256 characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| customTermsOfUseUrl | String | A custom URL to replace the default URL of the "Terms of Use" hyperlink in the footer. This URL must be in ASCII format or non-ASCII characters must be URL encoded, and not exceed 128characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| favicon | Stream | A custom icon \(favicon\) to replace a default Microsoft product favicon on a Microsoft Entra tenant. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| faviconRelativeUrl | String | A relative url for the favicon above that is combined with a CDN base URL from the **cdnList** to provide the version served by a CDN. Read-only. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| headerBackgroundColor | String | The RGB color to apply to customize the color of the header. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| headerLogo | Stream | A company logo that appears in the header of the sign-in page. The allowed types are PNG or JPEG not larger than 36 × 245 pixels. We recommend using a transparent image with no padding around the logo. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| headerLogoRelativeUrl | String | A relative URL for the **headerLogo** property that is combined with a CDN base URL from the **cdnList** to provide the read-only version served by a CDN. Read-only. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| id | String | An identifier that represents the locale specified using culture names. Culture names follow the RFC 1766 standard in the format "languagecode2-country/regioncode2", where "languagecode2" is a lowercase two-letter code derived from ISO 639-1 and "country/regioncode2" is an uppercase two-letter code derived from ISO 3166. For example, U.S. English is `en-US`. The **id** for the default /branding is always the String types `0` or `default`. Read-only.  <br>  <br>**NOTE:** Multiple branding for a single locale are currently not supported. |
| loginPageLayoutConfiguration | [loginPageLayoutConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/loginpagelayoutconfiguration?view=graph-rest-1.0) | Represents the layout configuration to be displayed on the login page for a tenant. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| loginPageTextVisibilitySettings | [loginPageTextVisibilitySettings](https://learn.microsoft.com/en-us/graph/api/resources/loginpagetextvisibilitysettings?view=graph-rest-1.0) | Represents the various texts that can be hidden on the login page for a tenant. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| signInPageText | String | Text that appears at the bottom of the sign-in box. Use this to communicate additional information, such as the phone number to your help desk or a legal statement. This text must be in Unicode format and not exceed 1024 characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| squareLogo | Stream | A square version of your company logo that appears in Windows 10 out-of-box experiences \(OOBE\) and when Windows Autopilot is enabled for deployment. Allowed types are PNG or JPEG not larger than 240 x 240 pixels and not more than 10 KB in size. We recommend using a transparent image with no padding around the logo. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| squareLogoRelativeUrl | String | A relative URL for the **squareLogo** property that is combined with a CDN base URL from the **cdnList** to provide the version served by a CDN. Read-only. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| squareLogoDark | Stream | A square dark version of your company logo that appears in Windows 10 out-of-box experiences \(OOBE\) and when Windows Autopilot is enabled for deployment. Allowed types are PNG or JPEG not larger than 240 x 240 pixels and not more than 10 KB in size. We recommend using a transparent image with no padding around the logo. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| squareLogoDarkRelativeUrl | String | A relative URL for the **squareLogoDark** property that is combined with a CDN base URL from the **cdnList** to provide the version served by a CDN. Read-only. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |
| usernameHintText | String | A string that shows as the hint in the username textbox on the sign-in screen. This text must be a Unicode, without links or code, and can't exceed 64 characters. Inherited from [organizationalBrandingProperties](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingproperties?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "@odata.type": "#microsoft.graph.organizationalBrandingLocalization",
  "id": "String (identifier)",
  "backgroundColor": "String",
  "backgroundImage": "Stream",
  "backgroundImageRelativeUrl": "String",
  "bannerLogo": "Stream",
  "bannerLogoRelativeUrl": "String",
  "cdnList": [
    "String"
  ],
 "contentCustomization": {
    "@odata.type": "microsoft.graph.contentCustomization"
  }, 
  "signInPageText": "String",
  "squareLogo": "Stream",
  "squareLogoRelativeUrl": "String",
  "squareLogoDark": "Stream",
  "squareLogoDarkRelativeUrl": "String",
  "usernameHintText": "String",
  "customAccountResetCredentialsUrl": "String",
  "customCannotAccessYourAccountText": "String",
  "customCannotAccessYourAccountUrl": "String",
  "customCSS": "Stream",
  "customCSSRelativeUrl": "String",
  "customForgotMyPasswordText": "String",
  "customPrivacyAndCookiesText": "String",
  "customPrivacyAndCookiesUrl": "String",
  "customResetItNowText": "String",
  "customTermsOfUseText": "String",
  "customTermsOfUseUrl": "String",
  "favicon": "Stream",
  "faviconRelativeUrl": "String",
  "headerBackgroundColor": "String",
  "headerLogo": "Stream",
  "headerLogoRelativeUrl": "String",
  "loginPageLayoutConfiguration": {
    "@odata.type": "microsoft.graph.loginPageLayoutConfiguration"
  },
  "loginPageTextVisibilitySettings": {
    "@odata.type": "microsoft.graph.loginPageTextVisibilitySettings"
  }
}
```
