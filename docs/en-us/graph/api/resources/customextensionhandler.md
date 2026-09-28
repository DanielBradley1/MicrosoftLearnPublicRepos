<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensionhandler?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# customExtensionHandler resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines when to execute a [custom access package workflow extension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

Note

1. To read the customExtensionHandler objects on a policy, append `?$expand=customExtensionHandlers` to a [GET accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-beta) request. For example, `GET https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/4540a08f-8ab5-43f6-a923-015275799197?$expand=customExtensionHandlers`. For more information, see [Example 2: Retrieve the custom extension handlers for a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-beta#example-2-retrieve-the-custom-extension-handlers-for-a-policy).
2. To delete the **customExtensionHandlers** objects from a policy, call the [Update accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-update?view=graph-rest-beta) and specify the customExtensionHandlers property as an empty collection. For more information, see [Example 2: Remove the customExtensionHandlers and verifiableCredentialSettings from a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-update?view=graph-rest-beta#example-2-remove-the-customextensionhandlers-and-verifiablecredentialsettings-from-a-policy).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier of the stage. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| stage | accessPackageCustomExtensionStage | Indicates the stage of the access package assignment request workflow when the access package custom extension runs. The possible values are: `assignmentRequestCreated`, `assignmentRequestApproved`, `assignmentRequestGranted`, `assignmentRequestRemoved`, `assignmentFourteenDaysBeforeExpiration`, `assignmentOneDayBeforeExpiration`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) | Indicates which custom workflow extension is executed at this stage. Nullable. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionHandler",
  "id": "String (identifier)",
  "stage": "String"
}
```
