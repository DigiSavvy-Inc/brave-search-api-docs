# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/ai-grounding/query](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/query)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Get Started](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/responses)[Code Samples](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/code-samples)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/api-changelog)[Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave AI Grounding API

 ## Query Parameters

 #### # Chat Completions API Request

  Model of Chat Completions API (POST /res/v1/chat/completions) request JSON body. The request will include the question to be answered.

Note: The following parameters are the ones supported by the Brave AI Grounding API integration. When more parameters are supported they will be added to this document.

 FieldTypeRequiredDescriptionmessageslist [ [ChatCompletionsMessage](https://api-dashboard.search.brave.com#ChatCompletionsMessage) ]true The messages to use for the chat completion. The value is a list of           ChatCompletionsMessage           response models.

modelstringfalse The model to use for the chat completion. The value can be (default) or brave.

streamboolfalse Whether to stream the response. The value is true by default. For async clients use openai.AsyncOpenAI and openai.OpenAI for blocking clients.

countrystringfalse The country backend to use for the chat completion. The value is us by default.

Note: This parameter is passed in extra_body field when using the OpenAI CLI.

languagestringfalse The language to use for the chat completion. The value is en by default.

Note: This parameter is passed in extra_body field when using the OpenAI CLI.

enable_entitiesboolfalse Whether to enable entities in the chat completion. The value is false by default.

Note: This parameter is passed in extra_body field when using the OpenAI CLI.

enable_citationsboolfalse Whether to enable citations in the chat completion. The value is false by default.

Note: This parameter is passed in extra_body field when using the OpenAI CLI.

enable_researchboolfalse Whether to enable research mode. Enabling this allows the model to perform multiple searches. The value is false by default.

Note: This parameter is passed in extra_body field when using the OpenAI CLI.

#### # ChatCompletionsMessage

  A message to use for the chat completion. Required to be length of 1 (single user message).

 FieldTypeRequiredDescriptionrolestringtrue The role of the message. Only user is supported for now.

contentstringtrue The content of the message. The value is the question to be answered.

 