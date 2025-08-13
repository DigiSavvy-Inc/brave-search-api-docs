# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/spellcheck/get-started](https://api-dashboard.search.brave.com/app/documentation/spellcheck/get-started)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [Get Started](https://api-dashboard.search.brave.com/app/documentation/spellcheck/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/spellcheck/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/spellcheck/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/spellcheck/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/spellcheck/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/spellcheck/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/spellcheck/api-changelog)[General](https://api-dashboard.search.brave.com/app/documentation/general)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # Spellcheck API

 ##### Getting Started

 Brave Search API is a REST API to query Brave Search and get back
search results from the web. The following sections describe how
to curate requests, including parameters and headers, to
Brave Search API and get a JSON response back.

To try the API on a Free plan, you’ll still need to subscribe — you
simply won’t be charged. Once subscribed, you can get an API key
in the API Keys section.

## Endpoints

The Spellcheck API is currently available at the
following endpoint and exposes an API to spell check a given query.

```
https://api.search.brave.com/res/v1/spellcheck/search
```

Brave Search API exposes multiple endpoints for specific types of data,
based on the level of your subscription. If you don’t see the endpoint
you’re interested in, you may need to change your subscription.

## Examples

Get started immediately with CURL. An example request will look
something like this:

```
curl -s --compressed "https://api.search.brave.com/res/v1/spellcheck/search?q=helo&country=US" \
  -H "Accept: application/json" \
  -H "Accept-Encoding: gzip" \
  -H "X-Subscription-Token: <YOUR_API_KEY>"
```

## Next Steps

To learn what parameters are available and what responses
can be expected while querying Brave Search, please review
the following pages:

 