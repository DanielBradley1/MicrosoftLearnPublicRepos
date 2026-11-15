<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-supported-resources -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# Supported Microsoft Entra resource policy resources and actions \(preview\)

A custom policy's `__metadata__.selector` identifies its target resource type or action and operations. Use supported targets rather than assuming that every Microsoft Graph endpoint participates in resource policy evaluation.

This reference lists policy targets, not the available built-in policies. Use the linked Microsoft Graph references to review resource properties, methods, request formats, and API versions.

## Resource types

Policies can target the following resource types. Resource selectors include supported derived types by default. Set `includeDerivedTypes` to `false` to target only the named type.

| Resource type | Resource |
| --- | --- |
| [`microsoft.graph.user`](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta&preserve-view=true) | Users. |
| [`microsoft.graph.group`](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta&preserve-view=true) | Groups. |
| [`microsoft.graph.application`](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta&preserve-view=true) | Application registrations. |
| [`microsoft.graph.federatedIdentityCredential`](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-beta&preserve-view=true) | Federated identity credentials. |
| [`microsoft.graph.servicePrincipal`](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta&preserve-view=true) | Service principals. |
| [`microsoft.graph.appRoleAssignment`](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-beta&preserve-view=true) | App role assignments. |
| [`microsoft.graph.oAuth2PermissionGrant`](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-beta&preserve-view=true) | Delegated permission grants. |
| [`microsoft.graph.administrativeUnit`](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-beta&preserve-view=true) | Administrative units. |
| [`microsoft.graph.scopedRoleMembership`](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-beta&preserve-view=true) | Scoped role memberships. |
| [`microsoft.graph.device`](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta&preserve-view=true) | Devices. |
| [`microsoft.graph.directoryRole`](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-beta&preserve-view=true) | Directory roles. |
| [`microsoft.graph.unifiedRoleDefinition`](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta&preserve-view=true) | Unified role definitions. |
| [`microsoft.graph.unifiedRoleAssignment`](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta&preserve-view=true) | Unified role assignments. |
| [`microsoft.graph.invitation`](https://learn.microsoft.com/en-us/graph/api/resources/invitation?view=graph-rest-beta&preserve-view=true) | Invitations. |
| [`microsoft.graph.authorizationPolicy`](https://learn.microsoft.com/en-us/graph/api/resources/authorizationpolicy?view=graph-rest-beta&preserve-view=true) | Authorization policies. |
| [`microsoft.graph.crossTenantAccessPolicy`](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy?view=graph-rest-beta&preserve-view=true) | Cross-tenant access policies. |
| [`microsoft.graph.crossTenantAccessPolicyConfigurationDefault`](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-beta&preserve-view=true) | Cross-tenant access default configurations. |
| [`microsoft.graph.crossTenantAccessPolicyConfigurationPartner`](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-beta&preserve-view=true) | Cross-tenant access partner configurations. |
| [`microsoft.graph.crossTenantIdentitySyncPolicyPartner`](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantidentitysyncpolicypartner?view=graph-rest-beta&preserve-view=true) | Cross-tenant identity synchronization partner policies. |
| [`microsoft.graph.conditionalAccessPolicy`](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-beta&preserve-view=true) | Conditional Access policies. |
| [`microsoft.graph.countryNamedLocation`](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-beta&preserve-view=true) | Country/region named locations. |
| [`microsoft.graph.ipNamedLocation`](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation?view=graph-rest-beta&preserve-view=true) | IP named locations. |
| [`microsoft.graph.privilegedAccessGroupAssignmentScheduleRequest`](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-beta&preserve-view=true) | Privileged access group assignment schedule requests. |
| [`microsoft.graph.privilegedAccessGroupEligibilityScheduleRequest`](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-beta&preserve-view=true) | Privileged access group eligibility schedule requests. |
| [`microsoft.graph.agentUser`](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-beta&preserve-view=true) | Agent users. |
| [`microsoft.graph.agentIdentity`](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-beta&preserve-view=true) | Agent identities. |
| [`microsoft.graph.agentIdentityBlueprint`](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-beta&preserve-view=true) | Agent identity blueprints. |
| [`microsoft.graph.agentIdentityBlueprintPrincipal`](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-beta&preserve-view=true) | Agent identity blueprint principals. |

## Actions

Specify an action target as the binding type followed by its fully qualified action name.

| Target | Binding types |
| --- | --- |
| [`microsoft.graph.addPassword`](https://learn.microsoft.com/en-us/graph/api/application-addpassword?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.application`](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.addPassword`](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addpassword?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.servicePrincipal`](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.removePassword`](https://learn.microsoft.com/en-us/graph/api/application-removepassword?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.application`](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.removePassword`](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-removepassword?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.servicePrincipal`](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.addKey`](https://learn.microsoft.com/en-us/graph/api/application-addkey?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.application`](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.addKey`](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addkey?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.servicePrincipal`](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.removeKey`](https://learn.microsoft.com/en-us/graph/api/application-removekey?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.application`](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.removeKey`](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-removekey?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.servicePrincipal`](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.addTokenSigningCertificate`](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addtokensigningcertificate?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.servicePrincipal`](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.assignLicense`](https://learn.microsoft.com/en-us/graph/api/user-assignlicense?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.user`](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.assignLicense`](https://learn.microsoft.com/en-us/graph/api/group-assignlicense?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.group`](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta&preserve-view=true). |
| [`microsoft.graph.instantiate`](https://learn.microsoft.com/en-us/graph/api/applicationtemplate-instantiate?view=graph-rest-beta&preserve-view=true) | [`microsoft.graph.applicationTemplate`](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-beta&preserve-view=true). |

For example, the application key action uses the target [`microsoft.graph.application/microsoft.graph.addKey`](https://learn.microsoft.com/en-us/graph/api/application-addkey?view=graph-rest-beta&preserve-view=true).

Action selectors use the operation `invokeAction` and omit `includeDerivedTypes`.

## Operations

The policy contract uses `create`, `updateOrUpsert`, `delete`, and `invokeAction`. Listing a resource type doesn't establish that every operation or endpoint shape for that type is supported.

Use explicit operation metadata and test the intended request shape, including alternate keys, reference requests, or partial updates where relevant.

## Related content

- [Author resource policies with Rego](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-rego).
- [Test and troubleshoot a resource policy](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-test-troubleshoot).
- [Resource policy service limits](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/resource-policy-service-limits).
