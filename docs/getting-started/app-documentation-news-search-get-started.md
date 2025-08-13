# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/news-search/get-started](https://api-dashboard.search.brave.com/app/documentation/news-search/get-started)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/news-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/news-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/news-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/news-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/news-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/news-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/news-search/api-changelog)[Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # Brave News Search API

  Brave Search API is a REST API to query Brave Search and get
back search results from the web. The following sections
describe how to curate requests, including parameters and headers,
to Brave Search API and get a JSON response back.

To try the API on a Free plan, you’ll still need to subscribe — you
simply won’t be charged. Once subscribed, you can get an API key
in the API Keys section.

## Endpoints

Brave Search API exposes multiple endpoints for specific types of
data, based on the level of your subscription. If you don’t see
the endpoint you’re interested in, you may need to change your
subscription.

Brave News Search API is currently available at the following
endpoint and exposes an API to get news from the web relevant
to the query.

```
https://api.search.brave.com/res/v1/news/search
```

## Example

Get started immediately with CURL. An example request will look
something like this:

```
curl -s --compressed "https://api.search.brave.com/res/v1/news/search?q=munich&count=10&country=us&search_lang=en&spellcheck=1" \
  -H "Accept: application/json" \
  -H "Accept-Encoding: gzip" \
  -H "X-Subscription-Token: <YOUR_API_KEY>"
```

## Next Steps

To learn what parameters are available and what responses can be
expected while querying Brave Search, please review the following
pages:

 