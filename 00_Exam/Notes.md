# [1. Develop generative AI apps in Azure](https://learn.microsoft.com/en-us/training/paths/create-custom-copilots-ai-studio/)

Generative Artificial Intelligence (AI) is becoming more accessible through comprehensive development platforms like Azure AI Foundry. Learn how to build generative AI applications that use language models to chat with your users.

## [1.1 Plan and prepare to develop AI solutions on Azure](https://learn.microsoft.com/en-us/training/modules/prepare-azure-ai-development/)

Microsoft Azure offers multiple services that enable developers to build amazing AI-powered solutions. Proper planning and preparation involves identifying the services you'll use and creating an optimal working environment for your development team.

### 1.1.1 Introduction

The growth in the use of artificial intelligence (AI) in general, and generative AI in particular means that developers are increasingly required to create comprehensive AI solutions. These solutions need to combine machine learning models, AI services, prompt engineering solutions, and custom code.

Microsoft Azure provides multiple services that you can use to create AI solutions. However, before embarking on an AI application development project, it's useful to consider the available options for services, tools, and frameworks as well as some principles and practices that can help you succeed.

This module explores some of the key considerations for planning an AI development project, and introduces Azure AI Foundry; a comprehensive platform for AI development on Microsoft Azure.

### 1.1.2 What is AI?

The term "Artificial Intelligence" (AI) covers a wide range of software capabilities that enable applications to exhibit human-like behavior. AI has been around for many years, and its definition has varied as the technology and use cases associated with it have evolved. In today's technological landscape, AI solutions are built on machine learning models that encapsulate semantic relationships found in huge quantities of data; enabling applications to appear to interpret input in various formats, reason over the input data, and generate appropriate responses and predictions.

Common AI capabilities that developers can integrate into a software application include:

Capability	Description
Diagram of speech bubbles.
Generative AI	The ability to generate original responses to natural language prompts. For example, software for a real estate business might be used to automatically generate property descriptions and advertising copy for a property listing.
Diagram of a human head with a cog for a brain.
Agents	Generative AI applications that can respond to user input or assess situations autonomously, and take appropriate actions. For example, an "executive assistant" agent could provide details about the location of a meeting on your calendar, or even attach a map or automate the booking of a taxi or rideshare service to help you get there.
Diagram of an eye being scanned.
Computer vision	The ability to accept, interpret, and process visual input from images, videos, and live camera streams. For example, an automated checkout in a grocery store might use computer vision to identify which products a customer has in their shopping basket, eliminating the need to scan a barcode or manually enter the product and quantity.
Diagram of a speech bubble and a sound wave.
Speech	The ability to recognize and synthesize speech. For example, a digital assistant might enable users to ask questions or provide audible instructions by speaking into a microphone, and generate spoken output to provide answers or confirmations.
Diagram of a text document.
Natural language processing	The ability to process natural language in written or spoken form, analyze it, identify key points, and generate summaries or categorizations. For example, a marketing application might analyze social media messages that mention a particular company, translate them to a specific language, and categorize them as positive or negative based on sentiment analysis.
Diagram of a form containing information.
Information extraction	The ability to use computer vision, speech, and natural language processing to extract key information from documents, forms, images, recordings, and other kinds of content. For example, an automated expense claims processing application might extract purchase dates, individual line item details, and total costs from a scanned receipt.
Diagram of a chart showing an upward trend.
Decision support	The ability to use historic data and learned correlations to make predictions that support business decision making. For example, analyzing demographic and economic factors in a city to predict real estate market trends that inform property pricing decisions.
Determining the specific AI capabilities you want to include in your application can help you identify the most appropriate AI services that you'll need to provision, configure, and use in your solution.

A closer look at generative AI
Generative AI represents the latest advance in artificial intelligence, and deserves some extra attention. Generative AI uses language models to respond to natural language prompts, enabling you to build conversational apps and agents that support research, content creation, and task automation in ways that were previously unimaginable.

Diagram of a prompt, a language model, and a response.

The language models used in generative AI solutions can be large language models (LLMs) that have been trained on huge volumes of data and include many millions of parameters; or they can be small language models (SLMs) that are optimized for specific scenarios with lower overhead. Language models commonly respond to text-based prompts with natural language text; though increasingly new multi-modal models are able to handle image or speech prompts and respond by generating text, code, speech, or images.

### 1.1.3 Azure AI services

Microsoft Azure provides a wide range of cloud services that you can use to develop, deploy, and manage an AI solution. The most obvious starting point for considering AI development on Azure is Azure AI services; a set of out-of-the-box prebuilt APIs and models that you can integrate into your applications. The following table lists some commonly used Azure AI services (for a full list of all available Azure AI services, see Available Azure AI services).

