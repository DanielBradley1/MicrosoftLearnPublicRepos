<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/known-issues-graph-bicep -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Known issues: Microsoft Graph Bicep templates

This article lists known issues with Bicep templates for Microsoft Graph resources, and gives alternatives and workarounds where available.

## Child resources

Child resources are resources that exist only within the context of a parent resource. For example, [`federatedIdentityCredentials`](https://learn.microsoft.com/en-us/graph/templates/reference/federatedidentitycredentials) is a child of `applications`.

Bicep supports [three ways to declare a child resource](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/child-resource-name-type). For Microsoft Graph resources, not all methods are supported.

To avoid authoring or deployment errors with child resources, use either:

- The [within parent resource](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/child-resource-name-type#within-parent-resource) method \(recommended\), or
- The [outside parent without specifying parent property](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/child-resource-name-type#full-resource-name-outside-parent) method.

In both options, the identifier property must use the full resource name format: `<parent-identifier>/<child-identifier>`.

### Linting error: The property "parent" isn't allowed on objects of type "Microsoft.Graph/<full resource name of child resource>"

If you specify the `parent` property, you may see a linting error. Microsoft Graph resources don't support the `parent` property like Azure resources. The [outside parent resource](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/child-resource-name-type#outside-parent-resource) method isn't currently supported.

### Linting error: Remove unnecessary dependsOn entry '<parent-identifier-name>'

If the parent resource is referenced in the full resource name, you may see a linting error about an unnecessary `dependsOn` entry. The reference implies the dependency. However, if the full resource name is plain text, you must use `dependsOn` so Bicep can determine the dependency.

### Deployment error: Invalid identifier format for {<parent-identifier>/<child-identifier>}

This error means the child resource's name property doesn't use the required `<parent-identifier>/<child-identifier>` format.

## Deployment warnings and errors about unknown types, properties, or capabilities

After upgrading the Bicep extension for VS Code, upgrade the Bicep CLI to match. Mismatched versions cause warnings about unknown types and properties or deployment errors about unknown capabilities. Azure CLI warns if a newer version is available; Azure PowerShell doesn't.

### Resolution

Upgrade your Bicep CLI to match the VS Code Bicep extension version.

1. Check the Bicep CLI version:

   ```bicep
   bicep --version
   ```

2. If the version is different from the VS Code extension, continue:

   - For Azure CLI, upgrade with:

     ```azurecli
     az bicep upgrade
     ```

   - For Azure PowerShell or custom apps, [install or upgrade manually](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/install#install-manually).

## Deployment Error: Another object with the same value for property uniqueName already exists

If you redeploy a Bicep file and a Microsoft Graph resource was deleted outside of Bicep \(for example, by using PowerShell, CLI, or REST API\), you may see a conflict error about the unique name.

### Resolution

Choose one of these options:

- [Permanently delete](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete) the deleted item, and then redeploy.
- Use a different unique name in your Bicep file, and then redeploy.
- [Restore the deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore), and then redeploy.

## Deployment Error: App-only deployment fails when property membershipRule is declared on a group

If you use app-only deployment and declare a group resource with the **membershipRule** property, deployment fails with the following error:

```json
{
    "error": {
        "code":"BadRequest",
        "target":"/resources/<groupsResourceName>",
        "message":"AppOnly OBO tokens not supported by target service. ..."
    }
}
```

This happens because the service that supports dynamic group membership doesn't support template automation flows.

## Deployment error: Publisher verification ID \(MPN\) can't be set on an application

If you set `verifiedPublisher.publisherVerificationId` on an application resource, deployment fails:

```json
{
    "error": {
        "code":"Forbidden",
        "message":"verifiedPublisher properties cannot be set during Application creation. Graph client request id: {request-id-value}. Graph request timestamp: {UTC-timestamp-value}."
    }
}
```

The `verifiedPublisher` property is read-only. You need to use a different Microsoft Graph endpoint to set it.

### Resolution

Create the application without `verifiedPublisher`. Then, use Microsoft Graph REST API, CLI, or PowerShell to [set the verified publisher](https://learn.microsoft.com/en-us/graph/api/application-setverifiedpublisher). Or, use a deployment script in your Bicep file.
