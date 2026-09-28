<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-policyset-devicecompliancepolicypolicysetitem-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create deviceCompliancePolicyPolicySetItem

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [deviceCompliancePolicyPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-devicecompliancepolicypolicysetitem?view=graph-rest-beta) object.

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
POST /deviceAppManagement/policySets/{policySetId}/items
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the deviceCompliancePolicyPolicySetItem object.

The following table shows the properties that are required when you create the deviceCompliancePolicyPolicySetItem.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | Creation time of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last modified time of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| payloadId | String | PayloadId of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| itemType | String | policySetType of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| displayName | String | DisplayName of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| status | [policySetStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetstatus?view=graph-rest-beta) | Status of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta). Possible values are: `unknown`, `validating`, `partialSuccess`, `success`, `error`, `notAssigned`. |
| errorCode | [errorCode](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-errorcode?view=graph-rest-beta) | Error code if any occured. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta). Possible values are: `noError`, `unauthorized`, `notFound`, `deleted`. |
| guidedDeploymentTags | String collection | Tags of the guided deployment Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |

## Response

If successful, this method returns a `201 Created` response code and a [deviceCompliancePolicyPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-devicecompliancepolicypolicysetitem?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceAppManagement/policySets/{policySetId}/items
Content-type: application/json
Content-length: 317

{
  "@odata.type": "#microsoft.graph.deviceCompliancePolicyPolicySetItem",
  "payloadId": "Payload Id value",
  "itemType": "Item Type value",
  "displayName": "Display Name value",
  "status": "validating",
  "errorCode": "unauthorized",
  "guidedDeploymentTags": [
    "Guided Deployment Tags value"
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 489

{
  "@odata.type": "#microsoft.graph.deviceCompliancePolicyPolicySetItem",
  "id": "5c0bc827-c827-5c0b-27c8-0b5c27c80b5c",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "payloadId": "Payload Id value",
  "itemType": "Item Type value",
  "displayName": "Display Name value",
  "status": "validating",
  "errorCode": "unauthorized",
  "guidedDeploymentTags": [
    "Guided Deployment Tags value"
  ]
}
```
