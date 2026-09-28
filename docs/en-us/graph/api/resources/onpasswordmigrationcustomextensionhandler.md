<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpasswordmigrationcustomextensionhandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# onPasswordMigrationCustomExtensionHandler resource type

Namespace: microsoft.graph

Represents a handler that invokes a custom authentication extension API to validate user credentials against a legacy authentication system during the sign-in process. This handler enables Just-In-Time \(JIT\) migration scenarios where passwords can't be exported from the legacy system.

When triggered, this handler:

1. Checks if the user requires migration based on the specified **migrationPropertyI** custom attribute
2. If migration is needed, calls the configured custom extension API with the user's credentials
3. Upon successful validation, persists the credentials in Microsoft Entra ID and updates the migration status

Inherits from [onPasswordSubmitHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmithandler?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [customExtensionOverwriteConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionoverwriteconfiguration?view=graph-rest-1.0) | Configuration that overrides the default settings from the referenced custom extension, such as timeout and retry values. Optional. |
| migrationPropertyId | String | The name of the custom extension attribute that indicates whether a user requires migration. This property must reference a valid custom attribute on the user object \(for example, `extension_<appId>_requiresMigration`\). Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [onPasswordSubmitCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitcustomextension?view=graph-rest-1.0) | Reference to the custom authentication extension that will be invoked to validate the user's password against the legacy system. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPasswordMigrationCustomExtensionHandler",
  "configuration": {
    "@odata.type": "microsoft.graph.customExtensionOverwriteConfiguration"
  },
  "migrationPropertyId": "String"
}
```
