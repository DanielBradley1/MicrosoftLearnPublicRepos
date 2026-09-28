<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/connecting-agents-overview -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Connecting agents overview

The Employee Self-Service agent supports a multi-agent model where multiple Copilot agents work together to serve employee needs. This article helps you understand the patterns for connecting agents within the Copilot ecosystem: **hub agent** and **agent handoff**, choose the right approach for your scenarios, and avoid common pitfalls in multi-agent architecture design.

Note

This article covers multi-agent patterns for agents that exist within Microsoft Copilot.

## Patterns at a glance

|  | Hub agent | Agent handoff |
| --- | --- | --- |
| **What it does** | The Employee Self-Service agent coordinates across multiple agents to fulfill a request, synthesizing responses or chaining actions. | The Employee Self-Service agent routes the user to another agent for a domain-specific scenario. The target agent owns the conversation for that task. |
| **User experience** | The user stays in one conversation and the Employee Self-Service agent assembles the answer. | The user remains in the Employee Self-Service agent experience. Context is passed to the target agent so the conversation feels continuous. |
| **Who decides** | The Employee Self-Service agent \(the hub agent\) decides at runtime which agents to involve. | The Employee Self-Service agent decides based on predefined instructions that specify when handoffs should occur. |
| **Example** | "I'm returning from parental leave. What do I need to do for benefits and IT access?" → The Employee Self-Service agent routes queries across HR and IT agents. | "I need to order a laptop" → The Employee Self-Service agent hands off to the procurement agent. |

Tip

These patterns aren't mutually exclusive. The Employee Self-Service agent can use both hub agent and agent handoff depending on the scenario. A single deployment can route across some agents while handing off to others. The right pattern depends on the nature of each interaction.

## Hub agent

In this pattern, the Employee Self-Service agent acts as the router. The hub agent coordinates across multiple connected agents to fulfill a user's request.

### Benefits

- **Unified experience**: The user interacts with a single surface. The Employee Self-Service agent assembles responses from multiple agents without the user needing to know which agent answered what.
- **Runtime intelligence**: The Hub decides which agents to involve based on the user's intent, so the right agents are engaged automatically.
- **Cross-domain scenarios**: Handles requests that span multiple domains in a single interaction \(for example, HR + IT\).

### Considerations

- **Scope management**: The more agents connected, the more important it's to define clear boundaries and routing logic so the Hub engages the right agents accurately.

[Learn more about the hub agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/multi-agent-hub).

## Agent handoff

In this pattern, the Employee Self-Service agent identifies that a user's request belongs to a specific domain and hands off the conversation and context to the target agent. The target agent owns the interaction for that task, but the user remains within the Employee Self-Service agent experience.

### Benefits

- **Seamless experience**: The user stays in the same surface. The Employee Self-Service agent passes full conversation context to the target agent, so the experience feels continuous rather than a disruptive switch.
- **Deep domain expertise**: The target agent can provide a rich, specialized experience without the Employee Self-Service agent needing to understand every detail of that domain.
- **Clear ownership**: One agent owns the task end-to-end, reducing ambiguity in who's responsible for the outcome.
- **Step-up authentication**: Agent handoff supports scenarios where the target agent needs to trigger elevated authentication \(for example, MFA prompt for sensitive actions\). The target agent owns the full session and can manage auth flows directly with the user.

Note

Live agent scenarios also require agent handoff. When a user needs to connect with a human agent, the Employee Self-Service agent hands off the conversation. Live agent support can't be routed with the hub agent.

### Considerations

- **Tone and capability differences**: While the user remains in the Employee Self-Service agent experience, the target agent can respond with a different tone or different capabilities than what the user is accustomed to from the Employee Self-Service agent itself.
- **Return path**: When the user is done with the target agent, they must take an explicit action to return to the Employee Self-Service agent.

[Learn more about agent handoff](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/agent-handoff).

## Choosing the right pattern

These patterns complement each other. Use this table to guide which pattern fits a given scenario:

| Scenario | Recommended pattern |
| --- | --- |
| Request spans multiple domains | Hub agent |
| You want a unified, blended response | Hub agent |
| One domain agent owns the request | Agent handoff |
| The target agent has a rich, specialized experience | Agent handoff |

## Best practices for multi-agent architecture

When connecting multiple agents, keep your architecture simple and maintainable. The following guidance helps you avoid common issues as your multi-agent ecosystem grows.

### Keep your architecture flat—avoid deep nesting

**Don't go more than two levels deep in your agent hierarchy.**

A two-level architecture means: the Employee Self-Service agent \(hub\) connects to worker agents. Those worker agents should **not** connect to their own worker agents.

```
✅ Recommended (2 levels):
Hub → HR Agent
Hub → IT Agent
Hub → Procurement Agent

❌ Avoid (3+ levels):
Hub → HR Agent → Benefits Sub-Agent → Claims Sub-Agent
```

**Why this matters:**

- **Latency**: Each level adds round-trip time.
- **Debugging**: When something goes wrong in a deeply nested chain, tracing the issue across multiple agent boundaries becomes harder.
- **Context loss**: Conversation context degrades as it passes through multiple layers. Each hop risks losing nuance from the original user request.
- **Routing confusion**: Nested agents create ambiguity about which agent should handle edge cases, leading to circular routing or dropped requests.

### Consider alternatives before adding depth

When an agent's scope grows complex, there are several approaches to handle it without adding layers to your hierarchy. The right choice depends on your domain:

- **Extend the existing agent**: Add topics, knowledge, or actions to the current agent rather than creating another worker agent layer. This works well when the scenarios are closely related and share context.
- **Create a separate connected agent at the hub level**: If the scenarios are distinct enough to warrant their own routing logic and instructions, connect a new agent directly to the hub as a peer. Define clear boundaries so the hub can accurately distinguish between them.
- **Use handoff**: Handoff can make sense when an agent requires extension to a new agent within the same domain. It keeps the architecture flat while giving the target agent full control of the interaction.

The key question: **does the complexity warrant a new layer, or can it be handled within the existing structure?** In most cases, flattening \(extending or creating a peer agent\) is preferable to nesting.

Note

**Cross-environment consideration**: Currently, the hub agent model only supports connecting agents within the same environment. Agent handoff can route to agents across environments.

### Scope each agent clearly

Each connected agent should have a well-defined domain boundary. Overlap between agents creates routing ambiguity and inconsistent responses.

- Define what each agent **does and doesn't** handle in its instructions
- Avoid agents with overly broad scopes \(for example, "general HR" is harder to route to accurately than "benefits enrollment" or "leave management"\)
