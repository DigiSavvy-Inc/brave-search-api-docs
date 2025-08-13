# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/video-search/query](https://api-dashboard.search.brave.com/app/documentation/video-search/query)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/video-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/video-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/video-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/video-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/video-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/video-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/video-search/api-changelog)[News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Video Search API

 ## Query Parameters

 #### # Video Search API

 This table lists the query parameters supported by the Video Search API. Some are required, but
    most are optional.

 ParameterRequiredTypeDefaultDescriptionqtruestring The user’s search query term. Query can not be empty.                Maximum of 400 characters and 50 words in the query.

countryfalsestringUS The search query country, where the results come from.

The country string is limited to 2 character country codes
of supported countries. For a list of supported values,
see Country Codes.

search_langfalsestringen The search language preference.

The 2 or more character language code for which the search
results are provided. For a list of possible values, see
Language Codes.

ui_langfalsestringen-US User interface language preferred in response.

Usually of the format <language_code>-<country_code>. For more,
see RFC 9110.
For a list of supported values, see
UI Language Codes.

countfalseint20 The number of search results returned in response.

The maximum is 50. The actual number delivered may be less
than requested. Combine this parameter with offset to paginate
search results.

offsetfalseint0 The zero based offset that indicates number of search
results per page (count) to skip before returning the result.
The maximum is 9. The actual number delivered may be less
than requested based on the query.

In order to paginate results use this parameter together
with count. For example, if your user interface displays
20 search results per page, set count to 20 and offset to
0 to show the first page of results. To get subsequent pages,
increment offset by 1 (e.g. 0, 1, 2). The results may
overlap across multiple pages.

spellcheckfalsebooltrue Whether to spellcheck provided query. If the spellchecker
is enabled, the modified query is always used for search.
The modified query can be found in altered key from the
query response model.

safesearchfalsestringmoderate Filters search results for adult content.

The following values are supported:

freshnessfalsestring Filters search results by when they were discovered.

The following values are supported:
- pd: Discovered within the last 24 hours.
- pw: Discovered within the last 7 Days.
- pm: Discovered within the last 31 Days.
- py: Discovered within the last 365 Days…
- YYYY-MM-DDtoYYYY-MM-DD:  timeframe is also supported by specifying
the date range e.g. 2022-04-01to2022-07-30.

 