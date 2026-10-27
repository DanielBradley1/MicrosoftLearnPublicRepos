<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/microsoft-365-education-ai-application-card -->
<!-- Sitemap-Last-Modified: 2026-10-21 -->

# Application card: AI in Microsoft 365 Education

## What is an application or platform card?

Microsoft’s application and platform cards are intended to help you understand how our AI technology works, the choices application owners can make that influence application performance and behavior, and the importance of considering the whole application, including the technology, the people, and the environment. Application cards are created for AI applications and platform cards are created for AI platform services. These resources can support the development or deployment of your own applications and can be shared with users or stakeholders impacted by them.

As part of its commitment to responsible AI, Microsoft values six core principles: fairness, reliability and safety, privacy and security, inclusiveness, transparency, and accountability. These principles are embedded in the [Responsible AI Standard](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Responsible-AI-Standard-General-Requirements.pdf?culture=en-us&country=us), which guides teams in designing, building, and testing AI applications. Application and platform cards play a key role in operationalizing these principles by offering transparency around capabilities, intended uses, and limitations. For further insight, readers are encouraged to explore Microsoft’s Responsible AI Transparency Report and Code of Conduct, which outline how enterprise customers and individuals can engage with AI responsibly.

## 1. Overview

Microsoft 365 Education AI brings generative AI capabilities to Microsoft 365 experiences for education organizations. Educator-facing capabilities help draft instructional content, organize class materials, create practice activities, and review suggested feedback. Eligible learners can use supported experiences for guided practice, coaching, and study. Intended customers are education organizations using eligible Microsoft 365 Education products. Intended users include educators, education administrators, and eligible learners. Licensing, age requirements, administrator controls, and availability differ by feature.

The capabilities use generative models to produce plans, questions, activities, stories, feedback, or conversational responses from user instructions and, where supported, source material. Educator-directed capabilities produce editable drafts that an educator can revise, regenerate, accept, or discard. Learner-facing capabilities operate inside defined learning workflows with constrained inputs, safety controls, or age and tenant eligibility requirements. Feedback capabilities produce suggestions that an educator reviews before returning them to a learner.

