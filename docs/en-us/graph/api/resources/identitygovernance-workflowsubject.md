<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# workflowSubject resource type

Namespace: microsoft.graph.identityGovernance

Represents an abstract base type for subjects that can be activated in identity governance lifecycle workflows. The derived types of this object are configured in the following resources:

- **subject** property of [awaitedWorkflowProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-awaitedworkflowprocessingresult?view=graph-rest-1.0)
- **subject** property of [subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-1.0)
- **workflowSubject** property of [taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0)
- **targetSubject** property of [customTaskExtensionCallbackData](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackdata?view=graph-rest-1.0)
- **targetSubject** property of [customTaskExtensionCalloutData](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncalloutdata?view=graph-rest-1.0)
- **targetSubject** property of [customTaskExtensionResponseData](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensionresponsedata?view=graph-rest-1.0)

This is an abstract type. It cannot be instantiated directly. Use one of the following derived types:

- [directoryObjectWorkflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-directoryobjectworkflowsubject?view=graph-rest-1.0) to represent an existing directory object, such as a user, as the workflow subject.
- [provisioningObjectWorkflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-provisioningobjectworkflowsubject?view=graph-rest-1.0) to represent a provisioning object as the workflow subject.

Instances of these derived types are differentiated by the `@odata.type` property.

## Methods

None.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflowSubject"
}
```
