<!-- Source: https://learn.microsoft.com/en-us/graph/toolkit/overview -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# Microsoft Graph Toolkit overview

Caution

The Microsoft Graph Toolkit is deprecated. The retirement period begins September 1, 2025, with full retirement planned for August 28, 2026. Developers should migrate to using the Microsoft Graph SDKs or other supported Microsoft Graph tools for building web experiences. For more information, see the [deprecation announcement](https://devblogs.microsoft.com/microsoft365dev/microsoft-graph-toolkit-retirement/).

Microsoft Graph Toolkit is a collection of reusable, framework-agnostic components and authentication providers for accessing and working with Microsoft Graph. The components are fully functional right out of the box, with built-in providers that authenticate with and fetch data from Microsoft Graph.

Microsoft Graph Toolkit makes it easy to use Microsoft Graph in your application. In the following example, a signed-in user and their calendar events are displayed with just two lines of code by using the [Login](https://learn.microsoft.com/en-us/graph/toolkit/components/login) and [Agenda](https://learn.microsoft.com/en-us/graph/toolkit/components/agenda) components.

- [HTML](#tabpanel_1_html)
- [React](#tabpanel_1_react)

<iframe src="https://mgt.dev/iframe.html?id=samples-embed--login-to-show-agenda&amp;source=docs" data-linktype="external" height="400"></iframe>

[Open this example in mgt.dev](https://mgt.dev/?path=/story/samples-embed--login-to-show-agenda&source=docs).

<iframe src="https://mgt.dev/iframe.html?id=samples-embed--login-to-show-agenda-react&amp;source=docs" data-linktype="external" height="400"></iframe>

[Open this example in mgt.dev](https://mgt.dev/?path=/story/samples-embed--login-to-show-agenda-react&source=docs).

## Why use Microsoft Graph Toolkit?

Microsoft Graph Toolkit enables you to quickly and easily integrate common experiences powered by Microsoft Graph into your own application. The toolkit:

- **Cuts development time**. The work to connect to Microsoft Graph APIs and render the data in a UI that looks and feels like a Microsoft 365 experience is done for you, with no customization required.
- **Works everywhere**. All components are based on web standards and work seamlessly with any modern browser and web framework \(such as React, Angular, or Vue\).
- **Is beautiful but flexible**. The components are designed to look and feel like Microsoft 365 experiences but are also customizable by using [CSS custom properties](https://learn.microsoft.com/en-us/graph/toolkit/customize-components/style) and [templating](https://learn.microsoft.com/en-us/graph/toolkit/customize-components/templates).

## Who should use it?

Microsoft Graph Toolkit is great for developers of all experience levels that want to develop an app that connects to and accesses data from Microsoft Graph, such as a:

- Web app
- Microsoft Teams tab
- Progressive Web App \(PWA\)
- Electron app
- SharePoint web part

## What's in Microsoft Graph Toolkit?

### Components

Microsoft Graph Toolkit includes a collection of web components for the most commonly built experiences powered by Microsoft Graph APIs.

The components are also available as [React components](https://learn.microsoft.com/en-us/graph/toolkit/get-started/mgt-react).

| Component | Description |
| --- | --- |
| [Agenda](https://learn.microsoft.com/en-us/graph/toolkit/components/agenda) | Displays events in a user's or group's calendar. |
| [Chat \(preview\)](https://learn.microsoft.com/en-us/graph/toolkit/components/chat) | Displays a 1:1 or a group conversation from Microsoft Teams |
| [File](https://learn.microsoft.com/en-us/graph/toolkit/components/file) | Represents a file or folder with an icon, a file name, an author, and more. |
| [File list](https://learn.microsoft.com/en-us/graph/toolkit/components/file-list) | Displays a list of multiple files or folders. |
| [Get](https://learn.microsoft.com/en-us/graph/toolkit/components/get) | Lets you make a GET query to any Microsoft Graph API directly in your HTML. |
| [Login](https://learn.microsoft.com/en-us/graph/toolkit/components/login) | A button and a flyout control to authenticate a user with the Microsoft Identity platform and display the user's profile information when they sign in. |
| [New chat \(preview\)](https://learn.microsoft.com/en-us/graph/toolkit/components/new-chat) | A form to create a new 1:1 or group conversation in Microsoft Teams |
| [People](https://learn.microsoft.com/en-us/graph/toolkit/components/people) | Displays a group of people or contacts by their photos or initials. |
| [People picker](https://learn.microsoft.com/en-us/graph/toolkit/components/people-picker) | Search for people and renders the list of results. |
| [Person](https://learn.microsoft.com/en-us/graph/toolkit/components/person) | Displays a person or contact by their photo, name, and/or email address. |
| [Person card](https://learn.microsoft.com/en-us/graph/toolkit/components/person-card) | A flyout used on the person component to display more profile information about a user. |
| [Picker](https://learn.microsoft.com/en-us/graph/toolkit/components/picker) | Renders a dropdown control that allows a selection of a single resource from an array of resources. |
| [Planner tasks](https://learn.microsoft.com/en-us/graph/toolkit/components/planner) | Displays and enables adding, removing, completing, or editing of tasks from Microsoft Planner or Microsoft To Do. |
| [Search box](https://learn.microsoft.com/en-us/graph/toolkit/components/search-box) | Search for Microsoft Teams channels to select a channel from a rendered list of results. |
| [Search results](https://learn.microsoft.com/en-us/graph/toolkit/components/search-results) | Lets you make a query to the search endpoint of Microsoft Graph directly in your HTML. |
| [Taxonomy picker](https://learn.microsoft.com/en-us/graph/toolkit/components/taxonomy-picker) | Use the taxonomy picker component to query the Microsoft Graph API for Taxonomy and render a dropdown control with terms. |
| [Teams Channel picker](https://learn.microsoft.com/en-us/graph/toolkit/components/teams-channel-picker) | Search for Microsoft Teams channels to select a channel from a rendered list of results. |
| [To Do](https://learn.microsoft.com/en-us/graph/toolkit/components/todo) | Displays and enables adding, removing, completing, or editing of tasks from Microsoft To Do. |

### Providers

[Providers](https://learn.microsoft.com/en-us/graph/toolkit/providers/providers) enable authentication, provide the implementation for acquiring access tokens on various platforms, and expose a Microsoft Graph client for calling the Microsoft Graph APIs. The components work best when used with a provider, but the providers can be used on their own.

| Providers | Description |
| --- | --- |
| [Custom](https://learn.microsoft.com/en-us/graph/toolkit/providers/custom) | Creates a custom provider to enable authentication and access to Microsoft Graph by using your application's existing authentication code. |
| [Electron](https://learn.microsoft.com/en-us/graph/toolkit/providers/electron) | Authenticates and provides Microsoft Graph access to components inside of Electron apps. |
| [MSAL2](https://learn.microsoft.com/en-us/graph/toolkit/providers/msal2) | Uses msal-browser to sign in users and acquire tokens to use with Microsoft Graph. |
| [Proxy](https://learn.microsoft.com/en-us/graph/toolkit/providers/proxy) | Allows the use of backend authentication by routing all calls to Microsoft Graph through your backend. |
| [SharePoint](https://learn.microsoft.com/en-us/graph/toolkit/providers/sharepoint) | Authenticates and provides Microsoft Graph access to components inside of SharePoint web parts. |
| [TeamsFx](https://learn.microsoft.com/en-us/graph/toolkit/providers/teamsfx) | Use the TeamsFx provider inside your Microsoft Teams applications to provide Microsoft Graph Toolkit components access to Microsoft Graph. |

## Where can I use it?

Microsoft Graph Toolkit is supported in the following browsers:

| ![Edge](https://learn.microsoft.com/en-us/graph/toolkit/images/edgeicon.png) | ![Firefox](https://learn.microsoft.com/en-us/graph/toolkit/images/firefoxicon.png) | ![Chrome](https://learn.microsoft.com/en-us/graph/toolkit/images/chromeicon.png) | ![Safari](https://learn.microsoft.com/en-us/graph/toolkit/images/safariicon.png) | ![Opera](https://learn.microsoft.com/en-us/graph/toolkit/images/operaicon.png) | ![Samsung Internet](https://learn.microsoft.com/en-us/graph/toolkit/images/samsunginterneticon.png) |
| --- | --- | --- | --- | --- | --- |
| **Edge** | **Firefox** | **Chrome** | **Safari** | **Opera** | **Samsung** |

## Next steps

- Try out the components in the [playground](https://mgt.dev).
- [Get started](https://learn.microsoft.com/en-us/graph/toolkit/get-started/overview) with Microsoft Graph Toolkit.
- Check out Microsoft Graph Toolkit on [GitHub](https://aka.ms/mgt).
