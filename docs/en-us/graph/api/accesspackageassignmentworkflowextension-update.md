<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentworkflowextension-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-22 -->

# Update accessPackageAssignmentWorkflowExtension

Namespace: microsoft.graph

Update the properties of an [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- One of the following [Azure role](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) assignments are required either on the Logic App itself, or on a higher scope such as the resource group, subscription or management group:

  - Logic App contributor
  - Contributor
  - Owner

And one of the following:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged role is *Catalog owner*. **This is the least privileged option**.
- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Catalog owner* role is less privileged than the `EntitlementManagement.Read.All` application permission.. If it's a delegated call without the `URL` property in [logicAppTriggerEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/logicapptriggerendpointconfiguration), the caller also needs to be authorized on the Logic App.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
PUT /identityGovernance/entitlementManagement/catalogs/{catalogId}/customWorkflowExtensions/{customAccessPackageWorkflowExtensionId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | Authentication type. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| description | String | Description for the accessPackageCustomWorkflowExtension object. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| displayName | String | Display name for the accessPackageCustomWorkflowExtension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The type and details for configuring the endpoint to call the logic app's workflow. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| callbackConfiguration | [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0) | The timeout duration for callback. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs/32efb28c-9a7a-446c-986b-ca6528c6669d/customWorkflowExtensions/78ffaec5-ae8e-4902-a434-5ffc5d3d3cd0
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentWorkflowExtension",
  "displayName": "test_action_0124_email",
  "description": "this is for graph testing only"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customCalloutExtension = {
  '@odata.type': '#microsoft.graph.accessPackageAssignmentWorkflowExtension',
  displayName: 'test_action_0124_email',
  description: 'this is for graph testing only'
};

await client.api('/identityGovernance/entitlementManagement/catalogs/32efb28c-9a7a-446c-986b-ca6528c6669d/customWorkflowExtensions/78ffaec5-ae8e-4902-a434-5ffc5d3d3cd0')
	.put(customCalloutExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "value":{
      "@odata.type":"#microsoft.graph.accessPackageAssignmentWorkflowExtension",
      "id":"78ffaec5-ae8e-4902-a434-5ffc5d3d3cd0",
      "displayName":"test_action_0127_email",
      "description": "this is for graph testing only",
      "createdDateTime":"2022-01-24T21:48:57.15Z",
      "lastModifiedDateTime":"2022-01-24T21:55:44.953Z",
      "clientConfiguration":null,
      "endpointConfiguration":{
         "@odata.type":"#microsoft.graph.logicAppTriggerEndpointConfiguration",
         "subscriptionId":"38ab2ccc-3747-4567-b36b-9478f5602f0d",
         "resourceGroupName":"test",
         "logicAppWorkflowName":"elm-extension-email",
         "url":"https://prod-31.eastus.logic.azure.com:443/workflows/7ccffea766ae48e680gd9a22d1549bbc/triggers/manual/paths/invoke?api-version=2016-10-01"
      },
      "authenticationConfiguration":{
         "@odata.type":"#microsoft.graph.azureAdPopTokenAuthentication"
      }
   }
}
```
