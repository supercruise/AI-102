# [Develop generative AI apps in Azure](https://learn.microsoft.com/en-us/training/paths/create-custom-copilots-ai-studio/)

---

# Plan and prepare to develop AI solutions on Azure

## Learning objectives
By the end of this module, you'll be able to:

- Identify common AI capabilities that you can implement in applications
- Describe Azure AI Services and considerations for using them
- Describe Azure AI Foundry and considerations for using it
- Identify appropriate developer tools and SDKs for an AI project
- Describe considerations for responsible AI

## Introduction

The growth in the use of artificial intelligence (AI) in general, and generative AI in particular means that developers are increasingly required to create comprehensive AI solutions. These solutions need to combine **machine learning models, AI services, prompt engineering solutions, and custom code**.

Microsoft Azure provides multiple services that you can use to create AI solutions. However, before embarking on an AI application development project, it's useful to consider the available options for services, tools, and frameworks as well as some principles and practices that can help you succeed.

This module explores some of the key considerations for planning an AI development project, and introduces **Azure AI Foundry**; a comprehensive platform for AI development on Microsoft Azure.

---

## What is AI?

The term "Artificial Intelligence" (AI) covers a wide range of software capabilities that enable applications to exhibit human-like behavior. AI has been around for many years, and its definition has varied as the technology and use cases associated with it have evolved. In today's technological landscape, AI solutions are built on machine learning models that encapsulate semantic relationships found in huge quantities of data; enabling applications to appear to interpret input in various formats, reason over the input data, and generate appropriate responses and predictions.

Common AI capabilities that developers can integrate into a software application include:


| Capability |Description|
|--|--|
| Generative AI | The ability to generate original responses to natural language prompts. For example, software for a real estate business might be used to automatically generate property descriptions and advertising copy for a property listing. |
| Agents | Generative AI applications that can respond to user input or assess situations autonomously, and take appropriate actions. For example, an "executive assistant" agent could provide details about the location of a meeting on your calendar, or even attach a map or automate the booking of a taxi or rideshare service to help you get there. |
| Computer vision | The ability to accept, interpret, and process visual input from images, videos, and live camera streams. For example, an automated checkout in a grocery store might use computer vision to identify which products a customer has in their shopping basket, eliminating the need to scan a barcode or manually enter the product and quantity. |
| Speech | The ability to recognize and synthesize speech. For example, a digital assistant might enable users to ask questions or provide audible instructions by speaking into a microphone, and generate spoken output to provide answers or confirmations.|
| Natural language processing | The ability to process natural language in written or spoken form, analyze it, identify key points, and generate summaries or categorizations. For example, a marketing application might analyze social media messages that mention a particular company, translate them to a specific language, and categorize them as positive or negative based on sentiment analysis. |
| Information extraction | The ability to use computer vision, speech, and natural language processing to extract key information from documents, forms, images, recordings, and other kinds of content. For example, an automated expense claims processing application might extract purchase dates, individual line item details, and total costs from a scanned receipt.|
| Decision support | The ability to use historic data and learned correlations to make **predictions** that support business decision making. For example, analyzing demographic and economic factors in a city to predict real estate market trends that inform property pricing decisions.|

### A closer look at generative AI

Generative AI represents the latest advance in artificial intelligence, and deserves some extra attention. Generative AI uses language models to respond to natural language prompts, enabling you to build **conversational apps and agents** that support research, content creation, and task automation in ways that were previously unimaginable.

The language models used in generative AI solutions can be large language models (LLMs) that have been trained on huge volumes of data and include many millions of parameters; or they can be small language models (SLMs) that are optimized for specific scenarios with lower overhead. Language models commonly respond to text-based prompts with natural language text; though increasingly new **multi-modal models** are able to handle image or speech prompts and respond by generating text, code, speech, or images.

---

## Azure AI services

