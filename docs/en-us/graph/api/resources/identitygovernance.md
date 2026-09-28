<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# identityGovernance resource type

Namespace: microsoft.graph

The identity governance singleton is the container for the following Microsoft Entra ID Governance features that are exposed through the following resources and APIs:

- [Access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0)
- [Entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0)
- [App consent](https://learn.microsoft.com/en-us/graph/api/resources/consentrequests-overview?view=graph-rest-1.0)
- [Lifecycle Workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-overview?view=graph-rest-1.0)
- [Terms of use](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0)

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessReviews | [accessReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewset?view=graph-rest-1.0) | Container for the base resources that expose the access reviews API and features. |
| appConsent | [appConsent](https://learn.microsoft.com/en-us/graph/api/resources/appconsentapprovalroute?view=graph-rest-1.0) | Container for base resources that expose the app consent request API and features. Currently exposes only the [appConsentRequests](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) resource. |
| entitlementManagement | [entitlementManagement](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement?view=graph-rest-1.0) | Container for entitlement management resources, including [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0), [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0), and [entitlementManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementsettings?view=graph-rest-1.0). |
| termsOfUse | [termsOfUseContainer](https://learn.microsoft.com/en-us/graph/api/resources/termsofusecontainer?view=graph-rest-1.0) | Container for the resources that expose the terms of use API and its features, including [agreements](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) and [agreementAcceptances](https://learn.microsoft.com/en-us/graph/api/resources/agreementacceptance?view=graph-rest-1.0). |
| lifecycleWorkflows | [microsoft.graph.identityGovernance.lifecycleWorkflowsContainer](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflowscontainer?view=graph-rest-1.0) | Container for Lifecycle Workflow resources, including [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0), [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0), and [lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0). |
| privilegedAccess | [privilegedAccessRoot](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessroot?view=graph-rest-1.0) | Container for the base resources that expose the API and features related to Privileged Identity Management \(PIM\) for Groups. |
