<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalueconstraint -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackagePolicyValueConstraint resource type

This reference describes only the proposed beta contract. Select **beta** to view it; availability requires the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Trusted constraints for one configurable [copilotPackagePolicyChoiceDefinition](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicychoicedefinition). Select a matching derived [copilotPackagePolicyValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue); arbitrary JSON or type coercion isn't supported.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `allowedValues` | [copilotPackagePolicyValue](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyvalue) collection | Non-nullable. Complete active allowed scalar values of `dataType`. Only scalar derived types occur here, even for collection-valued choices. Source failure doesn't produce an empty collection. |
| `dataType` | copilotPackagePolicyValueDataType | Non-nullable. Accepted scalar type; unknown types don't authorize writes. |
| `isCollection` | Boolean | Non-nullable. Whether the selected value is a collection of the scalar type. Boolean collections aren't supported. |
| `usePredefinedValuesOnly` | Boolean | Non-nullable. Whether every selected scalar or collection element must match an allowed value. It isn't inferred from whether `allowedValues` is empty. |

With `usePredefinedValuesOnly: true`, an empty allowed-value list permits no configured value. With false, values still must satisfy the trusted type and cardinality; false doesn't permit arbitrary JSON.

### copilotPackagePolicyValueDataType enumeration

| Value | Description |
| :--- | :--- |
| `boolean` | Boolean scalar. |
| `integer` | Signed 32-bit integer scalar, or collection when `isCollection` is true. |
| `string` | String scalar, or collection when `isCollection` is true. |
| `unknownFutureValue` | Reserved for enum evolution; not a supported configurable type. |

No undocumented unknown-enum preference-header behavior is implied.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackagePolicyValueConstraint",
  "allowedValues": [
    {
      "@odata.type": "microsoft.graph.copilotPackagePolicyValue"
    }
  ],
  "dataType": "String",
  "isCollection": "Boolean",
  "usePredefinedValuesOnly": "Boolean"
}
```