Service	Description
Azure OpenAI service icon.
Azure OpenAI	Azure OpenAI in Foundry Models provides access to OpenAI generative AI models including the GPT family of large and small language models and DALL-E image-generation models within a scalable and securable cloud service on Azure.
Azure AI Vision service icon.
Azure AI Vision	The Azure AI Vision service provides a set of models and APIs that you can use to implement common computer vision functionality in an application. With the AI Vision service, you can detect common objects in images, generate captions, descriptions, and tags based on image contents, and read text in images.
Azure AI Speech service icon.
Azure AI Speech	The Azure AI Speech service provides APIs that you can use to implement text to speech and speech to text transformation, as well as specialized speech-based capabilities like speaker recognition and translation.
Azure AI Language service icon.
Azure AI Language	The Azure AI Language service provides models and APIs that you can use to analyze natural language text and perform tasks such as entity extraction, sentiment analysis, and summarization. The AI Language service also provides functionality to help you build conversational language models and question answering solutions.
Azure AI Foundry Content Safety service icon.
Azure AI Foundry Content Safety	Azure AI Foundry Content Safety provides developers with access to advanced algorithms for processing images and text and flagging content that is potentially offensive, risky, or otherwise undesirable.
Azure AI Translator service icon.
Azure AI Translator	The Azure AI Translator service uses state-of-the-art language models to translate text between a large number of languages.
Azure AI Face service icon.
Azure AI Face	The Azure AI Face service is a specialist computer vision implementation that can detect, analyze, and recognize human faces. Because of the potential risks associated with personal identification and misuse of this capability, access to some features of the AI Face service are restricted to approved customers.
Azure AI Custom Vision service icon.
Azure AI Custom Vision	The Azure AI Custom Vision service enables you to train and use custom computer vision models for image classification and object detection.
Azure AI Document Intelligence service icon.
Azure AI Document Intelligence	With Azure AI Document Intelligence, you can use pre-built or custom models to extract fields from complex documents such as invoices, receipts, and forms.
Azure AI Content Understanding service icon.
Azure AI Content Understanding	The Azure AI Content Understanding service provides multi-modal content analysis capabilities that enable you to build models to extract data from forms and documents, images, videos, and audio streams.
Azure AI Search service icon.
Azure AI Search	The Azure AI Search service uses a pipeline of AI skills based on other Azure AI Services and custom code to extract information from content and create a searchable index. AI Search is commonly used to create vector indexes for data that can then be used to ground prompts submitted to generative AI language models, such as those provided in Azure OpenAI.
Considerations for Azure AI services resources
To use Azure AI services, you create one or more Azure AI resources in an Azure subscription and implement code in client applications to consume them. In some cases, AI services include web-based visual interfaces that you can use to configure and test your resources - for example to train a custom image classification model using the Custom Vision service you can use the visual interface to upload training images, manage training jobs, and deploy the resulting model.

 Note

You can provision Azure AI services resources in the Azure portal (or by using BICEP or ARM templates or the Azure command-line interface) and build applications that use them directly through various service-specific APIs and SDKs. However, as we'll discuss later in this module, in most medium to large-scale development scenarios it's better to provision Azure AI services resources as part of an Azure AI Foundry project - enabling you to centralize access control and cost management, and making it easier to manage shared resources and build the next generation of generative AI apps and agents.

Single service or multi-service resource?
Most Azure AI services, such as Azure AI Vision, Azure AI Language, and so on, can be provisioned as standalone resources, enabling you to create only the Azure resources you specifically need. Additionally, standalone Azure AI services often include a free-tier SKU with limited functionality, enabling you to evaluate and develop with the service at no cost. Each standalone Azure AI resource provides an endpoint and authorization keys that you can use to access it securely from a client application.

Alternatively, you can provision a multi-service resource that encapsulates multiple AI services in a single Azure resource. Using a multi-service resource can make it easier to manage applications that use multiple AI capabilities. There are two multi-service resource types you can use:

Resource	Description
Azure AI service icon.
Azure AI services	The Azure AI Services resource type includes the following services, making them available from a single endpoint:
Azure AI Speech
Azure AI Language
Azure AI Translator
Azure AI Vision
Azure AI Face
Azure AI Custom Vision
Azure AI Document Intelligence
Azure AI Foundry icon.
Azure AI Foundry	The Azure AI Foundry resource type includes the following services, and supports working with them through an Azure AI Foundry project*:
Azure OpenAI
Azure AI Speech
Azure AI Language
Azure AI Foundry Content Safety
Azure AI Translator
Azure AI Vision
Azure AI Face
Azure AI Document Intelligence
Azure AI Content Understanding
* Azure AI Foundry is discussed in the next unit.

Regional availability
Some services and models are available in only a subset of Azure regions. Consider service availability and any regional quota restrictions for your subscription when provisioning Azure AI services. Use the product availability table to check regional availability of Azure services. Use the model availability table in the Azure OpenAI documentation to determine regional availability for Azure OpenAI models.

Cost
Azure AI services are charged based on usage, with different pricing schemes available depending on the specific services being used. As you plan an AI solution on Azure, use the Azure AI services pricing documentation to understand pricing for the AI services you intend to incorporate into your application. You can use the Azure pricing calculator to estimate the costs your expected usage will incur.

### 1.1.4 Azure AI Foundry

Azure AI Foundry is a platform for AI development on Microsoft Azure. While you can provision individual Azure AI services resources and build applications that consume them without it, the project organization, resource management, and AI development capabilities of Azure AI Foundry makes it the recommended way to build all but the most simple solutions.

Azure AI Foundry provides the Azure AI Foundry portal, a web-based visual interface for working with AI projects. It also provides the Azure AI Foundry SDK, which you can use to build AI solutions programmatically.

Azure AI Foundry projects
In Azure AI Foundry, you manage the resource connections, data, code, and other elements of the AI solution in projects. There are two kinds of project:

Foundry projects
Diagram of a Foundry project.

Foundry projects are associated with an Azure AI Foundry resource in an Azure subscription. Foundry projects provide support for Azure AI Foundry models (including OpenAI models), Azure AI Foundry Agent Service, Azure AI services, and tools for evaluation and responsible AI development.

An Azure AI Foundry resource supports the most common AI development tasks to develop generative AI chat apps and agents. In most cases, using a Foundry project provides the right level of resource centralization and capabilities with a minimal amount of administrative resource management. You can use Azure AI Foundry portal to work in projects that are based in Azure AI Foundry resources, making it easy to add connected resources and manage model and agent deployments.

Hub-based projects
Diagram of a hub-based project.

Hub-based projects are associated with an Azure AI hub resource in an Azure subscription. Hub-based projects include an Azure AI Foundry resource, as well as managed compute, support for Prompt Flow development, and connected Azure storage and Azure key vault resources for secure data storage.

Azure AI hub resources support advanced AI development scenarios, like developing Prompt Flow based applications or fine-tuning models. You can also use Azure AI hub resources in both Azure AI Foundry portal and Azure Machine learning portal, making it easier to work on collaborative projects that involve data scientists and machine learning specialists as well as developers and AI software engineers

Tip

For more information about Azure AI Foundry project types, see What is Azure AI Foundry?

### 1.1.5 Developer tools and SDKs

While you can perform many of the tasks needed to develop an AI solution directly in the Azure AI Foundry portal, developers also need to write, test, and deploy code.

