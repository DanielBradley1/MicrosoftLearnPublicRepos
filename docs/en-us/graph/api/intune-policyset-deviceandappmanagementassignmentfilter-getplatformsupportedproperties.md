<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-getplatformsupportedproperties?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# getPlatformSupportedProperties function

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

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
GET /deviceManagement/assignmentFilters/getPlatformSupportedProperties
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request URL, provide the following query parameters with values. The following table shows the parameters that can be used with this function.

| Property | Type | Description |
| :--- | :--- | :--- |
| platform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceplatformtype?view=graph-rest-beta) |  |

## Response

If successful, this function returns a `200 OK` response code and a [assignmentFilterSupportedProperty](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltersupportedproperty?view=graph-rest-beta) collection in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/assignmentFilters/getPlatformSupportedProperties(platform='parameterValue')
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 407

{
  "value": [
    {
      "@odata.type": "microsoft.graph.assignmentFilterSupportedProperty",
      "dataType": "Data Type value",
      "isCollection": true,
      "name": "Name value",
      "propertyRegexConstraint": "Property Regex Constraint value",
      "supportedOperators": [
        "equals"
      ],
      "supportedValues": [
        "Supported Values value"
      ]
    }
  ]
}
```
