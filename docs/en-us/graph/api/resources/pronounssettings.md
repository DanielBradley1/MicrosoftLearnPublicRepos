<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/pronounssettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# pronounsSettings resource type

Namespace: microsoft.graph

Represents the settings that manage the support of pronouns in an organization. By default, pronouns are disabled. If enabled, users can optionally add or update their pronouns.

For more information about enabling pronouns support, see [Manage pronouns settings for an organization using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/pronouns-configure-pronouns-availability).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-pronouns?view=graph-rest-1.0) | [pronounsSettings](https://learn.microsoft.com/en-us/graph/api/resources/pronounssettings?view=graph-rest-1.0) | Get the properties of the [pronounsSettings](https://learn.microsoft.com/en-us/graph/api/resources/pronounssettings?view=graph-rest-1.0) resource for an organization. |
| [Update](https://learn.microsoft.com/en-us/graph/api/pronounssettings-update?view=graph-rest-1.0) | [pronounsSettings](https://learn.microsoft.com/en-us/graph/api/resources/pronounssettings?view=graph-rest-1.0) | Update the properties of a [pronounsSettings](https://learn.microsoft.com/en-us/graph/api/resources/pronounssettings?view=graph-rest-1.0) object in an organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabledInOrganization | Boolean | `true` to enable pronouns in the organization; otherwise, `false`. The default value is `false`, and pronouns are disabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isEnabledInOrganization": "Boolean"
}
```
