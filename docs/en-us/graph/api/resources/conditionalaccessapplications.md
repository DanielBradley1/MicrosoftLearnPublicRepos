<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessapplications?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-24 -->

# conditionalAccessApplications resource type

Namespace: microsoft.graph

Represents the applications and user actions included in and excluded from the conditional access policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeApplications | String collection | Can be one of the following:<br><br><li> The list of client IDs (<strong>appId</strong>) explicitly excluded from the policy.</li><br><br><li> <code>Office365</code> - For the list of apps included in <code>Office365</code>, see <a href="https://learn.microsoft.com/en-us/entra/identity/conditional-access/reference-office-365-application-contents" data-linktype="absolute-path">Apps included in Conditional Access Office 365 app suite</a> </li><br><br><li> <code>MicrosoftAdminPortals</code> - For more information, see <a href="https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps#microsoft-admin-portals" data-linktype="absolute-path">Conditional Access Target resources: Microsoft Admin Portals</a></li> |
| includeApplications | String collection | Can be one of the following:<br><br><li> The list of client IDs (<strong>appId</strong>) the policy applies to, unless explicitly excluded (in <strong>excludeApplications</strong>) </li><br><br><li> <code>All</code> </li><br><br><li> <code>Office365</code> - For the list of apps included in <code>Office365</code>, see <a href="https://learn.microsoft.com/en-us/entra/identity/conditional-access/reference-office-365-application-contents" data-linktype="absolute-path">Apps included in Conditional Access Office 365 app suite</a> </li><br><br><li> <code>MicrosoftAdminPortals</code> - For more information, see <a href="https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps#microsoft-admin-portals" data-linktype="absolute-path">Conditional Access Target resources: Microsoft Admin Portals</a></li> |
| applicationFilter | [conditionalAccessFilter](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessfilter?view=graph-rest-1.0) | Filter that defines the dynamic-application-syntax rule to include/exclude cloud applications. A filter can use custom security attributes to include/exclude applications. |
| includeUserActions | String collection | User actions to include. Supported values are `urn:user:registersecurityinfo` and `urn:user:registerdevice` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "excludeApplications": ["String"],
  "includeApplications": ["String"],
  "applicationFilter": {"@odata.type": "microsoft.graph.conditionalAccessFilter"},
  "includeUserActions": ["String"]
}
```