Microsoft Azure provides a wide range of cloud services that you can use to develop, deploy, and manage an AI solution. The most obvious starting point for considering AI development on Azure is **Azure AI services**; a set of out-of-the-box prebuilt APIs and models that you can integrate into your applications. The following table lists some commonly used Azure AI services (for a full list of all available Azure AI services, see Available [Azure AI services](https://learn.microsoft.com/en-us/azure/ai-services/what-are-ai-services#available-azure-ai-services?azure-portal=true)).

| Service | Description |
| -- | -- |
| Azure OpenAI | The Azure OpenAI service provides access to OpenAI generative AI models including the **GPT family of large and small language models** and **DALL-E image-generation models** within a scalable and securable cloud service on Azure. |
| Azure AI Vision | The Azure AI Vision service provides a set of models and APIs that you can use to implement common computer vision functionality in an application. With the AI Vision service, you can **detect common objects in images, generate captions, descriptions, and tags based on image contents, and read text in images**. |
| Azure AI Speech | The Azure AI Speech service provides APIs that you can use to implement **text to speech** and **speech to text transformation**, as well as specialized speech-based capabilities like **speaker recognition and translation**. |
| Azure AI Language|The Azure AI Language service provides models and APIs that you can use to analyze natural language text and perform tasks such as **entity extraction, sentiment analysis, and summarization**. The AI Language service also provides functionality to help you **build conversational language models and question answering solutions**.|
| Azure AI Content Safety|Azure AI Content Safety provides developers with access to advanced algorithms for processing images and text and **flagging content that is potentially offensive, risky, or otherwise undesirable**.|
| Azure AI Translator|The Azure AI Translator service uses state-of-the-art language models to **translate text** between a large number of languages.|
| Azure AI Face|The Azure AI Face service is a specialist computer vision implementation that can **detect, analyze, and recognize human faces**. Because of the potential risks associated with personal identification and misuse of this capability, access to some features of the AI Face service are restricted to approved customers.|
| Azure AI Custom Vision|The Azure AI Custom Vision service enables you to train and use custom computer vision models for **image classification and object detection**.|
| Azure AI Document Intelligence|With Azure AI Document Intelligence, you can use pre-built or custom models to **extract fields from complex documents such as invoices, receipts, and forms**.
| Azure AI Content Understanding|The Azure AI Content Understanding service provides **multi-modal content analysis** capabilities that enable you to build models to extract data from forms and documents, images, videos, and audio streams.|
| Azure AI Search |The Azure AI Search service uses a pipeline of AI skills based on other Azure AI Services and custom code to **extract information from content and create a searchable index**. AI Search is commonly used to **create vector indexes for data** that can then be used to ground prompts submitted to generative AI language models, such as those provided in the Azure OpenAI service.|

### Considerations for Azure AI services resources

To use Azure AI services, you create one or more Azure AI resources in an Azure subscription and implement code in client applications to consume them. In some cases, AI services include **web-based visual interfaces** that you can use to configure and test your resources - for example to train a custom image classification model using the Custom Vision service you can use the visual interface to upload training images, manage training jobs, and deploy the resulting model.

> Note: You can provision Azure AI services resources in the Azure portal (or by using BICEP or ARM templates or the Azure command-line interface) and build applications that use them directly through various service-specific APIs and SDKs. However, as we'll discuss later in this module, in most medium to large-scale development scenarios it's better to provision Azure AI services resources as part of an **Azure AI Foundry project** - enabling you to centralize access control and cost management, and making it easier to manage shared resources and build the next generation of generative AI apps and agents.

### Single service or multi-service resource?

Most Azure AI services, such as **Azure AI Vision, Azure AI Language**, and so on, can be provisioned as standalone resources, enabling you to create only the Azure resources you specifically need. Additionally, **standalone Azure AI services often include a free-tier SKU with limited functionality**, enabling you to evaluate and develop with the service at no cost. Each standalone Azure AI resource provides **an endpoint and authorization keys** that you can use to access it securely from a client application.

Alternatively, you can provision a **multi-service resource** that **encapsulates multiple AI services in a single Azure resource**. Using a multi-service resource can make it easier to manage applications that use multiple AI capabilities. There are two multi-service resource types you can use:

#### Azure AI services

The Azure AI Services resource type includes the following services, making them available from a single endpoint:

- Azure AI Speech
- Azure AI Language
- Azure AI Translator
- Azure AI Vision
- Azure AI Face
- Azure AI Custom Vision
- Azure AI Document Intelligence

#### Azure AI Foundry

The Azure AI Foundry resource type includes the following services, and supports working with them through an Azure AI Foundry project:

- Azure OpenAI
- Azure AI Speech
- Azure AI Language
- Azure AI Foundry Content Safety
- Azure AI Translator
- Azure AI Vision
- Azure AI Face
- Azure AI Document Intelligence
- Azure AI Content Understanding

Using a multi-service resource can make it easier to manage applications that use multiple AI capabilities.

### Regional availability

Some services and models are available in only a subset of Azure regions. Consider service availability and any regional quota restrictions for your subscription when provisioning Azure AI services. Use the [product availability table](https://azure.microsoft.com/explore/global-infrastructure/products-by-region/table) to check regional availability of Azure services. Use the [model availability table](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/models#model-summary-table-and-region-availability?azure-portal=true) in the Azure OpenAI service documentation to determine regional availability for Azure OpenAI models.

### Cost

Azure AI services are charged based on usage, with different pricing schemes available depending on the specific services being used. As you plan an AI solution on Azure, use the [Azure AI services pricing documentation](https://azure.microsoft.com/pricing/details/cognitive-services) to understand pricing for the AI services you intend to incorporate into your application. You can use the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator) to estimate the costs your expected usage will incur.

---

## Azure AI Foundry

**Azure AI Foundry is a platform for AI development** on Microsoft Azure. While you can provision individual Azure AI services resources and build applications that consume them without it, the project organization, resource management, and AI development capabilities of Azure AI Foundry makes it the recommended way to build all but the most simple solutions.

Azure AI Foundry provides the _Azure AI Foundry portal_, a web-based visual interface for working with AI projects. It also provides the _Azure AI Foundry SDK_, which you can use to build AI solutions programmatically.

### Azure AI Foundry projects
In Azure AI Foundry, you manage the resource connections, data, code, and other elements of the AI solution in projects. There are two kinds of project:

#### Foundry projects

*Foundry projects* are associated with an **Azure AI Foundry** resource in an Azure subscription. Foundry projects provide support for *Azure AI Foundry models (including OpenAI models), Azure AI Foundry Agent Service, Azure AI services, and tools for evaluation and responsible AI development*.

An Azure AI Foundry resource supports the most common AI development tasks to develop generative AI chat apps and agents. In most cases, using a Foundry project provides the right level of resource centralization and capabilities with a minimal amount of administrative resource management. You can use Azure AI Foundry portal to work in projects that are based in Azure AI Foundry resources, making it easy to add connected resources and manage model and agent deployments.

#### Hub-based projects

*Hub-based projects* are associated with an **Azure AI hub** resource in an Azure subscription. Hub-based projects include an Azure AI Foundry resource, as well as managed compute, support for Prompt Flow development, and connected **Azure storage** and **Azure key vault** resources for secure data storage.

Azure AI hub resources support advanced AI development scenarios, like developing **Prompt Flow based applications or fine-tuning models**. You can also **use Azure AI hub resources in both Azure AI Foundry portal and Azure Machine learning portal**, making it easier to work on collaborative projects that involve data scientists and machine learning specialists as well as developers and AI software engineers

> Tip: For more information about Azure AI Foundry project types, see [What is Azure AI Foundry?](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry).

> Note: the notes below are from the old course.

### Hubs and projects

In Azure AI Foundry, you manage the resources, assets, code, and other elements of the AI solution in hubs and projects. **Hubs provide a top-level container for managing shared resources, data, connections and security configuration for AI application development**. A hub can support multiple projects, in which developers collaborate on building a specific solution.

#### Hubs

A hub provides a centrally managed collection of shared resources and management configuration for AI solution development. You need at least one hub to use all of the solution development features and capabilities of AI Foundry.

In a hub, you can define shared resources to be used across multiple projects. When you create a hub using the Azure AI Foundry portal, an **Azure AI Hub** resource is created in a resource group associated with the hub. Additionally, the following resources are created for the hub:

- A multi-service **Azure AI services** resource to provide access to Azure OpenAI and other Azure AI services.
- A **Key vault** in which sensitive data such as connections and credentials can be stored securely.
- A **Storage account** for data used in the hub and its projects.
- Optionally, an **Azure AI Search** resource that can be used to index data and support grounding for generative AI prompts.

You can create more resources as required (for example, an **Azure AI Face** resource) and add it to the hub (or an individual project) by defining a connected resource. As you create more items in your hub, such as compute instances or endpoints, more resources will be created for them in the Azure resource group.

Access to the resources in a hub is governed by creating _users_ and assigning them to _roles_. An IT administrator can manage access to the resources centrally at the hub level, and projects associated with the hub inherit the resources and role assignments; enabling development teams to use the resources they need without needing to request access on a project-by-project basis.

#### Projects

A hub can support one or more projects, each of which is used to organize the resources and assets required for a particular AI development effort.

Users can collaborate in a project, sharing data in project-specific storage containers and connected resources, and using the shared resources defined in the hub associated with the project. Azure AI Foundry provides tools and functionality within a project that developers can use to build AI solutions efficiently, including:

- A **model catalog** in which you can find and deploy machine learning models from multiple sources, including Azure OpenAI and the Hugging Face model library.
- **Playgrounds** in which you can test prompts with generative AI models.
- Access to **Azure AI services**, including visual interfaces to experiment with and configure services as well as endpoints and keys that you can use to connect to them from client applications.
- **Visual Studio Code** containers that define a hosted development environment in which you can write, test, and deploy code.
- **Fine-tuning** functionality for generative AI models that you need to customize based on custom training prompts and responses.
- **Prompt Flow**, a prompt orchestration tool that you can use to define the logic for a generative AI application's interaction with a model.
- Tools to assess, evaluate, and improve your AI applications, including _tracing, evaluations, and content safety and security management_.
- Management of project **assets**, including models and endpoints, data and indexes, and deployed web apps.

### Considerations for Azure AI Foundry

When planning an AI solution built on Azure AI Foundry, there are some additional considerations to those discussed previously in relation to Azure AI services.

#### Hub and project organization

Plan your hub and project organization for the most effective management of resources and efficiency of administration. **Use Hubs to centralize management of users and shared resources that are involved in related projects, and then add project-specific resources as necessary.** For example, an organization might have separate software development teams for each area of the business, so it may make sense to create separate hubs for each business area (such as Marketing, HR, and so on) in which AI application development projects for each business area can be created. The shared resources in each hub will automatically be available in projects created in those hubs.

#### Connected resources

At the hub level, an IT administrator can create shared resource connections in a hub that will be used in downstream projects. Projects access the connected resources by proxy on behalf of project users, so users in those projects don't need direct access to those resources in order to use them within the context of the project. Connections in a hub are automatically available in new projects in the hub without further requests to the IT administrator. If an individual project needs access to a specific resource that other projects in the same hub don't use, you can create more connected resources at the project level.

As you plan your Azure AI Foundry hubs and projects, identify the shared connected resources you should add to each hub so that they're inherited by projects in that hub, while allowing for project-level exceptions.

### Security and authorization

For each hub and project, identify the users who will need access and the roles to which they should be assigned.

#### Hub-level roles
Hub-level roles can perform infrastructure management tasks, such as creating hub-level connected resources or new projects. The default roles in a hub are:

- **Owner**: Full access to the hub, including the ability to manage and create new hubs and assign permissions. This role is automatically assigned to the hub creator
- **Contributor**: Full access to the hub, including the ability to create new hubs, but isn't able to manage hub permissions on the existing resource.
- **Azure AI Developer**: All permissions except create new hubs and manage the hub permissions.
- **Azure AI Inference Deployment Operator**: All permissions required to create a resource deployment within a resource group.
- **Reader**: Read only access to the hub. This role is automatically assigned to all project members within the hub.

#### Project-level roles
Project-level roles determine the tasks that a user can perform within an individual project. The default roles in a project are:

- **Owner**: Full access to the project, including the ability to assign permissions to project users.
- **Contributor**: Full access to the project but can't assign permissions to project users.
- **Azure AI Developer**: Permissions to perform most actions, including create deployments, but can't assign permissions to project users.
- **Azure AI Inference Deployment Operator**: Permissions to perform all actions required to create a resource deployment within a resource group.
- **Reader**: Read only access to the project.

### Regional availability

As with all Azure services, the availability of specific Azure AI Foundry capabilities can vary by region. As you plan your solution, determine regional availability for the capabilities you require.

### Costs and quotas

In addition to the cost of the Azure AI services your solution uses, there are costs associated with Azure AI Foundry related to the resources that support hubs and projects as well as storage and compute for assets, development, and deployed solutions. You should consider these costs when planning to use Azure AI Foundry for AI solution development.

In addition to service consumption costs, you should consider the resource quotas you need to support the AI applications you intend to build. Quotas are used to limit utilization, and play a key role in cost management and managing Azure capacity. In some cases, you may need to request additional quota to increase rate limits for AI model operations or available compute for development and solution deployment.

---

## Developer tools and SDKs

While you can perform many of the tasks needed to develop an AI solution directly in the Azure AI Foundry portal, developers also need to write, test, and deploy code.

### Development tools and environments

There are many development tools and environments available, and developers should choose one that supports the languages, SDKs, and APIs they need to work with and with which they're most comfortable. For example, a developer who focuses strongly on building applications for Windows using the .NET Framework might prefer to work in an integrated development environment (IDE) like **Microsoft Visual Studio**. Conversely, a web application developer who works with a wide range of open-source languages and libraries might prefer to use a code editor like **Visual Studio Code (VS Code)**. Both of these products are suitable for developing AI applications on Azure.

### The Azure AI Foundry for Visual Studio Code extension

When developing Azure AI Foundry based generative AI applications in Visual Studio Code, you can use the **Azure AI Foundry for Visual Studio Code extension** to simplify key tasks in the workflow, including:

- Creating a project.
- Selecting and deploying a model.
- Testing a model in the playground.
- Creating an agent.

> Tip: For more information about using the Azure AI Foundry for Visual Studio Code extension, see [Work with the Azure AI Foundry for Visual Studio Code extension](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/develop/get-started-projects-vs-code).

### The Azure AI Foundry VS Code container image

As an alternative to installing and configuring your own development environment, within Azure AI Foundry portal, you can create compute and use it to host a container image for VS Code (installed locally or as a hosted web application in a browser). The benefit of using the container image is that it includes the latest versions of the SDK packages you're most likely to work with when building AI applications with Azure AI Foundry.

### GitHub and GitHub Copilot

GitHub is the world's most popular platform for **source control and DevOps management**, and can be a critical element of any team development effort. Visual Studio and VS Code (including the Azure AI Foundry VS Code container image) both provide native integration with GitHub, and access to GitHub Copilot; an AI assistant that can significantly improve developer productivity and effectiveness.

>  Tip: For more information about using GitHub Copilot in Visual Studio Code, see [GitHub Copilot in VS Code](https://code.visualstudio.com/docs/copilot/overview).

### Programming languages, APIs, and SDKs

You can develop AI applications using many common programming languages and frameworks, including **Microsoft C#, Python, Node, TypeScript, Java**, and others. When building AI solutions on Azure, some common SDKs you should plan to install and use include:

- The [Azure AI Foundry SDK](https://learn.microsoft.com/en-us/azure/ai-studio/how-to/develop/sdk-overview), which enables you to write code to connect to Azure AI Foundry projects and access resource connections, which you can then work with using service-specific SDKs.
- The [Azure AI Foundry Models API](https://learn.microsoft.com/en-us/rest/api/aifoundry/modelinference/), which provides an interface for working with generative AI model endpoints hosted in Azure AI Foundry.
- The [Azure OpenAI in Azure AI Foundry Models API](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference), which enables you to build chat applications based on OpenAI models hosted in Azure AI Foundry.
- [Azure AI Services SDKs](https://learn.microsoft.com/en-us/azure/ai-services/reference/sdk-package-resources) - AI service-specific libraries for multiple programming languages and frameworks that enable you to consume Azure AI Services resources in your subscription. You can also use Azure AI Services through their [REST APIs](https://learn.microsoft.com/en-us/azure/ai-services/reference/rest-api-resources).
- The [Azure AI Foundry Agent Service](https://learn.microsoft.com/en-us/azure/ai-services/agents/overview), which is accessed through the Azure AI Foundry SDK and can be integrated with frameworks like [Semantic Kernel](https://learn.microsoft.com/en-us/semantic-kernel/overview) to build comprehensive AI agent solutions.

---

## Responsible AI

It's important for software engineers to consider the impact of their software on users, and society in general; including considerations for its responsible use. When the application is imbued with artificial intelligence, these considerations are particularly important due to the nature of how AI systems work and inform decisions; often based on probabilistic models, which are in turn dependent on the data with which they were trained.

The human-like nature of AI solutions is a significant benefit in making applications user-friendly, but it can also lead users to place a great deal of trust in the application's ability to make correct decisions. **The potential for harm to individuals or groups through incorrect predictions or misuse of AI capabilities is a major concern**, and software engineers building AI-enabled solutions should apply due consideration to mitigate risks and ensure fairness, reliability, and adequate protection from harm or discrimination.

Let's discuss some core principles for responsible AI that have been adopted at Microsoft.

### Fairness

**AI systems should treat all people fairly**. For example, suppose you create a machine learning model to support a loan approval application for a bank. The model should make predictions of whether or not the loan should be approved **without incorporating any bias** based on gender, ethnicity, or other factors that might result in an unfair advantage or disadvantage to specific groups of applicants.

Fairness of machine learned systems is a highly active area of ongoing research, and some software solutions exist for evaluating, quantifying, and mitigating unfairness in machine learned models. However, tooling alone isn't sufficient to ensure fairness. **Consider fairness from the beginning of the application development process; carefully reviewing training data to ensure it's representative of all potentially affected subjects, and evaluating predictive performance for subsections of your user population throughout the development lifecycle**.

### Reliability and safety

AI systems should **perform reliably and safely**. For example, consider an AI-based software system for an autonomous vehicle; or a machine learning model that diagnoses patient symptoms and recommends prescriptions. Unreliability in these kinds of system can result in substantial risk to human life.

As with any software, AI-based software application development must be subjected to rigorous testing and deployment management processes to ensure that they **work as expected** before release. Additionally, software engineers need to **take into account the probabilistic nature of machine learning models**, and apply appropriate thresholds when **evaluating confidence scores for predictions**.

### Privacy and security

AI systems should be secure and respect privacy. The machine learning models on which AI systems are based rely on large volumes of data, which may contain personal details that must be kept private. Even after models are trained and the system is in production, they use new data to make predictions or take action that may be subject to privacy or security concerns; so **appropriate safeguards to protect data and customer content** must be implemented.

### Inclusiveness

AI systems should **empower everyone and engage people**. AI should bring benefits to all parts of society, regardless of physical ability, gender, sexual orientation, ethnicity, or other factors.

One way to optimize for inclusiveness is to ensure that the _design, development, and testing of your application includes input from as diverse a group of people as possible_.

### Transparency

**AI systems should be understandable**. Users should be made fully aware of the purpose of the system, how it works, and what limitations may be expected.

For example, when an AI system is based on a machine learning model, you should generally make users aware of **factors that may affect the accuracy of its predictions**, such as the number of cases used to train the model, or the specific features that have the most influence over its predictions. You should also share information about the **confidence score** for predictions.

When an AI application relies on personal data, such as a facial recognition system that takes images of people to recognize them; you should **make it clear to the user how their data is used and retained, and who has access to it**.

### Accountability

People should be accountable for AI systems. Although many AI systems seem to operate autonomously, ultimately it's the **responsibility of the developers** who trained and validated the models they use, and defined the logic that bases decisions on model predictions to **ensure that the overall system meets responsibility requirements**. To help meet this goal, designers and developers of AI-based solution should work within a framework of governance and organizational principles that ensure the solution meets responsible and legal standards that are clearly defined.

> Tip: For more information about Microsoft's principles for responsible AI, see [the Microsoft responsible AI site](https://microsoft.com/ai/responsible-ai).

---

## [Exercise - Prepare for an AI development project](https://learn.microsoft.com/en-us/training/modules/prepare-azure-ai-development/7-exercise-explore-ai-foundry)

### [Prepare for an AI development project](https://microsoftlearning.github.io/mslearn-ai-studio/Instructions/01-Explore-ai-studio.html)

In this exercise, you use Azure AI Foundry portal to create a project, ready to build an AI solution.

- Open Azure AI Foundry portal
- Create a project
- Review project connections
- Test a generative AI model
- Summary: In this exercise, you’ve explored Azure AI Foundry, and seen how to create and manage projects and their related resources.

---

## Module assessment

1. Which Azure resource provides language and vision services from a single endpoint? **Azure AI service**.
2. You plan to create a simple chat app that uses a generative AI model. What kind of project should you create? **Azure AI Foundry Project**.
3. Which SDK enables you to connect to resources in a project? **Azure AI Foundry SDK**.
*How should you provide access to resources for developers who will work on multiple AI projects? Create resource connections in an Azure AI Foundry hub.
Which SDK enables you to connect to shared resources in a hub? Azure AI Foundry SDK.*

---

## Summary

In this module, you explored some of the key considerations when planning and preparing for AI application development. You've also had the opportunity to become familiar with **Azure AI Foundry**, the recommended platform for developing AI solutions on Azure.

---
---

# Create and consume Azure AI services

Azure AI services enable developers to easily add AI capabilities into their applications. Learn how to create and consume these services.

## Learning objectives
After completing this module, you'll able to:

- Create Azure AI services resources in an Azure subscription.
- Identify endpoints, keys, and locations required to consume an Azure AI services resource.
- Use a REST API and an SDK to consume Azure AI services.

---

## Introduction

**Azure AI services are cloud-based services that encapsulate AI capabilities**. Rather than a single product, you should think of AI services as a set of individual services that you can use as building blocks to compose sophisticated, intelligent applications.

AI services includes a wide range of individual services across language, speech, vision, generative AI, and more. You can use AI services to build your own AI solutions to provide out-of-the-box solutions for common AI scenarios. A few examples of individual Azure AI services include:

- _Azure AI Vision_ - Analyze content in **images and videos**.
- _Azure AI Language_ - Build apps with industry-leading **natural language understanding** capabilities.
- _Azure AI Speech_ - **Speech to text, text to speech, translation, and speaker recognition**.
- _Azure AI Document Intelligence_ - An **optical character recognition (OCR)** solution that can **extract semantic meaning from forms**, such as invoices, receipts, and others.
- _Azure AI Search_ - A cloud-scale search solution that uses AI services to **extract insights from data and documents**.
- _Azure AI Foundry_ - An Azure AI service that provides a**ccess to generative AI models and agents**.

While the details of each AI service can vary, the approach to provisioning and consuming them is generally the same.

In this module, you will learn how to:

- Create Azure AI services resources in an Azure subscription.
- Identify **endpoints, keys, and locations** required to consume an AI services resource.
- Use a **REST API** to consume an AI service.
- Use an **SDK** to consume an AI service.

---

## Provision an Azure AI services resource

Azure AI services include a wide range of AI capabilities that you can use in your applications. To use any of the AI services, you need to create appropriate resources in an Azure subscription to define an **endpoint** where the service can be consumed, provide **access keys** for authenticated access, and to **manage billing** for your application's usage of the service.

### Options for Azure resources
For many of the available AI services, you can choose between the following provisioning options:

#### Multi-service resource
You can provision an **AI services** resource that supports multiple different AI services. For example, you could create a single resource that enables you to use the Azure AI Language, Azure AI Vision, Azure AI Speech, and other services.

This approach enables you to manage a single set of access credentials to **consume multiple services at a single endpoint**, and with **a single point of billing** for usage of all services.

#### Single-service resource
Each AI service can be provisioned individually, for example by creating discrete AI Language and AI Vision resources in your Azure subscription.

This approach enables you to **use separate endpoints for each service** (for example to provision them in different geographical regions) and to manage access credentials for each service independently. It also enables you to manage billing separately for each service.

Single-service resources generally offer **a free tier** (with usage restrictions), making them a good choice to try out a service before using it in a production application.

### Training and prediction resources
While most AI services can be used through a single Azure resource, some offer (or require) separate resources for model **training** and **prediction**. This enables you to manage billing for training custom models separately from model consumption by applications, and in most cases enables you to use a dedicated service-specific resource to train a model, but a generic AI services resource to make the model available to applications for inferencing.

---

## Identify endpoints and keys

When you provision an Azure AI services service resource in your Azure subscription, you are defining an endpoint through which the service can be consumed by an application.

To consume the service through the endpoint, applications require the following information:

- **The endpoint URI**. This is the **HTTP address** at which the REST interface for the service can be accessed. Most AI services software development kits (SDKs) use the endpoint URI to initiate a connection to the endpoint.
- **A subscription key**. Access to the endpoint is restricted based on a subscription key. Client applications must provide a valid key to consume the service. When you provision an AI services resource, two keys are created - applications can use either key. You can also regenerate the keys as required to control access to your resource.
- **The resource location**. When you provision a resource in Azure, you generally assign it to a geographic location, which determines the Azure data center in which the resource is defined. While most SDKs use the endpoint URI to connect to the service, some require the location.

---

## Use a REST API

Azure AI services provide **REST application programming interfaces (APIs)** that client applications can use to consume services. In most cases, service functions can be called by **submitting data in JSON format over an HTTP request**, which may be a _POST, PUT, or GET_ request depending on the specific function being called. The results of the function are returned to the client as an HTTP response, often with JSON contents that encapsulate the output data from the function.

The use of REST interfaces with an HTTP endpoint means that any programming language or tool capable of submitting and receiving JSON over HTTP can be used to consume AI services. You can use common programming languages such as Microsoft C#, Python, and JavaScript; as well as utilities such as **Postman and cURL**, which can be useful for testing.

---

## Use an SDK

You can develop an application that uses Azure AI services using REST interfaces, but it's easier to build more complex solutions by using native libraries for the programming language in which you're developing the application.

Software development kits (SDKs) for common programming languages abstract the REST interfaces for most AI services. SDK availability varies by individual AI services, but for most services there's an SDK for languages such as:

- Microsoft C# (.NET Core)
- Python
- JavaScript (Node.js)
- Go
- Java

Each SDK includes packages that you can install in order to use service-specific libraries in your code, and online documentation to help you determine the appropriate classes, methods, and parameters used to work with the service.

---

## Exercise
https://microsoftlearning.github.io/mslearn-ai-services/Instructions/Exercises/01-use-azure-ai-services.html

---

## Quiz
1. How are client applications typically granted access to an Azure AI Services endpoint? The app must specify a valid subscription key for the Azure resource.
2. In which format are message exchanged between a client app and an Azure AI Services resource when using a REST API? JSON.

---

# Secure Azure AI services

Securing Azure AI services can help prevent data loss and privacy violations for user data that may be a part of the solution.

## Learning objectives
After completing this module, you will know how to:

- Consider authentication for Azure AI services
- Manage network security for Azure AI services

---

## Consider authentication

By default, access to Azure AI services resources is restricted by using **subscription keys**. Management of access to these keys is a primary consideration for security.

### Regenerate keys

You should regenerate keys regularly to protect against the risk of keys being shared with or accessed by unauthorized users. You can regenerate keys using the Azure portal, or using the `az cognitiveservices account keys regenerate` Azure command-line interface (CLI) command.

Each AI service is provided with two keys, enabling you to regenerate keys without service interruption. To accomplish this:

1. If you're using both keys in production, change your code so that only one key is in use. For example, configure all production applications to use key 1.
2. Regenerate key 2.
3. Switch all production applications to use the newly regenerated key 2.
4. Regenerate key 1
5. Finally, update your production code to use the new key 1.

For example, to regenerate keys in the Azure portal, you can do the following:

1. In the Azure portal, go to your resource's Keys and Endpoint pane.
2. Then select Regenerate Key1 or select Regenerate Key2, depending on which one you want to regenerate at the time.

### Protect keys with Azure Key Vault

**Azure Key Vault is an Azure service in which you can securely store secrets** (such as passwords and keys). Access to the key vault is granted to security principals, which you can think of user identities that are authenticated using Microsoft Entra ID. _Administrators can assign a security principal to an application_ (in which case it is known as a **service principal**) to define a managed identity for the application. The application can then use this identity to access the key vault and retrieve a secret to which it has access. Controlling access to the secret in this way minimizes the risk of it being compromised by being hard-coded in an application or saved in a configuration file.

You can **store the subscription keys for an AI services resource in Azure Key Vault, and assign a managed identity to client applications that need to use the service**. The applications can then retrieve the key as needed from the key vault, without risk of exposing it to unauthorized users.

### Token-based authentication

When using the REST interface, some AI services support (or even require) token-based authentication. In these cases, the subscription key is presented in an initial request to obtain an authentication token, which has a valid period of 10 minutes. Subsequent requests must present the token to validate that the caller has been authenticated.

When using an SDK, the calls to obtain and present a token are handled for you by the SDK.

### Microsoft Entra ID authentication

Azure AI services supports Microsoft Entra ID authentication, enabling you to grant access to specific service principals or managed identities for apps and services running in Azure.

There are different ways you can authenticate against Azure AI services using Microsoft Entra ID, including:

#### Authenticate using service principals

The overall process to authenticate against Azure AI services using service principals is as follows:

##### Create a custom subdomain

You can create a custom subdomain in different ways including through the Azure portal, Azure CLI, or PowerShell.

For example, you can create a subdomain using PowerShell in the Azure Cloud Shell. To do this, you select your subscription using the following command:

`Set-AzContext -SubscriptionName <Your-Subscription-Name>`

Then, you create your Azure AI services resource specifying a custom subdomain by running the following:

`$account = New-AzCognitiveServicesAccount -ResourceGroupName <your-resource-group-name> -name <your-account-name> -Type <your-account-type> -SkuName <your-sku-type> -Location <your-region> -CustomSubdomainName <your-unique-subdomain-name>`

Once created, your subdomain name will be returned in the response.

##### Assign a role to a service principal

You've created an Azure AI resource that is linked with a custom subdomain. Next, you assign a role to a service principal.

To start, you'll need to register an application. To do this, you run the following command:

`$SecureStringPassword = ConvertTo-SecureString -String <your-password> -AsPlainText -Force`
`$app = New-AzureADApplication -DisplayName <your-app-display-name> -IdentifierUris <your-app-uris> -PasswordCredentials $SecureStringPassword`

This creates the application resource.

Then you use the New-AzADServicePrincipal command to create a service principal and provide your application's ID:

`New-AzADServicePrincipal -ApplicationId <app-id>`

Finally, you assign the Cognitive Services Users role to your service principal by running:

`New-AzRoleAssignment -ObjectId <your-service-principal-object-id> -Scope <account-id> -RoleDefinitionName "Cognitive Services User"`

### Authenticate using managed identities

Managed identities come in two types:

- **System-assigned managed identity**: A managed identity is created and linked to a specific resource, such as a virtual machine that needs to access Azure AI services. When the resource is deleted, the identity is deleted as well.
- **User-assigned managed identity**: The managed identity is created to be useable by multiple resources instead of being tied to one. It exists independently of any single resource.
You can assign each type of managed identity to a resource either during creation of the resource, or after it has already been created.

For example, suppose you have a virtual machine in Azure that you intend to use for daily access to Azure AI services. To enable a system-assigned identity for this virtual machine, first you make sure your Azure account has the [Virtual Machine Contributor role](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles). Then you can run the following command using Azure CLI in the Azure Cloud Shell terminal:

`az vm identity assign -g <my-resource-group> -n <my-vm>`

Then you can grant access to Azure AI services in the Azure portal using the following:

1. Go to the Azure AI services resource you want to grant the virtual machine's managed identity access.
2. In the overview panel, select Access control (IAM).
3. Select Add, and then select Add role assignment.
4. In the Role tab, select Cognitive Services Contributor.
5. In the Members tab, for the Assign access to, select Managed identity. Then, select + Select members.
6. Ensure that your subscription is selected in the Subscription dropdown. And for Managed identity, select Virtual machine.
7. Select your virtual machine in the list, and select Select.
8. Finally, select Review + assign to review, and then Review + assign again to finish.

---

## Implement network security

Network security is an important measure to **ensure unauthorized users can't reach the services** that you're protecting. Limiting what users can see is always a great idea, since they can’t compromise what they can’t see.

### Network access restrictions

By default, Azure AI services are accessible from all networks.

The following services allow for network access restrictions:

- Anomaly Detector
- Azure OpenAI
- Content Moderator
- Custom Vision
- Face
- Language Understanding (LUIS)
- Personalizer
- Speech service
- Language
- QnA Maker
- Translator

To limit access to selected networks, you must first change the default action.

### Changing the default action

**When you change the default configuration, all access to the resource is effectively denied**. When all access is denied, requests that attempt to consume the Azure AI services resource aren't permitted. This means your AI service isn't reachable by its clients. **We recommended that you add an exception to a virtual network or firewall policy as you change the default action.**

Note: The Azure portal, Azure PowerShell, or the Azure CLI can still be used to configure the Azure AI services resource.

### Configuring network access restrictions

Network setting for Azure AI services supports three options:

- **(Default) All networks**: The default option applies no networking restrictions to the resource.
- **Selected Networks and Private Endpoints**: Blocks connections to the resource, unless a rule allows access to it. These rules can be set for Azure virtual networks, IP addresses, CIDR, or Private Endpoints.
- **Disabled**: Blocks all traffic to the resource. You can still add access to Private Endpoints. This is the most restrictive option.

### Configuring access rules for virtual networks and IP addresses

To configure access rules for virtual networks and IP addresses:

1. On the Azure portal, open the Azure AI service you want to configure.
2. On the resource page, expand Resource Management on the menu on the left-hand side.
3. Choose Networking.
4. On Allow access from, select Selected Networks and Private Endpoints.
5. Under Virtual Networks, choose + Add existing virtual network.
6. You can search for the desired virtual network by typing its name in the search box.
7. Once you find the virtual network, select it from the list, and select the subnet you want to provide access to the Azure AI service resource.
8. If a Service endpoint isn't present, a warning message shows: The following networks don’t have service endpoints enabled for 'Microsoft.CognitiveServices'. Enabling access takes up to 15 minutes to complete.
9. Choose Enable.
10. Once the service is enabled, choose Add.
11. Choose Save on the resource’s Networking page.
12. Alternatively, under Firewall, you can add an IP address or IP range. Under Firewall, type the IP address you want to allow access to the Azure AI service resource.
13. Choose Save.

Note: To grant access from your on-premises networks to your Azure AI services resource with an IP network rule, you must first identify the internet-facing IP addresses used by your network. Contact your network administrator for help. If you use Azure ExpressRoute or a VPN on-premises for Microsoft peering, you need to identify the NAT IP addresses.

### Configuring access rules for private endpoint connections

**When configuring network access rules for private endpoints, you first need to consider if you want to also allow virtual networks and IP addresses.** If your goal is to restrict access to private endpoints only, you can change the Allow access from option to Disabled. However, **we recommended that you configure the private endpoint connections before you change the network access to Disabled.**

1. On the Azure portal, open the Azure AI service you want to configure.
2. On the resource page, expand Resource Management on the menu on the left-hand side.
3. Choose Networking.
4. On the Networking page, Choose Private endpoint connections.
5. Choose + Private endpoint to create a new connection.
6. On the Create a private endpoint page, make sure the Subscription, and Resource group are correct.
7. Provide a Name, Network Interface Name, and Region for the endpoint of the AI service resource and Choose Next.
8. On the Resource tab, make sure the Target subresource is the AI service you want to configure and Choose Next.
9. On the Virtual Network tab, the wizard shows the available virtual networks and subnets for your private endpoint. Select the virtual network and subnet you want to configure for this private endpoint.
10. You can also configure Dynamic or Statically allocation of IPs and Application security groups. For this tutorial, we use the default configuration. Choose Next.
11. By default, a private DNS integration is configured so the resources can query each other’s DNS name using the IP address of the private endpoint. You can change that configuration if needed. Choose Next.
12. Add the necessary Tags if needed and Choose Next.
13. On the Review + create page, make sure the configuration is validated and Choose Create.
14. The Deployment page shows the deployment progress. Once the deployment is successfully completed, close the Deployment page. 1.Open the Azure AI resource and Choose the Networking option under Resource Management.
15. Under Firewalls and virtual networks, select the option Disabled and Choose Save.
16. Choose the Private endpoint connections tab.
17. If necessary, you can reject or remove the private endpoint connection to remove access from that subnet.

### Exceptions for trusted services

A small subset of Azure services can have a preconfigured exception to network access rules for Azure AI services.

The Azure services under this class of trusted services are:

| Service name | Resource provider name |
| -- | -- |
| Azure AI Services | Microsoft.CognitiveServices |
| Azure Machine Learning (also applies to Azure AI Foundry) | Microsoft.MachineLearningServices |
| Azure AI Search | Microsoft.Search |

To enable or disable exceptions for trusted services:

1. On the Azure portal, open the Azure AI service you want to configure.
2. On the resource page, expand Resource Management on the menu on the left-hand side.
3. Choose Networking.
4. Under Firewalls and virtual networks, make sure Allow access from is set to either Selected Networks and Private Endpoints or Disabled.
5. You can check or uncheck the option Allow Azure services on the trusted services list to access this cognitive services account under Exceptions.

Note: When exceptions are enabled, these trusted services use managed identity to authenticate with your Azure AI service.

---

## Exercise

https://microsoftlearning.github.io/mslearn-ai-services/Instructions/Exercises/02-ai-services-security.html

---

## Module assessment

1. You need to regenerate the primary subscription key for an Azure AI Services resource that an app uses. What should you do first to minimize service interruption for the app? Switch the app to use the secondary key.
2. You want to store the subscription keys for an Azure AI Services resource securely, so that authorized apps can retrieve them when needed. What kind of Azure resource should you provision? Azure Key Vault
3. You want to store the subscription keys for an Azure AI Services resource securely, so that authorized apps can retrieve them when needed. What kind of Azure resource should you provision? In Networking properties, add your client's IP address to the Firewall allowed list.

---

# Monitor Azure AI services

Azure AI services enable you to integrate artificial intelligence into your applications and services. It's important to be able to monitor Azure AI Services in order to **track utilization, determine trends, and detect and troubleshoot issues**.

## Learning objectives
After completing this module, you will be able to:

- Monitor Azure AI services costs.
- Create **alerts** and view **metrics** for Azure AI services.
- Manage Azure AI services **diagnostic logging**.

---

## Monitor cost

One of the main benefits of using cloud services is that you can gain cost efficiencies by only paying for services as you use them. Some Azure AI services resources offer a free tier with restrictions on use, which is useful for development and testing; and one or more billed tiers that incur charges based on transactions. The specific billing rate depends on the resource type.

### Plan costs for AI services
Before deploying a solution that depends on AI services, you can estimate costs by using the [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/).

To use the pricing calculator to estimate AI services costs, create a new estimate and select **Azure AI services** in the **AI + Machine Learning** category. Select the specific AI service API you plan to use. For example, *Azure AI Language*. For the API, select the region where you plan to provision it and the pricing tier of the instance you plan to use. Then, fill in the expected usage metrics and support option. To create an estimate that includes multiple AI services APIs, add more Azure AI services products to the estimate.

After you create an estimate, you can save it. You can also export it in Microsoft Excel format.

### View costs for AI services
In common with other Azure resources, you can view details of accumulated costs for AI services resources in the Azure portal.

To view costs for AI services, sign into the Azure portal and select your subscription. You can then view overall costs for the subscription by selecting the Cost analysis tab. To view only costs for AI services, add a filter that restricts the data to reflect resources with a service name of Azure AI Services.

---

## Create alerts

Microsoft Azure provides alerting support for resources through the creation of *alert rules*. You use alert rules to configure notifications and alerts for your resources based on events or metric thresholds. These alerts will ensure that the correct team knows when a problem arises.

### Alert rules
To create an alert rule for an Azure AI services resource, select the resource in the Azure portal and on the Alerts tab, add a new alert rule. To define the alert rule, you must specify:

- The **scope** of the alert rule - in other words, the **resource** you want to monitor.
- A **condition** on which the alert is triggered. The specific **trigger** for the alert is based on a signal type, which can be Activity Log (an entry in the activity log created by an action performed on the resource, such as regenerating its subscription keys) or Metric (a metric threshold such as the number of errors exceeding 10 in an hour).
- Optional **actions**, such as sending an email to an administrator notifying them of the alert, or running an Azure Logic App to address the issue automatically.
- **Alert rule details**, such as a name for the alert rule and the resource group in which it should be defined.

---

## View metrics

Azure Monitor collects metrics for Azure resources at regular intervals so that you can track indicators of **resource utilization, health, and performance**. The specific metrics gathered depend on the Azure resource. In the case of Azure AI services, Azure Monitor collects metrics relating to **endpoint requests, data submitted and returned, errors**, and other useful measurements.

### View metrics in the Azure portal

You can view metrics for an individual resource in the Azure portal by selecting the resource and viewing its **Metrics** page. On this page, you can add resource-specific metrics to charts. By default an empty chart is created for you, and you can add more charts as required.

For example, the following image shows the Metrics page for an AI services resource, showing the count of total calls to the service over a period of time.

You can add multiple metrics to a chart and choose appropriate aggregations and chart types. When you're satisfied with chart, you can share it by exporting it to Excel or copying a link to it, and you can clone it to create a duplicate chart in the Metrics page - potentially as a starting point for a new chart that shows the same metrics in a different way.

### Add metrics to a dashboard

In the Azure portal, you can create **dashboards** that consist of multiple visualizations from different resources in your Azure environment to help you gain an overall view of **the health and performance of your Azure resources**.

To create a dashboard, select Dashboard in the Azure portal menu (your default view may already be set to a dashboard rather than the portal home page). From here, you can add up to 100 named dashboards to encapsulate views for specific aspects of your Azure services that you want to track.

You can add a range of tiles and other visualizations to a dashboard, and when viewing metrics for a specific resource in a chart, as described previously, you can add the chart to a new or existing dashboard. In the following image, two charts showing metrics for an AI services resource have been added to a dashboard.

---

## Manage diagnostic logging

Diagnostic logging enables you to capture rich operational data for an Azure AI services resource, which can be used to analyze service usage and troubleshoot problems.

### Create resources for diagnostic log storage

To capture diagnostic logs for an AI services resource, you need **a destination for the log data**. In certain cases, you can use **Azure Event Hubs** as a destination for the log data. Azure Event Hubs allows you to forward the data on to a custom telemetry solution and connect directly to some third-party solutions. However, **in most cases you'll use one (or both) of the following kinds of resource** within your Azure subscription:

- **Azure Log Analytics** - a service that enables you to query and visualize log data within the Azure portal.
- **Azure Storage** - a cloud-based data store that you can use to store log archives (which can be exported for analysis in other tools as needed).

You should create these resources before configuring diagnostic logging for your AI services resource. If you intend to archive log data to Azure Storage, create the Azure Storage account in the same region as your AI services resource.

### Configure diagnostic settings

With your log destinations in place, you can configure diagnostic settings for your AI services resource. You define diagnostic settings on the **Diagnostic settings** page of the blade for your AI services resource in the Azure portal. When you add diagnostic settings, you must specify:

- A name for your diagnostic settings.
- The categories of log event data that you want to capture.
- Details of the destinations in which you want to store the log data.

In the following example, the diagnostic settings store all available log data and metrics in Azure Log Analytics and Azure Storage.

### View log data in Azure Log Analytics

It can take an hour or more before diagnostic data starts flowing to the destinations, but when the data has been captured, you can view it in your Azure log Analytics resource by running queries, as shown in this example.

---

## Exercise - Monitor Azure AI services

https://microsoftlearning.github.io/mslearn-ai-services/Instructions/Exercises/03-monitor-ai-services.html

---

## Module assessment

1. How should you collect telemetry for your Azure AI Services resource for later analysis? Configure diagnostic settings
2. You are defining an alert that notifies you when a key regeneration event is recorded in the activity log for your Azure AI Services resource. What should you do? Specify a condition with a Singal Type of Activity Log.
3. You are viewing a metric for your Azure AI Services resource in a chart. You want to combine the chart with visualizations of other resources and data. What should you do? Add the chart to a dashboard.

---

# Deploy Azure AI services in containers

Learn about Container support in Azure AI services allowing the use of APIs available in Azure and enable flexibility in where to deploy and host the services with Docker containers.

## Learning objectives

After completing this module, learners will be able to:

- Create containers for reuse
- Deploy to a container and secure a container
- Consume Azure AI services from a container

---

## Why should I use container?

From MS Copilot:
While you can use Azure AI services directly from the cloud, Azure AI containers provide additional flexibility and control. Here’s why you might still need them:
- **Data Privacy & Compliance**: If your organization has strict regulations that prevent sending data to the cloud, containers allow you to run AI services on-premises or in a private cloud.
- **Performance & Latency**: Containers enable low-latency AI processing by running services closer to your data. This is useful for applications requiring real-time responses.
- **Scalability & Portability**: Containers can be deployed in hybrid environments, including Azure Kubernetes Service (AKS), Azure Stack, or even edge devices.
- **Control Over Model Updates**: You can manage versioning and updates of AI models independently, rather than relying on cloud-based updates.
- **Disconnected Environments**: Some Azure AI containers can run without internet access, making them ideal for remote locations or highly secure environments.

If your workload requires high security, low latency, or offline capabilities, Azure AI containers might be the right choice.


---

## Understand containers

When you deploy a software service, it must be hosted in an environment that provides the hardware, operating system, and supporting runtime components on which the service depends.

Azure AI services is provided as a cloud service, in which the service software is hosted in an Azure data center that provides the underlying runtime services, operating system, and hardware. However, you can also deploy some Azure AI services in a **container**, which encapsulates the necessary runtime components, and which is in turn deployed in a container host that provides the underlying operating system and hardware.

### What is a container?

A container comprises an application or service and the runtime components needed to run it, while abstracting the underlying operating system and hardware. In practice, this abstraction results in two significant benefits:

- **Containers are portable across hosts, which may be running different operating systems or use different hardware** - making it easier to move an application and all its dependencies.
- **A single container host can support multiple isolated containers, each with its own specific runtime configuration** - making it easier to consolidate multiple applications that have different configuration requirement.

A container is encapsulated in **a container image** that defines the software and configuration it must support. Images can be stored in a central registry, such as Docker Hub, or you can maintain a set of images in your own registry.

### Container deployment

To use a container, you typically pull the container image from a registry and deploy it to a container host, specifying any required configuration settings. The container host can be in the cloud, in a private network, or on your local computer. For example:

- A Docker* server.
- An Azure Container Instance (ACI).
- An Azure Kubernetes Service (AKS) cluster.

_*Docker is an open source solution for container development and management that includes a server engine that you can use to host containers. There are versions of the Docker server for common operating systems, including Microsoft Windows and Linux._

---

## Use Azure AI services containers

There are container images for Azure AI services in the Microsoft Container Registry that you can use to deploy a containerized service that encapsulates an individual Azure AI services service API.

To deploy and use an **Azure AI services container**, the following three activities must occur:

1. The container image for the specific Azure AI services API you want to use is downloaded and deployed to a container host, such as a local Docker server, an Azure Container Instance (ACI), or Azure Kubernetes Service (AKS).
2. Client applications submit data to the endpoint provided by the containerized service, and retrieve results just as they would from an Azure AI services cloud resource in Azure.
3. Periodically, usage metrics for the containerized service are sent to an Azure AI services resource in Azure in order to calculate billing for the service.

Even when using a container, you must provision an Azure AI services resource in Azure for billing purposes. **Client applications send their requests to the containerized service, meaning that potentially sensitive data is not sent to the Azure AI services endpoint in Azure**; but the container must be able to connect to the Azure AI services resource in Azure periodically to send usage metrics for billing.

### Azure AI services container images

**Each container provides a subset of Azure AI services functionality**. For example, **not all features of the Azure AI Language service are in a single container**. Language detection, translation, and sentiment analysis are each separate container images. However, the setup steps are similar for each container.

#### Language containers

For the AI Language service, the core features map to separate images:

| Feature | Image |
| -- | -- |
| Key Phrase Extraction | mcr.microsoft.com/azure-cognitive-services/textanalytics/keyphrase |
|Language Detection | mcr.microsoft.com/azure-cognitive-services/textanalytics/language |
|Sentiment Analysis | mcr.microsoft.com/azure-cognitive-services/textanalytics/sentiment |
|Named Entity Recognition | mcr.microsoft.com/product/azure-cognitive-services/textanalytics/language/about |
|Text Analytics for health | mcr.microsoft.com/product/azure-cognitive-services/textanalytics/healthcare/about |
|Translator | mcr.microsoft.com/product/azure-cognitive-services/translator/text-translation/about |
|Summarization | mcr.microsoft.com/azure-cognitive-services/textanalytics/summarization |

#### Speech containers

| Feature | Image |
| -- | -- |
| Speech to textm | mcr.microsoft.com/product/azure-cognitive-services/speechservices/speech-to-text/about|
| Custom Speech to text | mcr.microsoft.com/product/azure-cognitive-services/speechservices/custom-speech-to-text/about|
| Neural Text to speech | mcr.microsoft.com/product/azure-cognitive-services/speechservices/neural-text-to-speech/about|
| Speech language detection | mcr.microsoft.com/product/azure-cognitive-services/speechservices/language-detection/about|

#### Vision containers

| Feature | Image |
| -- | -- |
| Read OCR | mcr.microsoft.com/product/azure-cognitive-services/vision/read/about |
| Spatial analysis | mcr.microsoft.com/product/azure-cognitive-services/vision/spatial-analysis/about |

You can use the Docker pull command to download container images to work with them directly from your machine. Some of the containers are in a "Gated" public preview state, and you need to explicitly request access to use them. Otherwise the containers are available for anyone to use with their Azure AI services deployment.

For a full list of currently available Azure AI services container images, and [specific notes for each one, see Azure AI services container image tags and release notes](https://learn.microsoft.com/en-us/azure/ai-services/cognitive-services-container-support#containers-in-azure-ai-services).

### Azure AI services container configuration

When you deploy an Azure AI services container image to a host, you must specify three settings.

| Setting | Description |
| -- | -- |
| ApiKey | Key from your deployed Azure AI service; used for billing. |
| Billing | Endpoint URI from your deployed Azure AI service; used for billing. |
| Eula | Value of accept to state you accept the license for the container. |

### Consuming Azure AI services from a Container

After your Azure AI services container is deployed, **applications consume the containerized Azure AI services endpoint rather than the default Azure endpoint**. The client application must be configured with the appropriate endpoint for your container, but does not need to provide a subscription key to be authenticated. You can implement your own authentication solution and apply network security restrictions as appropriate for your specific application scenario.

---

## Exercise - Use a container

https://microsoftlearning.github.io/mslearn-ai-services/Instructions/Exercises/04-use-a-container.html

---

## Module assessment

1. You plan to use an Azure AI services container in a local Docker host. Which of the following statements is true? The continaer must be able to connect to the Azure resource endpoint to send usage data for billing.
2. Which of the following parameters must you specify when deploying an Azure AI services container image? End-User License Agreement (EULA)
3. You plan to use the language detection functionality of Azure AI Language in a container. Which container image should you deploy? mcr.microsoft.com/azure-cognitive-services/textanalytics/language

---

# Use AI responsibly with Azure AI Content Safety

https://learn.microsoft.com/en-us/training/modules/responsible-content-safety/

Azure AI Content Safety is a comprehensive tool designed to **detect and manage harmful content** in both user-generated and AI-generated materials. Learn how Azure AI Content Safety uses text and image APIs to help **identify and filter out content related to violence, hate, sexual content, and self-harm**.

## Learning objectives
By the end of this module, you'll be able to:

- Describe Azure AI Content Safety.
- Describe how Azure AI Content Safety operates.
- Describe when to use Azure AI Content Safety.

---

## Introduction

The amount of user-generated content being posted online is growing rapidly. We are also increasingly aware of the need to protect everyone from inappropriate or harmful content.

**Azure AI Content Safety is an AI service designed to help developers include advanced content safety into their applications and services.**

The challenges in maintaining safe and respectful online spaces are growing for developer teams responsible for hosting online discussions. Azure AI Content Safety identifies potentially unsafe content and helps organizations to comply with regulations and meet their own quality standards.

The need for improving online content safety has four main drivers:

- **Increase in harmful content**: There's been a huge growth in user-generated online content, including harmful and inappropriate content.
- **Regulatory pressures**: Government pressure to regulate online content.
- **Transparency**: Users need transparency in content moderation standards and enforcement.
- **Complex content**: Advances in technology are making it easier for users to post multimodal content and videos.

Note: Azure AI Content Safety replaces Azure Content Moderator, which was deprecated in February 2024 and will be retired by February 2027.

In this module, you'll learn about the key features of Azure AI Content Safety, and when each might be used.

---

## What is Content Safety

Azure AI Content Safety is a set of advanced content moderating features that can be incorporated into your applications and services. Azure AI Content Safety is available as a resource in the Azure portal.

Online content safeguarding is needed in a growing number of situations. Not only are we concerned with moderating content generated by people, but must also guard against the malicious use of AI.

### Trusting user-generated content

Social interaction is increasingly a part of many digital spaces. Genuine user-generated content is seen as independent and trustworthy, and used alongside advertising and marketing. Different industries are encouraging their customers to connect with each other and their brand.

Harmful content has many negative effects. It damages trusted brands, discourages users from participating in online forums, and can have a devastating impact on individuals.

**Azure AI Content Safety is designed to be used in applications and services to protect against harmful user-generated and AI-generated content.**

### Content Safety in Azure AI Foundry

Azure [AI Content Safety](https://ai.azure.com/explore/contentsafety) is available as part of Azure AI Foundry, a unified platform that enables you to explore many different Azure AI services, including Content Safety.

From the Azure AI Foundry home page, scroll down and select Explore Azure AI Services. From here, you can explore Content Safety by selecting View all Content Safety capabilities.

**Azure AI Content Safety Studio** enables you to explore and test Content Safety features for yourself. Select the feature you want to try, and then select Try it out. You can then use the user interface to test samples or your own material. Select View code to generate sample code in C#, Java, or Python. You can then copy and paste the sample code and amend the variables to use your own data.

---

## How does Azure AI Content Safety work?

**Azure AI Content Safety works with text and images, and AI-generated content.**

Content Safety vision capabilities are powered by Microsoft's Florence foundation model, which has been trained with billions of text-image pairs. Text analysis uses natural language processing techniques, giving a better understanding of nuance and context. Azure AI Content Safety is multilingual and can detect harmful content in both short form and long form. It's currently available in English, German, Spanish, French, Portuguese, Italian, and Chinese.

Azure AI Content Safety classifies content into **four categories**:

- **Hate**
- **Sexual**
- **Self-harm**
- **Violence**

A severity level for each category is used to determine whether content should be blocked, sent to a moderator, or auto approved.

Azure AI Content Safety features include:

### Safeguarding text content

- **Moderate text** scans text across **four categories**: *violence, hate speech, sexual content, and self-harm*. **A severity level from 0 to 6** is returned for each category. This level helps to prioritize what needs immediate attention by people, and how urgently. You can also create a blocklist to scan for terms specific to your situation.

- **Prompt shields** is a unified API to identify and block jailbreak attacks from inputs to LLMs. It includes both user input and documents. These attacks are prompts to LLMs that attempt to bypass the model's in-built safety features. User prompts are tested to ensure the input to the LLM is safe. Documents are tested to ensure they don't contain unsafe instructions embedded within the text.

- **Protected material detection** checks AI-generated text for protected text such as recipes, copyrighted song lyrics, or other original material.

- **Groundedness detection** protects against inaccurate responses in AI-generated text by LLMs. Public LLMs use data available at the time they were trained. However, data can be introduced after the original training of the model or be built on private data. A **grounded response** is one where *the model’s output is based on the source information*. An **ungrounded response** is one where *the model's output varies from the source information*. Groundedness detection includes a reasoning option in the API response. This adds a reasoning field that explains any ungroundedness detection. However, reasoning increases processing time and costs.

### Safeguarding image content

- **Moderate images** scans for inappropriate content across **four categories**: *violence, self-harm, sexual, and hate*. A **severity level** is returned: *safe, low, or high*. You then set a **threshold level** of *low, medium, or high*. The combination of the severity and threshold level determines whether the image is allowed or blocked for each category.

- **Moderate multimodal content** scans both images and text, including text extracted from an image using optical character recognition (OCR). Content is analyzed across **four categories**: *violence, hate speech, sexual content, and self-harm*.

### Custom safety solutions

- **Custom categories** enables you to create your own categories by *providing positive and negative examples*, and training the model. Content can then be scanned according to your own category definitions.

- **Safety system message** helps you to write effective prompts to guide an AI system's behavior.

### Limitations

Foundry Content Safety uses AI algorithms, and so may not always detect inappropriate language. And on occasions it might block acceptable language because it relies on algorithms and machine learning to detect problematic language.

Foundry Content Safety should be *tested and evaluated on real data before being deployed*. And once deployed, you should *continue to monitor the system* to see how accurately it's performing.

### Evaluating accuracy

When evaluating how accurately Foundry Content Safety is for your situation, compare its performance against **four criteria**:

- **True positive** - correct identification of harmful content.
- **False positive** - incorrect identification of harmful content.
- **True negative** - correct identification of harmless content.
- **False negative** - harmful content isn't identified.

Foundry Content Safety works best to support human moderators who can resolve cases of incorrect identification. When people add content to a site, they don't expect posts to be removed without reason. Communicating with users about why content is removed or flagged as inappropriate helps everyone to understand what is permissible and what isn't.

---

## [When to use Azure AI Foundry Content Safety](https://learn.microsoft.com/en-us/training/modules/responsible-content-safety/4-when-to-use-content-safety)

Many online sites encourage users to share their views. People trust other people's feedback about products, services, brands, and more. These comments are often frank, insightful, and seen to be free of marketing bias. But not all content is well intended.

**Azure AI Foundry Content Safety** is an AI service designed to provide a more comprehensive approach to content moderation. Foundry Content Safety helps organizations to prioritize work for human moderators in a growing number of situations:

### Education
The number of learning platforms and online educational sites is growing rapidly, with more and more information being added all the time. Educators need to be sure that students aren't being exposed to inappropriate content, or inputting harmful requests to LLMs. In addition, both educators and students want to know that the content they're consuming is correct and close to the source material.

### Social
Social media platforms are dynamic and fast moving, requiring real-time moderation. Moderation of user-generated content includes posts, comments, and images. Foundry Content Safety helps moderate content that is nuanced and multi-lingual to identify harmful material.

### Brands
Brands are making more use of chat rooms and message forums to encourage loyal customers to share their views. However offensive material can damage a brand, and discourage customers from contributing. They want to be assured that inappropriate material can be quickly identified and removed. Brands are also adding generative AI services to help people to communicate with them, and therefore need to guard against bad actors attempting to exploit large language models (LLMs).

### E-Commerce
User content is generated by reviewing products and discussing products with other people. This material is powerful marketing, but when inappropriate content is posted it damages consumer confidence. In addition, regulatory and compliance issues are increasingly important. Foundry Content Safety helps screen product listings for fake reviews and other unwanted content.

### Gaming
Gaming is a challenging area to moderate due to its highly visual and often violent graphics. Gaming has strong communities where people are enthusiastic about sharing progress and their experiences. Supporting human moderators to keep gaming safe includes monitoring avatars, usernames, images, and text-based materials. Foundry Content Safety has advanced AI vision tools to help moderate gaming platforms to detect misconduct.

### Generative AI services
Organizations are increasingly using generative AI services to enable internal data to be accessed more easily. To maintain the integrity and safety of internal data, both user prompts and AI-generated outputs need to be checked to prevent malicious use of these systems.

### News
News websites need to moderate user comments to prevent the spread of misinformation. Foundry Content Safety can identify language that includes hate speech and other harmful content.

### Other situations
There are many other situations where content needs to be moderated. Foundry Content Safety can be customized to identify problematic language for specific cases.

---

## [Exercise - Implementing Azure AI Foundry Content Safety](https://learn.microsoft.com/en-us/training/modules/responsible-content-safety/5-exercise-content-safety)

### [Implement Azure AI Content Safety](https://microsoftlearning.github.io/mslearn-ai-services/Instructions/Exercises/05-implement-content-safety.html)

In this exercise, you will provision a Content Safety resource, test the resource in Azure AI Studio, and test the resource in code.

---

## Module assessment

1. Which feature of Azure AI Foundry Content Safety helps protect large language models from document injection attacks? Prompt Shields
2. What is the purpose of the Groundedness detection feature in Foundry Content Safety? To verify AI-generated text is based on provided source materials.
3. Which social media issues does Foundry Content Safety address? The growth of inappropriate online content including bullying and hate speech.
4. How does Foundry Content Safety help businesses to protect their brand image? By moderating comments and messages from customers.
5. What is a benefit of Foundry Content Safety? Reducing the amount of psychologically damaging material that human moderators are exposed to.

---

## Summary

The proliferation of user-generated content makes it near-impossible for human moderators to effectively manage online platforms. Yet as the amount of user-generated content grows, so does the importance of online safety.

**Azure AI Foundry Content Safety uses AI models to automatically detect violent, sexual, self-harm, or hateful language in real time**. It allocates a severity level, so that human moderators can focus on high-priority cases and be exposed to a smaller amount of disturbing content. Foundry Content Safety includes features to moderate both people-generated and AI-generated material.

In this module, you've seen how the features of Foundry Content Safety can help e-commerce brands, gaming companies, and educators to provide safer spaces for users.