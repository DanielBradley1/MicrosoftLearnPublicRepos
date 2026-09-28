<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensionstagesetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# customExtensionStageSetting resource type

Namespace: microsoft.graph

Defines when to execute a [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-1.0) or [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0) object.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

To read the **customExtensionStageSettings** objects on a policy, append `?$expand=customExtensionStageSettings($expand=customExtension)` to a [GET accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-1.0) request. For example, `GET https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/4540a08f-8ab5-43f6-a923-015275799197?$expand=customExtensionStageSettings($expand=customExtension)`. For more information, see [Example 2: Retrieve the custom extension stage settings for a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-1.0#example-2-retrieve-the-custom-extension-stage-settings-for-a-policy).

To delete the **customExtensionStageSettings** objects from a policy, call the [Update accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-update?view=graph-rest-1.0) and specify the customExtensionHandlers property as an empty collection. For more information, see [Example 2: Remove the customExtensionStageSettings from a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-update?view=graph-rest-1.0#example-2-remove-the-customextensionstagesettings-from-a-policy).

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier of the stage. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| stage | accessPackageCustomExtensionStage | Indicates the stage of the access package assignment request workflow when the access package custom extension runs. The possible values are: `assignmentRequestCreated`, `assignmentRequestApproved`, `assignmentRequestGranted`, `assignmentRequestRemoved`, `assignmentFourteenDaysBeforeExpiration`, `assignmentOneDayBeforeExpiration`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0) | Indicates the custom workflow extension that will be executed at this stage. Nullable. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionStageSetting",
  "id": "String (identifier)",
  "stage": "String"
}
```
