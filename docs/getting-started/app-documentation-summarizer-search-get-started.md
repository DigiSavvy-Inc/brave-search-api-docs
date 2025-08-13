# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/summarizer-search/get-started](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/get-started)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/responses)[Code Samples](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/code-samples)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/api-changelog)[AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # Brave Summarizer Search API

 ##### Getting Started

 Brave Summarizer Search API is a REST API to query Brave Search
and get back a summary of the search results from the web for a
given query. The following sections describe how to curate requests
including parameters and headers to Brave Summarizer Search API and
get a response back.

Access to summarizer is available through the Pro AI plan.

## Endpoints

Brave Summarizer Search API exposes multiple endpoints for specific
types of data for a given query. The endpoints that can be used
to get a summarized response to a query are given below.

```
https://api.search.brave.com/res/v1/web/search
https://api.search.brave.com/res/v1/summarizer/search
https://api.search.brave.com/res/v1/summarizer/summary
https://api.search.brave.com/res/v1/summarizer/summary_streaming
https://api.search.brave.com/res/v1/summarizer/title
https://api.search.brave.com/res/v1/summarizer/enrichments
https://api.search.brave.com/res/v1/summarizer/followups
https://api.search.brave.com/res/v1/summarizer/entity_info
https://api.search.brave.com/res/v1/chat/completions
```

## Example summarizing web search results

An initial request has to be made to the Web Search API endpoint
with a given query. An example CURL request is given below.

```
curl -s --compressed "https://api.search.brave.com/res/v1/web/search?q=what+is+the+second+highest+mountain&summary=1" \
  -H "Accept: application/json" \
  -H "Accept-Encoding: gzip" \
  -H "X-Subscription-Token: <YOUR_API_KEY>"
```

The response specification for the Web Search API request above
can be seen in the (WebSearchApiResponse)
model.

If the query is eligible for a summary or an answer, as in this case,
a summarizer key is provided in the response.

The key is equal
to summarizer key (key)
as part of the (Summarizer)
response model. An example is below:

```
{
  "summarizer": {
    "type": "summarizer",
    "key": "{\"query\": \"what is the second highest mountain\", \"country\": \"us\", \"language\": \"en\", \"safesearch\": \"moderate\", \"results_hash\": \"a51e129180225a2f4fe1a00984bcbf58f0ae0625c97723aae43c2c6e3440715b}"
  }
}
```

The key should be treated as a string and passed as is. The format can change in the future.

The key can be used to poll the summarizer endpoint for the summarized
content. Requests to summarizer are not counted towards your plan and
only the initial request to web search endpoint is billed based on the
selected plan. An example request is below:

```
curl -s --compressed "https://api.search.brave.com/res/v1/summarizer/search?key=%7B%22query%22%3A%22what%20is%20the%20second%20highest%20mountain%22%2C%22country%22%3A%22us%22%2C%22language%22%3A%22en%22%2C%22safesearch%22%3A%22moderate%22%2C%22results_hash%22%3A%22a51e129180225a2f4fe1a00984bcbf58f0ae0625c97723aae43c2c6e3440715b%22%7D&entity_info=1" \
  -H "accept: application/json" \
  -H "Accept-Encoding: gzip" \
  -H "x-subscription-token: <YOUR_API_KEY>"
```

The summarizer results are cached for a limited time, after which the
flow has to be started again to get summarized content.

The response specification for Summarizer Search API can be seen in
the SummarizerSearchApiResponse model.

## Example using OpenAI SDK

The default Brave Search API Summarizer begins with a web search which can then
be summarized using Brave Search’s Answer with AI feature. In addition to this flow
there is an OpenAI compatible endpoint
(/res/v1/chat/completions) which can be used directly with a question to get an answer.

When using this endpoint, the AI model uses Brave Search to gather relevant
context from the Web behind the scene and then summarizes the content for you.

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
  model="brave-pro",
  stream=False,
)

print(completions.choices[0].message.content)
```

## Next Steps

To learn what parameters are available and what responses can be
expected while querying Brave Search, please review the following pages:

 