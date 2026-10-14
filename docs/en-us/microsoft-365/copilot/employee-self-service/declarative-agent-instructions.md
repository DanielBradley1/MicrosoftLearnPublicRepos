<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-instructions -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Craft agent instructions for the Employee Self-Service declarative agent

Note

This article applies to the Employee Self-Service declarative agent. For the Employee Self-Service custom engine agent, see [Craft agent instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/design-best-practices).

The Employee Self-Service agent is a template in Microsoft Copilot Studio that can be infinitely customized to assist users in your organization with HR and IT tasks. Use guidance here to learn more about how to craft high-quality responses using a mix of techniques to fit your ideal response.

## About response quality

A great response is **accurate, actionable, and engaging** to ensure we earn trust, provide useful responses, and help the user take the next step using self-service tools. The Employee Self-Service agent requires a blend of design elements, agent instructions, and conversational design techniques to craft great responses.

## How responses are formed

Responses are a combination of **instructions, knowledge, topics, data from connectors, and UI elements**. Employee Self-Service agent responses combine these elements to deliver accurate, actionable, and trustworthy experiences. This approach solves common challenges like ambiguous intent, inconsistent tone, and static answers by ensuring structured guidance, personalized context, and interactive components that move tasks forward.

## Instructions: Define voice, behaviors, and reasoning

Instructions act as a blueprint for tone, structure, and decision-making across workflows, preventing fragmented user experiences. Instructions specify clear role definitions and handoff rules to prevent agents from giving redundant or conflicting answers.

- **Global agent instructions on the overview page**: Apply to the entire agent to maintain consistent tone, style, and decision-making.
- **Workflow-level instructions and triggers in topics**: [Guide specific scenarios](https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-generative-answers-prompt-modification) or tasks, ensuring responses follow the right logic and conversational flow.
- **Advanced knowledge instructions**: Provide detailed guidance on how to use or prioritize knowledge sources \(for example, specify which user context variables to prioritize\).
- **Channel description for Teams and Microsoft Copilot**: Give instruction on intent recognition between domains and similar scenarios. [Channel instruction](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-add-bot-to-microsoft-teams) ensures accurate intent routing, consistent user experience across domain agents, and drives actionable responses for a multi-domain deployment.

### Knowledge and data: Ensure accuracy and personalization

[Knowledge](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-existing-copilot) and data connectors eliminate guesswork, ensuring answers are factually correct and personalized to the user's role, organization, and intent.

- **Knowledge sources**: Your enterprise content from SharePoint or other knowledge bases like ServiceNow.
- **Data connectors**: Pull real-time, contextual data from content management systems and connectors like Workday, ServiceNow, or SAP to personalize responses. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-copilot-connector) about Copilot connectors.

### UI Elements and actions: Build trust and enable action

UI elements like Adaptive cards, inline actions, and references turn static responses into interactive workflows.

- **Disclaimers and badges**: Increase transparency and compliance.
- **Adaptive cards and rich components**: Allow users to act directly within the conversation \(for example, approve requests, order a new device, file an HR ticket\).
- **Actions**: Uses trigger integrated actions, like creating tasks, updating records, or generating content, directly from chat, so they can complete work without switching apps.

## About writing instructions for your Employee Self-Service agent

When you're designing global system prompts for an AI agent, especially one deployed across various domains, languages, and use cases, it's crucial to define clear, consistent instructions. These instructions should shape the agent's behavior, tone, boundaries, and adaptability. These prompts act as the backbone of how the agent interprets and responds across all interactions.

To begin with:

- Start with a clear identity statement. Example: "*I'm a friendly, knowledgeable workplace assistant. I explain things simply and clearly, like a helpful teammate.*"
- Use behavioral examples. Do: Give concise answers in 2-3 sentences. Don't: Use jargon or long-winded explanations.
- Incorporate metaphors or analogies. "*Speak like a trusted representative, not a technical manual.*"
- Add adaptive instructions. "*Use a more direct tone during troubleshooting. Be warmer and more supportive when helping with HR questions.*"
- Plan to reference variables in instructions. "*Prioritize information and entities mentioned in `userprofile`.*"

### Developing agent personality to define content strategy

An agent's role and identity shape every interaction it has with users. When well-defined, the agent feels purposeful, trustworthy, and aligned with your product or service. When vague or inconsistent, it can create confusion, damage credibility, and lead to misaligned responses. Users need to understand who they're talking to, why that agent exists, and what they can expect from the conversation.