Development tools and environments
There are many development tools and environments available, and developers should choose one that supports the languages, SDKs, and APIs they need to work with and with which they're most comfortable. For example, a developer who focuses strongly on building applications for Windows using the .NET Framework might prefer to work in an integrated development environment (IDE) like Microsoft Visual Studio. Conversely, a web application developer who works with a wide range of open-source languages and libraries might prefer to use a code editor like Visual Studio Code (VS Code). Both of these products are suitable for developing AI applications on Azure.

The Azure AI Foundry for Visual Studio Code extension
When developing Azure AI Foundry based generative AI applications in Visual Studio Code, you can use the Azure AI Foundry for Visual Studio Code extension to simplify key tasks in the workflow, including:

Creating a project.
Selecting and deploying a model.
Testing a model in the playground.
Creating an agent.
Screenshot of the Azure AI Foundry Visual Studio Code extension.

 Tip

For more information about using the Azure AI Foundry for Visual Studio Code extension, see Work with the Azure AI Foundry for Visual Studio Code extension.

GitHub and GitHub Copilot
GitHub is the world's most popular platform for source control and DevOps management, and can be a critical element of any team development effort. Visual Studio and VS Code both provide native integration with GitHub, and access to GitHub Copilot; an AI assistant that can significantly improve developer productivity and effectiveness.

Screenshot of GitHub Copilot in Visual Studio Code.

 Tip

For more information about using GitHub Copilot in Visual Studio Code, see GitHub Copilot in VS Code.

Programming languages, APIs, and SDKs
You can develop AI applications using many common programming languages and frameworks, including Microsoft C#, Python, Node, TypeScript, Java, and others. When building AI solutions on Azure, some common SDKs you should plan to install and use include:

The Azure AI Foundry SDK, which enables you to write code to connect to Azure AI Foundry projects and access resource connections, which you can then work with using service-specific SDKs.
The Azure AI Foundry Models API, which provides an interface for working with generative AI model endpoints hosted in Azure AI Foundry.
The Azure OpenAI in Azure AI Foundry Models API, which enables you to build chat applications based on OpenAI models hosted in Azure AI Foundry.
Azure AI Services SDKs - AI service-specific libraries for multiple programming languages and frameworks that enable you to consume Azure AI Services resources in your subscription. You can also use Azure AI Services through their REST APIs.
The Azure AI Foundry Agent Service, which is accessed through the Azure AI Foundry SDK and can be integrated with frameworks like Semantic Kernel to build comprehensive AI agent solutions.

### 1.1.6 Responsible AI

It's important for software engineers to consider the impact of their software on users, and society in general; including considerations for its responsible use. When the application is imbued with artificial intelligence, these considerations are particularly important due to the nature of how AI systems work and inform decisions; often based on probabilistic models, which are in turn dependent on the data with which they were trained.

The human-like nature of AI solutions is a significant benefit in making applications user-friendly, but it can also lead users to place a great deal of trust in the application's ability to make correct decisions. The potential for harm to individuals or groups through incorrect predictions or misuse of AI capabilities is a major concern, and software engineers building AI-enabled solutions should apply due consideration to mitigate risks and ensure fairness, reliability, and adequate protection from harm or discrimination.

Let's discuss some core principles for responsible AI that have been adopted at Microsoft.

Fairness
A diagram of scales.

AI systems should treat all people fairly. For example, suppose you create a machine learning model to support a loan approval application for a bank. The model should make predictions of whether or not the loan should be approved without incorporating any bias based on gender, ethnicity, or other factors that might result in an unfair advantage or disadvantage to specific groups of applicants.

Fairness of machine learned systems is a highly active area of ongoing research, and some software solutions exist for evaluating, quantifying, and mitigating unfairness in machine learned models. However, tooling alone isn't sufficient to ensure fairness. Consider fairness from the beginning of the application development process; carefully reviewing training data to ensure it's representative of all potentially affected subjects, and evaluating predictive performance for subsections of your user population throughout the development lifecycle.

Reliability and safety
A diagram of a shield.

AI systems should perform reliably and safely. For example, consider an AI-based software system for an autonomous vehicle; or a machine learning model that diagnoses patient symptoms and recommends prescriptions. Unreliability in these kinds of system can result in substantial risk to human life.

As with any software, AI-based software application development must be subjected to rigorous testing and deployment management processes to ensure that they work as expected before release. Additionally, software engineers need to take into account the probabilistic nature of machine learning models, and apply appropriate thresholds when evaluating confidence scores for predictions.

Privacy and security
A diagram of a padlock.

AI systems should be secure and respect privacy. The machine learning models on which AI systems are based rely on large volumes of data, which may contain personal details that must be kept private. Even after models are trained and the system is in production, they use new data to make predictions or take action that may be subject to privacy or security concerns; so appropriate safeguards to protect data and customer content must be implemented.

Inclusiveness
A diagram of a diverse group of people.

AI systems should empower everyone and engage people. AI should bring benefits to all parts of society, regardless of physical ability, gender, sexual orientation, ethnicity, or other factors.

One way to optimize for inclusiveness is to ensure that the design, development, and testing of your application includes input from as diverse a group of people as possible.

Transparency
A diagram of an eye.

AI systems should be understandable. Users should be made fully aware of the purpose of the system, how it works, and what limitations may be expected.

For example, when an AI system is based on a machine learning model, you should generally make users aware of factors that may affect the accuracy of its predictions, such as the number of cases used to train the model, or the specific features that have the most influence over its predictions. You should also share information about the confidence score for predictions.

When an AI application relies on personal data, such as a facial recognition system that takes images of people to recognize them; you should make it clear to the user how their data is used and retained, and who has access to it.

Accountability
A diagram of a handshake.

People should be accountable for AI systems. Although many AI systems seem to operate autonomously, ultimately it's the responsibility of the developers who trained and validated the models they use, and defined the logic that bases decisions on model predictions to ensure that the overall system meets responsibility requirements. To help meet this goal, designers and developers of AI-based solution should work within a framework of governance and organizational principles that ensure the solution meets responsible and legal standards that are clearly defined.

 Tip

For more information about Microsoft's principles for responsible AI, see the Microsoft responsible AI site.

