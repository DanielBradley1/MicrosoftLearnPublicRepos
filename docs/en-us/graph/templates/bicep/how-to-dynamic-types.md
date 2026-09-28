<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/how-to-dynamic-types -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Use dynamic types for Microsoft Graph Bicep resources

The Microsoft Graph Bicep extension supports dynamic types, which let you use semantic versioning for both Microsoft Graph beta and v1.0. Dynamic types let you use specific versions of Microsoft Graph Bicep resource types, so future breaking changes don't affect your existing Bicep files. When you use dynamic types, Bicep gets the required type version from the [Microsoft Artifact Registry](https://mcr.microsoft.com/). These type versions are independent of the Bicep compiler NuGet package.

You can configure dynamic types in two ways:

- Directly in your **main.bicep** file.
- By defining a user-friendly type version alias in the **bicepconfig.json** file and referencing it in **main.bicep**.

## Choose a type version

To use Microsoft Graph Bicep resource types, add a reference to the types repo in the Microsoft Artifact Registry. Go to the [Microsoft Artifact Registry](https://mcr.microsoft.com/) and search for "Microsoft Graph Bicep Extension" to find the latest or required version for Microsoft Graph beta and v1.0.

## Configure dynamic types in a Bicep file

In your **main.bicep** file, reference the Microsoft Graph Bicep types repo version you want. Replace `<v1.0-version>` with the Microsoft Graph v1.0 type version you want to use.

```Bicep
extension 'br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:<v1.0-version>'
```

You can also use types from both versions in the same file:

```Bicep
extension 'br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:<v1.0-version>'
extension 'br:mcr.microsoft.com/bicep/extensions/microsoftgraph/beta:<beta-version>'

// Use Microsoft Graph v1.0
resource group 'Microsoft.Graph/groups@v1.0' existing = {
    uniqueName: groupName
}

// Use Microsoft Graph beta
resource app 'Microsoft.Graph/applications@beta' existing = {
    uniqueName: appName
}
```

Declare resources using different type versions. To distinguish between types with the same name from different extensions, use a fully qualified type name:

```Bicep
extension 'br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:<v1.0-version-latest>' as latestGraphV1
extension 'br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:<v1.0-version-older>' as olderGraphV1

// Use the latest Microsoft Graph v1.0 Bicep types
resource group 'latestGraphV1:Microsoft.Graph/groups@v1.0' existing = {
    uniqueName: groupName
}

// Use an older Microsoft Graph v1.0 Bicep type version
resource app 'olderGraphV1:Microsoft.Graph/applications@v1.0' existing = {
    uniqueName: appName
}
```

## Configure dynamic types in the Bicep config

Define user-friendly aliases for Microsoft Graph Bicep type versions in **bicepconfig.json**. Replace `<v1.0-version>` and `<beta-version>` with the versions you want.

```json
{
    "extensions": {
        "graphV1": "br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:<v1.0-version>",
        "graphBeta": "br:mcr.microsoft.com/bicep/extensions/microsoftgraph/beta:<beta-version>"
    }
}
```

Next, use these aliases in your **main.bicep** file:

```Bicep
extension graphV1
extension graphBeta

// Use Microsoft Graph v1.0
resource group 'Microsoft.Graph/groups@v1.0' existing = {
    uniqueName: groupName
}

// Use Microsoft Graph beta
resource app 'Microsoft.Graph/applications@beta' existing = {
    uniqueName: appName
}
```

You can also define aliases for different type versions from the same Microsoft Graph version \(such as newer and older v1.0 types\) in **bicepconfig.json** and reference them in **main.bicep** using fully qualified type names.

For example, in **bicepconfig.json**:

```json
{
    "extensions": {
        "graphV1Latest": "br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:0.2.0-preview",
        "graphV1Older": "br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:0.1.8-preview"
    }
}
```

Next, in **main.bicep**:

```Bicep
extension graphV1Latest
extension graphV1Older

// Use the latest Microsoft Graph v1.0 Bicep types
resource group 'graphV1Latest:Microsoft.Graph/groups@v1.0' existing = {
    uniqueName: groupName
}

// Use an older Microsoft Graph v1.0 Bicep type version
resource app 'graphV1Older:Microsoft.Graph/applications@v1.0' existing = {
    uniqueName: appName
}
```
