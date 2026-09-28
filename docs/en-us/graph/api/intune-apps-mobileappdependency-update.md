<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappdependency-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update mobileAppDependency

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [mobileAppDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappdependency?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceAppManagement/mobileAppRelationships/{mobileAppRelationshipId}
PATCH /deviceAppManagement/mobileApps/{mobileAppId}/relationships/{mobileAppRelationshipId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [mobileAppDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappdependency?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [mobileAppDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappdependency?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the mobile app relationship entity. This unique identifier is assigned at MobileAppRelationship entity creation. For example: 2dbc75b9-e993-4e4d-a071-91ac5a218672\_43aaaf35-ce51-4695-9447-5eac6df31161. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetId | String | The unique app identifier of the target of the mobile app relationship entity. For example: 2dbc75b9-e993-4e4d-a071-91ac5a218672. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetDisplayName | String | The display name of the app that is the target of the mobile app relationship entity. For example: Firefox Setup 52.0.2 32bit.intunewin. Maximum length is 500 characters. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetDisplayVersion | String | The display version of the app that is the target of the mobile app relationship entity. For example 1.0 or 1.2203.156. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetPublisher | String | The publisher of the app that is the target of the mobile app relationship entity. For example: Fabrikam. Maximum length is 500 characters. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetPublisherDisplayName | String | The publisher display name of the app that is the target of the mobile app relationship entity. For example: Fabrikam. Maximum length is 500 characters. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| sourceId | String | The unique app identifier of the source of the mobile app relationship entity. For example: 2dbc75b9-e993-4e4d-a071-91ac5a218672. If null during relationship creation, then it will be populated with parent Id. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| sourceDisplayName | String | The display name of the app that is the source of the mobile app relationship entity. For example: Orca. Maximum length is 500 characters. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| sourceDisplayVersion | String | The display version of the app that is the source of the mobile app relationship entity. For example 1.0.12 or 1.2203.156 or 3. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| sourcePublisherDisplayName | String | The publisher display name of the app that is the source of the mobile app relationship entity. For example: Fabrikam. Maximum length is 500 characters. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetType | [mobileAppRelationshipType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationshiptype?view=graph-rest-beta) | The type of relationship indicating whether the target application of a relationship is a parent or child in the relationship. Possible values are: parent, child. Read-Only. Returned by default. Supports: $select, $filter. Does not support $search, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta). Possible values are: `child`, `parent`, `unknownFutureValue`. |
| dependencyType | [mobileAppDependencyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappdependencytype?view=graph-rest-beta) | The type of dependency relationship between the parent and child apps. Possible values are: detect, autoInstall. Read-Only. Possible values are: `detect`, `autoInstall`, `unknownFutureValue`. |
| dependentAppCount | Int32 | The total number of apps that directly or indirectly depend on the parent app. Read-Only. This property is read-only. |
| dependsOnAppCount | Int32 | The total number of apps the child app directly or indirectly depends on. Read-Only. This property is read-only. |

## Response

If successful, this method returns a `200 OK` response code and an updated [mobileAppDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappdependency?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceAppManagement/mobileAppRelationships/{mobileAppRelationshipId}
Content-type: application/json
Content-length: 662

{
  "@odata.type": "#microsoft.graph.mobileAppDependency",
  "targetId": "Target Id value",
  "targetDisplayName": "Target Display Name value",
  "targetDisplayVersion": "Target Display Version value",
  "targetPublisher": "Target Publisher value",
  "targetPublisherDisplayName": "Target Publisher Display Name value",
  "sourceId": "Source Id value",
  "sourceDisplayName": "Source Display Name value",
  "sourceDisplayVersion": "Source Display Version value",
  "sourcePublisherDisplayName": "Source Publisher Display Name value",
  "targetType": "parent",
  "dependencyType": "autoInstall",
  "dependentAppCount": 1,
  "dependsOnAppCount": 1
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 711

{
  "@odata.type": "#microsoft.graph.mobileAppDependency",
  "id": "c7f6f9ab-f9ab-c7f6-abf9-f6c7abf9f6c7",
  "targetId": "Target Id value",
  "targetDisplayName": "Target Display Name value",
  "targetDisplayVersion": "Target Display Version value",
  "targetPublisher": "Target Publisher value",
  "targetPublisherDisplayName": "Target Publisher Display Name value",
  "sourceId": "Source Id value",
  "sourceDisplayName": "Source Display Name value",
  "sourceDisplayVersion": "Source Display Version value",
  "sourcePublisherDisplayName": "Source Publisher Display Name value",
  "targetType": "parent",
  "dependencyType": "autoInstall",
  "dependentAppCount": 1,
  "dependsOnAppCount": 1
}
```