### 1.1.7 Exercise - Prepare for an AI development project

In this exercise, you use Azure AI Foundry portal to create a project, ready to build an AI solution.

### 1.1.8 Module assessment

### 1.1.9 Summary

In this module, you explored some of the key considerations when planning and preparing for AI application development. You've also had the opportunity to become familiar with Azure AI Foundry, the recommended platform for developing AI solutions on Azure.

 Tip

For latest news and information about developing AI applications on Azure, see Azure AI.

---

## [1.2 Choose and deploy models from the model catalog in Azure AI Foundry portal](https://learn.microsoft.com/en-us/training/modules/explore-models-azure-ai-studio/)

Choose the various language models that are available through the Azure AI Foundry's model catalog. Understand how to select, deploy, and test a model, and to improve its performance.

Learning objectives
By the end of this module, you'll be able to:

Select a language model from the model catalog.
Deploy a model to an endpoint.
Test a model and improve the performance of the model.

### 1.2.1 Introduction

Generative AI applications are built on language models. The development process usually starts with an exploration and comparison of available foundation models to find the one that best suits the particular needs of your application. After selecting a suitable model, you deploy it to an endpoint where it can be consumed by a client application or AI agent.

Foundation models, such as the GPT family of models, are state-of-the-art language models designed to understand, generate, and interact with natural language. Some common use cases for models are:

Speech-to-text and text-to-speech conversion. For example, generate subtitles for videos.
Machine translation. For example, translate text from English to Japanese.
Text classification. For example, label an email as spam or not spam.
Entity extraction. For example, extract keywords or names from a document.
Text summarization. For example, generate a short one-paragraph summary from a multi-page document.
Question answering. For example, provide answers to questions like "What is the capital of France?"
Reasoning. For example, solve a mathematical problem.
In this module, you focus on exploring foundation models used for question answering. The foundation models you explore can be used for chat applications in which you use a language model to generate a response to a user's question.

 Note

The latest breakthrough in generative AI models is owed to the development of the Transformer architecture. Transformers were introduced in the Attention is all you need paper by Vaswani, et al. from 2017. The Transformer architecture provided two innovations to NLP that resulted in the emergence of foundation models:

Instead of processing words sequentially, Transformers process each word independently and in parallel by using attention.
Next to the semantic similarity between words, Transformers use positional encoding to include the information about the position of a word in a sentence.

### 1.2.2 Explore the model catalog

The model catalog in Azure AI Foundry provides a central repository of models that you can browse to find the right language model for your particular generative AI use case.

Screenshot of the model catalog in Azure AI Foundry portal.

Selecting a foundation model for your generative AI app is important as it affects how well your app works. To find the best model for your app, you can use a structured approach by asking yourself the following questions:

Can AI solve my use case?
How do I select the best model for my use case?
Can I scale for real-world workloads?
Let's explore each of these questions.

Can AI solve my use case?
Nowadays we have thousands of language models to choose from. The main challenge is to understand if there's a model that satisfies your needs and to answer the question: Can AI solve my use case?

To start answering this question, you need to discover, filter, and deploy a model. You can explore the available language models through three different catalogs:

Hugging Face: Vast catalog of open-source models across various domains.
GitHub: Access to diverse models via GitHub Marketplace and GitHub Copilot.
Azure AI Foundry: Comprehensive catalog with robust tools for deployment.
Though you can use each of these catalogs to explore models, the model catalog in Azure AI Foundry makes it easiest to explore and deploy a model to build you prototype, while offering the best selection of models.

Let's explore some of the options you need to consider when searching for suitable models.

Choose between large and small language models
First of all, you have a choice between Large Language Models (LLMs) and Small Language Models (SLMs).

LLMs like GPT-4, Mistral Large, Llama3 70B, Llama 405B, and Command R+ are powerful AI models designed for tasks that require deep reasoning, complex content generation, and extensive context understanding.

SLMs like Phi3, Mistral OSS models, and Llama3 8B are efficient and cost-effective, while still handling many common Natural Language Processing (NLP) tasks. They're perfect for running on lower-end hardware or edge devices, where cost and speed are more important than model complexity.

Focus on a modality, task, or tool
Language models like GPT-4 and Mistral Large are also known as chat completion models, designed to generate coherent and contextually appropriate text-based responses. When you need higher levels of performance in complex tasks like math, coding, science, strategy, and logistics, you can also use reasoning models like DeepSeek-R1 and o1.

Beyond text-based AI, some models are multi-modal, meaning they can process images, audio, and other data types alongside text. Models like GPT-4o and Phi3-vision are capable of analyzing and generating both text and images. Multi-modal models are useful when your application needs to process and understand images, such as in computer vision or document analysis. Or when you want to build an AI app that interacts with visual content, such as a digital tutor explaining images or charts.

If your use case involves generating images, tools like DALL·E 3 and Stability AI can create realistic visuals from text prompts. Image generation models are great for designing marketing materials, illustrations, or digital art.

Another group of task-specific models are embedding models like Ada and Cohere. Embeddings models convert text into numerical representations and are used to improve search relevance by understanding semantic meaning. These models are often implemented in Retrieval Augmented Generation (RAG) scenarios to enhance recommendation engines by linking similar content.

When you want to build an application that interacts with other software tools dynamically, you can add function calling and JSON support. These capabilities allow AI models to work efficiently with structured data, making them useful for automating API calls, database queries, and structured data processing.

Specialize with regional and domain-specific models
Certain models are designed for specific languages, regions, or industries. These models can outperform general-purpose generative AI in their respective domains. For example:

Core42 JAIS is an Arabic language LLM, making it the best choice for applications targeting Arabic-speaking users.
Mistral Large has a strong focus on European languages, ensuring better linguistic accuracy for multilingual applications.
Nixtla TimeGEN-1 specializes in time-series forecasting, making it ideal for financial predictions, supply chain optimization, and demand forecasting.
If your project has regional, linguistic, or industry-specific needs, these models can provide more relevant results than general-purpose AI.

Balance flexibility and performance with open versus proprietary models
You also need to decide whether to use open-source models or proprietary models, each with its own advantages.

