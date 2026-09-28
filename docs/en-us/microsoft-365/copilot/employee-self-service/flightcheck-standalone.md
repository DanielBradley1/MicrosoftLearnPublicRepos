<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/flightcheck-standalone -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Run FlightCheck without installing the full Agent Developer Kit

FlightCheck runs a predeployment readiness check against your Employee Self-Service agent. It validates licenses, environment configuration, identity, integrations, agent files, and publishing readiness across more than 40 verifications.

If you only want to run FlightCheck and you don't need to customize your agent, you don't need to install the full Agent Developer Kit, Visual Studio Code, or GitHub Copilot. The FlightCheck-only installer sets up the minimum needed \(Python and Git\) and runs the check for you.

Use FlightCheck-only when:

- You're an administrator triaging a customer issue and want a single report.
- You're getting ready to publish and want a final readiness check.
- You don't have a GitHub Copilot subscription, or your role doesn't require one.

If you already use the full kit, run FlightCheck through `/flightcheck` in Copilot Chat. See [Commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/commands-reference#flightcheck-readiness-check).

## Before you start

You need:

- A Windows 10 or Windows 11 machine where you can install software.
- A work account with the **Environment Maker** role in the Power Platform environment that has Employee Self-Service installed.
- Permission to run PowerShell with internet access.

## Run the installer

1. Open **PowerShell** \(Windows key, type `powershell`, select **Windows PowerShell**\).
2. Paste this command and select **Enter**:

   ```powershell
   iex (irm https://raw.githubusercontent.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/main/setup/bootstrap-flightcheck.ps1)
   ```

The installer prints what it's about to do, then walks you through the rest.

Tip

On macOS, Linux, or any device where you can't install software, run FlightCheck from a [GitHub Codespace](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-codespaces) instead. After the Codespace opens, run `python scripts/flightcheck/cli.py --scope full` from the integrated terminal.

## What happens

The installer:

1. Installs Python and Git if you don't already have them.
2. Opens a browser window. Sign in with your Microsoft work account that has access to the Power Platform environment.
3. Shows your available environments. Pick one by number.
4. Shows the agents in the environment. Pick one, or skip to run environment-level checks only.
5. Runs FlightCheck and shows the results.

The check produces an HTML report you can share with stakeholders. When FlightCheck finds an issue it can resolve, it offers to fix the issue for you.

## You should see

When FlightCheck finishes, the terminal prints a summary like:

```text
FlightCheck complete
  Licenses:     ok
  Environment:  ok
  Identity:     ok
  Integrations: 1 warning
  Agent files:  ok
  Publishing:   ok
Report saved to ...\flightcheck-report.html
```

The full report opens in your browser. Each section lists what was checked, what passed, and any issues with suggested fixes.

## Run FlightCheck again

After the first run, you can rerun FlightCheck directly without going through the installer:

```powershell
cd $env:USERPROFILE\source\Employee-Self-Service-Agent-Developer-Kit\solutions\ess-maker-skills
python scripts/flightcheck/cli.py --scope full
```

## Switch environment or agent

Run the original installer command again. It detects the existing install and asks if you want to reconfigure:

```powershell
iex (irm https://raw.githubusercontent.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/main/setup/bootstrap-flightcheck.ps1)
```

Select the new environment and agent when prompted.

## Next step

After FlightCheck reports a clean run, see [Publish the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish) to take the agent live.

If the installer fails or FlightCheck can't reach your environment, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).
