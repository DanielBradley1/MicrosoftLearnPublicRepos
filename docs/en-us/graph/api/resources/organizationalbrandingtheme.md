<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingtheme?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-01 -->

# organizationalBrandingTheme resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains details about the organization's branding themes.

You can create up to 5 branding themes to customize the sign-in pages that appear when users sign in to your organization's tenant-specific apps, or when Microsoft Entra External ID identifies the user's tenant from their username. The app can retrieve the branding theme information and customize the signed-in user's app experience to their company's branding. When this custom branding theme isn't available or linked to an app, the default tenant-level [organizationalBranding](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding?view=graph-rest-beta) settings apply.

You can't change your original Theme configuration's language. However, you can add different branding based on locale. For language-specific Theme branding, see the [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) object.

For more information about app-specific branding in External ID, see [Customize the sign-in experience for your application with branding themes \(Preview\)](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-themes-apps).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/organizationalbranding-list-themes?view=graph-rest-beta) | [organizationalBrandingTheme](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingtheme?view=graph-rest-beta) collection | Get a list of the organizationalBrandingTheme objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/organizationalbranding-post-themes?view=graph-rest-beta) | [organizationalBrandingTheme](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingtheme?view=graph-rest-beta) | Create a new organizationalBrandingTheme object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/organizationalbrandingtheme-get?view=graph-rest-beta) | [organizationalBrandingTheme](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingtheme?view=graph-rest-beta) | Read the properties and relationships of [organizationalBrandingTheme](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingtheme?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/organizationalbrandingtheme-update?view=graph-rest-beta) | [organizationalBrandingTheme](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingtheme?view=graph-rest-beta) | Update the properties of an organizationalBrandingTheme object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/organizationalbranding-delete-themes?view=graph-rest-beta) | None | Delete an organizationalBrandingTheme object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | An identifier that represents the theme created using custom names. Required. |
| isDefaultTheme | Boolean | Indicates whether the theme is set as the default branding theme for the entire tenant and includes all applications within the tenant. When set to `true`, this theme is automatically applied to any application that does not have a specific theme assigned. This property is useful for enforcing consistent branding across multiple apps without configuring each one individually. Optional. |
| name | String | The name of the branding theme. Up to 120 characters. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| localizations | [organizationalBrandingThemeLocalization](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingthemelocalization?view=graph-rest-beta) collection | Represents a locale-based branding theme. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.organizationalBrandingTheme",
  "id": "String (identifier)",
  "name": "String",
  "isDefaultTheme": "Boolean"
}
```