Proprietary models are best for cutting-edge performance and enterprise use. Azure offers models like OpenAI’s GPT-4, Mistral Large, and Cohere Command R+, which deliver industry-leading AI capabilities. These models are ideal for businesses needing enterprise-level security, support, and high accuracy.

Open-source models are best for flexibility and cost-efficiency. There are hundreds of open-source models available in the Azure AI Foundry model catalog from Hugging Face, and models from Meta, Databricks, Snowflake, and Nvidia. Open models give developers more control, allowing fine-tuning, customization, and local deployment.

Whatever model you choose, you can use the Azure AI Foundry model catalog. Using models through the model catalog meets the key enterprise requirements for usage:

Data and privacy: you get to decide what happens with your data.
Security and compliance: built-in security.
Responsible AI and content safety: evaluations and content safety.
Now you know the language models that are available to you, you should have an understanding of whether AI can indeed solve your use case. If you think a language model would enrich your application, you then need to select the specific model that you want to deploy and integrate.

How do I select the best model for my use case?
To select the best language model for you use case, you need to decide on what criteria you're using to filter the models. The criteria are the necessary characteristics you identify for a model. Four characteristics you can consider are:

Task type: What type of task do you need the model to perform? Does it include the understanding of only text, or also audio, or video, or multiple modalities?
Precision: Is the base model good enough or do you need a fine-tuned model that is trained on a specific skill or dataset?
Openness: Do you want to be able to fine-tune the model yourself?
Deployment: Do you want to deploy the model locally, on a serverless endpoint, or do you want to manage the deployment infrastructure?
You already explored the various types of models available in the previous section. Now, let's explore in more detail how precision and performance can be important filters when choosing a model.

Filter models for precision
In generative AI, precision refers to the accuracy of the model in generating correct and relevant outputs. It measures the proportion of true positive results (correct outputs) among all generated outputs. High precision means fewer irrelevant or incorrect results, making the model more reliable.

When integrating a language model into an app, you can choose between a base model or a fine-tuned model. A base model, like GPT-4, is pretrained on a large dataset and can handle various tasks but can lack precision for specific domains. Techniques like prompt engineering can improve this, but sometimes fine-tuning is necessary.

A fine-tuned model is trained further on a smaller, task-specific dataset to improve its precision and ability to generate relevant outputs for specific applications. You can either use a fine-tuned model or fine-tune a model yourself.

Filter models for performance
You can evaluate your model performance at different phases, using various evaluation approaches.

When you're exploring models through the Azure AI Foundry model catalog, you can use model benchmarks to compare publicly available metrics like coherence and accuracy across models and datasets. These benchmarks can help you in the initial exploration phase, but give little information on how the model would perform in your specific use case.

Benchmark	Description
Accuracy	Compares model-generated text with correct answer according to the dataset. Result is one if generated text matches the answer exactly, and zero otherwise.
Coherence	Measures whether the model output flows smoothly, reads naturally, and resembles human-like language.
Fluency	Assesses how well the generated text adheres to grammatical rules, syntactic structures, and appropriate usage of vocabulary, resulting in linguistically correct and natural-sounding responses.
Groundedness	Measures alignment between the model's generated answers and the input data.
GPT Similarity	Quantifies the semantic similarity between a ground truth sentence (or document) and the prediction sentence generated by an AI model.
Quality index	A comparative aggregate score between 0 and 1, with better-performing models scoring a higher value
Cost	The cost of using the model based on a price-per-token. Cost is a useful metric with which to compare quality, enabling you to determine an appropriate tradeoff for your needs.
To evaluate how a selected model performs regarding your specific requirements, you can consider manual or automated evaluations. Manual evaluations allow you to rate your model's responses. Automated evaluations include traditional machine learning metrics and AI-assisted metrics that are calculated and generated for you.

When you evaluate a model’s performance, it's common to start with manual evaluations, as they quickly assess the quality of the model’s responses. For more systematic comparisons, automated evaluations using metrics like precision, recall, and F1 score based on your own ground truth offer a faster, scalable, and more objective approach.

Can I scale for real-world workloads?
You selected a model for your use case and have successfully built a prototype. Now, you need to understand how to scale for real-world workloads.

Considerations for scaling a generative AI solution include:

Model deployment: Where will you deploy the model for the best balance of performance and cost?
Model monitoring and optimization: How will you monitor, evaluate, and optimize model performance?
Prompt management: How will you orchestrate and optimize prompts to maximize the accuracy and relevance of generated responses?
Model lifecycle: How will you manage model, data, and code updates as part of an ongoing Generative AI Operations (GenAIOps) lifecycle?
Azure AI Foundry provides visual and code-first tools that can help you build and maintain a scalable generative AI solution.

### 1.2.3 Deploy a model to an endpoint

When you develop a generative AI app, you need to integrate language models into your application. To be able to use a language model, you need to deploy the model. Let's explore how to deploy language models in the Azure AI Foundry, after first understanding why to deploy a model.

Why deploy a model?
You train a model to generate output based on some input. To get value out of your model, you need a solution that allows you to send input to the model, which the model processes, after which the output is visualized for you.

With generative AI apps, the most common type of solution is a chat application that expects a user question, which the model processes, to generate an adequate response. The response is then visualized to the user as a response to their question.

Diagram of user question being processed by model deployed to endpoint.

You can integrate a language model with a chat application by deploying the model to an endpoint. An endpoint is a specific URL where a deployed model or service can be accessed. Each model deployment typically has its own unique endpoint, which allows different applications to communicate with the model through an API (Application Programming Interface).

When a user asks a question:

An API request is sent to the endpoint.
The endpoint specifies the model that processes the request.
The result is sent back to the app through an API response.
Now that you understand why you want to deploy a model, let's explore the deployment options with Azure AI Foundry.

Deploy a language model with Azure AI Foundry
When you deploy a language model with Azure AI Foundry, you have several types available, which depend on the model you want to deploy.

Deploy options include:

