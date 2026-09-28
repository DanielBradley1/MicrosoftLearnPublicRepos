<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-wip-intunebrandingprofile-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update intuneBrandingProfile

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/intuneBrandingProfiles/{intuneBrandingProfileId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta).

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

## Response

If successful, this method returns a `200 OK` response code and an updated [intuneBrandingProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-intunebrandingprofile?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/intuneBrandingProfiles/{intuneBrandingProfileId}
Content-type: application/json
Content-length: 2005

{
  "@odata.type": "#microsoft.graph.intuneBrandingProfile",
  "profileName": "Profile Name value",
  "profileDescription": "Profile Description value",
  "isDefaultProfile": true,
  "displayName": "Display Name value",
  "themeColor": {
    "@odata.type": "microsoft.graph.rgbColor",
    "r": 1,
    "g": 1,
    "b": 1
  },
  "showLogo": true,
  "showDisplayNameNextToLogo": true,
  "themeColorLogo": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "Type value",
    "value": "dmFsdWU="
  },
  "lightBackgroundLogo": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "Type value",
    "value": "dmFsdWU="
  },
  "landingPageCustomizedImage": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "Type value",
    "value": "dmFsdWU="
  },
  "contactITName": "Contact ITName value",
  "contactITPhoneNumber": "Contact ITPhone Number value",
  "contactITEmailAddress": "Contact ITEmail Address value",
  "contactITNotes": "Contact ITNotes value",
  "onlineSupportSiteUrl": "https://example.com/onlineSupportSiteUrl/",
  "onlineSupportSiteName": "Online Support Site Name value",
  "privacyUrl": "https://example.com/privacyUrl/",
  "customPrivacyMessage": "Custom Privacy Message value",
  "customCanSeePrivacyMessage": "Custom Can See Privacy Message value",
  "customCantSeePrivacyMessage": "Custom Cant See Privacy Message value",
  "isRemoveDeviceDisabled": true,
  "isFactoryResetDisabled": true,
  "companyPortalBlockedActions": [
    {
      "@odata.type": "microsoft.graph.companyPortalBlockedAction",
      "platform": "androidForWork",
      "ownerType": "company",
      "action": "remove"
    }
  ],
  "disableDeviceCategorySelection": true,
  "showAzureADEnterpriseApps": true,
  "showOfficeWebApps": true,
  "showConfigurationManagerApps": true,
  "enrollmentAvailability": "availableWithoutPrompts",
  "disableClientTelemetry": true,
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 2177

{
  "@odata.type": "#microsoft.graph.intuneBrandingProfile",
  "id": "fcd6136c-136c-fcd6-6c13-d6fc6c13d6fc",
  "profileName": "Profile Name value",
  "profileDescription": "Profile Description value",
  "isDefaultProfile": true,
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "displayName": "Display Name value",
  "themeColor": {
    "@odata.type": "microsoft.graph.rgbColor",
    "r": 1,
    "g": 1,
    "b": 1
  },
  "showLogo": true,
  "showDisplayNameNextToLogo": true,
  "themeColorLogo": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "Type value",
    "value": "dmFsdWU="
  },
  "lightBackgroundLogo": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "Type value",
    "value": "dmFsdWU="
  },
  "landingPageCustomizedImage": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "Type value",
    "value": "dmFsdWU="
  },
  "contactITName": "Contact ITName value",
  "contactITPhoneNumber": "Contact ITPhone Number value",
  "contactITEmailAddress": "Contact ITEmail Address value",
  "contactITNotes": "Contact ITNotes value",
  "onlineSupportSiteUrl": "https://example.com/onlineSupportSiteUrl/",
  "onlineSupportSiteName": "Online Support Site Name value",
  "privacyUrl": "https://example.com/privacyUrl/",
  "customPrivacyMessage": "Custom Privacy Message value",
  "customCanSeePrivacyMessage": "Custom Can See Privacy Message value",
  "customCantSeePrivacyMessage": "Custom Cant See Privacy Message value",
  "isRemoveDeviceDisabled": true,
  "isFactoryResetDisabled": true,
  "companyPortalBlockedActions": [
    {
      "@odata.type": "microsoft.graph.companyPortalBlockedAction",
      "platform": "androidForWork",
      "ownerType": "company",
      "action": "remove"
    }
  ],
  "disableDeviceCategorySelection": true,
  "showAzureADEnterpriseApps": true,
  "showOfficeWebApps": true,
  "showConfigurationManagerApps": true,
  "enrollmentAvailability": "availableWithoutPrompts",
  "disableClientTelemetry": true,
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ]
}
```
