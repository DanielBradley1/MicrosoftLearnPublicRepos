<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-skills -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Build or reuse skills

Use the skill decisions from your component plan to implement reusable instructions and workflows for the plugin. Each skill should perform a defined job and include the resources, scripts, tools, and ownership information required by its target Microsoft experience.

## Reuse or extend a skill

Before you create a skill:

1. Review approved skills that already perform the required job.
2. Confirm that the skill format and capabilities are supported by the target agent or Microsoft experience.
3. Review its instructions, resources, scripts, tools, and data access.
4. Determine whether you can reuse it as-is, configure it, or extend it.
5. Confirm ownership, versioning, sharing, support, and update expectations.
6. Test the skill with representative inputs and expected outputs.

Create a new skill only when an existing approved skill can't meet the requirement.

## Choose the implementation path

Use the path supported by the selected development tool and target experience.

| Development approach | Start with |
| --- | --- |
| Agent Builder | [Add custom skills with Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-skills) |
| Work IQ Dev Tools | [Build a plugin with Work IQ Dev Tools](https://microsoft.github.io/wiqd/getting-started/build-a-plugin/) |
| Microsoft 365 Agents Toolkit | [Add custom skills with Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-custom-skills) |
| Cowork | [Build plugins for Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365-copilot/cowork/cowork-plugin-development) |

GitHub Copilot can assist with skill instructions, supporting scripts, resources, tests, and repository changes. The target experience and authoring tool determine the supported skill format and runtime.

### Work IQ Dev Tools

WIQD provides two different skill-authoring routes:

- `wiqd plugin add skill` adds a top-level skill to a standalone plugin project. The plugin can be skill-only or combine the skill with supported agents or remote MCP connectors. The entire `wiqd plugin` command tree is alpha.
- `wiqd agent add skill` adds a skill to an existing declarative-agent project. This route uses the `agent-skills` preview flag, which is off by default.

Both routes create a `SKILL.md`-based capability, but they operate on different project types. In the WIQD plugin format, the skill name must match its folder name, and its description should include the phrases that should activate it. See [What is a plugin?](https://microsoft.github.io/wiqd/concepts/plugins/) and the [plugin authoring reference](https://microsoft.github.io/wiqd/getting-started/plugin-reference/).

Static WIQD plugin validation doesn't inspect skill content. After packaging, run package-first deep validation to check the top-level manifest, skill folders, and `SKILL.md` requirements.

## Implement the skill

Complete the applicable work:

1. Define the job, inputs, expected outputs, boundaries, and success criteria.
2. Create or import the skill instructions.
3. Add the required supporting resources and scripts.
4. Configure any connector, MCP-based tool, API, identity, permission, or data dependency.
5. Confirm supported file types, script types, sandbox behavior, storage, and sensitivity requirements.
6. Test expected, ambiguous, unsupported, and failure scenarios.
7. Record the skill version, owner, dependencies, known limitations, and support process.

For current support and runtime constraints, see [Custom skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills).

## Confirm that the skill is working

The skill is ready for integration when:

- The target agent or experience can load and use it.
- Its instructions perform the defined job consistently.
- Required resources, scripts, tools, and data are available.
- Permissions and external dependencies work in the development or test environment.
- Unsupported or failed operations produce understandable behavior.
- Ownership, versioning, limitations, and test evidence are recorded.

Continue with any other components in the plan. When they are complete, [integrate and test your components](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/integrate-test-plugin-components).

## Related content

- [Skills as plugin capabilities](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-skills)
- [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin)
- [Add custom skills with Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-skills)
- [Add custom skills with Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-custom-skills)