Standard deployment: Models are hosted in the Azure AI Foundry project resource.
Serverless compute: Models are hosted in Microsoft-managed dedicated serverless endpoints in an Azure AI Foundry hub project.
Managed compute: Models are hosted in managed virtual machine images in an Azure AI Foundry hub project.
The associated cost depends on the type of model you deploy, which deployment option you choose, and what you are doing with the model:

Standard deployment	Serverless compute	Managed compute
Supported models	Azure AI Foundry models (including Azure OpenAI models and Models-as-a-service models)	Foundry Models with pay-as-you-go billing	Open and custom models
Hosting service	Azure AI Foundry resource	AI Project resource in a hub	AI Project resource in a hub
Billing basis	Token-based billing	Token-based billing	Compute-based billing

 Note: Standard deployment is recommended for most scenarios.

### 1.2.4 Optimize model performance

After you deploy your model to an endpoint, you can start interacting with it to see how it works. Let's explore how you can use prompt engineering techniques to optimize your model's performance.

Apply prompt patterns to optimize your model's output
The quality of the questions you send to the language model, directly influences the quality of the responses you get back. You can carefully construct your question, or prompt, to receive better and more interesting responses. The process of designing and optimizing prompts to improve the model's performance is also known as prompt engineering.

Prompt engineering requires users to ask relevant, specific, unambiguous, and well-structured questions, instructing the model to generate more accurate responses. To understand how to create well-defined prompts, let's explore some patterns that help you improve the output of a model:

Instruct the model to act as a persona.
Guide the model to suggest better questions.
Provide a template to generate output in a specific format.
Understand how a model reasons by asking it to reflect.
Add context to improve the accuracy of the model's output.
 Note

The patterns listed here are based on the work by White et al., (2023) who constructed a prompt pattern catalog.

As a developer, an effective approach is to add instructions to your deployed model in the form of a system prompt. The system prompt sets the model's behavior and allows you to guide the model without exposing the end user to the instructions. The best results are often achieved through the assignment of an explicit system prompt and guidance (or templates) that help users submit prompts that reflect the patterns described here.

Instruct the model to act as a persona
When you want the model to take a specific point of view or perspective when answering a question, you can ask it to act as a persona.

For example, you can ask the model to respond as if it's a seasoned marketing professional if you're working in sales and need insights about a new CRM software.

No persona specified	With persona specified
System prompt	None	You're a seasoned marketing professional that writes advertising copy for an audience of technical customers.
User prompt	Write a one-sentence description of a CRM product.	Write a one-sentence description of a CRM product.
Model response	A CRM product is a software tool designed to manage a company's interactions with current and potential customers, encompassing sales, marketing, customer service, and technical support.	Experience seamless customer relationship management with our CRM product, designed to streamline your business operations, enhance customer interactions, and drive sales growth with its intuitive interface and robust analytics tools.
You can create different personas for various business roles. Think of roles like a product manager, data analyst, customer service expert, or teacher. Define the persona and add more detail to what you expect that persona to know or do to get tailored, context-driven responses.

Ask for better question suggestions
When you want the model to help refine your question, you can ask it to suggest better ways to phrase your query. You can also ask it to provide extra context.

For example, if you're seeking advice on cooking a meal, you can prompt the model to suggest clarifying questions to help you get a more targeted answer.

No suggestions given	With suggestions given
System prompt	You're an AI chef who can advise on menus.	You're an AI chef who can advise on menus. You're approachable and always want to provide the best advice you can.
User prompt	I have to host a dinner party for four people. What should I cook?	I have to host a dinner party for four people. What should I cook? What other information do you need to help me plan a great meal for my guests?
Model response	Hosting a dinner party for four is a wonderful opportunity to showcase your culinary skills. Here's a suggested three-course menu that balances flavors and provides a pleasant dining experience:

Appetizer
Caprese Salad Skewers
- Ingredients: Cherry tomatoes, fresh mozzarella balls, fresh basil leaves, balsamic glaze, olive oil, salt, and pepper.
- Instructions: Thread a cherry tomato, a basil leaf, and a mozzarella ball onto small skewers. Drizzle with olive oil and balsamic glaze, then season with salt and pepper. This dish is light, refreshing, and easy to prepare ahead of time.

Main Course
Herb-Crusted Salmon with Lemon Asparagus
- Ingredients: Salmon fillets, fresh herbs (such as parsley, dill, and thyme), breadcrumbs, lemon, asparagus, olive oil, salt, and pepper.
- Instructions: Preheat your oven to 400°F (200°C). Mix breadcrumbs with chopped fresh herbs and a bit of olive oil to form a paste. Press this mixture onto the salmon fillets and season with salt and pepper. Place salmon on a baking sheet and bake for about 15-20 minutes, or until cooked through. In the last 10 minutes of cooking, toss asparagus with olive oil, lemon zest, salt, and pepper, and roast alongside the salmon. Serve with a squeeze of fresh lemon juice over the salmon and asparagus.

Dessert
Chocolate Mousse with Fresh Berries
-Ingredients: Dark chocolate, eggs, sugar, heavy cream, vanilla extract, and mixed berries (such as strawberries, blueberries, and raspberries).
- Instructions: Melt the chocolate over a double boiler, then let it cool slightly. Separate egg yolks and whites. Whip the egg whites to soft peaks, then gradually add sugar to make a meringue. Whip the heavy cream until soft peaks form and mix in vanilla extract. Fold the melted chocolate into the egg yolks, then gently fold in the whipped cream and meringue until combined. Spoon the mousse into serving dishes and refrigerate for at least 2 hours. Serve topped with fresh berries for a burst of color and freshness.

Additional Tips
- Pairings: Consider serving a light white wine with the appetizer and main course, and perhaps a dessert wine with the chocolate mousse.
- Timing: Prepare the appetizer and dessert in advance to minimize last-minute stress. The main course will take the most time in the oven, so plan accordingly.

This menu is designed to be elegant yet approachable, ensuring your guests enjoy both the food and the experience. Enjoy your dinner party!	Hosting a dinner party is a wonderful opportunity to showcase your culinary skills and create memorable experiences for your guests. To help you plan a great meal, here are a few questions that can guide you in choosing the perfect menu:

