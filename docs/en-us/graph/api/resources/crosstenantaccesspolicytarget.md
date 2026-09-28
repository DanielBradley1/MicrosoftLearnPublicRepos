<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# crossTenantAccessPolicyTarget resource type

Namespace: microsoft.graph

Defines how to target your cross-tenant access policy settings. Settings can be targeted to specific users, groups, or applications. You can also use keywords to target specific groups or applications.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| target | String | Defines the target for cross-tenant access policy settings and can have one of the following values:<br><br><li> The unique identifier of the user, group, or application </li><br><br><li> <code>AllUsers</code> </li><br><br><li> <code>AllApplications</code> - Refers to any <a href="https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#microsoft-cloud-applications" data-linktype="absolute-path">Microsoft cloud application</a>. </li><br><br><li> <code>Office365</code> - Includes the applications mentioned as part of the <a href="https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365" data-linktype="absolute-path">Office 365</a> suite.</li> |
| targetType | crossTenantAccessPolicyTargetType | The type of resource that you want to target. The possible values are: `user`, `group`, `application`, `unknownFutureValue`. |

### Reserved values for targets that are applications

When setting application targets, you can also use the following reserved values:

| Symbol | Description |
| :--- | :--- |
| AllMicrosoftApps | Refers to any [Microsoft cloud application](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#microsoft-cloud-applications). |
| Office365 | Includes the applications mentioned as part of the [Office365](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365) suite. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyTarget",
  "target": "String",
  "targetType": "microsoft.graph.crossTenantAccessPolicyTargetType"
}
```
