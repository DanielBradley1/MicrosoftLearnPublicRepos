<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/authenticate?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-19 -->

# Sign in and choose your Copilot Studio environment \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Sign in to the CLI and choose your Copilot Studio environment before you create projects or contact cloud services. Start with the installed CLI, an authorized work or school account, and the intended tenant and environment IDs from your administrator.

## Sign in to the intended account

1. Run authentication login:

   ```powershell
   msagent auth login
   ```


   You can also specify the account, tenant, and cloud explicitly. Replace the sample account and tenant with your values:


   ```powershell
   msagent auth login --account 'developer@contoso.com' `
     --tenant '<tenant-id>' --cloud prod
   ```

2. Complete the operating-system broker account picker. When the broker is unavailable, the CLI reports the reason and falls back to device code. Canceling sign-in doesn't trigger fallback. If your policy permits device code and you need to bypass the broker, use device-code login:

   ```powershell
   msagent auth login --device-code
   ```


   To cancel the device-code sign-in flow and terminate the command, press Ctrl+C in the terminal.

3. Inspect authentication status:

   ```powershell
   msagent auth status
   ```


   Check that the account, tenant, and ring are correct. This command shows your saved sign-in details without asking you to sign in again. It doesn't check whether you can currently access the service.

## Select an accessible development environment

1. Use the environment list:

   ```powershell
   msagent env list
   ```


   This service request tests access more directly than saved authentication status. If your environment is missing, verify the tenant, ring, and permissions with the administrator. The CLI doesn't provision environments.

2. Copy the intended environment ID and use environment select:

   ```powershell
   msagent env select '<development-environment-id>'
   ```

3. Recheck authentication status. Success means the saved account, tenant, ring, and selected environment match your intended development context.

Important

Selecting an environment doesn't change where your existing projects, workspace connections, or deployments point. Check their settings separately: evaluations can use the project's original environment, deployment commands use the environment saved in the selected deployment, and `msagent agent pull` uses the workspace's existing cloud connection.

## Switch accounts, tenants, or rings

Use authentication switch for an account already stored locally, followed by environment list and environment select:

```powershell
msagent auth switch --account 'release@contoso.com' --cloud prod
msagent env list
msagent env select '<release-environment-id>'
```

Switching doesn't sign in or acquire tokens. If the account isn't stored, use authentication login with the intended tenant. An ambiguous username requires the exact stored home-account ID.

`--cloud` selects the Power Platform API ring: `prod`, `preprod`, or `test`. It isn't a sovereign-cloud selector or tenant selector. Only use a nonproduction ring when your preview owner directs you to it. For example, ring switching is:

```powershell
msagent auth switch --cloud preprod
```

Your next CLI command uses the selected ring. If you need to sign in or grant consent for that ring, run `msagent auth login --cloud preprod` and follow your organization's sign-in requirements. If the ring name isn't valid, the CLI reports an error instead of connecting to production.

If you sign in without `--cloud`, the CLI keeps that account's saved ring. For a new account, it uses the active account's ring, or `prod` if this is your first sign-in.

Changing the account, tenant, or ring clears your saved environment selections, so select your environment again afterward. Switching back doesn't restore an earlier selection. Signing in again with the same account, tenant, and ring keeps your selection.

## Sign out and recover access

On shared machines, use authentication logout:

```powershell
msagent auth logout
```

Logout clears all local CLI profiles, not only the active one, and best-effort clears the CLI token cache. It doesn't sign out the operating-system broker or other apps. Stored environment selections can't be used while signed out.

For expired credentials or missing consent, reauthenticate interactively with the intended account and tenant, then verify service access and targeting again. Don't disable organizational identity protections or enable an unprotected cache as a default recovery action.

The CLI rejects authentication login with non-interactive mode, even if a token might be available silently. That flag doesn't provide application or service-principal login.

## Next steps

[Create a new agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide)

[Open an existing definition](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/open-existing-agent?view=o365-worldwide)
