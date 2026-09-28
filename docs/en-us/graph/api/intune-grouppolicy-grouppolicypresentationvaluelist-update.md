<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluelist-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update groupPolicyPresentationValueList

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [groupPolicyPresentationValueList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluelist?view=graph-rest-beta) object.

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
PATCH /deviceManagement/groupPolicyConfigurations/{groupPolicyConfigurationId}/definitionValues/{groupPolicyDefinitionValueId}/presentationValues/{groupPolicyPresentationValueId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [groupPolicyPresentationValueList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluelist?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [groupPolicyPresentationValueList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluelist?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| lastModifiedDateTime | DateTimeOffset | The date and time the object was last modified. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the object was created. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| values | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-keyvaluepair?view=graph-rest-beta) collection | A list of pairs for the associated presentation. |

## Response

If successful, this method returns a `200 OK` response code and an updated [groupPolicyPresentationValueList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluelist?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations/{groupPolicyConfigurationId}/definitionValues/{groupPolicyDefinitionValueId}/presentationValues/{groupPolicyPresentationValueId}
Content-type: application/json
Content-length: 222

{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationValueList",
  "values": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "Name value",
      "value": "Value value"
    }
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 394

{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationValueList",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "id": "1dbb7865-7865-1dbb-6578-bb1d6578bb1d",
  "values": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "Name value",
      "value": "Value value"
    }
  ]
}
```
