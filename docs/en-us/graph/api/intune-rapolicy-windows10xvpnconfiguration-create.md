<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xvpnconfiguration-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create windows10XVpnConfiguration

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [windows10XVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xvpnconfiguration?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/resourceAccessProfiles
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the windows10XVpnConfiguration object.

The following table shows the properties that are required when you create the windows10XVpnConfiguration.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Profile identifier Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| version | Int32 | Version of the profile Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| displayName | String | Profile display name Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| description | String | Profile description Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| creationDateTime | DateTimeOffset | DateTime profile was created Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime profile was last modified Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| roleScopeTagIds | String collection | Scope Tags Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| serverApplicabilityRules | [applicabilityRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-applicabilityrule?view=graph-rest-beta) collection | The list of Applicability Rules for a Device Configuration Profile Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| authenticationCertificateId | Guid | ID to the Authentication Certificate |
| customXmlFileName | String | Custom Xml file name. |
| customXml | Binary | Custom XML commands that configures the VPN connection. \(UTF8 byte encoding\) |

## Response

If successful, this method returns a `201 Created` response code and a [windows10XVpnConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xvpnconfiguration?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/resourceAccessProfiles
Content-type: application/json
Content-length: 589

{
  "@odata.type": "#microsoft.graph.windows10XVpnConfiguration",
  "version": 7,
  "displayName": "Display Name value",
  "description": "Description value",
  "creationDateTime": "2017-01-01T00:00:43.1365422-08:00",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "serverApplicabilityRules": [
    {
      "@odata.type": "microsoft.graph.applicabilityRule",
      "filterType": "include"
    }
  ],
  "authenticationCertificateId": "39b4cd38-cd38-39b4-38cd-b43938cdb439",
  "customXmlFileName": "Custom Xml File Name value",
  "customXml": "Y3VzdG9tWG1s"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 702

{
  "@odata.type": "#microsoft.graph.windows10XVpnConfiguration",
  "id": "6ee1c04f-c04f-6ee1-4fc0-e16e4fc0e16e",
  "version": 7,
  "displayName": "Display Name value",
  "description": "Description value",
  "creationDateTime": "2017-01-01T00:00:43.1365422-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "serverApplicabilityRules": [
    {
      "@odata.type": "microsoft.graph.applicabilityRule",
      "filterType": "include"
    }
  ],
  "authenticationCertificateId": "39b4cd38-cd38-39b4-38cd-b43938cdb439",
  "customXmlFileName": "Custom Xml File Name value",
  "customXml": "Y3VzdG9tWG1s"
}
```
