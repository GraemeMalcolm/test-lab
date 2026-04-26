---
lab:
  title: Get started with agent development in Microsoft Foundry
  description: Use Microsoft Foundry to deploy a generative AI model and create an agent.
  level: 200
  duration: 20 minutes
  islab: true
---

# Get started with agent development in Microsoft Foundry

In this lab, we'll quickly explore some basic concepts about generative AI and agents, and then get you started creating your own agent.

> **Tip**: At any point, you can use the *Ask Anton* chat interface on the left to ask about AI concepts and Microsoft Foundry.

This lab should take approximately **30** minutes to complete.

## Conceptual overview: Generative AI and agents

Before creating an agent, let's set some context about *generative* AI and how it relates to *agentic* AI.

{% include lab-tabs-assets.html %}

{% capture conceptual_overview_video %}
<div style="position: relative; overflow: hidden; aspect-ratio: 1920/1080; width: 100%; max-width: 800px;"><iframe src="https://share.synthesia.io/embeds/videos/904e700e-4549-42ac-8056-7e4dfd505966" loading="lazy" title="Synthesia video player - AI Concepts 02" allowfullscreen allow="encrypted-media; fullscreen; microphone; screen-wake-lock;" style="position: absolute; width: 100%; height: 100%; top: 0; left: 0; border: none; padding: 0; margin: 0; overflow:hidden;"></iframe></div>
{% endcapture %}

{% capture conceptual_overview_text %}

### Generative AI

*Generative AI* is a branch of AI that enables software applications to generate new content; often natural language dialogs, but also images, video, code, and other formats.

For example, a computing history web site could provide a generative AI chat interface into which users can enter questions about key figures, technologies, and events in the history of computing.

![Screenshot of a computing history chat interface.](./media/computing-history-chat.png)

The ability to chat with the site and have it generate original responses to questions creates a compelling interactive experience for users.

Generative AI is based on *Large language models* (LLMs), which are models that have  been trained with huge volumes of data - often documents from the Internet or other public sources of information.

![Diagram of a generative AI application in which a user chats with a language model.](./media/generative-ai.png)

Users interact with generative AI language models through *prompts* - natural language statements of questions. The language model in a generative AI solution uses the prompt to initiate the generation of a meaningful response.