This card covers the generative AI capabilities listed in [section 3](#3-key-features-and-capabilities). It explains their intended uses, operating conditions, limitations, evaluations, safety measures, and deployment practices. Predictive analytics, automatic error detection, speech recognition, recommendation systems, and other non-generative AI features are outside its scope unless they directly support a listed generative capability.

For information on Microsoft 365 Copilot and Microsoft 365 Copilot Chat in Education, see this application card: [Application card: Microsoft Copilot \(for organizations\) \| Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-application-card)

## 2. Key terms

The following list provides a glossary of key terms related to Microsoft 365 Education AI:

- **Content grounding:** Information supplied to a generative AI capability to make an output more relevant. Grounding might include instructions, uploaded files, standards, curriculum content, or content already present in the product.
- **Educator-directed generation:** A workflow in which an educator requests a draft and decides whether and how to use it.
- **Generative AI:** AI that creates new content, such as plans, questions, activities, stories, or feedback.
- **Human oversight:** Review and judgment by a responsible person before relying on an AI output or using it in a consequential process.

## 3. Key features and capabilities

The key features and capabilities outlined here describe what Microsoft 365 Education AI is designed to do and how it performs across supported tasks.

- **Teach planning and content:** Lesson Plans, Quiz, Unit Plans, Rubrics, Minecraft Lesson Plans, and Modify Content generate editable instructional drafts or revisions from educator instructions and, where supported, source material. Educators decide whether and how to use the output.
- **Teams Assignments:** Assignment Instructions drafts task directions, while AI Feedback Suggestions proposes feedback on learner work. Educators review and edit these suggestions before sharing them with learners.
- **Teams Classwork:** Module Generation proposes module titles and descriptions from educator input. Educators can edit or discard the suggestions.
- **Learning Activities:** Flashcards, Quiz, Matching, and Fill in the Blanks generate practice from source content for educators or eligible learners age 13 or older. Flashcards support practice, not grading.
- **Reading Progress:** Passage Generation drafts reading passages, and Comprehension Question Generation proposes questions and expected answers. Educators review the results before assigning them.
- **Math Progress:** Short answer math questions can have various “correct answer” formats. Answer checker reviews responses for correctness. Educators review the results and must confirm before returning work.
- **Learning Zone:** Interactive Lesson Generation produces an editable lesson outline, content slides, and exercises with immediate learner feedback. Educators review the lesson before assigning or sharing it.
- **Reading Coach:** Generated Stories creates personalized reading practice from constrained learner choices. Stories appear to learners without routine human review before display.
- **Speaker Progress:** AI Feedback drafts summary and sentence-level feedback from learner speech transcripts. Educators review and can edit it before returning it.
- **Study Guide in Copilot Notebooks:** Study Guide generates multi-page study companions grounded in provided learning materials, including concept summaries and practice activities such as flashcards and quizzes. Eligible learners age 13 or older use the generated material to review and practice.
- **Study and Learn Agent:** The Study and Learn agent gives eligible learners age 13 or older tutoring without giving away answers or doing the work for learners, and practice activities. It can create or read supported learning resources through approved tools; educators can't view learner conversations in this experience.
- **Class Insights Agent:** the Class Insights agent helps educators understand trends and gain deeper insights from data from assignments, grades, feedback, and rubrics. This agent is only available for educators, and they have access only to classes they teach.

## 4. Intended uses

Microsoft 365 Education AI supports teaching and learning workflows in eligible education organizations. Some examples of use cases include:

- **Prepare a class:** An educator can draft a lesson, unit, rubric, assignment, or Classwork module. The draft gives them a starting point for planning. They check accuracy and fit with their curriculum and learners before using it.
- **Create practice:** Educators can generate reading passages, comprehension questions, interactive lessons, or activities from source material. Learners can practice with flashcards and other supported activities. Educators check generated questions and answers before sharing them.
- **Support reading and speaking:** Learners can practice with personalized Reading Coach stories. Speaker Progress suggests feedback on a learner’s speech for an educator to review and edit. These experiences support practice and coaching rather than definitive assessment.
- **Guide independent study:** Eligible learners can generate a Study Guide from learning materials in Copilot Notebooks to review key concepts and practice activities. Separately, learners age 13 or older can ask Study and Learn for explanations and hints or practice with quizzes and flashcards. These tools support learning and practice rather than replacing the learner’s work.
- **Understand and adjust to student performance:** Educator can use the Class Insights agent to understand where students are in their journey. It gives educators insights in what topics or what part of the curriculum they are struggling with and help them identify supportive next steps for the learner.

The following boundaries apply:

- Learning Activities support practice rather than secure assessment. Activities might reveal answers, and lesson completion information or scores synchronized through an assignment workflow indicate participation or completion rather than reliable mastery of the subject. These experiences don't replace complete study materials, educator judgment, or a validated grading process.
- Educator-directed generation and feedback require educator review. No generated content or feedback should be used to assign grades automatically.
- Study and Learn supports understanding, study, and practice, not assignment completion or educator assessment of learner understanding.
- None of these capabilities is intended to make autonomous decisions about grades, discipline, placement, admissions, accommodations, special education eligibility, or access to education services.

## 5. Models and training data

Microsoft 365 Education AI uses a variety of AI models to power the experience that users see. Examples include Phi Silica and GPT-family models described in the [Azure OpenAI Service transparency note](https://learn.microsoft.com/en-us/legal/cognitive-services/openai/transparency-note).

Learning Zone combines a cloud-based large language model with Phi Silica on supported Copilot+ PCs. Phi Silica runs locally through Windows AI APIs. Its inputs and outputs stay on the device during local execution.

Study and Learn works as a Microsoft 365 Copilot declarative agent and uses the models selected by that service.

Customer content, inputs, and conversations aren't used to train foundational AI models. Microsoft 365 Education AI complies with Enterprise Data Protection. Learn more [here](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection).

## 6. Performance

Microsoft 365 Education AI works best within each capability’s intended education workflow, with clear instructions and relevant source material. Results can vary with the subject, learner level, input quality, language, and model version. Repeating a request can produce a different answer. Educator review remains important even when the output appears complete.

Most capabilities take typed instructions or text extracted from supported source files and produce plans, questions, activities, stories, feedback, or conversational responses. Speaker Progress follows a different input path: it captures learner speech, converts that speech into a transcript, and generates feedback from the transcript rather than directly from the audio. Supported input formats and file types vary by feature and should be checked in the relevant product documentation.

Generative language support differs by feature and by task. Most features automatically are detected based on user inputs and are validated and supported for the following languages: **English** \(United States\) en-US, **German** \(Germany\) de-DE, **Spanish** \(Spain\) es-ES, **Norwegian Bokmål** \(Norway\) nb-NO, **French** \(France\) fr-FR, **French** \(Canada\) fr-CA, **Spanish** \(Mexico\) es-MX, **Portuguese** \(Brazil\) pt-BR, **Japanese** \(Japan\) ja-JP, **Dutch** \(Netherlands\) nl-NL, and **Swedish** \(Sweden\) sv-SE.

Study and Learn agent has been validated and supported for the [languages listed here.](https://support.microsoft.com/education/copilot/study-learn-agent#supported-languages)

Reading Coach has been validated and supported for the [languages listed here.](https://support.microsoft.com/education/learning-accelerators/getting-started-with-reading-progress-in-teams#tabpanel_1_supported-languages)

Learning Zone has been validated and supported for the [languages listed here.](https://support.microsoft.com/education/learning-zone/microsoft-learning-zone-interactive-lesson-generation#supported-languages)

Availability alone doesn't establish equal quality in other languages or dialects.

Output quality depends on clear requests, readable source material, and the limits of each feature. Test representative content and languages in your setting, and review the limitations in [section 7](#7-limitations) before relying on results.

## 7. Limitations

Understanding Microsoft 365 Education AI’s limitations is crucial to determine if it is used within safe and effective boundaries. While we encourage customers to use Microsoft 365 Education AI in their innovative solutions or applications, it’s important to note that Microsoft 365 Education AI was not designed for every possible scenario. We encourage users to refer to either the [Microsoft Enterprise AI Services Code of Conduct](https://learn.microsoft.com/en-us/legal/ai-code-of-conduct) \(for organizations\) or the Code of Conduct section in the Microsoft Services Agreement \(for individuals\) as well as the following considerations when choosing a use case:

- **Accuracy and grounding:** Generated facts, answer keys, standards references, and feedback may be wrong even when phrased confidently. Files can be misread, truncated, or only partly used, especially when layouts or objects cannot be extracted. Compare important claims and constraints with the original source before use.
- **Instructional fit and bias:** Generated material might miss local curriculum, learner needs, accessibility requirements, or cultural context because the system can't fully know a classroom. Prompts, sources, and models can also lead to stereotypes or uneven quality. Educators should adapt material and check whether examples and feedback work for their learners.
- **Languages and dialects:** A localized interface or language option doesn't guarantee equal generation or evaluation quality across languages, scripts, and dialects. Mixed-language inputs and regional terminology can increase errors. Test representative content before deploying a language-sensitive use case.
- **Learning** **Zone:** Source images and other non-text objects are ignored; code, mathematics, or long sources may be mishandled or omitted. File-size and device limits can prevent lesson generation.
- **Learner-facing content:** Automated controls can't prevent every unsuitable or incorrect response. Reading Coach stories appear without routine human review before display, so constrained choices and age-appropriate adult support matter. These experiences are unsuitable when every output must have prior expert approval.
- **Speech and study guidance:** Speaker Progress feedback depends on the quality and amount of transcribed speech and can misread dialects, disabilities, or limited input. Educators must review it; it's not a diagnosis or definitive speaking measure. Study and Learn isn't designed for grading, proctoring, surveillance, or educator assessment of learner understanding, and learners might try to circumvent its assignment-completion refusals.
- **Consequential decisions:** These capabilities aren't designed to decide grades, discipline, placement, admissions, accommodations, special education eligibility, or access to education services autonomously. Errors or bias in these settings can harm learners. Qualified people must retain review, correction, and appeal procedures. Product terms and codes of conduct still apply.

## 8. Evaluations

Performance and safety evaluations assess whether AI applications are operating reliably and securely by examining factors like groundedness, relevance, and coherence while identifying the risks of generating harmful content. The following evaluations were conducted with safety components already in place, which are also described in [section 9, Safety Components and Mitigations](#9-safety-components-and-mitigations).

### Evaluation data for quality and safety

Our evaluation data is custom-built to assess AI application performance across key areas of safety and quality, simulating real-world scenarios and risks. We begin by identifying relevant evaluation aspects of concern based on multi-disciplinary research and expert input. These concerns are translated into targeted evaluation objectives and guide formulation of evaluation metrics. For safety, we create adversarial prompts to elicit undesirable or edge-case responses, which are then scored using AI-assisted annotators trained to assess alignment with Microsoft’s safety standards. For quality, we craft rubric-based prompts relevant to scenarios including evaluating retrieval-augmented generation \(RAG\) applications and agents. Datasets are curated from diverse sources including synthetic and public datasets to simulate real-world user scenarios. Using the curated datasets, both evaluations undergo iterative refinement and human alignment to improve metric efficacy and reliability. This methodology forms the foundation of repeatable, rigorous assessments that reflect how customers use evaluations to build better and safer AI.

## 9. Safety components and mitigations

- **Content and learner safeguards:** All systems are covered by automated moderation layers to ensure harmful content is caught. Automated safeguards can still miss unsuitable content. Learning Zone uses validators and content moderation, including Windows AI API moderation for Phi Silica inputs and outputs. No generative AI functionality is available to students under the age of 13, with the exception of Reading Coach. Generative AI functionality must be manually enabled for students ages 13-18 by following these directions:
- **Human review:** Users can revise, regenerate, or discard drafts before use. Learning Zone flags slides the creator hasn't reviewed. Review reduces risk but can't guarantee that it finds subtle errors or bias.
- **Speech-feedback controls:** Speaker Progress applies minimum-content checks and a structured output format before presenting feedback to an educator. These controls help limit malformed or unsupported feedback from short transcripts. The educator decides whether the result is appropriate to return.
- **Data and access protection:** Applicable Microsoft 365 services use encryption, tenant isolation, authentication, and role-based access controls. Inputs, prompts, responses, and Microsoft Graph data aren't used to train foundation models. Data collection and retention differ by feature; customers should consult linked product and privacy documentation and limit access to what each role needs.
- **Reporting and response:** Customers can report harmful, biased, or inaccurate output through product feedback and support channels. Organizations should set up their own learner-safeguarding, correction, and escalation procedures. Reported issues and evaluation findings can inform changes to safety measures.

## 10. Best practices for deploying and adopting Microsoft 365 Education AI

Responsible AI is a shared commitment between Microsoft and its customers. While Microsoft builds AI applications and platform services with safety, fairness, and transparency at the core, customers play a critical role in deploying and using these technologies responsibly within their own contexts. To support this partnership, we offer the following best practices for deployers and end users to help customers implement responsible AI effectively.

Microsoft 365 Education AI is designed to augment educator and learner work, not replace qualified judgment. Customers remain responsible for reviewing outputs, validating decisions, and meeting applicable laws, regulations, product terms, and organizational policies.

### 10.1 Deployers and end users responsibilities

- **Exercise caution and evaluate outcomes when using Microsoft 365 Education AI for consequential decisions or in sensitive domains:** Consequential decisions are those that might have a legal or significant impact on a person’s access to education, employment, financial platforms, government benefits, healthcare, housing, insurance, legal platforms, or that could result in physical, psychological, or financial harm. Sensitive domains—such as financial platforms, healthcare, and housing—require particular care due to the potential for disproportionate impact on different groups of people. When using AI for decisions in these areas, ensure that impacted stakeholders can understand how decisions are made, appeal decisions, and update any relevant input data.
- **Evaluate legal and regulatory considerations:** Customers need to evaluate potential specific legal and regulatory obligations when using any AI platforms and solutions, which may not be appropriate for use in every industry or scenario. Additionally, AI platforms or solutions are not designed for and may not be used in ways prohibited in applicable terms of service and relevant codes of conduct.
- **Retain educator judgment in education decisions:** Microsoft 365 Education AI shouldn't make consequential education decisions autonomously or provide the sole basis for them. Organizations should account for accessibility, local education policies, privacy, security, and safeguarding requirements. Involve qualified specialists where needed.

### 10.2 End users responsibilities

- **Review results and avoid overreliance:** AI output might be inaccurate, incomplete, or biased, even when it sounds convincing. Verify important claims, answer keys, and feedback before using them. Study and Learn should support learners’ reasoning rather than replace their work.
- **Give useful context:** State the objective, learner level, language, and relevant constraints when the feature accepts them. Provide readable and current source material, with no more personal data than needed. Compare grounded output with the source before relying on it.
- **Report concerns:** Use product feedback or support channels for harmful, inaccessible, or unsuitable output. Learners should tell a responsible adult about urgent or sensitive concerns. Include enough context to investigate without unnecessary personal data.

### 10.3 Deployers responsibilities

- **Configure access:** Check licenses, learner ages, roles, languages, and tenant settings before enabling a capability. Grant users and agents only the data and actions needed for their tasks. Recheck permissions and policy settings when roles or features change. See the [Microsoft Education Solution Guide](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start/a-start) for recommended tenant setup and access controls.
- **Test the intended use:** Test representative subjects, learner groups, languages, accessibility needs, and foreseeable misuse before broad deployment. Include factual accuracy, bias, harmful output, and attempts to redirect an agent through untrusted content. Results from one feature, language, or release don't establish the quality of another.
- **Maintain oversight:** Define who can review, correct, remove, or appeal generated content and feedback, and how safeguarding or privacy incidents are escalated. Monitor user reports and representative outputs, then retest when models, prompts, controls, or features change. Keep people in control of agent actions, especially in sensitive settings, and pause uses that fall below local requirements.