This context is especially critical in enterprise and productivity settings, where users rely on agents to act with clarity, accuracy, and consistency. A strong sense of role and identity reduces ambiguity for both the user and the underlying model.

### Persona definition and context

When supporting sensitive areas like HR and IT, it's especially important that the agent reflects the organization's professional yet approachable tone. Match the agent's communication style to how your organization speaks with employees in internal documentation, help centers, and service desks.

1. **Choose 3-5 key attributes**: Define a small set of core traits that capture the agent's personality. These attributes should reflect your organization's internal culture, and the expectations employees have when seeking help with HR or IT topics.
2. **Document with examples**: Pair each personality trait with example triggers and phrases to help the LLM map user intent with conversational context.
3. **Adapt for context**: Maintain a consistent core personality but allow tone to flex slightly based on task type. For instance, you may decide IT troubleshooting calls for a more direct tone, while HR topics require a bit more empathy and care.

#### Tangible examples

Give the agent tangible examples of how the agent sounds for specific scenarios:

- **Adapt to emotion type**: Grief/Loss: "I'm so sorry for your loss. Let's handle this with care."
- **Stress/Anxiety/Overwhelm**: Normalize, break steps down, set timelines. Performance Anxiety \(for example, promotion concerns\): Reassure effort, note many feel this way, provide clarity and next steps.
- **Frustration/Confusion** \(for example, because of denied leave or form overload\): Validate emotion, explain simply, simplify process.
- **Urgency/Crisis**: Recognize urgency, prioritize fastest fix.

  - Do: Rotate empathetic phrases \("This sounds challenging," "I get why this is frustrating"\), then transition \("Here's how we can tackle this step by step"\). Provide guidance, resources, and escalation if needed.
  - Don't: Provide counseling, medical/legal advice, or overpromise certain outcomes.

