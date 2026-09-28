<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/dotnet-extend-app -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Extend .NET apps with more Microsoft Graph APIs

In this article, you add your own Microsoft Graph capabilities to the application you created in [Build .NET apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/dotnet). For example, you might want to add a code snippet from Microsoft Graph [documentation](https://learn.microsoft.com/en-us/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created.

## Update the app

1. Open **./GraphHelper.cs** and add the following function to the **GraphHelper** class.

   ```csharp
   /* This function serves as a playground for testing Graph snippets */
   /* or other code */
   public static async Task MakeGraphCallAsync()
   {
       // INSERT YOUR CODE HERE
   }
   ```

2. Replace the empty `MakeGraphCallAsync` function in **Program.cs** with the following.

   ```csharp
   async Task MakeGraphCallAsync()
   {
       await GraphHelper.MakeGraphCallAsync();
   }
   ```

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](https://learn.microsoft.com/en-us/graph/api/user-post-events) API. You can use one of the examples in the API documentation, or you can customize an API request in Graph Explorer and use the generated snippet.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support app-only, or personal Microsoft accounts, for example.

- To call an API with user authentication \(if the API supports user \(delegated\) authentication\), add the required permission scope in **appsettings.json**.
- To call an API with app-only authentication, see the [app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only) tutorial.

## Add your code

Copy your code into the `MakeGraphCallAsync` function in **GraphHelper.cs**. If you're copying a snippet from documentation or Graph Explorer, be sure to rename the `GraphServiceClient` to `_userClient`.

## Related content

Now that you have a working app that calls Microsoft Graph, you can experiment and add new features.

- Learn how to use [app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/dotnet-app-only) with the Microsoft Graph .NET SDK.
- Visit the [Overview of Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) to see all of the data you can access with Microsoft Graph.

### .NET samples

- [ASP.NET Core MVC app](https://github.com/microsoftgraph/msgraph-training-aspnet-core)
- [Universal Windows Platform \(UWP\) app](https://github.com/microsoftgraph/msgraph-training-uwp)
- [Xamarin app](https://github.com/microsoftgraph/msgraph-training-xamarin)
- [Blazor WebAssembly app](https://github.com/microsoftgraph/msgraph-training-blazor-clientside)
- [Azure Functions](https://github.com/microsoftgraph/msgraph-training-azurefunction-csharp)
- [Bot Framework](https://github.com/microsoftgraph/msgraph-training-botframework)
- [Teams app](https://github.com/microsoftgraph/msgraph-training-teamsapp-dotnet)
- [Change notifications](https://github.com/microsoftgraph/aspnetcore-webhooks-sample)
- [ASP.NET Core snippets](https://github.com/microsoftgraph/aspnet-snippets-sample)
