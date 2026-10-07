<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/deploy-managed-apps-github-actions?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Deploy Microsoft Copilot Managed Runtime apps with GitHub Actions

You can deploy [Copilot Managed Runtime apps](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/?view=o365-worldwide) with GitHub Actions without going through the platform-managed build pipeline. Build each app with your own toolchain and deploy the external artifact directly through the Microsoft Copilot Managed Runtime CLI \(`ms`\).

Three GitHub Actions in the [`microsoft/Managed-Apps`](https://github.com/microsoft/Managed-Apps) repository \(under the `github-actions/` path\) do the work:

- `install-ms-cli` installs the Copilot Managed Runtime CLI on the runner.
- `ms-app-pack` builds the app and packs it into a deployable artifact.
- `ms-app-deploy` deploys the artifact to your environment.

After you complete the steps in this article, every push to your repository's main branch automatically deploys to your environment.

Note

External artifact deployment is for apps that don't use the default platform-managed build and deploy pipeline. An app that uses external artifact deployment has `"repoType": "none"` in its `ms.config.json`.

## Prerequisites

Before you deploy an app from GitHub Actions:

1. Create an **app with `"repoType": "none"`**. Run [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-create) `--repo none` locally to create the app and generate its `ms.config.json` \(stamped with `"repoType": "none"`\). This step needs the **`@microsoft/managed-apps-cli`** version `0.7.0` or later installed locally; the workflow installs the CLI on the runner for you.
2. Use a **GitHub repository** that contains your app source \(including `ms.config.json`\) and the workflow file. You need permission to manage the repository's Actions secrets.
3. Configure a **service principal** with permission on the app's environment. You create one in [Step 1](#step-1-create-and-configure-the-service-principal).
4. External artifact deployment is disallowed by default. See [External artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment).

Important

Your organization is responsible for validating externally built artifacts and securing the pipeline to meet its security, compliance, and software supply-chain requirements.

## Step 1: Create and configure the service principal

The workflow authenticates as a service principal by using the OAuth 2.0 client credentials flow. Configure the service principal once per tenant.

### Register an application in Microsoft Entra ID

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Go to **Microsoft Entra ID** > **App registrations** > **+ New registration**.
3. Enter a name \(for example, `managed-apps-spn`\), choose **Accounts in this organizational directory only**, leave the redirect URI blank, and then select **Register**.
4. On the **Overview** page, copy the **Application \(client\) ID** and **Directory \(tenant\) ID** for later.
5. Go to **Certificates & secrets** > **+ New client secret**. Enter a description, choose an expiry, and then select **Add**. Immediately copy the **Value** column. You can't see the secret again after you leave this page.

### Grant the service principal permission on the app's environment

The exact grant depends on whether the environment is Dataverse-enabled.

#### Dataverse-enabled environments

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
2. Select **Environments**, and then select the app's environment.
3. Go to **Settings** > **Users + permissions** > **Application users**.
4. Select **+ New app user**, select **+ Add an app**, search by the application \(client\) ID, and then select **Add**.
5. Set the business unit, assign the **System Administrator** and **System Customizer** security roles, and then select **Create**.

#### Non-Dataverse environments

Non-Dataverse \(sandbox-SKU\) environments don't host application users. Grant the **EnvironmentAdmin** role directly through the Business Application Platform \(BAP\) API.

Important

Use the **service principal's** object ID \(from **Azure portal** > **Enterprise applications** > your app > **Overview**\), not the app registration's object ID. They're different GUIDs, and using the wrong one returns a `400 Principal not found` error.

Get an access token from a user who has the `EnvironmentAdmin` role on the app's environment:

```azurecli
az login --tenant <your-tenant-id>
az account get-access-token --resource https://service.powerapps.com/ --query accessToken -o tsv
```

Then issue a POST request to the BAP API to add the role assignment. For production, use `https://api.bap.microsoft.com` as the base URL.

```http
POST https://<bap-base-url>/providers/Microsoft.BusinessAppPlatform/scopes/admin/environments/<environment-id>/modifyRoleAssignments?api-version=2021-04-01
Authorization: Bearer <user-token>
Content-Type: application/json

{
  "add": [
    {
      "properties": {
        "roleDefinition": {
          "id": "/providers/Microsoft.BusinessAppPlatform/scopes/admin/environments/<environment-id>/roleDefinitions/EnvironmentAdmin"
        },
        "principal": {
          "id": "<service-principal-object-id>",
          "type": "ServicePrincipal",
          "tenantId": "<tenant-id>"
        }
      }
    }
  ],
  "remove": []
}
```

Note

Instead of calling the BAP API directly, you can use the **Power Platform for Admins** connector's [Edit Environment Role Assignment](https://learn.microsoft.com/en-us/connectors/powerplatformforadmins/#edit-environment-role-assignment) action, which is convenient when you grant the role from a Power Automate cloud flow. For programmatic access to the same admin capabilities, see [Get started with the Power Platform API](https://learn.microsoft.com/en-us/power-platform/admin/powerplatform-api-getting-started).

## Step 2: Add the secrets to your GitHub repository

In your repository, select **Settings** > **Secrets and variables** > **Actions** > **New repository secret**, and then add these three secrets from the app registration:

| Secret name | Value |
| --- | --- |
| `PP_SP_CLIENT_ID` | Application \(client\) ID. |
| `PP_SP_CLIENT_SECRET` | Client secret value. |
| `PP_SP_TENANT_ID` | Directory \(tenant\) ID. |

## Step 3: Add the deployment workflow

Add the following workflow to your repository at `.github/workflows/deploy-managed-app.yml`. Replace `apps/my-app` with the path to your app.

```yaml
name: Deploy Copilot Managed Runtime app

on:
  push:
    branches: [main]
    paths:
      - 'apps/my-app/**'
      - '.github/workflows/deploy-managed-app.yml'
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v5

    - name: Setup Node 24
      uses: actions/setup-node@v5
      with:
        node-version: '24'

    - name: Install app dependencies
      working-directory: apps/my-app
      run: npm install

    - name: Install ms CLI
      uses: microsoft/Managed-Apps/github-actions/install-ms-cli@v1

    - name: Pack app
      uses: microsoft/Managed-Apps/github-actions/ms-app-pack@v1
      with:
        working-directory: 'apps/my-app'
        app-id:        ${{ secrets.PP_SP_CLIENT_ID }}
        client-secret: ${{ secrets.PP_SP_CLIENT_SECRET }}
        tenant-id:     ${{ secrets.PP_SP_TENANT_ID }}

    - name: Deploy app
      uses: microsoft/Managed-Apps/github-actions/ms-app-deploy@v1
      with:
        working-directory: 'apps/my-app'
        app-id:        ${{ secrets.PP_SP_CLIENT_ID }}
        client-secret: ${{ secrets.PP_SP_CLIENT_SECRET }}
        tenant-id:     ${{ secrets.PP_SP_TENANT_ID }}
```

The `paths:` filter runs the workflow only when files inside the app's directory change. In a monorepo with multiple apps, give each app its own workflow file and `paths:` filter.

Important

The `npm install` step must run in your app's working directory before the pack step. `ms-app-pack` builds the app by running `npm run build`, which requires `node_modules` to be present. Use the same `working-directory` for `npm install`, `ms-app-pack`, and `ms-app-deploy`.

That's all you need for the standard workflow: `ms-app-pack` builds and stages the artifact, and `ms-app-deploy` deploys it. The next section covers the actions in more detail, including how to deploy a prebuilt artifact.

## Reference: the GitHub Actions

Reference each action as `microsoft/Managed-Apps/github-actions/<name>@v1`. The `v1` tag moves to the latest release; pin an immutable tag such as `@v1.0.1` for reproducible builds.

`ms-app-pack` and `ms-app-deploy` authenticate with the service principal, so pass these required inputs to each action from the secrets you added in [Step 2](#step-2-add-the-secrets-to-your-github-repository):

| Input | Description |
| --- | --- |
| `app-id` | Service principal client ID. |
| `client-secret` | Service principal secret. |
| `tenant-id` | Microsoft Entra ID tenant ID. |

### install-ms-cli

Installs `@microsoft/managed-apps-cli` onto the runner and adds the `ms` binary to the PATH. It works with no inputs for public npm. To install from a private feed \(for example, Azure DevOps Artifacts\) or to pin a version, set the optional inputs:

| Name | Default | Description |
| --- | --- | --- |
| `version` | `latest` | Semver or `latest`. Pin a specific version for reproducibility. |
| `registry-url` | `https://registry.npmjs.org` | npm registry URL. Override it for internal feeds. |
| `registry-auth-token` | *\(empty\)* | Bearer token or PAT for private registries. |
| `npm-package-name` | `@microsoft/managed-apps-cli` | Override it for testing alternate builds. |

The action outputs `cli-version`, the installed CLI version.

### ms-app-pack

Builds and packs the app by running `ms app pack`. Pack runs the `buildCommand` from `ms.config.json` \(defaults to `npm run build`\) and stages the artifact under `<working-directory>/.ms/packed/`. Use this action before `ms-app-deploy` so build and packaging failures are visible as their own workflow step.

Set `working-directory` \(optional, defaults to the repo root\) to the directory that contains `ms.config.json` and `package.json`, plus the three service principal inputs.

### ms-app-deploy

Deploys to the app's environment by running `ms app deploy`. The action reads `appId`, `environmentId`, and `repoType` from `ms.config.json` and selects the deploy mode automatically. To deploy a prebuilt artifact and skip the build, set `artifact-path`:

```yaml
- uses: microsoft/Managed-Apps/github-actions/ms-app-deploy@v1
  with:
    working-directory: 'apps/my-app'
    artifact-path: '../app.zip'
    app-id:        ${{ secrets.PP_SP_CLIENT_ID }}
    client-secret: ${{ secrets.PP_SP_CLIENT_SECRET }}
    tenant-id:     ${{ secrets.PP_SP_TENANT_ID }}
```

Optional inputs, in addition to the three service principal inputs:

| Name | Default | Description |
| --- | --- | --- |
| `working-directory` | *\(repo root\)* | Path to the directory that contains `ms.config.json`. |
| `commit-sha` | `$GITHUB_SHA` | Commit SHA for git-backed apps. Mutually exclusive with `artifact-path`. |
| `artifact-path` | *\(empty\)* | Path to a prebuilt `.zip` artifact. Valid only for `repoType: 'none'` apps. Mutually exclusive with `commit-sha`. |
| `app-name` | *\(from `ms.config.json`\)* | Override the app name. |

The action outputs `app-id`, `environment-id`, `commit-sha`, and `app-play-uri` for the deployment.

## Troubleshooting

| Symptom | Cause | Fix |
| --- | --- | --- |
| The action reports that it isn't signed in. | The action didn't receive all three service principal inputs. | Pass `app-id`, `client-secret`, and `tenant-id` to both `ms-app-pack` and `ms-app-deploy`. |
| `External artifact deployment is disabled for this environment` | External artifact deployment isn't enabled. | See [External artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment). |
| `Forbidden — 'Repositories.MicrosoftApps.Deploy.Write'` \(Dataverse environment\) | The service principal is missing the required Dataverse roles. | Assign both the **System Administrator** and **System Customizer** roles to the application user. |
| `400 Principal not found` \(non-Dataverse environment\) | You used the app registration's object ID instead of the service principal's object ID. | Use the object ID from **Enterprise applications**, not from **App registrations**. |
| `ms.config.json not found in working-directory` | `working-directory` doesn't point to the directory that contains `ms.config.json`. | Set `working-directory` to that path. The `paths:` filter, `npm install` step, and the actions must all use the same path. |
| `npm error code E401 Incorrect or missing password` | A private registry is configured, but the auth token has the wrong scope or organization. | Make sure `registry-auth-token` is a PAT with the right scope and organization for that feed. |

## Related content

- [Copilot Managed Runtime CLI command reference \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide)
- [`microsoft/Managed-Apps` repository](https://github.com/microsoft/Managed-Apps)
- [Get started with the Power Platform API](https://learn.microsoft.com/en-us/power-platform/admin/powerplatform-api-getting-started)
- [Power Platform for Admins connector reference](https://learn.microsoft.com/en-us/connectors/powerplatformforadmins/)
