<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# customCalloutExtension resource type

Namespace: microsoft.graph

An abstract type that defines the configuration for apps that can extend the customer's identity flows.

This abstract type is inherited by the following derived types.

- [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0)
- [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0)
- [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-1.0)
- [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

In entitlement management, the derived types of this object are configured in the following properties and relationships:

- **accessPackageCustomWorkflowExtensions** relationship of [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0)
- **customExtension** relationship of [accessPackageDynamicApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagedynamicapprovalstage?view=graph-rest-1.0)
- **customExtension** relationship of [customExtensionStageSetting](https://learn.microsoft.com/en-us/graph/api/resources/customextensionstagesetting?view=graph-rest-1.0)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | Configuration for securing the API call to the logic app. For example, using OAuth client credentials flow. |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | HTTP connection settings that define how long Microsoft Entra ID can wait for a connection to a logic app, how many times you can retry a timed-out connection and the exception scenarios when retries are allowed. |
| description | String | Description for the customCalloutExtension object. |
| displayName | String | Display name for the customCalloutExtension object. |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The type and details for configuring the endpoint to call the logic app's workflow. |
| id | String | Identifier for the customCalloutExtension object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customCalloutExtension",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "endpointConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionEndpointConfiguration"
  },
  "clientConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
  },
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionAuthenticationConfiguration"
  }
}
```
