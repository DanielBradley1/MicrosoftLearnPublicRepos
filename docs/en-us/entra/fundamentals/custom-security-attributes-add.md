<!-- Source: https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-add -->
<!-- Sitemap-Last-Modified: 2025-05-30 -->

# Add or deactivate custom security attribute definitions in Microsoft Entra ID

[Custom security attributes](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-overview) in Microsoft Entra ID are business-specific attributes \(key-value pairs\) that you can define and assign to Microsoft Entra objects. This article describes how to add, edit, or deactivate custom security attribute definitions.

## Prerequisites

To add or deactivate custom security attributes definitions, you must have:

- [Attribute Definition Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-definition-administrator)
- Microsoft.Graph module when using [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation)

Important

By default, [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) and other administrator roles do not have permissions to read, define, or assign custom security attributes.

## Add an attribute set

An attribute set is a collection of related attributes. All custom security attributes must be part of an attribute set. Attribute sets cannot be renamed or deleted.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Attribute Definition Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-definition-administrator).
2. Browse to **Entra ID** > **Custom security attributes**.
3. Select **Add attribute set** to add a new attribute set.

   If Add attribute set is disabled, make sure you are assigned the Attribute Definition Administrator role. For more information, see [Troubleshoot custom security attributes](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-troubleshoot).
