# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/ai-grounding/get-started](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/get-started)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Get Started](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/responses)[Code Samples](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/code-samples)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/api-changelog)[Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # Brave AI Grounding API

 ##### Getting Started

 This API provides answers backed by verifiable sources on the Web. This is a step forward to improve accuracy, relevance and trustworthiness of AI-generated answers. Under the hood, the grounding service already powers our Answers with AI, which serves tens of millions of answers every day.

Brave’s grounded answers demonstrate strong performance across a wide range of queries, from simple trivia questions to complex research inquiries. Beyond internal quality assessments, Brave’s grounded answers achieve state-of-the-art (SOTA) performance on the SimpleQA benchmark. Notably, Brave’s grounding service achieves these results without being specifically optimized for the SimpleQA benchmark — the performance emerges as a natural byproduct of the system’s design.

Access to AI Grounding is available through the AI Grounding.

## Endpoints

Brave AI Grounding API exposes the following endpoint.

```
https://api.search.brave.com/res/v1/chat/completions
```

## Example Usage

It is recommended to use OpenAI SDK client, curl is here for demonstration purposes only.

```
curl -X POST  -s --compressed "https://api.search.brave.com/res/v1/chat/completions" \
  -H "accept: application/json" \
  -H "Accept-Encoding: gzip" \
  -H "Content-Type: application/json" \
  -d '{"stream": "false", "messages": [{"role": "user", "content": "What is the second highest mountain?"}]}' \
  -H "x-subscription-token: <YOUR_BRAVE_SEARCH_API_KEY>"
```

The answer can be streamed as a list of messages or it can be awaited and retrieved all at once. Messages are stringified, but follow these models.

## Single vs Multiple Searches

The decision between single-search and multi-search methods significantly influences both cost efficiency and user experience. Single-search systems execute a single web query, process results via an LLM, and deliver answers rapidly—answers on search.brave.com stream in under 4.5 seconds on average with minimal computational overhead. In contrast, multi-search systems conduct sequential searches as the LLM iteratively refines its strategy, leading to substantially higher costs due to multiple API calls, larger context processing, and extended reasoning compute. Response times extend to minutes, rendering multi-search appropriate for background tasks prioritizing thoroughness over speed, while single-search remains ideal for real-time applications.

Brave Search API achieves SOTA performance in both scenarios.

By default, a single search is issued. If you want to allow the model to issue multiple searches, you can add a field "enable_research": "true" to the request body.

Note on internal limits: When answering questions on the SimpleQA benchmark, we observed that for p99 the model issued 53 queries, analyzed 1000 pages and the final response took about 300 seconds. We have selected reasonable limits based on SimpleQA and other use-cases for all the parameters. We want to highlight that making models more efficient at querying search engines and come to answer faster is an active field of research and development at Brave. For instance, the median question on the SimpleQA benchmark is already answered with a single search.

### Access via OpenAI SDK

Answers with Grounding can also be accessed via the OpenAI SDK like so:

```
from openai import OpenAI

client = OpenAI(
  api_key="<YOUR_BRAVE_SEARCH_API_KEY>",
  base_url="https://api.search.brave.com/res/v1",
)

completions = client.chat.completions.create(
  messages=[
    {
      "role": "user",
      "content": "What are the best things to do in Paris with kids?",
    }
  ],
  model="brave",
  stream=False,
)

print(completions.choices[0].message.content)
```

Because we use custom messages with richer data available than what the SDK allows, we stringify these messages. Message types and their definitions are documented here.

## Spending Limits

This API is publicly offered at 2 requests per second. If this is not enough for your use case, please reach out at searchapi-support@brave.com. Developers can also control the spend by imposing a limit on the credit allowed per month here. Alongside each answer, we will also be sending metadata on the number of searches, input and ouput tokens and the cost per answer. When the answer is streamed, such metadata will be sent as the last message. When the answer is retrieved at once (sync client), this metadata will come with the response header.

Example Metadata message:

```
{
   "tokens_input": 1234,
   "tokens_output": 300,
   "searches": 2,
   "cost": 0.01567,   // $0.01567 = 2 *(4/1000) + (5/1000000) * 1234 + (5/1000000) * 300
}
```

Spending limits will be checked before answering a question. If the limits are not exceeded at the time when a question starts being answered, it will be answered in full, even if it exceeds the limits. Nonetheless, developers will only be charged up to the imposed limit.

## Next Steps

To learn what parameters are available and what responses can be
expected while querying Brave AI Grounding API, please review the following pages:

 