# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/image-search/query](https://api-dashboard.search.brave.com/app/documentation/image-search/query)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/image-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/image-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/image-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/image-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/image-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/image-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/image-search/api-changelog)[How to Guides](https://api-dashboard.search.brave.com/app/documentation/image-search/guides)[Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Image Search API

 ## Query Parameters

 #### # Image Search API

 This table lists the query parameters supported by the Image Search API. Some are required, but
    most are optional.

 ParameterRequiredTypeDefaultDescriptionqtruestring The user’s search query term. Query can not be empty.            Maximum of 400 characters and 50 words in the query.

countryfalsestringUS The search query country, where the results come from.

The country string is limited to 2 character country codes
of supported countries. For a list of supported values,
see Country Codes.

search_langfalsestringen The search language preference.

The 2 or more character language code for which the search
results are provided. For a list of possible values, see
Language Codes.

countfalseint50 The number of search results returned in response.

The maximum is 200. The actual number delivered may be less
than requested.

safesearchfalsestringstrict Filters search results for adult content.

The following values are supported:

spellcheckfalsebooltrue Whether to spellcheck provided query. If the spellchecker
is enabled, the modified query is always used for search.
The modified query can be found in altered key from the
query response model.

 