Dietary Preferences/Restrictions: Are any of your guests vegetarian, vegan, gluten-free, or have any food allergies or intolerances? Knowing this will help in selecting dishes that everyone can enjoy.
Flavor Preferences: Do your guests have any favorite cuisines or flavors? For example, do they enjoy Italian, Mexican, Mediterranean, or perhaps something more adventurous like Thai or Indian?
Time and Skill Level: How much time do you have to prepare the meal, and what is your comfort level in the kitchen? Are you looking for a simple meal or are you up for something more elaborate?
Occasion: Is this a casual get-together, a celebration, or something more formal? The nature of the event might influence the menu style.
Seasonal Ingredients: Are you interested in using seasonal ingredients? This can help in choosing fresh and flavorful produce.
Drinks Pairing: Would you like to include alcoholic or non-alcoholic beverages to pair with the meal?

With this information, I can suggest a tailored menu. Here’s a general idea that can be adapted based on your answers:

Starter
Garden Salad with Citrus Vinaigrette: Fresh greens, seasonal vegetables, and a light citrus dressing.
Stuffed Mushrooms: For a vegetarian option, filled with herbs and cheese.

Main Course
Herb-Crusted Chicken Breast: Served with roasted vegetables.
Quinoa Stuffed Bell Peppers: A flavorful vegetarian or vegan option.

Side Dishes
Garlic Butter Roasted Potatoes: Classic and comforting.
Steamed Green Beans with Almonds: A simple, healthy side.

Dessert
Chocolate Lava Cake: A decadent treat to end the meal.
Fruit Tart: A lighter, refreshing option.

Drinks
Wine Pairing: A versatile white wine like Sauvignon Blanc or a light red like Pinot Noir.
Mocktail Option: A refreshing citrus mocktail or sparkling water with herbs.


Feel free to share more details, and I can help refine the menu further!
When you encourage the model to suggest clarifications or extra details can help you ask the right questions and achieve better, more accurate answers in fewer interactions.

Specify the desired format for responses
When you want the model to generate output in a specific format, you can provide a template or structure in your prompt.

For example, if you're a sports reporting composing a historical article, you can request that the model follow a specific template, which includes headings, bullet points, and data breakdowns.

No template specified	With template specified
System prompt	You're a helpful AI assistant.	You're a helpful AI assistant for sports reporters.
User prompt	What happened in the 2018 Soccer World Cup final?	What happened in the 2018 Soccer World Cup final? Format the result to show the match date, location, and the two teams competing. Then the final score, and finally any notable events that occurred during the match.
Model response	The 2018 FIFA World Cup final took place on July 15, 2018, at the Luzhniki Stadium in Moscow, Russia. France faced Croatia in the match. France emerged victorious with a 4-2 win. The goals for France were scored by Mario Mandzukic (own goal), Antoine Griezmann (penalty), Paul Pogba, and Kylian Mbappé. Croatia's goals were scored by Ivan Perišić and Mandzukic. Kylian Mbappé, at just 19 years old, became the second youngest player to score in a World Cup final, after Pelé. This victory marked France's second World Cup title, their first being in 1998.	Match Date: July 15, 2018
Location: Luzhniki Stadium, Moscow, Russia
Teams Competing: France vs. Croatia
Final Score: France 4, Croatia 2

Notable Events:
First Half: France took an early lead in the 18th minute with an own goal by Mario Mandžukić after a cross from Antoine Griezmann. Croatia equalized in the 28th minute with a header from Ivan Perišić, who had just come on as a substitute. Just before halftime, in the 44th minute, Paul Pogba scored from a free kick to put France back in the lead.
Second Half: The game saw a dramatic increase in intensity after the break. In the 68th minute, Kylian Mbappé scored his first World Cup goal, bringing the score to 3-1 in favor of France. Croatia managed to score again in the 69th minute when Mandžukić headed in a cross from Perišić, reducing the deficit to 3-2.
Final Moments: In the 81st minute, a controversial penalty was awarded to France after a handball by Croatian defender Dejan Lovren. Griezmann converted the penalty, sealing the victory for France with a 4-2 scoreline.
Additional Context: This match was notable for being the youngest ever World Cup final in terms of average age, featuring players like Mbappé and N’Golo Kanté. France’s victory marked their second World Cup title, having previously won in 1998. Croatia reached the final for the first time in their history, finishing as runners-up.
You can apply this approach to other scenarios where a specific format is needed, such as generating emails, summaries, proposals, or even code and scripts. Define the format template clearly and provide details on how you want the output structured to get consistent and organized responses.

You can also use a one-shot or few-shots approach by providing one or more examples to help the model identify a desired pattern.

Ask for an explanation of reasoning
When you want the model to explain the reasoning behind its answers, you can ask the model to automatically reflect on its rationale and assumptions after providing a response.

For example, if you're working on a mathematical problem, you can ask the model to explain the reasoning behind specific calculations.

No reflection specified	With reflection specified
System prompt	You're an AI math assistant.	You're an AI math assistant. You always explain your answers.
User prompt	A right-angled triangle has a hypotenuse side of length 3 cm and an adjacent side length of 2cm.What is the length of the remaining side?	A right-angled triangle has a hypotenuse side of length 3 cm and an adjacent side length of 2cm.What is the length of the remaining side?
Model response	Approximately 2.24 cm.	We can use the Pythagorean theorem to solve this problem. The Pythagorean theorem states that in a right-angled triangle, the square of the length of the hypotenuse (the side opposite the right angle) is equal to the sum of the squares of the lengths of the other two sides. Mathematically, this can be written as:
c² = a² + b²
where c is the length of the hypotenuse, and a and b are the lengths of the other two sides.
In this problem, we are given the length of the hypotenuse (c = 3 cm) and the length of one of the other sides (a = 2 cm). We need to find the length of the remaining side (b).
Plugging the given values into the Pythagorean theorem, we get:
3² = 2² + b²
9 = 4 + b²
Now, we can solve for b²:
b² = 9 - 4
b² = 5
Finally, we take the square root of both sides to find the length of the remaining side:
b = √5 ≈ 2.24 cm
So, the length of the remaining side is approximately 2.24 cm.
You can apply this approach when you want explanations in data analysis, marketing strategy, or technical troubleshooting. When you ask the model to define its reasoning, you use a technique called chain-of-thought to make it think step by step.

