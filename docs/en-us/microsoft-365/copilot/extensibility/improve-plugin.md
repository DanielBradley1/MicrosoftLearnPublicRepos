<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Improve and update your plugin

Improve your plugin by using monitoring evidence and evaluations to find what needs to change. Apply the fix or improvement, release the exact package you tested, and confirm that the updated plugin keeps working for intended users.

Builders maintain and test the package. Microsoft 365 administrators complete organizational rollout actions when required. Service owners maintain the connectors, remote MCP servers, identities, and external services the plugin uses.

## Before you begin

Have:

- The current plugin identity and package version.
- How the current version reached users: direct sharing, administrator upload, or Microsoft Marketplace.
- Monitoring evidence, user feedback, support cases, or a planned improvement.
- Representative tasks and acceptance criteria.
- The affected users and Microsoft 365 experiences.
- Access to the plugin source and affected capabilities.
- Owners for required connections and external services.

If you don't yet know what needs to change, start with [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin).

## Establish a baseline

1. State the problem or improvement you want to address.
2. Identify the affected package version, users, experiences, capabilities, and dependencies.
3. Define representative tasks and measurable acceptance criteria.
4. Run the tasks against the current package and record the results.
5. If your organization administers the plugin, record its current status, user availability, and installation state in **Agents** > **Tools** > **Plugins**.
6. Preserve the evidence you need to compare the current and updated behavior.

For a plugin that includes an agent, use [Agent evaluation overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluation-overview) to design an evaluation when response quality, instructions, knowledge, or tool use is part of the change. Evaluation can provide pre-release evidence and help investigate post-deployment quality concerns, including those raised by usage signals, user feedback, or agent and dependency changes.

Agent evaluation isn't required for every plugin. It doesn't replace capability testing, package validation, or testing the complete user experience.

For deployed declarative agents, use the guided [`wiqd agent eval` workflow](https://microsoft.github.io/wiqd/extensions/provided/eval/). For direct command-line or pipeline control, see [Agent Evaluations CLI overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-overview).

## Apply and test the change

1. Update the plugin source or affected capability.
2. Update separately operated services or configuration when the change requires it.
3. Test each changed capability and affected dependency.
4. Run the baseline tasks and evaluations again.
5. Compare the results with the acceptance criteria.
6. Investigate regressions before you create the release package.

When the change affects a connector, remote MCP server, identity, permission, or external service, involve the owner of that dependency. Don't assume that changing the package updates a separately operated service.

## Create and validate the package

1. Assign a new package version and check the identity requirements for your publishing method.
2. [Create the plugin package](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/package-plugin).
3. [Validate and test the exact package](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/validate-plugin) you intend to release.
4. Test required sign-in, consent, connections, and external services.
5. Test the package in every Microsoft 365 experience you intend to support.
6. Record known limitations, required configuration, and the available rollback or replacement option.

Don't publish a package that differs from the package you validated.

## Publish and roll out the update

Choose a [supported publishing or sharing method](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish) for the updated package and intended audience. Check its instructions for how to update an existing plugin; don't assume that sharing or uploading a new version replaces its registry entry or carries over availability settings.

| How the current version reached users | Where to start with the update | Who acts |
| --- | --- | --- |
| Direct sharing | Follow the same tool's [sharing instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish#share-your-plugin-directly) for the tested package and intended audience. | Plugin owner |
| Administrator upload | Give the tested package to the administrator, who follows [Upload plugins or skills](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#upload-plugins-or-skills) and verifies the resulting registry entry and user scope. | Plugin owner and administrator |
| Microsoft Marketplace | Check the supported offer type and follow the applicable Partner Center procedure linked from [Publish your plugin through Microsoft Marketplace](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish-plugin-publicly). Wait for any required review and publication before directing customers to the update. | Publisher and customer administrator, where needed |

Before release, confirm whether the method reuses the package identity or creates a separate entry, whether previous user availability and installation settings carry over, and how to replace or restore a version if needed. If a second entry appears, verify that intended users have moved to the new version before restricting the old one. Don't remove an entry still in use.

Then:

1. Publish, upload, or share the exact tested package by the selected method and record whether it was submitted, published, shared, rejected, or blocked.
2. Give the administrator or rollout owner the exact package version, intended users, required configuration, known limitations, and support contact.
3. Complete only the applicable steps to [make the updated plugin available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin). Approval, assignment, and installation requirements depend on the method and organization settings.
4. Update separately controlled agents, connections, identities, remote MCP servers, or external services when required.
5. Confirm which package version reached each audience.

For an alpha Work IQ Dev Tools plugin, `wiqd plugin share` publishes to the plugin registry for the selected audience; public-store submission happens separately in Partner Center. Follow the [Work IQ Dev Tools plugin guide](https://microsoft.github.io/wiqd/getting-started/build-a-plugin/) for its provision, package, validate, and share sequence when preparing another release.

Before rollout, confirm whether the method supports restoring a previous version. Replacing the package doesn't automatically restore an external service, connection, identity, data, or permission change.

## Verify the update

1. Test the representative tasks with an intended user in each supported experience.
2. Confirm that the user received the expected package version.
3. Confirm that sign-in, consent, connections, tool calls, and external services work.
4. Where the plugin is administered in your organization, check that its status, user availability, and installation state match the intended audience in **Agents** > **Tools** > **Plugins**. Check for any superseded version still in use.
5. Repeat the evaluations used to approve the change.
6. Review usage signals, feedback, errors, and support cases after rollout.
7. If the update fails its acceptance criteria, follow the supported rollback or replacement procedure and restore affected dependencies when required.

The update is complete when the intended audience has the correct package version, its access settings match the intended rollout, the representative tasks meet their acceptance criteria, and every unresolved issue has an owner and next action.

## Record the update

Record:

- Previous and updated package versions.
- Change, reason, affected capabilities, and dependencies.
- Baseline, evaluation, validation, and user-test results.
- Publishing method, audience, rollout status, and applicable registry state.
- Configuration or service changes.
- Known limitations, rollback option, and support owner.

## Related content

- [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin)
- [Package your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/package-plugin)
- [Validate and test your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/validate-plugin)
- [Publish or share your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish)
- [Make your plugin available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin)
- [Manage plugins, skills, and MCP servers](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context)
- [Retire your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/retire-plugin)
