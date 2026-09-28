<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitybuiltinuserflowattribute?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-22 -->

# identityBuiltInUserFlowAttribute resource type

Namespace: microsoft.graph

Represents a built-in user flow attribute that can be used in self-service sign-up user flows in Microsoft Entra External ID in workforce and external tenants, and in Azure AD B2C tenants. These attributes can't be modified and are read-only.

Inherits from [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataType | identityUserFlowAttributeDataType | The data type of the user flow attribute, and can't be modified after the custom user flow attribute is created. The supported values for **dataType** are: `string` , `boolean` , `int64` , `stringCollection` , `dateTime`. Inherited from [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0). Read-only. |
| description | String | The description of the user flow attribute that's shown to the user at the time of sign up. Inherited from [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0). Read-only. |
| displayName | String | The display name of the user flow attribute. Inherited from [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0). Read-only. |
| id | String | The identifier of the user flow attribute. Read-only. Inherited from [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0) |
| userFlowAttributeType | identityUserFlowAttributeType | The type of the user flow attribute and is a read-only attribute that is automatically set. The value for this property is `builtIn`. Inherited from [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0). Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityBuiltInUserFlowAttribute",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "userFlowAttributeType": "String",
  "dataType": "String"
}
```
