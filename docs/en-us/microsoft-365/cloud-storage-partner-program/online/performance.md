<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/performance -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Load Time Performance

You can improve the load time performance of Microsoft 365 for the web applications by preloading the Microsoft 365 for the web static content.

## Preload static content

You can preload the Microsoft 365 for the web static content \(JavaScript, CSS, and images\) into the user’s browser cache. This ensures that when the user opens a document in Microsoft 365 for the web, they can use the previously cached static content. As in, they won't have to download the static content when they first load Microsoft 365 for the web.

To support preloading static content, Microsoft 365 for the web provides two WOPI actions for each Microsoft 365 for the web application in its discovery XML, one to preload static content for the `view` action \(`preloadview`\), and a second to preload static content for the `edit` action \(`preloadedit`\).

Hosts can use these URLs just like they use other [Action URLs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#action-urls), by pointing iframes in their pages at the action URL. Unlike most action URLs, the WopiSrc and access token don't need to be specified to use these actions.

Hosts can include both `preloadview` and `preloadedit` in their pages to preload static content for both. The static content preload actions contain the [UI\_LLCC](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#ui_llcc) placeholder value, which should be replaced with an appropriate language for the user so that the proper localized static content is preloaded.

Tip

If you want to preload static content for all applications and both view and edit modes, you must load multiple actions, one for each application and mode combination.
