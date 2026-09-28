<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# cloudPcCloudApp resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a cloud app. Cloud apps are built on frontline shared options and provide Windows 365 end users with an experience to access app-only sessions rather than a full desktop experience.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-cloudapps?view=graph-rest-beta) | [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) collection | List all the [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) objects filtered by a provision policy ID. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-cloudapps?view=graph-rest-beta) | [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) | Create a new [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-get?view=graph-rest-beta) | [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) | Read the properties of a specific [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-update?view=graph-rest-beta) | [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) | Update the properties of a [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object, such as the display name or icon path. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-delete?view=graph-rest-beta) | None | Delete a [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object. |
| [Publish](https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-publish?view=graph-rest-beta) | None | Publish a [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object to make it available to end users through their portal, such as the Windows App. |
| [Unpublish](https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-unpublish?view=graph-rest-beta) | None | Unpublish a [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) to remove it from the end-user portal, for example, the Windows App. |
| [Reset](https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-reset?view=graph-rest-beta) | None | Reset the app details of the [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object to the app details of the initially discovered app that this cloud app is mapped to. |
| [Retrieve discovered apps](https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-retrievediscoveredapps?view=graph-rest-beta) | [cloudPcDiscoveredApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdiscoveredapp?view=graph-rest-beta) | Get a list of [cloudPcDiscoveredApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdiscoveredapp?view=graph-rest-beta) objects whose app details can be used to map to a [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionFailedErrorCode | [cloudPcCloudAppActionFailedErrorCode](#cloudpccloudappactionfailederrorcode-values) | The error code if publishing, unpublishing, or resetting a cloud app fails. The possible values are: `cloudAppQuotaExceeded`, `cloudPcLicenseNotFound`, `internalServerError`, `appDiscoveryFailed`, `unknownFutureValue`, `iconPathInvalid`, `filePathInvalid`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this evolvable enum: `iconPathInvalid`, `filePathInvalid`. The default value is `null`. Supports `$filter`, `$select`, `$orderBy`. Read-only. |
| actionFailedErrorMessage | String | The error message when the IT admin failed to publish, unpublish, update, or reset a cloud app. For example: "Publish failed because it exceeds the 500 cloud apps limitation under the policy. You need to unpublish some cloud apps under this policy in order to publish this cloud app again." Read-only. |
| addedDateTime | DateTimeOffset | The date and time when the cloud app was added to this tenant and became visible in the admin portal. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Returned by default. An IT admin can't set or modify it. Supports `$filter`, `$select`, and `$orderBy`. Read-only. |
| appDetail | [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta) | The details about the cloud app. These values come initially from the **appDetail** property of the associated discovered app. The **iconPath**, **iconIndex**, and **commandLineArguments** properties can be changed as needed when you update the cloud app. The **cloudPcCloudAppDetail** type is polymorphic and includes the following derived types: [cloudPcAutomaticDiscoveredAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcautomaticdiscoveredappdetail?view=graph-rest-beta) for apps automatically discovered from the *start* menu, and [cloudPcFilePathAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcfilepathappdetail?view=graph-rest-beta) for apps manually created when a file path is specified. The **@odata.type** property indicates the specific type. Supports `$select`. |
| appStatus | [cloudPcCloudAppStatus](#cloudpccloudappstatus-values) | The status of the cloud app. The possible values are: `preparing`, `ready`, `publishing`, `published`, `unpublishing`, `failed`, `unknownFutureValue`. The default value is `preparing`. For example, the state is `preparing` when the cloud app appears in the Intune portal, which indicates that the cloud app isn't yet ready to be published. The state then transitions to `ready`, which indicates that the cloud app is ready to be published. When an admin publishes or unpublishes a cloud app, the status transitions to `publishing` or `unpublishing`, respectively, before finally moving to `published` or `ready`. Supports `$filter`, `$select`, and `$orderBy`. Read-only. |
| availableToUser | Boolean | Indicates whether this cloud app is available to end users through the end-user portal or the Windows App. The default value is `false`. It changes to `true` if the cloud app is successfully published, and reverts to `false` when the admin unpublishes the cloud app. Supports `$filter`, `$select`, and `$orderBy`. |
| description | String | The description associated with the cloud app. The maximum allowed length for this property is 512 characters. Supports `$filter`, `$select`, and `$orderBy`. |
| discoveredAppName | String | Name of the discovered app associated with the cloud app. For example, `Paint`, Supports `$filter`, `$select`, and `$orderBy`. Read-only. |
| displayName | String | The display name for the cloud app. The display name for the cloud app, which appears on the end-user portal and must be unique within a single provisioning policy. It uses the discovered app name as the default value. The maximum allowed length for this property is 64 characters. For example, `Paint`. Supports `$filter`, `$select`, and `$orderBy`. |
| id | String | The unique ID of the cloud app. Autogenerated value during the creation of a new cloud app. Supports `$filter`, `$select`, and `$orderBy`. Read-only. |
| lastPublishedDateTime | DateTimeOffset | The latest date time when the admin published the cloud app. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Returned by default. An IT admin can't set or modify it. Supports `$filter`, `$select`, and `$orderBy`. Read-only. |
| provisioningPolicyId | String | The ID of the provisioning policy associated with this cloud app. For example, `96133506-c05b-4dbb-a150-ed4adc59895f`. Supports `$filter`, `$select`, and `$orderBy`. Required. |
| scopeIds | String collection | The list of scope tag IDs for this cloud app. Inherited from the provisioning policy when the app is created or updated. Read-only. |

### cloudPcCloudAppStatus values

| Member | Description |
| :--- | :--- |
| preparing | Default. The initial state of a cloud app. Indicates that the cloud app isn't yet ready for publishing. |
| ready | Indicates that the cloud app is ready for publishing. |
| publishing | Indicates that the cloud app is in publishing or updating state. |
| published | Indicates that the application was published or updated successfully. |
| unpublishing | Indicates that the cloud app is in unpublishing state. |
| failed | Indicates that the application failed to complete the publishing, unpublishing, updating, or resetting process. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcCloudAppActionFailedErrorCode values

| Member | Description |
| :--- | :--- |
| cloudAppQuotaExceeded | Indicates that the provisioning policy reached the limit of 500 cloud apps. To proceed, unpublish an existing cloud app and try again. |
| cloudPcLicenseNotFound | Indicates that the tenant doesn't have any available frontline licenses. |
| internalServerError | Indicates that the cloud app can't be published or unpublished due to an internal server error. |
| appDiscoveryFailed | Indicates that the app discovery failed in the associated Cloud PC device. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| iconPathInvalid | Indicates that the icon path specified for the cloud app is invalid. |
| filePathInvalid | Indicates that the file path specified for the cloud app is invalid. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcCloudApp",
  "actionFailedErrorCode": "String",
  "actionFailedErrorMessage": "String",
  "addedDateTime": "String (timestamp)",
  "appDetail": {"@odata.type": "microsoft.graph.cloudPcCloudAppDetail"},
  "appStatus": "String",
  "availableToUser": "Boolean",
  "description": "String",
  "discoveredAppName": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastPublishedDateTime": "String (timestamp)",
  "provisioningPolicyId": "String",
  "scopeIds": ["String"]
}
```