The Employee Self-Service declarative agent already ships with instructions for empathetic responses. For details, see [Built-in instructions for empathy and clarification](#built-in-instructions-for-empathy-and-clarification).

### Write instructions that influence response structure

Writing clear instructions that shape the agent's response format is essential for ensuring readability and comprehension for specific kinds of answers. Copilot Studio allows Markdown in the instruction field, which isn't just for looks. It helps the AI parse your intent.

- Use headings, lists, and emphasis to structure the instructions.
- Use # Headings to label sections like "Objective", "Steps", "Guidelines".
- Use bullet points \(-\) for unordered lists \(general rules, multiple options\) and numbered lists \(1. 2. 3.\) for ordered sequences.
- Use backticks to denote tool or system names \(CRM Database, SalesReport\), so they stand out clearly.
- Bold critical keywords or whole lines if something is extremely important \(for example, "Always verify customer identity before proceeding."\).
- Keep different topics in separate paragraphs or list items. If providing example dialogues, set them apart \(for instance, start a new section or use a block quote\) to avoid mixing them with actual rules.

### Define non-standard words or acronyms

If your instructions mention internal jargon, product names, or acronyms that aren't universally known, define them in the instructions. For example: "CRM = Customer Relationship Management \(our client database\)." This ensures the AI doesn't misunderstand these terms and can even explain them to a user if needed. It's common to add a "Glossary" or "Definitions" section at the end of instructions for this purpose. This is particularly useful if the agent's domain is specific \(legal terms, medical terms, company codenames, and so on\).

### Define boundaries and fallback plans.

When crafting system prompts, you're guiding how the agent behaves in different contexts and not just what it says. Clear instructions help the agent respond responsibly, stay within scope, and build user trust. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-system-fallback-topic) about the system fallback topic.

Examples:

- Don't speculate or make up responses when unsure. Say you don't know and suggest a next step or escalation path.
- For sensitive topics \(for example, complaints or personal conflict\), don't offer advice. Recommend contacting HR or another trusted internal support.
- Only call the Inventory API if the product ID is provided; if not, politely ask the user for the product ID instead of guessing.

#### Include instructions on handling unsupported requests.

Instruct the agent to help the user understand what can be answered using this agent. Guide the agent to respond helpfully when it can't fulfill a request, by explaining its limitations and pointing users to the correct next step.

Examples:

- If you receive a request outside your scope, respond clearly and courteously.
- If a request falls outside of supported HR or IT tasks, say something like: 'I'm here to help with common HR and IT questions. For this type of request, reach out to \[support contact or system\].'
- When you can't complete a task, guide the user toward a resource, article, or help form. Always prioritize official knowledge sources first.

### Built-in instructions for empathy and clarification

The Employee Self-Service declarative agent ships with agent instructions that make it respond with empathy and ask clarifying questions when a request is unclear. The custom engine agent used separate topics for these behaviors: *Seek emotionally intelligent response* and *Seek clarification to avoid ambiguous answers*. In the declarative agent, there are no topics to turn on or off. To change these behaviors, edit the relevant parts of the agent instructions.

#### Emotional intelligence

When an employee's message shows stress, frustration, grief, or other emotional cues, the agent:

- Acknowledges the employee's feelings first, then helps with the task by offering relevant knowledge, topics, or options.
- Points employees to the Employee Assistance Program \(EAP\) or the People team only in severe cases or when they explicitly ask for support.
- Stays within boundaries. It never provides counseling or legal, medical, or financial advice, makes promises beyond its authority, compares your organization to others, ranks or evaluates employees, speculates on confidential matters, investigations, or personnel decisions, or makes policy exceptions.

**Example:** An employee says, "My dad passed away and I need to take time off." The agent acknowledges the loss with care, then gives clear steps for requesting bereavement leave.

Note

These instructions make responses supportive in tone while keeping them factually accurate and within appropriate boundaries. They don't replace human care or decision-making. The agent doesn't infer mental health conditions, store emotional states, or use this information to profile employees.

#### Clarifying ambiguous requests

The agent decides whether to search first or ask a clarifying question:

- **Searches first** when the request is specific enough to be useful, for example when it names an action, process, system, time period, or scenario. Some ambiguity about which knowledge article applies never blocks the first search. The agent retries once with a synonym if needed.
- **Asks before acting** only when the request is a broad umbrella term or when the ambiguity would change which action, policy, or topic applies. Examples of broad umbrella terms are access or permissions, a general IT symptom, device, software, network, account, security, pay, an unexplained acronym, ambiguous pronouns, or overlapping topics. Details in a request only resolve the ambiguity they address. If the target of an action is still unclear, such as which ticket to update, the agent asks.
- **Asks one question at a time.** It acknowledges the request and asks one question with two to five named options plus "something else". It doesn't answer, search, or cite sources until the employee replies.
- **Asks for missing details after searching.** If the knowledge source is missing a detail it needs, the agent asks one concise question. It doesn't fill the gap from general model knowledge.
- **Follows topic descriptions.** Topic descriptions are authoritative. If a description excludes a request, the agent uses the alternative it points to.

**Example:** An employee asks, "I need help with access." The agent replies with something like, "Happy to help. Which do you need access to: a shared mailbox, a SharePoint site, an app, or something else?"

#### Customize or test these instructions

1. Open the Employee Self-Service agent in Copilot Studio and go to the agent instructions.
2. Find the emotional cues or clarification guidance and edit it to fit your organization. For example, name your own EAP or support team. Keep the **Never** boundaries.
3. Publish your changes.

Before you release changes broadly, test with real prompts and check:

- **Empathy:** Does the agent acknowledge emotion before solving the problem? Is the tone right for the situation? Does it still complete the task?
- **Clarification:** Does it ask only when the request is truly ambiguous? Is it one targeted question with named options? Does it avoid guessing when information is missing?

### Influence behaviors by referencing variables in instructions

You can type instructions in plain text. At any point within the instructions, you can [type /](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-instructions#add-or-change-agent-instructions) to add a reference to a specific object, such as a tool, topic, [variable](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-variables-about?tabs=webApp), or Power Fx expression.

#### Add user context variables to map intent to users' data

To deliver personalized responses, the Employee Self-Service agent needs to understand both user intent and context. For example, the same question may require different answers for employees in Germany versus India because policies vary by region. To enable this, we've created a dedicated topic called User Context - Setup that defines variables representing key user attributes like level, country/region, and role. Once this topic is set up, you can reference these variables in your agent instructions to ensure responses are tailored to your organization's context.

User context variables allow your Employee Self-Service agent to personalize responses by using attributes like name, job title, and country/region. These variables are created either as system variables \(such as System.User.DisplayName\) or global variables \(such as Global.ESS\_UserContext\_Country\_Code\) that persist across topics.

To add them to your instructions, open the **Variable Properties** pane and set the scope to Global. For integration with Microsoft Entra or other content systems, use environment variables to securely pass user attributes into your agent. When customizing instructions, reference these variables to tailor responses and ensure they align with your configured topics and data sources.

##### How to edit variables

1. In the topic's menu bar, select **Variables**. This opens the **Variables** pane, which lists all variables associated with that topic.
2. From the **Variables** pane, select the variable you want to edit. This opens the **Variable Properties** pane.
3. In the **Variable Properties** pane, you can:

- Change the variable's name.
- Track its usage.
- Convert it to a global variable \(**Note**: once global, it can't be reverted to topic-level\).
- Configure whether it can accept values from or share values with other topics.

#### Name tools and knowledge sources explicitly

Refer to your agent's tools, connectors, and knowledge bases by their exact names in the instructions. The agent uses tool names and descriptions to decide what to call, so guiding it by name removes ambiguity. For example, instead of saying "check if there's any outage" say "call the ServiceNow Outage Lookup action to check for outages."

If you have a SharePoint file as a knowledge source, mention it: "Use Employee Handbook knowledge source to answer policy questions." Using the precise names ensures the agent doesn't confuse one tool for another, especially if you have several configured.

Slight differences in naming can affect results, so use the tool's exact name as configured. This practice ties into the earlier point: instructions must be grounded in what you've actually added to the agent. If the agent has numerous tools, naming the right one in context is even more helpful to avoid mistakes.

## Create a test plan to measure the quality of your Employee Self-Service agent's responses

This testing guide helps you evaluate the quality of your customized agent experience using standard quality frameworks. Whether your agent supports HR, IT, or other employee experience scenarios, this guide provides a consistent way to assess the helpfulness and trustworthiness of responses.

This guide is especially useful during pilot phases, as you update instructions, tune knowledge sources, or refine your agent's behavior across different business units or geographies.

Response quality principles:

- **Accurate**: The information is correct. The response gives the right answer based on trusted sources, with no guesses or misleading details.
- **Complete**: Nothing important is missing. The response includes all the key information the user needs, so they don't have to ask again or look elsewhere.
- **Relevant**: It fits the user's intent. The response is relevant to the question and considers the user's role, region, or past activity.
- **Useful**: It helps the user act by moving the user forward.
- **Exceptional**: It's exceptional. The response is more helpful than websites or chat tools.

### How to approach establishing benchmarks

Testing response quality and setting clear benchmarks help teams identify what's working well and where improvements are needed. Over time, this testing leads to more accurate, helpful, and personalized conversations that build trust and deliver better results for users. Each response can be scored from 1 \(poor\) to 5 \(exceptional\) across each category. Total score per response = 5 \(poor\) to 25 \(exceptional\).

Use benchmark scores to understand how well the agent is meeting user expectations. A score of around 15 means the response is good because it's functional, accurate, and meets the basic need. A higher score, like over 20, means the response is great or exceptional, offering more value, personalization, and ease of use.

### Tips for benchmark testing

1. Track quality using consistent prompts: Retest them after updates to knowledge sources, instructions, or workflows to compare improvements.
2. Vary the input styles: Try different prompt formats for the same intent:

- Keywords: "benefits enrollment"
- Phrases: "enroll in health insurance"
- Full questions: "How do I sign up for 2025 benefits?" The agent should respond well to all or ask for clarification when needed.

3. Test across scenarios and roles: If your deployment serves multiple departments or regions, test prompts from each area. A response that's relevant to IT might not make sense for HR, or vice versa.
4. Always test edge cases: Responses should gracefully handle:

- Unclear or vague inputs
- Topics outside the current scope
- System errors or unavailable data
- Sensitive topics

## How to troubleshoot common issues

### Fix issues with citations

Add these instructions to help reinforce consistent use of citations to knowledge sources for each response:

WHEN GENERATING A SUMMARY ALWAYS MAINTAIN ALL CITATIONS.

**Preserve all tags in the format \[^x\_y^\] exactly as they appear, including those from tool outputs and search\_result.** Don't alter, add, or remove any tags. x and y may be one or more digits \(for example, \[^17\_1^\], \[^539\_12^\]\). These tags serve as citations and must be retained in the final response.

## More design resources

[Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-instructions) about writing instructions in Copilot Studio.
