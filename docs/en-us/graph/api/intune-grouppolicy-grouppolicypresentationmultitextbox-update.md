<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationmultitextbox-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update groupPolicyPresentationMultiTextBox

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [groupPolicyPresentationMultiTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationmultitextbox?view=graph-rest-beta) object.

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
PATCH /deviceManagement/groupPolicyConfigurations/{groupPolicyConfigurationId}/definitionValues/{groupPolicyDefinitionValueId}/presentationValues/{groupPolicyPresentationValueId}/presentation
PATCH /deviceManagement/groupPolicyConfigurations/{groupPolicyConfigurationId}/definitionValues/{groupPolicyDefinitionValueId}/presentationValues/{groupPolicyPresentationValueId}/presentation/definition/presentations/{groupPolicyPresentationId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [groupPolicyPresentationMultiTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationmultitextbox?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [groupPolicyPresentationMultiTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationmultitextbox?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | Localized text label for any presentation entity. The default value is empty. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| required | Boolean | Requirement to enter a value in the text box. Default value is false. |
| maxLength | Int64 | An unsigned integer that specifies the maximum number of text characters. Default value is 1023. |
| maxStrings | Int64 | An unsigned integer that specifies the maximum number of strings. Default value is 0. |

## Response

If successful, this method returns a `200 OK` response code and an updated [groupPolicyPresentationMultiTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationmultitextbox?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations/{groupPolicyConfigurationId}/definitionValues/{groupPolicyDefinitionValueId}/presentationValues/{groupPolicyPresentationValueId}/presentation
Content-type: application/json
Content-length: 165

{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationMultiTextBox",
  "label": "Label value",
  "required": true,
  "maxLength": 9,
  "maxStrings": 10
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 278

{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationMultiTextBox",
  "label": "Label value",
  "id": "381ac035-c035-381a-35c0-1a3835c01a38",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "required": true,
  "maxLength": 9,
  "maxStrings": 10
}
```
