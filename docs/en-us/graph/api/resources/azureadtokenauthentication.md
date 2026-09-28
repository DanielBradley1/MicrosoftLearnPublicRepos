<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureadtokenauthentication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# azureAdTokenAuthentication resource type

Namespace: microsoft.graph

Defines the Microsoft Entra application used to authenticate a logic app with a [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0), [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-1.0), or [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0). This object is configured in the **authenticationConfiguration** property of those resources. Only the app ID of the application is required. Derived from [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceId | String | The **appID** of the Microsoft Entra application to use to authenticate an app with a custom extension. |

## JSON representation

The following JSON representation shows the resource type.

```json
{ 
  "@odata.type": "#microsoft.graph.azureAdTokenAuthentication", 
  "resourceId": "String" 
 } 
```
