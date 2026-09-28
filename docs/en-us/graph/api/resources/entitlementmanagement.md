<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# entitlementManagement resource type

Namespace: microsoft.graph

The entitlement management singleton is the container for entitlement management resources, including [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0), [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0), and [entitlementManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementsettings?view=graph-rest-1.0). For a full list of resources, see [entitlement management overview](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | This value indicates the resource is a singleton. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackageAssignmentApprovals | [approval](https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-1.0) collection | Approval stages for decisions associated with access package assignment requests. |
| accessPackages | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) collection | Access packages define the collection of resource roles and the policies for which subjects can request or be assigned access to those resources. |
| accessPackageSuggestions | [accessPackageSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0) collection | Suggested access packages for end users based on various criteria such as related people insights and assignment history. |
| availableAccessPackages | [availableAccessPackage](https://learn.microsoft.com/en-us/graph/api/resources/availableaccesspackage?view=graph-rest-1.0) collection | Access packages available for end users to browse and request. |
| assignmentPolicies | [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) collection | Access package assignment policies govern which subjects can request or be assigned an access package via an access package assignment. |
| assignmentRequests | [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) collection | Access package assignment requests created by or on behalf of a subject. |
| assignments | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) collection | The assignment of an access package to a subject for a period of time. |
| catalogs | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) collection | A container for access packages. |
| connectedOrganizations | [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) collection | References to a directory or domain of another organization whose users can request access. |
| controlConfigurations | [controlConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-1.0) collection | Configuration settings that control the lifecycle and access policies of entitlement management within a tenant. |
| externalOriginResourceConnectors | [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) collection | Represents the connectors used to communicate with external resource systems. |
| resourceEnvironments | [accessPackageResourceEnvironment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceenvironment?view=graph-rest-1.0) collection | A reference to the geolocation environments in which a resource is located. |
| resourceRequests | [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-1.0) collection | Represents a request to add or remove a resource to or from a catalog respectively. |
| resources | [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) collection | The resources associated with the catalogs. |
| settings | [entitlementManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementsettings?view=graph-rest-1.0) | The settings that control the behavior of Microsoft Entra entitlement management. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entitlementManagement",
  "id": "String (identifier)"
}
```
