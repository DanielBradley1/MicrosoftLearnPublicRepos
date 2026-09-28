<!-- Source: https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-post-profilecardproperties?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Create profileCardProperty

Namespace: microsoft.graph

Create a new [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) for an organization. The new property is identified by its **directoryPropertyName** property.

For more information about how to add properties to the profile card for an organization, see [Add or remove custom attributes on a profile card using the profile card API](https://learn.microsoft.com/en-us/graph/add-properties-profilecard).

Note

Profile card properties correspond to attributes in Microsoft Entra ID. Adding an attribute as a **profileCardProperty** to the **profileCardProperties** collection for an organization configures profile cards to display the attribute value. Deleting the **profileCardProperty** from the collection *doesn’t delete the attribute from Microsoft Entra ID*; it deletes the configuration so that profile cards no longer display the attribute value.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PeopleSettings.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). *People Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /admin/people/profileCardProperties
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

> **Note:** To avoid encoding issues that malform the payload, use `Content-Type: application/json; charset=utf-8`.

## Request body

In the request body, supply a JSON representation of a [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) object.

You can specify the following properties when you create a **profileCardProperty** for an organization.

| Property | Type | Description |
| :--- | :--- | :--- |
| annotations | [profileCardAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/profilecardannotation?view=graph-rest-1.0) collection | Any alternative or localized labels that an administrator chose to specify. Optional. |
| directoryPropertyName | String | The name of the directory property that is intended to surface on the profile card. Required. |
| isVisible | Boolean | Indicates whether the given directory property should be shown on a user’s profile card. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a new [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/admin/people/profileCardProperties
Content-type: application/json; charset=utf-8

{
  "annotations": [
    {
      "displayName": "Cost Center",
      "localizations": [
        {
          "languageTag": "ru",
          "displayName": "центр затрат"
        }
      ]
    }
  ],
  "directoryPropertyName": "CustomAttribute1",
  "isVisible": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ProfileCardProperty
{
	Annotations = new List<ProfileCardAnnotation>
	{
		new ProfileCardAnnotation
		{
			DisplayName = "Cost Center",
			Localizations = new List<DisplayNameLocalization>
			{
				new DisplayNameLocalization
				{
					LanguageTag = "ru",
					DisplayName = "центр затрат",
				},
			},
		},
	},
	DirectoryPropertyName = "CustomAttribute1",
	IsVisible = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.People.ProfileCardProperties.PostAsync(requestBody);
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

requestBody := graphmodels.NewProfileCardProperty()


profileCardAnnotation := graphmodels.NewProfileCardAnnotation()
displayName := "Cost Center"
profileCardAnnotation.SetDisplayName(&displayName) 


displayNameLocalization := graphmodels.NewDisplayNameLocalization()
languageTag := "ru"
displayNameLocalization.SetLanguageTag(&languageTag) 
displayName := "центр затрат"
displayNameLocalization.SetDisplayName(&displayName) 

localizations := []graphmodels.DisplayNameLocalizationable {
	displayNameLocalization,
}
profileCardAnnotation.SetLocalizations(localizations)

annotations := []graphmodels.ProfileCardAnnotationable {
	profileCardAnnotation,
}
requestBody.SetAnnotations(annotations)
directoryPropertyName := "CustomAttribute1"
requestBody.SetDirectoryPropertyName(&directoryPropertyName) 
isVisible := true
requestBody.SetIsVisible(&isVisible) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
profileCardProperties, err := graphClient.Admin().People().ProfileCardProperties().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ProfileCardProperty profileCardProperty = new ProfileCardProperty();
LinkedList<ProfileCardAnnotation> annotations = new LinkedList<ProfileCardAnnotation>();
ProfileCardAnnotation profileCardAnnotation = new ProfileCardAnnotation();
profileCardAnnotation.setDisplayName("Cost Center");
LinkedList<DisplayNameLocalization> localizations = new LinkedList<DisplayNameLocalization>();
DisplayNameLocalization displayNameLocalization = new DisplayNameLocalization();
displayNameLocalization.setLanguageTag("ru");
displayNameLocalization.setDisplayName("центр затрат");
localizations.add(displayNameLocalization);
profileCardAnnotation.setLocalizations(localizations);
annotations.add(profileCardAnnotation);
profileCardProperty.setAnnotations(annotations);
profileCardProperty.setDirectoryPropertyName("CustomAttribute1");
profileCardProperty.setIsVisible(true);
ProfileCardProperty result = graphClient.admin().people().profileCardProperties().post(profileCardProperty);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const profileCardProperty = {
  annotations: [
    {
      displayName: 'Cost Center',
      localizations: [
        {
          languageTag: 'ru',
          displayName: 'центр затрат'
        }
      ]
    }
  ],
  directoryPropertyName: 'CustomAttribute1',
  isVisible: true
};

await client.api('/admin/people/profileCardProperties')
	.post(profileCardProperty);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ProfileCardProperty;
use Microsoft\Graph\Generated\Models\ProfileCardAnnotation;
use Microsoft\Graph\Generated\Models\DisplayNameLocalization;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ProfileCardProperty();
$annotationsProfileCardAnnotation1 = new ProfileCardAnnotation();
$annotationsProfileCardAnnotation1->setDisplayName('Cost Center');
$localizationsDisplayNameLocalization1 = new DisplayNameLocalization();
$localizationsDisplayNameLocalization1->setLanguageTag('ru');
$localizationsDisplayNameLocalization1->setDisplayName('центр затрат');
$localizationsArray []= $localizationsDisplayNameLocalization1;
$annotationsProfileCardAnnotation1->setLocalizations($localizationsArray);

$annotationsArray []= $annotationsProfileCardAnnotation1;
$requestBody->setAnnotations($annotationsArray);

$requestBody->setDirectoryPropertyName('CustomAttribute1');
$requestBody->setIsVisible(true);

$result = $graphServiceClient->admin()->people()->profileCardProperties()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	annotations = @(
		@{
			displayName = "Cost Center"
			localizations = @(
				@{
					languageTag = "ru"
					displayName = "центр затрат"
				}
			)
		}
	)
	directoryPropertyName = "CustomAttribute1"
	isVisible = $true
}

New-MgAdminPeopleProfileCardProperty -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.profile_card_property import ProfileCardProperty
from msgraph.generated.models.profile_card_annotation import ProfileCardAnnotation
from msgraph.generated.models.display_name_localization import DisplayNameLocalization
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ProfileCardProperty(
	annotations = [
		ProfileCardAnnotation(
			display_name = "Cost Center",
			localizations = [
				DisplayNameLocalization(
					language_tag = "ru",
					display_name = "центр затрат",
				),
			],
		),
	],
	directory_property_name = "CustomAttribute1",
	is_visible = True,
)

result = await graph_client.admin.people.profile_card_properties.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json; charset=utf-8

{
  "annotations": [
    {
      "displayName": "Cost Center",
      "localizations": [
        {
          "languageTag": "ru",
          "displayName": "центр затрат"
        }
      ]
    }
  ],
  "directoryPropertyName": "CustomAttribute1",
  "isVisible": true
}
```