Add context
When you want the model to focus on specific topics, you can specify the context to consider. You can also tell the model to ignore irrelevant information.

For example, if you're planning a trip, you can provide the model with more context to help improve the relevance of its response.

No context specified	With context specified
System prompt	You're an AI travel assistant.	You're an AI travel assistant.
User question	When should I visit Edinburgh?	When should I visit Edinburgh? I'm particularly interested in attending Scotland's home matches in the Six Nations rugby tournament.
Model response	Edinburgh, the capital city of Scotland, is a wonderful destination with a rich history and vibrant culture. The best time to visit Edinburgh largely depends on your preferences for weather, events, and tourist crowds.
Spring (April to June): The weather starts to warm up, and the days get longer. Springtime is perfect for exploring the city's historic sites, gardens, and parks, such as the Royal Botanic Garden. The Edinburgh Festival Fringe, the world's largest arts festival, takes place in August, which is the end of summer.
Summer (July to August): The weather is at its warmest, and the days are long. This is a popular time to visit, but it can also be crowded with tourists. Summer is ideal for outdoor activities, and you can enjoy the Edinburgh International Festival and the Royal Edinburgh Military Tattoo.
Autumn (September to November): The weather begins to cool down, and the leaves change color, creating a picturesque backdrop for the city's historic architecture. It's less crowded, and you can enjoy events like the Edinburgh International Book Festival.
Winter (December to February): The weather is colder, and there may be snowfall, which can create a magical atmosphere. Winter is a quieter time to visit, with fewer tourists and lower prices. You can attend events like the Edinburgh Christmas Market and the Hogmanay Street Party, which celebrates the New Year.

In summary, the best time to visit Edinburgh depends on your preferences. Spring and autumn offer pleasant weather and fewer crowds, while summer is ideal for outdoor activities and festivals. Winter can be a quieter, more magical experience, with festive events to enjoy.	The Six Nations rugby tournament typically runs from late January to early March. Edinburgh, as a host city, often has matches at Murrayfield Stadium, which is Scotland's national stadium. To ensure you don't miss Scotland's home matches in the Six Nations, I recommend planning your visit for this period.

However, keep in mind that match dates and times can vary, so it's a good idea to check the official Six Nations website or the Scottish Rugby Union's website for the exact schedule of matches. Additionally, Edinburgh has a lot to offer beyond rugby, with its rich history, stunning architecture, and vibrant cultural scene, so you might consider extending your stay to explore the city before or after the tournament.

Also, remember that visiting during the tournament might mean larger crowds and busier accommodations, so book your flights, hotel, and transportation well in advance to ensure a smooth experience. Enjoy your trip to Edinburgh and the thrilling atmosphere of the Six Nations rugby matches!
By defining what the model should focus on or disregard, you can ensure the conversation stays on track and generate more relevant, tailored responses.

You can specify the context by describing what it should or shouldn't include, and by connecting the model to data sources it should retrieve context from before generating an answer.

Apply model optimization strategies
 Note

This section discusses options and considerations for model optimization that you may consider beyond prompt engineering. A full exploration of how to apply these optimization strategies is beyond the scope of this module.

Prompt engineering can be an effective way to optimize model responses, but in some cases it may not provide sufficient context or guidance to always meet your exact needs. As a developer, you can consider the following additional optimization strategies to improve the relevance of your generative AI application's responses:

Retrieval Augmented Generation (RAG): A technique that involves using a data source to provide grounding context to prompts. RAG can be a useful approach when you need the model to answer questions based on a specific knowledge domain or when you need the model to consider information related to events that occurred after the training data on which the model is based.
Fine-tuning: A technique that involves extending the training of a foundation model by providing example prompts and responses that reflect the desired output format and style.
Both of these approaches involve additional cost, complexity, and maintainability challenges, so as a general rule it's best to start your optimization efforts through prompt engineering, and then consider additional strategies if necessary.

The strategy you should choose as a developer depends on your requirements:

Diagram showing the various strategies to optimize the model's performance.

Optimize for context: When the model lacks contextual knowledge and you want to maximize responses accuracy.
Optimize the model: When you want to improve the response format, style, or speech by maximizing consistency of behavior.
To optimize for context, you can apply a Retrieval Augmented Generation (RAG) pattern. With RAG, you ground your data by first retrieving context from a data source before generating a response. For example, you want employees to ask questions about expense claim processes and limits based on your own corporation's expenses policy documentation.

When you want the model to respond in a specific style or format, you can instruct the model to do so by adding guidelines in the system message. When you notice the model's behavior isn't consistent, you can further enforce consistency in behavior by fine-tuning a model. With fine-tuning, you train a base language model on a dataset of example prompts and responses before integrating it in your application, with the result that the fine-tuned model will produce responses that are consistent with the examples in the fine-tuning training dataset.

You can use any combination of optimization strategies, for example prompt engineering, RAG and a fine-tuned model, to improve your language application.

### 1.2.5 Exercise - Explore, deploy, and chat with language models

The Azure AI Foundry model catalog serves as a central repository where you can explore and use a variety of models, facilitating the creation of your generative AI scenario.

In this exercise, you’ll explore the model catalog in Azure AI Foundry portal, and compare potential models for a generative AI application that assists in solving problems.

### 1.2.6 Module assessment

### 1.2.7 Summary

In this module, you learned how to:

Select a language model from the model catalog.
Deploy a model to an endpoint.
Test a model and improve the performance of the model.

---

## [1.3 Develop an AI app with the Azure AI Foundry SDK](https://learn.microsoft.com/en-us/training/modules/ai-foundry-sdk/)

---

## [1.4 Get started with prompt flow to develop language model apps in the Azure AI Foundry](https://learn.microsoft.com/en-us/training/modules/get-started-prompt-flow-ai-studio/)

---
