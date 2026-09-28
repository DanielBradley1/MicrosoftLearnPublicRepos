<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# intuneBrandingProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This entity contains data which is used in customizing the tenant level appearance of the Company Portal applications as well as the end user web portal.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List intuneBrandingProfiles](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofile-list?view=graph-rest-beta) | [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) collection | List properties and relationships of the [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) objects. |
| [Get intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofile-get?view=graph-rest-beta) | [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) | Read properties and relationships of the [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) object. |
| [Create intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofile-create?view=graph-rest-beta) | [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) | Create a new [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) object. |
| [Delete intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofile-delete?view=graph-rest-beta) | None | Deletes a [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta). |
| [Update intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofile-update?view=graph-rest-beta) | [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) | Update the properties of a [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofile-assign?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Profile Key |
| profileName | String | Name of the profile |
| profileDescription | String | Description of the profile |
| isDefaultProfile | Boolean | Boolean that represents whether the profile is used as default or not |
| createdDateTime | DateTimeOffset | Time when the BrandingProfile was created |
| lastModifiedDateTime | DateTimeOffset | Time when the BrandingProfile was last modified |
| displayName | String | Company/organization name that is displayed to end users |
| themeColor | [rgbColor](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-rgbcolor?view=graph-rest-beta) | Primary theme color used in the Company Portal applications and web portal |
| showLogo | Boolean | Boolean that represents whether the administrator-supplied logo images are shown or not |
| showDisplayNameNextToLogo | Boolean | Boolean that represents whether the administrator-supplied display name will be shown next to the logo image or not |
| themeColorLogo | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-beta) | Logo image displayed in Company Portal apps which have a theme color background behind the logo |
| lightBackgroundLogo | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-beta) | Logo image displayed in Company Portal apps which have a light background behind the logo |
| landingPageCustomizedImage | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-beta) | Customized image displayed in Company Portal apps landing page |
| contactITName | String | Name of the person/organization responsible for IT support |
| contactITPhoneNumber | String | Phone number of the person/organization responsible for IT support |
| contactITEmailAddress | String | E-mail address of the person/organization responsible for IT support |
| contactITNotes | String | Text comments regarding the person/organization responsible for IT support |
| onlineSupportSiteUrl | String | URL to the company/organization’s IT helpdesk site |
| onlineSupportSiteName | String | Display name of the company/organization’s IT helpdesk site |
| privacyUrl | String | URL to the company/organization’s privacy policy |
| customPrivacyMessage | String | Text comments regarding what the admin doesn't have access to on the device |
| customCanSeePrivacyMessage | String | Text comments regarding what the admin has access to on the device |
| customCantSeePrivacyMessage | String | Text comments regarding what the admin doesn't have access to on the device |
| isRemoveDeviceDisabled | Boolean | Boolean that represents whether the adminsistrator has disabled the 'Remove Device' action on corporate owned devices. |
| isFactoryResetDisabled | Boolean | Boolean that represents whether the adminsistrator has disabled the 'Factory Reset' action on corporate owned devices. |
| companyPortalBlockedActions | [companyPortalBlockedAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-companyportalblockedaction?view=graph-rest-beta) collection | Collection of blocked actions on the company portal as per platform and device ownership types. |
| disableDeviceCategorySelection | Boolean | Boolean that indicates if Device Category Selection will be shown in Company Portal |
| showAzureADEnterpriseApps | Boolean | Boolean that indicates if AzureAD Enterprise Apps will be shown in Company Portal |
| showOfficeWebApps | Boolean | Boolean that indicates if Office WebApps will be shown in Company Portal |
| showConfigurationManagerApps | Boolean | Boolean that indicates if Configuration Manager Apps will be shown in Company Portal |
| enrollmentAvailability | [enrollmentAvailabilityOptions](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmentavailabilityoptions?view=graph-rest-beta) | Customized device enrollment flow displayed to the end user . Possible values are: `availableWithPrompts`, `availableWithoutPrompts`, `unavailable`. |
| disableClientTelemetry | Boolean | Applies to telemetry sent from all clients to the Intune service. When disabled, all proactive troubleshooting and issue warnings within the client are turned off, and telemetry settings appear inactive or hidden to the device user. |
| roleScopeTagIds | String collection | List of scope tags assigned to the branding profile |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [intuneBrandingProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofileassignment?view=graph-rest-beta) collection | The list of group assignments for the branding profile |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.intuneBrandingProfile",
  "id": "String (identifier)",
  "profileName": "String",
  "profileDescription": "String",
  "isDefaultProfile": true,
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "themeColor": {
    "@odata.type": "microsoft.graph.rgbColor",
    "r": 1024,
    "g": 1024,
    "b": 1024
  },
  "showLogo": true,
  "showDisplayNameNextToLogo": true,
  "themeColorLogo": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "String",
    "value": "binary"
  },
  "lightBackgroundLogo": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "String",
    "value": "binary"
  },
  "landingPageCustomizedImage": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "String",
    "value": "binary"
  },
  "contactITName": "String",
  "contactITPhoneNumber": "String",
  "contactITEmailAddress": "String",
  "contactITNotes": "String",
  "onlineSupportSiteUrl": "String",
  "onlineSupportSiteName": "String",
  "privacyUrl": "String",
  "customPrivacyMessage": "String",
  "customCanSeePrivacyMessage": "String",
  "customCantSeePrivacyMessage": "String",
  "isRemoveDeviceDisabled": true,
  "isFactoryResetDisabled": true,
  "companyPortalBlockedActions": [
    {
      "@odata.type": "microsoft.graph.companyPortalBlockedAction",
      "platform": "String",
      "ownerType": "String",
      "action": "String"
    }
  ],
  "disableDeviceCategorySelection": true,
  "showAzureADEnterpriseApps": true,
  "showOfficeWebApps": true,
  "showConfigurationManagerApps": true,
  "enrollmentAvailability": "String",
  "disableClientTelemetry": true,
  "roleScopeTagIds": [
    "String"
  ]
}
```
