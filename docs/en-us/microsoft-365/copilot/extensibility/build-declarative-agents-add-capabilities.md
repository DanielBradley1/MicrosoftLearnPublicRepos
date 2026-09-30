<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-capabilities -->
<!-- Sitemap-Last-Modified: 2026-09-04 -->

# Add capabilities and custom actions to a declarative agent created with Microsoft 365 Agents Toolkit

You can enhance the abilities of your agent by adding capabilities or custom actions. You can enhance your agent by enabling built-in capabilities like [image generator](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/image-generator) or [code interpreter](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/code-interpreter), or by adding [MCP or API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-plugins) as custom actions. This tutorial adds an API plugin. To add an MCP server, see [Build or reuse MCP servers](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-mcp-servers) and [Build a plugin for a declarative agent from an MCP server](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-mcp-plugins).

Important

This guide assumes you have completed the [Create declarative agents by using Microsoft 365 Agents Toolkit and JSON](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents) tutorial.

## Add image generator to the agent

The image generator capability enables agents to generate images based on user prompts. To add image generator:

1. Open the `appPackage/declarativeAgent.json` file and add the `GraphicArt` entry to the `capabilities` array. For more information, see [Graphic art object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#graphic-art-object).

   ```json
   {
     "name": "GraphicArt"
   }
   ```

2. In the **Lifecycle** pane of Microsoft 365 Agents Toolkit, select **Provision**.

The declarative agent can generate images after you reload the page.

Note

Image generator isn't available to agents in Microsoft 365 Government Community Cloud High \(GCCH\) environments.

![A screenshot showing a response from the declarative agent that contains generated graphic art](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/graphic-art-content.png)

## Add code interpreter to the agent

Code interpreter is an advanced tool designed to solve complex tasks via Python code.

Note

In GCCH environments, code interpreter is only available to users with a Microsoft 365 Copilot add-on license.

1. Open the `appPackage/declarativeAgent.json` file and add the `CodeInterpreter` entry to the `capabilities` array.

   ```json
   {
     "name": "CodeInterpreter"
   }
   ```


   For more information, see [Code interpreter object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#code-interpreter-object).

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has the code interpreter capability after you reload the page.

![A screenshot showing a response from the declarative agent that contains a generated graph](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/code-interpreter-graph-content.png)

![A screenshot showing the Python code used to generate the requested graph](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/code-interpreter-python-content.png)

## Add an API plugin as a custom action to the agent

API plugins add new abilities to your agent by allowing your agent to interact with a REST API.

Note

Custom actions aren't supported in GCCH environments.

Before you begin, create a file named `posts-api.yml` and add the code from the [Posts API OpenAPI description document](#posts-api-openapi-description-document).

1. Select **Add Action** in the **Development** pane of Agents Toolkit.
2. Select **Start with an OpenAPI Description Document**.
3. Select **Browse** and browse to the `posts-api.yml` file.
4. Select all available APIs, then select **OK**.

   ![A screenshot of the API selection dialog in Visual Studio Code](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/select-apis.png)
5. Select **manifest.json**.
6. Review the warning in the dialog. When you're ready to proceed, select **Add**.
7. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to your plugin content to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains API plugin content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/plugin-response.png)

## Posts API OpenAPI description document

The following OpenAPI description is for the [JSONPlaceHolder API](https://jsonplaceholder.typicode.com/), a free online REST API that you can use whenever you need some fake data.

```yml
openapi: '3.0.2'
info:
  title: Posts API
  version: '1.0'
servers:
- url: https://jsonplaceholder.typicode.com/

components:
  schemas:
    post:
      type: object
      properties:
        userId:
          type: integer
          description: The ID of the user that authored the post.
        id:
          type: integer
        title:
          type: string
        body:
          type: string
    user:
      type: object
      properties:
        id:
          type: integer
        name:
          type: string
        username:
          type: string
        email:
          type: string
        phone:
          type: string
        website:
          type: string
        address:
          $ref: '#/components/schemas/address'
        company:
          $ref: '#/components/schemas/company'
    address:
      type: object
      properties:
        street:
          type: string
        suite:
          type: string
        city:
          type: string
        zipcode:
          type: string
        geo:
          $ref: '#/components/schemas/coordinates'
    coordinates:
      type: object
      properties:
        lat:
          type: string
          description: The latitude of the location
        lng:
          type: string
          description: The longitude of the location
    company:
      type: object
      properties:
        name:
          type: string
        catchPhrase:
          type: string
        bs:
          type: string
  parameters:
    post-id:
      name: post-id
      in: path
      description: 'key: id of post'
      required: true
      style: simple
      schema:
        type: integer
    user-id:
      name: user-id
      in: path
      description: 'key: id of user'
      required: true
      style: simple
      schema:
        type: integer

paths:
  /posts:
    get:
      description: Get posts
      operationId: GetPosts
      parameters:
      - name: userId
        in: query
        description: Filter results by user ID
        required: false
        style: form
        schema:
          type: integer
          maxItems: 1
      - name: title
        in: query
        description: Filter results by title
        required: false
        style: form
        schema:
          type: string
          maxItems: 1
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/post'
    post:
      description: 'Create post'
      operationId: CreatePost
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/post'
      responses:
        '201':
          description: Created
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/post'
  /posts/{post-id}:
    get:
      description: 'Get post by ID'
      operationId: GetPostById
      parameters:
      - $ref: '#/components/parameters/post-id'
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/post'
    patch:
      description: 'Update post'
      operationId: UpdatePost
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/post'
      parameters:
      - $ref: '#/components/parameters/post-id'
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/post'
    delete:
      description: 'Delete post'
      operationId: DeletePost
      parameters:
      - $ref: '#/components/parameters/post-id'
      responses:
        '200':
          description: OK
  /users:
    get:
      summary: Get users
      description: Returns details about users
      operationId: GetUsers
      parameters:
      - name: name
        in: query
        description: The user's real name
        schema:
          type: string
      - name: username
        in: query
        description: The user's login name
        schema:
          type: string
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/user'
  /users/{user-id}:
    get:
      description: 'Get user by ID'
      operationId: GetUserById
      parameters:
      - $ref: '#/components/parameters/user-id'
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/user'
```

## Related content

You've completed the declarative agent guide for Microsoft 365 Copilot. Now that you're familiar with the capabilities of a declarative agent, you can learn more about declarative agents in the following articles.

- [Create declarative agents by using Microsoft 365 Agents Toolkit and TypeSpec](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-typespec)
- Learn how to [write effective instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions) for your agent.
- Test your agent with developer mode to verify if and how the Copilot orchestrator selects your knowledge sources for use in response to given prompts. For more information, see [Test and debug agents in Microsoft 365 Agents Toolkit by using developer mode](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/debugging-agents-vscode).
- Get answers to [frequently asked questions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/transparency-faq-declarative-agent).
- Learn about other ways to build declarative agents: no-code in [Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder), or low-code in [Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extensions?context=/microsoft-365/copilot/extensibility/context).
