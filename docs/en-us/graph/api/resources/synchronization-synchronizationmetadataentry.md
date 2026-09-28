<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationmetadataentry?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationMetadataEntry resource type

Namespace: microsoft.graph

Metadata for the given object. This object is configured in the **metadata** property of [synchronizationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | synchronizationMetadata | The possible values are: `GalleryApplicationIdentifier`, `GalleryApplicationKey`, `IsOAuthEnabled`, `IsSynchronizationAgentAssignmentRequired`, `IsSynchronizationAgentRequired`, `IsSynchronizationInPreview`, `OAuthSettings`, `SynchronizationLearnMoreIbizaFwLink`, `ConfigurationFields`. |
| value | String | Value of the metadata property. |

### Supported key-value pairs

| Key | Value |
| :--- | :--- |
| GalleryApplicationIdentifier | The GUID that represents this enterprise application in Microsoft Entra ID. |
| GalleryApplicationKey | The name that represents this enterprise application in Microsoft Entra ID \(same value as the factoryTag attribute within the synchronizationTemplate resource type\). |
| IsOAuthEnabled | Indicates whether OAuth is enabled for this synchronization job's application. |
| IsSynchronizationAgentAssignmentRequired | Indicates whether to display certain UI elements applicable only during synchronization that requires an on-premises agent. |
| IsSynchronizationAgentRequired | Indicates whether an on-premises synchronization agent is required for this synchronization job. |
| IsSynchronizationInPreview | Indicates whether provisioning for this enterprise application is generally available. |
| OAuthSettings | A JSON containing values necessary for OAuth authentication, such as the token exchange URI and client identifier. |
| SynchronizationLearnMoreIbizaFwLink | The documentation link that's displayed in the Microsoft Entra admin center. |
| ConfigurationFields | A JSON containing the textbox configuration names that are displayed in the Microsoft Entra admin center. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.synchronizationMetadataEntry",
  "key": "String",
  "value": "String"
}
```
