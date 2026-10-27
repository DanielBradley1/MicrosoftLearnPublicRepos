<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# customExtensionEndpointConfiguration resource type

Namespace: microsoft.graph

Abstract base type that exposes the derived types used to configure the **endpointConfiguration** property of a custom extension. In Lifecycle Workflows, the derived types of this object are configured in the **endpointConfiguration** property of the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) resource. In Privileged Identity Management, they're configured in the **endpointConfiguration** property of the [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) resource. This abstract type is inherited by the following types:

- [logicAppTriggerEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/logicapptriggerendpointconfiguration?view=graph-rest-1.0) - configure this object for the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) in Lifecycle Workflows in Entitlement Management access package request and assignment cycles.
- [httpRequestEndpoint](https://learn.microsoft.com/en-us/graph/api/resources/httprequestendpoint?view=graph-rest-1.0) - configure this object for an HTTP-based custom extension, including a [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0), or to [validate a custom authentication extension](https://learn.microsoft.com/en-us/graph/api/customauthenticationextension-validateauthenticationconfiguration?view=graph-rest-1.0).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionEndpointConfiguration" 
}
```
