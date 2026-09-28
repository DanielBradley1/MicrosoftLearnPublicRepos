<!-- Source: https://learn.microsoft.com/en-us/graph/api/organizationalbranding-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# Update organizationalBranding

Namespace: microsoft.graph

Update the properties of the default branding object specified by the [organizationalBranding](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding?view=graph-rest-1.0) resource.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OrganizationalBranding.ReadWrite.All | Organization.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OrganizationalBranding.ReadWrite.All | Organization.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Organizational Branding Administrator* is the least privileged role supported for this operation.

## HTTP request

To update String data types, such as signInPageText and usernameHintText, use the PATCH method. To update Stream data types, such as backgroundLogo and backgroundImage, use the PUT method. You can't update Stream types with other data types in the same request.

```http
PATCH /organization/{organizationId}/branding
PUT /organization/{organizationId}/branding/localizations/{organizationalBrandingLocalizationId}/{Stream object type such as backgroundImage}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Accept-Language | A valid ISO 639-1 locale. Required. |

## Request body

In the request body, supply *only* the values for properties that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| backgroundColor | String | Color that appears in place of the background image in low-bandwidth connections. We recommend that you use the primary color of your banner logo or your organization color. Specify this in hexadecimal format, for example, white is `#FFFFFF`. |
| backgroundImage | Stream | Image that appears as the background of the sign-in page. The allowed types are PNG or JPEG not smaller than 300 KB and not larger than 1920 × 1080 pixels. A smaller image will reduce bandwidth requirements and make the page load faster. |
| bannerLogo | Stream | A banner version of your company logo that appears on the sign-in page. The allowed types are PNG or JPEG not larger than 245 x 36 pixels. We recommend using a transparent image with no padding around the logo. |
| contentCustomization | [contentCustomization](https://learn.microsoft.com/en-us/graph/api/resources/contentcustomization?view=graph-rest-1.0) | Represents the various content options to be customized throughout the authentication flow for a tenant.  <br>  <br>**NOTE:** Supported by Microsoft Entra ID for customers tenants only. |
| customAccountResetCredentialsUrl | String | A custom URL for resetting account credentials. This URL must be in ASCII format or non-ASCII characters must be URL encoded, and not exceed 128 characters. |
| customCannotAccessYourAccountText | String | A string to replace the default "Can't access your account?" self-service password reset \(SSPR\) hyperlink text on the sign-in page. This text must be in Unicode format and not exceed 256 characters. |
| customCSS | Stream | CSS styling that appears on the sign-in page. The allowed format is .css format only and not larger than 25KB. |
| customForgotMyPasswordText | String | A string to replace the default "Forgot my password" hyperlink text on the sign-in form. This text must be in Unicode format and not exceed 256 characters. |
| customPrivacyAndCookiesText | String | A string to replace the default "Privacy and Cookies" hyperlink text in the footer. This text must be in Unicode format and not exceed 256 characters. |
| customPrivacyAndCookiesUrl | String | A custom URL to replace the default URL of the "Privacy and Cookies" hyperlink in the footer. This URL must be in ASCII format or non-ASCII characters must be URL encoded, and not exceed 128 characters. |
| customTermsOfUseText | String | A string to replace the the default "Terms of Use" hyperlink text in the footer. This text must be in Unicode format and not exceed 256 characters. |
| customTermsOfUseUrl | String | A custom URL to replace the default URL of the "Terms of Use" hyperlink in the footer. This URL must be in ASCII format or non-ASCII characters must be URL encoded, and not exceed 128characters. |
| favicon | Stream | A custom icon \(favicon\) to replace a default Microsoft product favicon on a Microsoft Entra tenant. |
| headerBackgroundColor | String | The RGB color to apply to customize the color of the header. |
| headerLogo | Stream | A company logo that appears in the header of the sign-in page. The allowed types are PNG or JPEG not larger than 245 x 36 pixels. We recommend using a transparent image with no padding around the logo. |
| loginPageLayoutConfiguration | [loginPageLayoutConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/loginpagelayoutconfiguration?view=graph-rest-1.0) | Represents the layout configuration to be displayed on the login page for a tenant. |
| loginPageTextVisibilitySettings | [loginPageTextVisibilitySettings](https://learn.microsoft.com/en-us/graph/api/resources/loginpagetextvisibilitysettings?view=graph-rest-1.0) | Represents the various texts that can be hidden on the login page for a tenant. All the properties can be updated. |
| signInPageText | String | Text that appears at the bottom of the sign-in box. Use this to communicate additional information, such as the phone number to your help desk or a legal statement. This text must be in Unicode format and not exceed 1024 characters. |
| squareLogo | Stream | A square version of your company logo that appears in Windows 10 out-of-box experiences \(OOBE\) and when Windows Autopilot is enabled for deployment. Allowed types are PNG or JPEG not larger than 240 x 240 pixels and not more than 10 KB in size. We recommend using a transparent image with no padding around the logo. |
| squareLogoDark | Stream | A square dark version of your company logo that appears in Windows 10 out-of-box experiences \(OOBE\) and when Windows Autopilot is enabled for deployment. Allowed types are PNG or JPEG not larger than 240 x 240 pixels and not more than 10 KB in size. We recommend using a transparent image with no padding around the logo. |
| usernameHintText | String | A string that shows as the hint in the username textbox on the sign-in screen. This text must be a Unicode, without links or code, and can't exceed 64 characters. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Update the default branding

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

```msgraph
PATCH https://graph.microsoft.com/v1.0/organization/d69179bf-f4a4-41a9-a9de-249c0f2efb1d/branding
Content-Type: application/json
Accept-Language: 0

{
    "signInPageText":"Default",
    "usernameHintText":"DefaultHint"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OrganizationalBranding
{
	SignInPageText = "Default",
	UsernameHintText = "DefaultHint",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Organization["{organization-id}"].Branding.PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Accept-Language", "0");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphorganization "github.com/microsoftgraph/msgraph-sdk-go/organization"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Accept-Language", "0")

configuration := &graphorganization.ItemBrandingRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewOrganizationalBranding()
signInPageText := "Default"
requestBody.SetSignInPageText(&signInPageText) 
usernameHintText := "DefaultHint"
requestBody.SetUsernameHintText(&usernameHintText) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
branding, err := graphClient.Organization().ByOrganizationId("organization-id").Branding().Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OrganizationalBranding organizationalBranding = new OrganizationalBranding();
organizationalBranding.setSignInPageText("Default");
organizationalBranding.setUsernameHintText("DefaultHint");
OrganizationalBranding result = graphClient.organization().byOrganizationId("{organization-id}").branding().patch(organizationalBranding, requestConfiguration -> {
	requestConfiguration.headers.add("Accept-Language", "0");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const organizationalBranding = {
    signInPageText: 'Default',
    usernameHintText: 'DefaultHint'
};

await client.api('/organization/d69179bf-f4a4-41a9-a9de-249c0f2efb1d/branding')
	.update(organizationalBranding);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Organization\Item\Branding\BrandingRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\OrganizationalBranding;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OrganizationalBranding();
$requestBody->setSignInPageText('Default');
$requestBody->setUsernameHintText('DefaultHint');
$requestConfiguration = new BrandingRequestBuilderPatchRequestConfiguration();
$headers = [
		'Accept-Language' => '0',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->organization()->byOrganizationId('organization-id')->branding()->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	signInPageText = "Default"
	usernameHintText = "DefaultHint"
}

Update-MgOrganizationBranding -OrganizationId $organizationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.organization.item.branding.branding_request_builder import BrandingRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.organizational_branding import OrganizationalBranding
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OrganizationalBranding(
	sign_in_page_text = "Default",
	username_hint_text = "DefaultHint",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Accept-Language", "0")


result = await graph_client.organization.by_organization_id('organization-id').branding.patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Update bannerLogo for default branding

The following request updates the banner logo for the default branding. To update a Stream object type, use the PUT HTTP method and include the locale ID in the URL path.

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

```msgraph
PUT https://graph.microsoft.com/v1.0/organization/d69179bf-f4a4-41a9-a9de-249c0f2efb1d/branding/localizations/0/bannerLogo
Content-Type: image/jpeg

<Image>
```

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = <Image>;

await client.api('/organization/d69179bf-f4a4-41a9-a9de-249c0f2efb1d/branding/localizations/0/bannerLogo')
	.put(stream);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = Binary data for the image

Set-MgOrganizationBrandingLocalizationBannerLogo -OrganizationId $organizationId -OrganizationalBrandingLocalizationId $organizationalBrandingLocalizationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
