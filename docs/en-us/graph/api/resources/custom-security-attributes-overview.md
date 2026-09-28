<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/custom-security-attributes-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Overview of custom security attributes using the Microsoft Graph API

[Custom security attributes](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/custom-security-attributes-overview) in Microsoft Entra ID are business-specific attributes \(key-value pairs\) that you can define and assign to Microsoft Entra objects. You can use these attributes to store information, categorize objects, or enforce fine-grained access control over specific Azure resources. Custom security attributes can be used with [Azure attribute-based access control \(Azure ABAC\)](https://learn.microsoft.com/en-us/azure/role-based-access-control/conditions-overview).

This article provides an overview of how to use the Microsoft Graph API to programmatically define and assign your own custom security attributes.

## Key resource types

The following are the building blocks of custom security attributes.

### Attribute sets

An *attribute set* is a group of related custom security attributes. The following are the general characteristics of attribute sets:

- Name can't include spaces or special characters.
- Can't be renamed or deleted.
- Can be delegated to other users to define and assign custom security attributes.

To configure attribute sets, use the [attributeSet resource type](https://learn.microsoft.com/en-us/graph/api/resources/attributeset?view=graph-rest-1.0).

### Custom security attribute definitions

A *custom security attribute definition* is the schema of a custom security attribute or key-value pair. For example, the custom security attribute name, description, data type, and predefined values. The following are the general characteristics of custom security attributes definitions:

- Name can't include spaces or special characters.
- Can't be renamed or deleted, but can be deactivated.
- Must be part of an attribute set.

To configure custom security attribute definitions, use the [customSecurityAttributeDefinition resource type](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition?view=graph-rest-1.0).

### Allowed values

*Allowed values* represent the predefined values of a custom security attribute. The following are the general characteristics of allowed values:

- Values can include spaces, but some special characters are not allowed.
- Can't be renamed or deleted, but can be deactivated.
- More predefined values can be added later.
- Can be of Boolean, Integer, or String data types.

To configure allowed values, use the [allowedValue resource type](https://learn.microsoft.com/en-us/graph/api/resources/allowedvalue?view=graph-rest-1.0).

## Which directory objects support custom security attributes?

Custom security attributes can be assigned to the following objects by using the **customSecurityAttributes** property. Directory synced users from an on-premises Active Directory can also be assigned custom security attributes.

- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-v1.0&preserve-view=true)
- [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-v1.0&preserve-view=true)

For examples of custom security attribute assignments, see [Examples: Assign, update, list, or remove custom security attribute assignments using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/custom-security-attributes-examples).

## Limits and constraints

For a list of the limits and constraints for custom security attributes, see [Limits and constraints](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/custom-security-attributes-overview#limits-and-constraints).

## Permissions

To manage custom security attributes, the calling principal must be assigned one of the following Microsoft Entra roles. By default, Global Administrator and other administrator roles do not have permissions to read, define, or assign custom security attributes.

- [Attribute Definition Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-definition-reader)
- [Attribute Definition Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-definition-administrator)
- [Attribute Assignment Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-assignment-reader)
- [Attribute Assignment Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-assignment-administrator)

Also, the calling principal must be granted the appropriate [custom security attributes permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#custom-security-attributes-permissions).

## Next steps

- [customSecurityAttributeDefinition resource type](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributedefinition)
- [Examples: Assign, update, list, or remove custom security attribute assignments using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/custom-security-attributes-examples)
- [What are custom security attributes in Microsoft Entra ID?](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/custom-security-attributes-overview)
