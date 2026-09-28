<!-- Source: https://learn.microsoft.com/en-us/graph/toolkit/providers/sharepoint -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# SharePoint provider

Caution

The Microsoft Graph Toolkit is deprecated. The retirement period begins September 1, 2025, with full retirement planned for August 28, 2026. Developers should migrate to using the Microsoft Graph SDKs or other supported Microsoft Graph tools for building web experiences. For more information, see the [deprecation announcement](https://devblogs.microsoft.com/microsoft365dev/microsoft-graph-toolkit-retirement/).

Use the SharePoint provider inside your SharePoint web parts to power the components with Microsoft Graph access.

To learn more about authentication providers, see [Providers](https://learn.microsoft.com/en-us/graph/toolkit/providers/providers).

## Get started

Initialize the provider inside the `onInit()` method of your web part. This example uses the [`@microsoft/mgt-spfx` package](https://learn.microsoft.com/en-us/graph/toolkit/get-started/mgt-spfx).

```ts
// import the providers at the top of the page
import {Providers, SharePointProvider} from '@microsoft/mgt-spfx';

// add the onInit() method if not already there in your web part class
protected async onInit() {
  Providers.globalProvider = new SharePointProvider(this.context);
}
```

Now you can add any component in your `render()` method and it will use the SharePoint context to access Microsoft Graph.

```ts
public render(): void {
  this.domElement.innerHTML = `
    <mgt-agenda></mgt-agenda>
    `;
}
```

#### Use a different cloud endpoint

Use this when you want to use the toolkit to render your data from a different Microsoft 365 endpoint.

```ts
// import the providers at the top of the page
import {Providers, SharePointProvider} from '@microsoft/mgt-spfx';
import {GraphEndpoint} from '@microsoft/mgt-element';

const baseUrl: GraphEndpoint = 'https://graph.microsoft.us';

// add the onInit() method if not already there in your web part class
protected async onInit() {
  Providers.globalProvider = new SharePointProvider(this.context, baseUrl=baseUrl);
}
```

Then use the toolkit as usual.

> **Note:** The Microsoft Graph Toolkit requires Typescript 3.7 or newer. Make sure you're using a supported version of Typescript by [installing the right compiler](https://github.com/SharePoint/sp-dev-docs/wiki/SharePoint-Framework-v1.8-release-notes#support-for-typescript-27-29-and-3x).

## Sample

For details about how to initialize the SharePoint provider, see the [Build a SharePoint web part](https://learn.microsoft.com/en-us/graph/toolkit/get-started/build-a-sharepoint-web-part) getting started guide.

## Test in the workbench

If you're just getting started with SharePoint web parts, you can follow the [Build your first web part](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/build-a-hello-world-web-part) guidance.

After you've created a web part, and you're ready to use the components, you will need to make sure that your web part has the right permissions to access Microsoft Graph. For details, see [Consume Microsoft Graph in the SharePoint Framework](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/use-aad-tutorial).

In short, it's important to add the right permission to your `package-solution.json`. You will need to upload a package of your web part to SharePoint and have an administrator approve the requested permissions.

Tip

The [Build a SharePoint web part](https://learn.microsoft.com/en-us/graph/toolkit/get-started/build-a-sharepoint-web-part#configure-permissions) getting started guide provides step-by-step instructions for configuring and approving permissions.

> **Note:** if you're not sure what permissions to add, the documentation for each component includes all the permissions it needs.
