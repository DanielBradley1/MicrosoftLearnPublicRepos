<!-- Source: https://learn.microsoft.com/en-us/graph/toolkit/get-started/overview -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# Get started with Microsoft Graph Toolkit

Caution

The Microsoft Graph Toolkit is deprecated. The retirement period begins September 1, 2025, with full retirement planned for August 28, 2026. Developers should migrate to using the Microsoft Graph SDKs or other supported Microsoft Graph tools for building web experiences. For more information, see the [deprecation announcement](https://devblogs.microsoft.com/microsoft365dev/microsoft-graph-toolkit-retirement/).

Microsoft Graph Toolkit components can easily be added to your web application, SharePoint web part, or Microsoft Teams tabs. The components are based on web standards and can be used in both plain JavaScript projects or with popular web frameworks such as Reach, Angular, and Vue.js.

Watch this short video to get started using the toolkit.

<iframe src="https://www.youtube-nocookie.com/embed/oZCGb2MMxa0" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

For a step-by-step tutorial, see the [Get started with Microsoft Graph Toolkit](https://learn.microsoft.com/en-us/training/modules/msgraph-toolkit-intro/) module.

## Set up your Microsoft 365 tenant

To use Microsoft Graph Toolkit to develop an app, you need access to a Microsoft 365 tenant. If you don't have a Microsoft 365 tenant, you might qualify for one through the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program); for details, see the [FAQ](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). Alternatively, you can [sign up for a 1-month free trial or purchase a Microsoft 365 plan](https://www.microsoft.com/en-us/microsoft-365/try).

## Set up your development environment

To develop with the toolkit, you need:

- A text editor or IDE. You can use the editor or IDE of your choice, or you can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.
- A modern web browser such as Microsoft Edge, Google Chrome, or Firefox.
- An LTS version of Node.js, which you can install from [nodejs.org](https://nodejs.org).

## Use Microsoft Graph Toolkit

You can use Microsoft Graph Toolkit in your application by installing the `npm` packages or referencing the loader directly \(via `unpkg`\).

- [package](#tabpanel_1_package)
- [CDN](#tabpanel_1_html)

Using the toolkit via ES6 modules gives you full control of the bundling process and allows you to bundle only the code that you need for your application. To use the ES6 modules, add the `@microsoft/mgt-element`, `@microsoft/mgt-components`, and `@microsoft/mgt-msal2-provider` packages to your project:

```cmd
npm install @microsoft/mgt-element @microsoft/mgt-components @microsoft/mgt-msal2-provider
```

To use the components as a custom element in HTML, they must be registered. To use the components in your code, import and run the necessary component registration function. The following example shows how to do that for the agenda and login components:

```html
<script type="module">
  import { registerMgtMsal2Provider } from 'node_modules/@microsoft/mgt-msal2-provider/dist/es6/index.js';
  import { registerMgtLoginComponent, registerMgtAgendaComponent } from 'node_modules/@microsoft/mgt-components/dist/es6/index.js';
  registerMgtMsal2Provider();
  registerMgtLoginComponent();
  registerMgtAgendaComponent();
</script>

<mgt-msal2-provider client-id="<YOUR_CLIENT_ID>"></mgt-msal2-provider>
<mgt-login></mgt-login>
<mgt-agenda></mgt-agenda>
```

As a shortcut, if you want to register all the components from `@microsoft/mgt-components`, you can use the `registerMgtComponents()` helper method. Declarative usage of providers still requires that the appropriate provider is registered separately because they are sourced from different packages.

```html
<script type="module">
  import { registerMgtMsal2Provider } from 'node_modules/@microsoft/mgt-msal2-provider/dist/es6/index.js';
  import { registerMgtComponents } from 'node_modules/@microsoft/mgt-components/dist/es6/index.js';
  registerMgtMsal2Provider();
  registerMgtComponents();
</script>

<mgt-msal2-provider client-id="<YOUR_CLIENT_ID>"></mgt-msal2-provider>
<mgt-login></mgt-login>
<mgt-agenda></mgt-agenda>
```

Important

When working with a tree-shaking supporting bundler such as Webpack or Rollup, you will want to import and register the individual components. This ensures that any unused components are tree-shaken out of your builds.

You can also configure the provider imperatively, as shown in the following example:

```html
<script type="module">
  import { Providers } from 'node_modules/@microsoft/mgt-element/dist/es6/index.js';
  import { Msal2Provider } from 'node_modules/@microsoft/mgt-msal2-provider/dist/es6/index.js';
  import { registerMgtComponents } from 'node_modules/@microsoft/mgt-components/dist/es6/index.js';
  Providers.globalProvider = new Msal2Provider({clientId: '<YOUR_CLIENT_ID>'});
  registerMgtComponents();
</script>
<mgt-login></mgt-login>
<mgt-agenda></mgt-agenda>
```

To use the toolkit via a CDN, add the following script and markup to your HTML page:

```html
<script type="module">
  import { registerMgtComponents, Providers, Msal2Provider } from 'https://unpkg.com/@microsoft/mgt@4';
  Providers.globalProvider = new Msal2Provider({clientId: '[CLIENT-ID]'});
  registerMgtComponents();
</script>
<mgt-login></mgt-login>
```

### Packages

Microsoft Graph Toolkit is made up of several packages. This allows you to include only the code that you need for your applications.

**@microsoft/mgt-element**

The `@microsoft/mgt-element` is the core package that contains only the base classes used for building components and providers. This package exposes all the necessary classes and interfaces that you need to build your own components, and exports the [`IProvider` interface and SimpleProvider class](https://learn.microsoft.com/en-us/graph/toolkit/providers/custom) for building custom providers.

**@microsoft/mgt-components**

The `@microsoft/mgt-components` package contains all the Microsoft Graph connected web components, such as `Person`, `PeoplePicker`, and more.

**Providers**

Providers are available via a single package and can be installed as needed. The following provider packages are available:

- **@microsoft/mgt-msal2-provider**

  `@microsoft/mgt-msal2-provider` contains the `Msal2Provider` and `mgt-msal2-provider` component. The MSAL2 provider uses MSAL-browser for authenticating in web apps and PWAs.
- **@microsoft/mgt-sharepoint-provider**

  `@microsoft/mgt-sharepoint-provider` contains the `SharePointProvider` for authenticating in a SharePoint environment.
- **@microsoft/mgt-proxy-provider**

  `@microsoft/mgt-proxy-provider` contains the `ProxyProvider` for an application that proxy Graph calls through a backend service.

**@microsoft/mgt**

The `@microsoft/mgt` package is a wrapper package that includes all the preceding packages and re-exports them so they're available via a single package that you can install. This package also includes the `mgt.js` script, which can be used via a CDN link.

**@microsoft/mgt-react**

The `@microsoft/mgt-react` package contains all the autogenerated React components and takes dependency on the `@microsoft/mgt` package.

**@microsoft/mgt-chat**

The `@microsoft/mgt-chat` package contains all the chat React components and takes dependency on the `@microsoft/mgt-react` package.

**@microsoft/mgt-spfx**

The `@microsoft/mgt-spfx` package contains a SharePoint Framework library to use Microsoft Graph Toolkit in SharePoint Framework solutions.

**@microsoft/mgt-spfx-utils**

The `@microsoft/mgt-spfx-utils` package contains a helper function to assist with lazy loading for [disambiguation](https://learn.microsoft.com/en-us/graph/toolkit/customize-components/disambiguation#usage-in-sharepoint-framework-web-parts-with-react) when using Microsoft Graph Toolkit in SharePoint Framework solutions.

## Next steps

You're now ready to start developing with Microsoft Graph Toolkit! The following guides are available to help you get started:

- [Register a Microsoft Entra app](https://learn.microsoft.com/en-us/graph/toolkit/get-started/add-aad-app-registration)
- [Build a web app \(JavaScript\)](https://learn.microsoft.com/en-us/graph/toolkit/get-started/build-a-web-app) \(vanilla JavaScript\)
- [Build a web app \(React\)](https://learn.microsoft.com/en-us/graph/toolkit/get-started/use-toolkit-with-react)
- [Build a web app \(Angular\)](https://learn.microsoft.com/en-us/graph/toolkit/get-started/use-toolkit-with-angular)
- [Build a SharePoint web part](https://learn.microsoft.com/en-us/graph/toolkit/get-started/build-a-sharepoint-web-part)
- [Build a Microsoft Teams tab](https://learn.microsoft.com/en-us/graph/toolkit/get-started/build-a-microsoft-teams-tab)
- [Build an Electron app](https://learn.microsoft.com/en-us/graph/toolkit/get-started/build-an-electron-app)
