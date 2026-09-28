<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/go-extend-app -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Extend Go apps with more Microsoft Graph APIs

In this article, you add your own Microsoft Graph capabilities to the application you created in [Build Go apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/go). For example, you might want to add a code snippet from Microsoft Graph [documentation](https://learn.microsoft.com/en-us/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created. This section is optional.

## Update the app

1. Add the following function to **./graphhelper/graphhelper.go**.

   ```go
   func (g *GraphHelper) MakeGraphCall() error {
       // INSERT YOUR CODE HERE
       return nil
   }
   ```

2. Replace the empty `makeGraphCall` function in **graphtutorial.go** with the following.

   ```go
   func makeGraphCall(graphHelper *graphhelper.GraphHelper) {
       err := graphHelper.MakeGraphCall()
       if err != nil {
           log.Panicf("Error making Graph call: %v", err)
       }
   }
   ```

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](https://learn.microsoft.com/en-us/graph/api/user-post-events) API. You can use one of the examples in the API documentation, or you can customize an API request in Graph Explorer and use the generated snippet.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support app-only, or personal Microsoft accounts, for example.

- To call an API with user authentication \(if the API supports user \(delegated\) authentication\), add the required permission scope in **.env** \(or **.env.local**\).
- To call an API with app-only authentication, see the [app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/go-app-only) tutorial.

## Add your code

Copy your code into the `MakeGraphCall` function in **graphhelper.go**. If you're copying a snippet from documentation or Graph Explorer, be sure to rename the `GraphServiceClient` to `userClient`.

## Related content

Now that you have a working app that calls Microsoft Graph, you can experiment and add new features.

- Learn how to use [app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/go-app-only) with the Microsoft Graph SDK for Go.
- Visit the [Overview of Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) to see all of the data you can access with Microsoft Graph.
