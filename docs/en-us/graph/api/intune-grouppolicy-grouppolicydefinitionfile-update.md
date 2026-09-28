<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicydefinitionfile-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update groupPolicyDefinitionFile

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/groupPolicyDefinitionFiles/{groupPolicyDefinitionFileId}
PATCH /deviceManagement/groupPolicyConfigurations/{groupPolicyConfigurationId}/definitionValues/{groupPolicyDefinitionValueId}/presentationValues/{groupPolicyPresentationValueId}/presentation/definition/definitionFile
PATCH /deviceManagement/groupPolicyConfigurations/{groupPolicyConfigurationId}/definitionValues/{groupPolicyDefinitionValueId}/presentationValues/{groupPolicyPresentationValueId}/presentation/definition/category/definitionFile
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The localized friendly name of the ADMX file. |
| description | String | The localized description of the policy settings in the ADMX file. The default value is empty. |
| languageCodes | String collection | The supported language codes for the ADMX file. |
| targetPrefix | String | Specifies the logical name that refers to the namespace within the ADMX file. |
| targetNamespace | String | Specifies the URI used to identify the namespace within the ADMX file. |
| policyType | [groupPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicytype?view=graph-rest-beta) | Specifies the type of group policy. Possible values are: `admxBacked`, `admxIngested`. |
| revision | String | The revision version associated with the file. |
| fileName | String | The file name of the ADMX file without the path. For example: edge.admx |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. |

## Response

If successful, this method returns a `200 OK` response code and an updated [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitionFiles/{groupPolicyDefinitionFileId}
Content-type: application/json
Content-length: 392

{
  "@odata.type": "#microsoft.graph.groupPolicyDefinitionFile",
  "displayName": "Display Name value",
  "description": "Description value",
  "languageCodes": [
    "Language Codes value"
  ],
  "targetPrefix": "Target Prefix value",
  "targetNamespace": "Target Namespace value",
  "policyType": "admxIngested",
  "revision": "Revision value",
  "fileName": "File Name value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 505

{
  "@odata.type": "#microsoft.graph.groupPolicyDefinitionFile",
  "displayName": "Display Name value",
  "description": "Description value",
  "languageCodes": [
    "Language Codes value"
  ],
  "targetPrefix": "Target Prefix value",
  "targetNamespace": "Target Namespace value",
  "policyType": "admxIngested",
  "revision": "Revision value",
  "fileName": "File Name value",
  "id": "940aa2a1-a2a1-940a-a1a2-0a94a1a20a94",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00"
}
```
