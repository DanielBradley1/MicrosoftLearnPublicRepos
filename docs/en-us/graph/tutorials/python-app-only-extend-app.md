<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/python-app-only-extend-app -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Extend Python apps that use app-only authentication with more Microsoft Graph APIs

In this article, you add your own Microsoft Graph capabilities to the application you created in [Build Python apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/python-app-only). For example, you might want to add a code snippet from Microsoft Graph [documentation](https://learn.microsoft.com/en-us/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created.

## Update the app

1. Add the following function to **graph.py**.

   ```python
   async def make_graph_call(self):
       # INSERT YOUR CODE HERE
       return
   ```

2. Replace the empty `list_inbox` function in **main.py** with the following.

   ```python
   async def make_graph_call(graph: Graph):
       await graph.make_graph_call()
   ```

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](https://learn.microsoft.com/en-us/graph/api/user-post-events) API. You can use one of the examples in the API documentation, or create your own API request.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support app-only, or personal Microsoft accounts, for example.

- To call an API with user authentication \(if the API supports user \(delegated\) authentication\), see the [user \(delegated\) authentication](https://learn.microsoft.com/en-us/graph/tutorials/dotnet) tutorial.
- To call an API with app-only authentication \(if the API supports it\), add the required permission scope in the Microsoft Entra admin center.

## Add your code

Copy your code into the `make_graph_call` function in **graph.py**.

## Related content

Now that you have a working app that calls Microsoft Graph, you can experiment and add new features.

- Learn how to use [user \(delegated\) authentication](https://learn.microsoft.com/en-us/graph/tutorials/python) with the Microsoft Graph Python SDK.
- Visit the [Overview of Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) to see all of the data you can access with Microsoft Graph.

### Python samples

- [Django web app](https://github.com/microsoftgraph/msgraph-training-pythondjangoapp)
- [Security API sample](https://github.com/microsoftgraph/python-security-rest-sample)