Generative AI models encapsulate *semantic* relationships between language elements (that's a fancy way of saying that the models "know" how words relate to one another), and that's what enables them to generate a meaningful sequence of text.

### Agents

Agents are software applications built on generative AI that can reason over and generate natural language, automate tasks by using tools, and respond to contextual conditions to take appropriate action.

![Diagram of an agent with a model, instructions, and tools.](./media/agent.png)

AI agents have three key elements:

- **A large language model**: This is the agent's brain; using generative AI for language understanding and reasoning.
- **Instructions**: A system prompt that defines the agent’s role and behavior. Think of it as the agent’s job description.
- **Tools**: These are what the agent uses to interact with the world. Tools can include:
  - *Knowledge* tools that provide access to information, like search engines or databases.
  - *Action* tools that enable the agent to perform tasks, such as sending emails, updating calendars, or controlling devices.

With these capabilities, AI agents can take on the role of digital assistants that intelligently automate tasks and collaborate with you to work smarter and more efficiently.
{% endcapture %}

{% include lab-tabbed-video-text.html id="concept-overview" aria_label="Conceptual overview content" video_html=conceptual_overview_video text_markdown=conceptual_overview_text %}

## Exercise: Create an agent with Microsoft Foundry

Now it's your turn. In this exercise, you'll use Microsoft Foundry to start developing an AI agent that provides information and expertise on the history of computing.

> **Note**: Many components of Microsoft Foundry, including the Microsoft Foundry portal, are subject to continual development. This reflects the fast-moving nature of artificial intelligence technology. Some elements of your user experience may differ from the images and descriptions in this exercise!

{% capture hosted_lab_markdown %}

This exercise is available in a hosted lab environment, provided by our partner *Skillable*.

[![Screenshot of Skillable lab environment](./media/skillable.png)](https://labondemand.com/LabProfile/214910){:target="_blank"}

### [Launch Hosted Lab](https://labondemand.com/LabProfile/214910){:target="_blank"}

{% endcapture %}

{% capture own_setup_markdown %}
Use these instructions to complete the exercise in your own Azure subscription.

### Before you start

Use the [setup guide](./00-setup.md){:target="_blank"} to prepare your environment.

When you're ready, follow the instructions below to create your first agent.

### Create a Microsoft Foundry project

Microsoft Foundry uses *projects* to organize models, resources, data, and other assets used to develop an AI solution.

1. In a web browser, open [Microsoft Foundry](https://ai.azure.com){:target="_blank"} at `https://ai.azure.com` and sign in using your Azure credentials. Close any tips or quick start panes that are opened the first time you sign in, and if necessary use the **Foundry** logo at the top left to navigate to the home page.

1. If it is not already enabled, in the tool bar the top of the page, enable the **New Foundry** option. Then, if prompted, create a new project with a unique name; expanding the  **Advanced options** area to specify the following settings for your project:
    - **Foundry resource**: *A valid name for your Foundry resource.*
    - **Subscription**: *Your Azure subscription*
    - **Resource group**: *Create or select a resource group*
    - **Region**: Select any of the **AI Foundry recommended** regions

1. Select **Create**. Wait for your project to be created. It may take a few minutes. After creating or selecting a project in the new Foundry portal, it should open in a page similar to the following image:

    ![Screenshot of the Foundry project home page.](./media/foundry-portal-home.png)

### Deploy a model

At the heart of every AI agent, there's a large language model (LLM). Let's find one in the Foundry models catalog.

1. Now you're ready to **Start building**. Select **Find models** (or on the **Discover** page, select the **Models** tab) to view the Microsoft Foundry model catalog.

    Microsoft Foundry provides a large collection of models from Microsoft, OpenAI, and other providers, that you can use in your AI apps and agents.

    ![Screenshot of the AI Foundry model catalog.](./media/0-foundry-models.png)

1. Search for and select the `gpt-4.1-mini` model, and view the page for this model, which describes its features and capabilities.

    ![Screenshot of the gpt-4.1-mini model page.](./media/0-gpt-4.1-mini.png)

1. Use the **Deploy** button to deploy the model using the default settings. Deployment may take a minute or so.

    > **Tip**: Model deployments are subject to regional quotas. If you don't have enough quota to deploy the model in your project's region, you can use a different model - such as gpt-4.1-nano, or gpt-4o-mini. Alternatively, you can create a new project in a different region.

1. When the model has been deployed, view the model playground page that is opened, in which you can chat with the model.

    ![Screenshot of the model playground.](./media/0-model-playground.png)

### Chat with the model

You can use the playground to explore the model by chatting with it.

1. Use the button at the bottom of the left navigation pane to hide it and give yourself more room to work with.
1. In the **Chat** pane, enter a prompt such as `Who was Ada Lovelace?`, and review the response.

    ![Screenshot of the chat pane with a response.](./media/0-chat-response.png)

1. Enter a follow-up prompt, such as `Tell me more about her work with Charles Babbage.` and review the response.

    > **Note**: Generative AI chat applications often include the conversation history in the prompt; so the context of the conversation is retained between messages. In this case, "her" is interpreted as referring to Ada Lovelace.

1. At the top-right of the chat pane, use the **New chat** button to restart the conversation. This removes all conversation history.
1. Enter a new prompt, such as `Tell me about the ELIZA chatbot.` and view the response.
1. Continue the conversation with prompts such as `How does it compare with modern LLMs?`.

### Specify instructions in a *system prompt*

To support specific use cases, you should use a *system prompt* to provide the model with instructions that guide its responses. You can use the system prompt to give the model a specific focus or role, and provide guidelines about format, style, and constraints about what the model should and should not include in its responses.

1. In the model playground, at the top-right of the chat pane, use the **New chat** button to restart the conversation and remove the conversation history.
1. In the pane on the left, in the **Instructions** text area, change the system prompt to:

    ```
   You are an expert in the history of computing and AI. You only answer questions about significant people and events in the development of computing, and about notable vintage computers. Do not engage in conversations on any topic that is unrelated to computing history.
    ```

1. Now enter a new user prompt related to computing history, such as `What was Alan Turing's contribution to the development of AI?`

    Review the response, which should provide some history of computing information.

1. Try asking an "off-topic" question, such as `What's the capital of Spain?`; and view the response.

### Add a web_search tool

So far, the model has answered questions based on the data with which it was trained. While this is useful, that leaves out a lot of current information on the web; which might help the model give more relevant answers.

We can use *tools* to give models access to external data sources, and to perform custom tasks. Let's add a tool that enables the model to search the Web for up-to-date information.

1. In the pane on the left, under the instructions, expand the **Tools** section if it is not already expanded.
1. In the **Add** drop-down list, select **Web search**. Then read the information about the tool and add it.
1. In the chat pane, enter the prompt `Find a vintage computer store near Seattle` (*or your local city!*) and review the response.

    The model should have searched the Web for vintage computer stores near the specific city.

### Save the model configuration as an agent

While you can implement generative AI apps using a standalone model, to create a fully agentic AI experience, you need to encapsulate the model, its instructions, and any tool configuration that provides additional functionality, in an *agent*.

1. In the model playground, at the top right select **Save as agent**. Then, when prompted, name your new agent `computing-historian`.

    When the agent is created, it opens in a new playground specifically for working with agents.

    ![Screenshot of the agent playground.](./media/agent-playground.png)

1. In the pane on the right, view the **YAML** tab, which contains the definition for your agent. Note that its definition includes the model, its parameter settings, and the instructions you specified - similar to this:

    ```yml
    metadata:
      logo: Avatar_Default.svg
      microsoft.voice-live.enabled: "false"
    object: agent.version
    id: computing-historian:1
    name: computing-historian
    version: "1"
    description: ""
    created_at: 1776550090
    definition:
      kind: prompt
      model: gpt-4.1-mini
      instructions: You are an expert in the history of
        computing and AI. You only answer questions
        about significant people and events in the
        development of computing, and about notable
        vintage computers. Do not engage in
        conversations on any topic that is unrelated to
        computing history.
      temperature: 1
      top_p: 1
      tools:
        - type: web_search
    status: active
    ```

1. Switch back to the **Chat** tab, and enter the prompt `Who are you?`

    The response should indicate that the agent is "aware" of its role as a computing historian.

### Preview the agent

Now you have a working agent, you can preview it in a basic web chat application.

1. At the top of the chat pane, in the **Preview** drop-down list, select **Preview agent**.

    A preview chat interface is opened in a new browser tab.

1. Enter a prompt, such as `What can you tell me about the Altair 8800?` and view the response from your agent.

    ![Screenshot of an agent preview chat interface.](./media/agent-preview.png)
{% endcapture %}

{% assign hosted_lab_html = hosted_lab_markdown | markdownify %}
{% include lab-tabbed-video-text.html id="exercise-workflow" aria_label="Exercise workflow options" video_label="Hosted Lab" text_label="Use your own setup" video_html=hosted_lab_html text_markdown=own_setup_markdown %}

## Summary

In this lab, you explored how to deploy and chat with a generative AI model in Microsoft Foundry portal. You then configured instructions and tools before saving the model as an agent.

## Next steps

This is the first in a series of lab exercises; save your work and continue to the [next exercise](./02-continue-in-vscode.md) if you're ready.

> **Tip**: If you have finished exploring Microsoft Foundry, you should delete the Azure resources created in this exercise to avoid unnecessary utilization charges.