4. Enter a name, description, and maximum number of attributes.

   An attribute set name can be 32 characters with no spaces or special characters. Once you've specified a name, you can't rename it. For more information, see [Limits and constraints](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-overview#limits-and-constraints).

   [![Screenshot of New attribute set pane in Microsoft Entra admin center.](https://learn.microsoft.com/en-us/entra/fundamentals/media/custom-security-attributes-add/attribute-set-add.png)](https://learn.microsoft.com/en-us/entra/fundamentals/media/custom-security-attributes-add/attribute-set-add.png#lightbox)
5. When finished, select **Add**.

   The new attribute set appears in the list of attribute sets.

## Add a custom security attribute definition

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Attribute Definition Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-definition-administrator).
2. Browse to **Entra ID** > **Custom security attributes**.
3. On the Custom security attributes page, find an existing attribute set or select **Add attribute set** to add a new attribute set.

   All custom security attribute definitions must be part of an attribute set.
4. Select to open the selected attribute set.
5. Select **Add attribute** to add a new custom security attribute to the attribute set.

   [![Screenshot of New attribute pane in Microsoft Entra admin center.](https://learn.microsoft.com/en-us/entra/fundamentals/media/custom-security-attributes-add/attribute-new.png)](https://learn.microsoft.com/en-us/entra/fundamentals/media/custom-security-attributes-add/attribute-new.png#lightbox)
6. In the **Attribute name** box, enter a custom security attribute name.

   A custom security attribute name can be 32 characters with no spaces or special characters. Once you've specified a name, you can't rename it. For more information, see [Limits and constraints](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-overview#limits-and-constraints).
7. In the **Description** box, enter an optional description.

   A description can be 128 characters long. If necessary, you can later change the description.
8. From the **Data type** list, select the data type for the custom security attribute.
   | Data type | Description |
   | --- | --- |
   | Boolean | A Boolean value that can be true, True, false, or False. |
   | Integer | A 32-bit integer. |
   | String | A string that can be X characters long. |
9. For **Allow multiple values to be assigned**, select **Yes** or **No**.

   Select **Yes** to allow multiple values to be assigned to this custom security attribute. Select **No** to only allow a single value to be assigned to this custom security attribute.
10. For **Only allow predefined values to be assigned**, select **Yes** or **No**.

    Select **Yes** to require that this custom security attribute be assigned values from a predefined values list. Select **No** to allow this custom security attribute to be assigned user-defined values or potentially predefined values.
11. If **Only allow predefined values to be assigned** is **Yes**, select **Add value** to add predefined values.

    An active value is available for assignment to objects. A value that is not active is defined, but not yet available for assignment.

    [![Screenshot of New attribute pane with Add predefined value pane in Microsoft Entra admin center.](https://learn.microsoft.com/en-us/entra/fundamentals/media/custom-security-attributes-add/attribute-new-value-add.png)](https://learn.microsoft.com/en-us/entra/fundamentals/media/custom-security-attributes-add/attribute-new-value-add.png#lightbox)
12. When finished, select **Save**.

    The new custom security attribute appears in the list of custom security attributes.
13. If you want to include predefined values, follow the steps in the next section.

## Edit a custom security attribute definition

Once you add a new custom security attribute definition, you can later edit some of the properties. Some properties are immutable and cannot be changed.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Attribute Definition Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-definition-administrator).
2. Browse to **Entra ID** > **Custom security attributes**.
3. Select the attribute set that includes the custom security attribute you want to edit.
4. In the list of custom security attributes, select the ellipsis for the custom security attribute you want to edit, and then select **Edit attribute**.
5. Edit the properties that are enabled.
6. If **Only allow predefined values to be assigned** is **Yes**, select **Add value** to add predefined values. Select an existing predefined value to change the **Is active?** setting.

   [![Screenshot of Add predefined value pane in Microsoft Entra admin center.](https://learn.microsoft.com/en-us/entra/fundamentals/media/custom-security-attributes-add/attribute-predefined-value-add.png)](https://learn.microsoft.com/en-us/entra/fundamentals/media/custom-security-attributes-add/attribute-predefined-value-add.png#lightbox)

## Deactivate a custom security attribute definition

Once you add a custom security attribute definition, you can't delete it. However, you can deactivate a custom security attribute definition.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Attribute Definition Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-definition-administrator).
2. Browse to **Entra ID** > **Custom security attributes**.
3. Select the attribute set that includes the custom security attribute you want to deactivate.
4. In the list of custom security attributes, add a check mark next to the custom security attribute you want to deactivate.
5. Select **Deactivate attribute**.
6. In the Deactivate attribute dialog that appears, select **Yes**.

   The custom security attribute is deactivated and moved to the Deactivated attributes list.

## PowerShell or Microsoft Graph API

To manage custom security attribute definitions in your Microsoft Entra organization, you can also use PowerShell or Microsoft Graph API. The following examples manage attribute sets and custom security attribute definitions.

#### Get all attribute sets

The following example gets all attribute sets.

- [Microsoft Graph PowerShell](#tabpanel_1_ms-powershell)
- [Microsoft Graph](#tabpanel_1_ms-graph)

[Get-MgDirectoryAttributeSet](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectoryattributeset)

```powershell
Get-MgDirectoryAttributeSet | Format-List
```

```output
Description          : Attributes for engineering team
Id                   : Engineering
MaxAttributesPerSet  : 25
AdditionalProperties : {}

Description          : Attributes for marketing team
Id                   : Marketing
MaxAttributesPerSet  : 25
AdditionalProperties : {}
```

[List attributeSets](https://learn.microsoft.com/en-us/graph/api/directory-list-attributesets)

```http
GET https://graph.microsoft.com/v1.0/directory/attributeSets
```

#### Get top attribute sets

The following example gets the top attribute sets.

- [Microsoft Graph PowerShell](#tabpanel_2_ms-powershell)
- [Microsoft Graph](#tabpanel_2_ms-graph)

[Get-MgDirectoryAttributeSet](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectoryattributeset)

```powershell
Get-MgDirectoryAttributeSet -Top 10
```

[List attributeSets](https://learn.microsoft.com/en-us/graph/api/directory-list-attributesets)

```http
GET https://graph.microsoft.com/v1.0/directory/attributeSets?$top=10
```

#### Get attribute sets in order

The following example gets attribute sets in order.

- [Microsoft Graph PowerShell](#tabpanel_3_ms-powershell)
- [Microsoft Graph](#tabpanel_3_ms-graph)

[Get-MgDirectoryAttributeSet](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectoryattributeset)

```powershell
Get-MgDirectoryAttributeSet -Sort "Id"
```

[List attributeSets](https://learn.microsoft.com/en-us/graph/api/directory-list-attributesets)

```http
GET https://graph.microsoft.com/v1.0/directory/attributeSets?$orderBy=id
```

#### Get an attribute set

The following example gets an attribute set.

- Attribute set: `Engineering`

- [Microsoft Graph PowerShell](#tabpanel_4_ms-powershell)
- [Microsoft Graph](#tabpanel_4_ms-graph)

[Get-MgDirectoryAttributeSet](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectoryattributeset)

```powershell
Get-MgDirectoryAttributeSet -AttributeSetId "Engineering" | Format-List
```

```output
Description          : Attributes for engineering team
Id                   : Engineering
MaxAttributesPerSet  : 25
AdditionalProperties : {[@odata.context, https://graph.microsoft.com/v1.0/$metadata#directory/attributeSets/$entity]}
```

[Get attributeSet](https://learn.microsoft.com/en-us/graph/api/attributeset-get)

```http
GET https://graph.microsoft.com/v1.0/directory/attributeSets/Engineering
```

#### Add an attribute set

The following example adds a new attribute set.

- Attribute set: `Engineering`

- [Microsoft Graph PowerShell](#tabpanel_5_ms-powershell)
- [Microsoft Graph](#tabpanel_5_ms-graph)

[New-MgDirectoryAttributeSet](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/new-mgdirectoryattributeset)

```powershell
$params = @{
    Id = "Engineering"
    Description = "Attributes for engineering team"
    MaxAttributesPerSet = 25
}
New-MgDirectoryAttributeSet -BodyParameter $params
```

```output
Id          Description                     MaxAttributesPerSet
--          -----------                     -------------------
Engineering Attributes for engineering team 25
```

[Create attributeSet](https://learn.microsoft.com/en-us/graph/api/directory-post-attributesets)

```http
POST https://graph.microsoft.com/v1.0/directory/attributeSets 
{
    "id":"Engineering",
    "description":"Attributes for engineering team",
    "maxAttributesPerSet":25
}
```

#### Update an attribute set

The following example updates an attribute set.

- Attribute set: `Engineering`

- [Microsoft Graph PowerShell](#tabpanel_6_ms-powershell)
- [Microsoft Graph](#tabpanel_6_ms-graph)

[Update-MgDirectoryAttributeSet](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/update-mgdirectoryattributeset)

```powershell
$params = @{
    description = "Attributes for engineering team"
    maxAttributesPerSet = 20
}
Update-MgDirectoryAttributeSet -AttributeSetId "Engineering" -BodyParameter $params
```

[Update attributeSet](https://learn.microsoft.com/en-us/graph/api/attributeset-update)

```http
PATCH https://graph.microsoft.com/v1.0/directory/attributeSets/Engineering
{
    "description":"Attributes for engineering team",
    "maxAttributesPerSet":20
}
```

#### Get all custom security attribute definitions

The following example gets all custom security attribute definitions.

- [Microsoft Graph PowerShell](#tabpanel_7_ms-powershell)
- [Microsoft Graph](#tabpanel_7_ms-graph)

[Get-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectorycustomsecurityattributedefinition)

```powershell
Get-MgDirectoryCustomSecurityAttributeDefinition | Format-List
```

```output
AllowedValues           :
AttributeSet            : Engineering
Description             : Target completion date
Id                      : Engineering_ProjectDate
IsCollection            : False
IsSearchable            : True
Name                    : ProjectDate
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : False
AdditionalProperties    : {}

AllowedValues           :
AttributeSet            : Engineering
Description             : Active projects for user
Id                      : Engineering_Project
IsCollection            : True
IsSearchable            : True
Name                    : Project
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : True
AdditionalProperties    : {}

AllowedValues           :
AttributeSet            : Marketing
Description             : Country where is application is used
Id                      : Marketing_AppCountry
IsCollection            : True
IsSearchable            : True
Name                    : AppCountry
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : True
AdditionalProperties    : {}
```

[List customSecurityAttributeDefinitions](https://learn.microsoft.com/en-us/graph/api/directory-list-customsecurityattributedefinitions)

```http
GET https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions
```

#### Filter custom security attribute definitions

The following examples filter custom security attribute definitions.

- Filter: Attribute name eq 'Project' and status eq 'Available'

- [Microsoft Graph PowerShell](#tabpanel_8_ms-powershell)
- [Microsoft Graph](#tabpanel_8_ms-graph)

[Get-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectorycustomsecurityattributedefinition)

```powershell
Get-MgDirectoryCustomSecurityAttributeDefinition -Filter "name eq 'Project' and status eq 'Available'" | Format-List
```

```output
AllowedValues           :
AttributeSet            : Engineering
Description             : Active projects for user
Id                      : Engineering_Project
IsCollection            : True
IsSearchable            : True
Name                    : Project
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : True
AdditionalProperties    : {}
```

[List customSecurityAttributeDefinitions](https://learn.microsoft.com/en-us/graph/api/directory-list-customsecurityattributedefinitions)

```http
GET https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions?$filter=name+eq+'Project'%20and%20status+eq+'Available'
```

- Filter: Attribute set eq 'Engineering' and status eq 'Available' and data type eq 'String'

- [Microsoft Graph PowerShell](#tabpanel_9_ms-powershell)
- [Microsoft Graph](#tabpanel_9_ms-graph)

[Get-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectorycustomsecurityattributedefinition)

```powershell
Get-MgDirectoryCustomSecurityAttributeDefinition -Filter "attributeSet eq 'Engineering' and status eq 'Available' and type eq 'String'" | Format-List
```

```output
AllowedValues           :
AttributeSet            : Engineering
Description             : Target completion date
Id                      : Engineering_ProjectDate
IsCollection            : False
IsSearchable            : True
Name                    : ProjectDate
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : False
AdditionalProperties    : {}

AllowedValues           :
AttributeSet            : Engineering
Description             : Active projects for user
Id                      : Engineering_Project
IsCollection            : True
IsSearchable            : True
Name                    : Project
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : True
AdditionalProperties    : {}
```

[List customSecurityAttributeDefinitions](https://learn.microsoft.com/en-us/graph/api/directory-list-customsecurityattributedefinitions)

```http
GET https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions?$filter=attributeSet+eq+'Engineering'%20and%20status+eq+'Available'%20and%20type+eq+'String'
```

#### Get a custom security attribute definition

The following example gets a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`

- [Microsoft Graph PowerShell](#tabpanel_10_ms-powershell)
- [Microsoft Graph](#tabpanel_10_ms-graph)

[Get-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectorycustomsecurityattributedefinition)

```powershell
Get-MgDirectoryCustomSecurityAttributeDefinition -CustomSecurityAttributeDefinitionId "Engineering_ProjectDate" | Format-List
```

```output
AllowedValues           :
AttributeSet            : Engineering
Description             : Target completion date
Id                      : Engineering_ProjectDate
IsCollection            : False
IsSearchable            : True
Name                    : ProjectDate
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : False
AdditionalProperties    : {[@odata.context, https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions/$entity]}
```

[Get customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-get)

```http
GET https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_ProjectDate
```

#### Add a custom security attribute definition

The following example adds a new custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`
- Attribute data type: String

- [Microsoft Graph PowerShell](#tabpanel_11_ms-powershell)
- [Microsoft Graph](#tabpanel_11_ms-graph)

[New-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/new-mgdirectorycustomsecurityattributedefinition)

```powershell
$params = @{
    attributeSet = "Engineering"
    description = "Target completion date"
    isCollection = $false
    isSearchable = $true
    name = "ProjectDate"
    status = "Available"
    type = "String"
    usePreDefinedValuesOnly = $false
}
New-MgDirectoryCustomSecurityAttributeDefinition -BodyParameter $params | Format-List
```

```output
AllowedValues           :
AttributeSet            : Engineering
Description             : Target completion date
Id                      : Engineering_ProjectDate
IsCollection            : False
IsSearchable            : True
Name                    : ProjectDate
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : False
AdditionalProperties    : {[@odata.context, https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions/$entity]}
```

[Create customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/directory-post-customsecurityattributedefinitions)

```http
POST https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions
{
    "attributeSet":"Engineering",
    "description":"Target completion date",
    "isCollection":false,
    "isSearchable":true,
    "name":"ProjectDate",
    "status":"Available",
    "type":"String",
    "usePreDefinedValuesOnly": false
}
```

#### Add a custom security attribute definition that supports multiple predefined values

The following example adds a new custom security attribute definition that supports multiple predefined values.

- Attribute set: `Engineering`
- Attribute: `Project`
- Attribute data type: Collection of Strings

- [Microsoft Graph PowerShell](#tabpanel_12_ms-powershell)
- [Microsoft Graph](#tabpanel_12_ms-graph)

[New-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/new-mgdirectorycustomsecurityattributedefinition)

```powershell
$params = @{
    attributeSet = "Engineering"
    description = "Active projects for user"
    isCollection = $true
    isSearchable = $true
    name = "Project"
    status = "Available"
    type = "String"
    usePreDefinedValuesOnly = $true
}
New-MgDirectoryCustomSecurityAttributeDefinition -BodyParameter $params | Format-List
```

```output
AllowedValues           :
AttributeSet            : Engineering
Description             : Active projects for user
Id                      : Engineering_Project
IsCollection            : True
IsSearchable            : True
Name                    : Project
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : True
AdditionalProperties    : {[@odata.context, https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions/$entity]}
```

[Create customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/directory-post-customsecurityattributedefinitions)

```http
POST https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions
{
    "attributeSet":"Engineering",
    "description":"Active projects for user",
    "isCollection":true,
    "isSearchable":true,
    "name":"Project",
    "status":"Available",
    "type":"String",
    "usePreDefinedValuesOnly": true
}
```

#### Add a custom security attribute definition with a list of predefined values

The following example adds a new custom security attribute definition with a list of predefined values.

- Attribute set: `Engineering`
- Attribute: `Project`
- Attribute data type: Collection of Strings
- Predefined values: `Alpine`, `Baker`, `Cascade`

- [Microsoft Graph PowerShell](#tabpanel_13_ms-powershell)
- [Microsoft Graph](#tabpanel_13_ms-graph)

[New-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/new-mgdirectorycustomsecurityattributedefinition)

```powershell
$params = @{
    attributeSet = "Engineering"
    description = "Active projects for user"
    isCollection = $true
    isSearchable = $true
    name = "Project"
    status = "Available"
    type = "String"
    usePreDefinedValuesOnly = $true
    allowedValues = @(
        @{
            id = "Alpine"
            isActive = $true
        }
        @{
            id = "Baker"
            isActive = $true
        }
        @{
            id = "Cascade"
            isActive = $true
        }
    )
}
New-MgDirectoryCustomSecurityAttributeDefinition -BodyParameter $params | Format-List
```

```output
AllowedValues           :
AttributeSet            : Engineering
Description             : Active projects for user
Id                      : Engineering_Project
IsCollection            : True
IsSearchable            : True
Name                    : Project
Status                  : Available
Type                    : String
UsePreDefinedValuesOnly : True
AdditionalProperties    : {[@odata.context, https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions/$entity]}
```

[Create customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/directory-post-customsecurityattributedefinitions)

```http
POST https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions
{
    "attributeSet": "Engineering",
    "description": "Active projects for user",
    "isCollection": true,
    "isSearchable": true,
    "name": "Project",
    "status": "Available",
    "type": "String",
    "usePreDefinedValuesOnly": true,
    "allowedValues": [
        {
            "id": "Alpine",
            "isActive": true
        },
        {
            "id": "Baker",
            "isActive": true
        },
        {
            "id": "Cascade",
            "isActive": true
        }
    ]
}
```

#### Update a custom security attribute definition

The following example updates a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`

- [Microsoft Graph PowerShell](#tabpanel_14_ms-powershell)
- [Microsoft Graph](#tabpanel_14_ms-graph)

[Update-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/update-mgdirectorycustomsecurityattributedefinition)

```powershell
$params = @{
    description = "Target completion date (YYYY/MM/DD)"
}
Update-MgDirectoryCustomSecurityAttributeDefinition -CustomSecurityAttributeDefinitionId "Engineering_ProjectDate" -BodyParameter $params
```

[Update customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-update)

```http
PATCH https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_ProjectDate
{
  "description": "Target completion date (YYYY/MM/DD)",
}
```

#### Update the predefined values for a custom security attribute definition

The following example updates the predefined values for a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `Project`
- Attribute data type: Collection of Strings
- Update predefined value: `Baker`
- New predefined value: `Skagit`

- [Microsoft Graph PowerShell](#tabpanel_15_ms-powershell)
- [Microsoft Graph](#tabpanel_15_ms-graph)

[Invoke-MgGraphRequest](https://learn.microsoft.com/en-us/powershell/microsoftgraph/authentication-commands#using-invoke-mggraphrequest)

Note

For this request, you must add the **OData-Version** header and assign it the value `4.01`.

```powershell
$params = @{
    "allowedValues@delta" = @(
        @{
            id = "Baker"
            isActive = $false
        }
        @{
            id = "Skagit"
            isActive = $true
        }
    )
}
$header = @{
    "OData-Version" = 4.01
}
Invoke-MgGraphRequest -Method PATCH -Uri "https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_Project5" -Headers $header -Body $params
```

[Update customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-update)

Note

For this request, you must add the **OData-Version** header and assign it the value `4.01`.

```http
PATCH https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_Project
{
    "allowedValues@delta": [
        {
            "id": "Baker",
            "isActive": false
        },
        {
            "id": "Skagit",
            "isActive": true
        }
    ]
}
```

#### Deactivate a custom security attribute definition

The following example deactivates a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `Project`

- [Microsoft Graph PowerShell](#tabpanel_16_ms-powershell)
- [Microsoft Graph](#tabpanel_16_ms-graph)

[Update-MgDirectoryCustomSecurityAttributeDefinition](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/update-mgdirectorycustomsecurityattributedefinition)

```powershell
$params = @{
    status = "Deprecated"
}
Update-MgDirectoryCustomSecurityAttributeDefinition -CustomSecurityAttributeDefinitionId "Engineering_ProjectDate" -BodyParameter $params
```

[Update customSecurityAttributeDefinition](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-update)

```http
PATCH https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_Project
{
  "status": "Deprecated"
}
```

#### Get all predefined values

The following example gets all predefined values for a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `Project`

- [Microsoft Graph PowerShell](#tabpanel_17_ms-powershell)
- [Microsoft Graph](#tabpanel_17_ms-graph)

[Get-MgDirectoryCustomSecurityAttributeDefinitionAllowedValue](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectorycustomsecurityattributedefinitionallowedvalue)

```powershell
Get-MgDirectoryCustomSecurityAttributeDefinitionAllowedValue -CustomSecurityAttributeDefinitionId "Engineering_Project" | Format-List
```

```output
Id                   : Skagit
IsActive             : True
AdditionalProperties : {}

Id                   : Baker
IsActive             : False
AdditionalProperties : {}

Id                   : Cascade
IsActive             : True
AdditionalProperties : {}

Id                   : Alpine
IsActive             : True
AdditionalProperties : {}
```

[List allowedValues](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-list-allowedvalues)

```http
GET https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_Project/allowedValues
```

#### Get a predefined value

The following example gets a predefined value for a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `Project`
- Predefined value: `Alpine`

- [Microsoft Graph PowerShell](#tabpanel_18_ms-powershell)
- [Microsoft Graph](#tabpanel_18_ms-graph)

[Get-MgDirectoryCustomSecurityAttributeDefinitionAllowedValue](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdirectorycustomsecurityattributedefinitionallowedvalue)

```powershell
Get-MgDirectoryCustomSecurityAttributeDefinitionAllowedValue -CustomSecurityAttributeDefinitionId "Engineering_Project" -AllowedValueId "Alpine" | Format-List
```

```output
Id                   : Alpine
IsActive             : True
AdditionalProperties : {[@odata.context, https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions('Engineering_Project')/al
                       lowedValues/$entity]}
```

[Get allowedValue](https://learn.microsoft.com/en-us/graph/api/allowedvalue-get)

```http
GET https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_Project/allowedValues/Alpine
```

#### Add a predefined value

The following example adds a predefined value for a custom security attribute definition.

You can add predefined values for custom security attributes that have `usePreDefinedValuesOnly` set to `true`.

- Attribute set: `Engineering`
- Attribute: `Project`
- Predefined value: `Alpine`

- [Microsoft Graph PowerShell](#tabpanel_19_ms-powershell)
- [Microsoft Graph](#tabpanel_19_ms-graph)

[New-MgDirectoryCustomSecurityAttributeDefinitionAllowedValue](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/new-mgdirectorycustomsecurityattributedefinitionallowedvalue)

```powershell
$params = @{
    id = "Alpine"
    isActive = $true
}
New-MgDirectoryCustomSecurityAttributeDefinitionAllowedValue -CustomSecurityAttributeDefinitionId "Engineering_Project" -BodyParameter $params | Format-List
```

```output
Id                   : Alpine
IsActive             : True
AdditionalProperties : {[@odata.context, https://graph.microsoft.com/v1.0/$metadata#directory/customSecurityAttributeDefinitions('Engineering_Project')/al
                       lowedValues/$entity]}
```

[Create allowedValue](https://learn.microsoft.com/en-us/graph/api/customsecurityattributedefinition-post-allowedvalues)

```http
POST https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_Project/allowedValues
{
    "id":"Alpine",
    "isActive":"true"
}
```

#### Deactivate a predefined value

The following example deactivates a predefined value for a custom security attribute definition.

- Attribute set: `Engineering`
- Attribute: `Project`
- Predefined value: `Alpine`

- [Microsoft Graph PowerShell](#tabpanel_20_ms-powershell)
- [Microsoft Graph](#tabpanel_20_ms-graph)

[Update-MgDirectoryCustomSecurityAttributeDefinitionAllowedValue](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/update-mgdirectorycustomsecurityattributedefinitionallowedvalue)

```powershell
$params = @{
    isActive = $false
}
Update-MgDirectoryCustomSecurityAttributeDefinitionAllowedValue -CustomSecurityAttributeDefinitionId "Engineering_Project" -AllowedValueId "Alpine" -BodyParameter $params
```

[Update allowedValue](https://learn.microsoft.com/en-us/graph/api/allowedvalue-update)

```http
PATCH https://graph.microsoft.com/v1.0/directory/customSecurityAttributeDefinitions/Engineering_Project/allowedValues/Alpine
{
    "isActive":"false"
}
```

## Frequently asked questions

**Can you delete custom security attribute definitions?**

No, you can't delete custom security attribute definitions. You can only [deactivate custom security attribute definitions](#deactivate-a-custom-security-attribute-definition). Once you deactivate a custom security attribute, it can no longer be applied to the Microsoft Entra objects. Custom security attribute assignments for the deactivated custom security attribute definition are not automatically removed. There is no limit to the number of deactivated custom security attributes. You can have 500 active custom security attribute definitions per tenant with 100 allowed predefined values per custom security attribute definition.

## Related content

- [Manage access to custom security attributes in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-manage)
- [Assign, update, list, or remove custom security attributes for a user](https://learn.microsoft.com/en-us/entra/identity/users/users-custom-security-attributes)
- [Assign, update, list, or remove custom security attributes for an application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/custom-security-attributes-apps)
