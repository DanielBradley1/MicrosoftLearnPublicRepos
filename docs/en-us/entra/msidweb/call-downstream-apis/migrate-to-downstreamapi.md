<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/migrate-to-downstreamapi -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Migrate from DownstreamWebApi to DownstreamApi

## Review the interface history

Microsoft.Identity.Web 1.x introduced **IDownstreamWebApi**, an interface that handled authentication details \(token acquisition, authorization headers\) when calling APIs. As the interface grew based on feature requests, breaking changes became necessary to support all requested scenarios.

Instead of modifying the existing API, the team built a new interface: **IDownstreamApi**. The old interface is deprecated, and all future development focuses on the new implementation. You can migrate at your own pace.

This article explains:

- How to migrate from **IDownstreamWebApi** to **IDownstreamApi**
- The differences between **IDownstreamWebApi** and **IDownstreamApi**

## Migrate from IDownstreamWebApi to IDownstreamApi

To migrate from **IDownstreamWebApi** to Microsoft.Identity.Web 2.x and **IDownstreamApi**:

1. Add a reference to the Microsoft.Identity.Web.DownstreamApi NuGet package.
2. In your application initialization code \(typically **Startup.cs** or **Program.cs**\), replace the old registration call:

   ```csharp
   .AddDownstreamWebApi("serviceName", Configuration.GetSection("SectionName"))
   ```


   with the new registration call:


   ```csharp
   .AddDownstreamApi("serviceName", Configuration.GetSection("SectionName"))
   ```

3. In the configuration file \(**appsettings.json**\), in the section representing the downstream web API, change the **Scopes** value from a string to an array of strings. The following example shows the original space-delimited string format:

   ```json
   "DownstreamApi1": {
       "BaseUrl": "https://myapi.domain.com",
       "Scopes": "https://myapi.domain.com/read  https://myapi.domain.com/write"
   },  
   ```


   Update the scopes to use the new array format:


   ```json
   "DownstreamApi1": {
       "BaseUrl": "https://myapi.domain.com",
       "Scopes": [
           "https://myapi.domain.com/read",
           "https://myapi.domain.com/write" 
       ]
   },  
   ```


   Warning


   If you forget to change the Scopes to an array, when you try to use the IDownstreamApi the scopes will appear null, and IDownstreamApi will attempt an anonymous \(unauthenticated\) call to the downstream API, which will result in a 401/unauthenticated.

4. In the controller:

   - Add `using namespace Microsoft.Identity.Abstractions`
   - Inject `IDownstreamApi` instead of `IDownstreamWebApi`
   - Replace `CallWebApiForUserAsync` with `CallApiForUserAsync`
   - If you used one of the methods GetForUser, PutForUser, or PostForUser, change the string that expressed the relative path to a delegate that sets this relative path. The following example shows the original string parameter approach:

     ```csharp
     Todo value = await _downstreamWebApi.GetForUserAsync<Todo>(ServiceName,
                                                                 $"api/todolist/{id}");
     ```


     Update the code to use a delegate that sets the relative path:


     ```csharp
     Todo value = await _downstreamWebApi.GetForUserAsync<Todo>(
           ServiceName,
           options => options.RelativePath = $"api/todolist/{id}";);
     ```

## Review example code

The following sample shows how to use IDownstreamApi in a working application.

See the complete example: [ASP.NET Core web app calling web API/TodoListController](https://github.com/AzureAD/microsoft-identity-web/pull/2036/files).

## Compare IDownstreamWebApi and IDownstreamApi

The following table summarizes the key differences between the deprecated `IDownstreamWebApi` and the new `IDownstreamApi`:

| Feature | IDownstreamWebApi \(deprecated\) | IDownstreamApi |
| --- | --- | --- |
| **NuGet package** | Microsoft.Identity.Web.DownstreamWebApi | Microsoft.Identity.Web.DownstreamApi |
| **Registration** | `AddDownstreamWebApi()` | `AddDownstreamApi()` |
| **Scopes configuration** | Space-delimited string | Array of strings |
| **Options pattern** | Limited | Full `Action<DownstreamApiOptions>` delegate support |
| **Relative path** | String parameter | Set through options delegate \(`options.RelativePath`\) |
| **Serialization** | Manual JSON handling | Built-in serialization with `<TInput, TOutput>` generics |
| **HTTP methods** | `GetForUserAsync`, `PostForUserAsync`, etc. | Unified `CallApiForUserAsync` with HTTP method in options, plus typed helpers |
| **App-only calls** | `CallWebApiForAppAsync` | `CallApiForAppAsync` |
| **Custom HTTP message** | Not supported | `options.CustomizeHttpRequestMessage` delegate |
| **Clone/override options** | Not supported | Per-call option overrides via delegate |
| **Protocol abstraction** | Tied to Microsoft.Identity.Web | Based on `Microsoft.Identity.Abstractions` \(reusable across identity libraries\) |

### Understand migration benefits

Migrating to `IDownstreamApi` gives you access to ongoing improvements and a more flexible API surface.

- **`IDownstreamWebApi` is deprecated** and won't receive new features or bug fixes.
- **`IDownstreamApi`** provides a cleaner API surface, better serialization support, and full options customization.
- The abstraction layer \(`Microsoft.Identity.Abstractions`\) means your downstream API code isn't tightly coupled to a specific identity library.

### Explore related content

Use these resources to learn more about calling downstream APIs.

- [Call downstream APIs overview](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview)
- [Call custom APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/custom-apis)
