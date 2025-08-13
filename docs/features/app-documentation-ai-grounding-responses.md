# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/ai-grounding/responses](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/responses)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Get Started](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/responses)[Code Samples](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/code-samples)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/api-changelog)[Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave AI Grounding API

 ## Response Objects

 #### # AIGroundingResponse

  Response model for AI Grounding API request when stream is true.

 FieldTypeRequiredDescriptionmodelstringtrue The model to use for the chat completion. The value can be (default) or brave.

createdinttrue The Unix timestamp (in seconds) of when the chat completion was created.

idstringtrue A unique identifier for the chat completion. Each chunk has the same ID.

objectstringtrue The object type, which is always chat.completion.

choiceslist [ [ChoiceBlocking](https://api-dashboard.search.brave.com#ChoiceBlocking) ]true A list of chat completion choices. Can contain more than one elements if n is greater than 1. Can also be empty for the last chunk if you set stream_options: {“include_usage”: true}.

usage[Usage](https://api-dashboard.search.brave.com#Usage)false The usage information for the request.

#### # ChoiceBlocking

  A choice in the response.

 FieldTypeRequiredDescriptionindexinttrue The index of the choice. Always 0 as there is only single choice.

message[ChoiceMessage](https://api-dashboard.search.brave.com#ChoiceMessage)true The message for the choice.

finish_reasonstringfalse The reason the choice was finished. Either stop or length or null if not finished.

#### # ChoiceMessage

  The message for the choice.

 FieldTypeRequiredDescriptionrolestringtrue The role of the message. Always assistant.

contentstringfalse The content of the message. Can be empty for the last chunk if you set stream_options: {“include_usage”: true}.

#### # Usage

  The usage information for the request.

 FieldTypeRequiredDescriptionprompt_tokensinttrue The number of tokens in the prompt.

completion_tokensinttrue The number of tokens in the completion.

total_tokensinttrue The total number of tokens in the request.

completion_tokens_details[CompletionTokensDetails](https://api-dashboard.search.brave.com#CompletionTokensDetails)false The details of the completion tokens.

#### # CompletionTokensDetails

  The details of the completion tokens.

 FieldTypeRequiredDescriptionreason_tokensintfalse The number of reasoning tokens.

 