<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-install-bicep-tools -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Quickstart: Install Bicep tools for deploying Microsoft Graph Bicep resource types

In this quickstart, you learn how to set up your authoring and deployment environment for Microsoft Graph Bicep resource types.

- **For authoring:** Visual Studio Code \(VS Code\) and the Bicep extension

  - Use Bicep version [v0.36.1](https://github.com/Azure/bicep/releases/tag/v0.36.1) or later.

- **For deployment:** Azure CLI

You can also use Visual Studio with the Bicep extension for authoring, and Azure PowerShell for deployment. For more information, see [Install Bicep tools](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/install).

## Install VS Code and the Bicep extension

To create Bicep files, use a supported editor:

- **Visual Studio Code:** [Download and install](https://code.visualstudio.com/) if you don't have it.
- **Bicep extension for Visual Studio Code:**

  - In VS Code, search for *bicep* in the **Extensions** tab or visit the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep). Select **Install**.


  ![Screenshot of installing Bicep extension.](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/install/install-extension.png)

To verify the extension is installed, open a `.bicep` file. The language mode in the lower right corner should display **Bicep**.

![Screenshot of Bicep language mode.](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/install/language-mode.png)

If you encounter errors, see [Troubleshoot Bicep installation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/installation-troubleshoot).

## Install Azure CLI

Azure CLI includes everything you need to [deploy](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/deploy-cli) and [decompile](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/decompile?tabs=azure-cli) Bicep files. The Bicep CLI is installed automatically when needed.

- Install Azure CLI version **2.73.0 or later**:

  - [Windows](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows)
  - [Linux](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux)
  - [macOS](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-macos)

To check your version:

```azurecli
az --version
```

To check your Bicep CLI version:

```azurecli
az bicep version
```

To upgrade to the latest version:

```azurecli
az bicep upgrade
```

For more commands, see [Bicep CLI](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/bicep-cli).

Important

Azure CLI installs a self-contained Bicep CLI instance. This instance doesn't conflict with any manually installed versions and isn't added to your PATH.

Your Bicep environment is now set up. You can now author Bicep files that declare Microsoft Graph resources and deploy them in interactive mode.

## Next step

[Quickstart: Create and deploy your first Bicep file with Microsoft Graph resources](https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-create-bicep-interactive-mode)
