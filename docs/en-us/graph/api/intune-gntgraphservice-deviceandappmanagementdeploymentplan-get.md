<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentplan-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# Get deviceAndAppManagementDeploymentPlan

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Read properties and relationships of the [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.Read.All, DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
GET /deviceManagement/deploymentPlans/{deviceAndAppManagementDeploymentPlanId}
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/deploymentPlans/{deviceAndAppManagementDeploymentPlanId}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1841

{
  "value": {
    "@odata.type": "#microsoft.graph.deviceAndAppManagementDeploymentPlan",
    "id": "137dc698-c698-137d-98c6-7d1398c67d13",
    "versionNumber": 13,
    "displayName": "Display Name value",
    "description": "Description value",
    "roleScopeTagIds": [
      "Role Scope Tag Ids value"
    ],
    "topologyDefinitions": [
      {
        "@odata.type": "microsoft.graph.deviceAndAppManagementDeploymentTopologyDefinition",
        "topologyDisplayName": "Topology Display Name value",
        "topologyOrder": 13,
        "topologyActivationCriteria": {
          "@odata.type": "microsoft.graph.deviceAndAppManagementRingActivationDateTimeCriteria",
          "startDateTime": "2016-12-31T23:58:46.7156189-08:00"
        },
        "assignmentConfigurations": [
          {
            "@odata.type": "microsoft.graph.deviceAndAppManagementDeploymentTopologyAssignmentConfiguration",
            "target": {
              "@odata.type": "microsoft.graph.organizationalUnitAssignmentTarget",
              "deviceAndAppManagementAssignmentFilterId": "Device And App Management Assignment Filter Id value",
              "deviceAndAppManagementAssignmentFilterType": "include",
              "organizationalUnitId": "Organizational Unit Id value",
              "assignmentConflictSetting": {
                "@odata.type": "microsoft.graph.organizationalUnitAssignmentConflictSetting",
                "assignmentOverride": "denied",
                "versionNumber": 13
              }
            },
            "operation": "unknownFutureValue"
          }
        ]
      }
    ],
    "allowedPlatform": "androidForWork",
    "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
    "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
    "topologyCount": 13
  }
}
```
