# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/web-search/query](https://api-dashboard.search.brave.com/app/documentation/web-search/query)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/web-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/web-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/web-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/web-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/web-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/web-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/web-search/api-changelog)[Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Web Search API

 ## Query Parameters

 #### # Web Search API

 This table lists the query parameters supported by the Web Search API. Some are required, but
    most are optional.

 ParameterRequiredTypeDefaultDescriptionqtruestring The user’s search query term. Query can not be empty.      Maximum of 400 characters and 50 words in the query.

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

The maximum is 20. The actual number delivered may be less
than requested. Combine this parameter with offset to
paginate search results.

NOTE: Count only applies to web results.

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

safesearchfalsestringmoderate Filters search results for adult content.

The following values are supported:

freshnessfalsestring Filters search results by when they were discovered.

The following values are supported:

text_decorationsfalsebooltrue Whether display strings (e.g. result snippets) should
include decoration markers (e.g. highlighting characters).

spellcheckfalsebooltrue Whether to spellcheck provided query. If the spellchecker
is enabled, the modified query is always used for search.
The modified query can be found in altered key from the
query response model.

result_filterfalsestring A comma delimited string of result types to include in the
search response.

Not specifying this parameter will return back all result types
in search response where data is available and a plan with the
corresponding option is subscribed. The response always includes
query and type to identify any query modifications and response
type respectively.

Available result filter values are:

Example result filter param result_filter=discussions, videos
returns only discussions, and videos responses. Another
example where only location results are required, set the
result_filter param to result_filter=locations.

NOTE: count only applies to web results.

goggles_idfalsestring Goggles act as a custom re-ranking on top of Brave’s
search index. For more details, refer to the
Goggles repository. This parameter is deprecated. Please use the goggles parameter.

gogglesfalselist[string] Goggles act as a custom re-ranking on top of Brave’s
search index. The parameter supports both a url where the Goggle is hosted or the definition of the goggle. For more details, refer to the
Goggles repository. The parameter can be repeated to query with multiple goggles.

unitsfalsestring The measurement units. If not provided, units are derived
from search country.

Possible values are:
- metric: The standardized measurement system
- imperial: The British Imperial system of units.

extra_snippetsfalsebool A snippet is an excerpt from a page you get as a
result of the query, and extra_snippets allow you
to get up to 5 additional, alternative excerpts.

Only available under Free AI, Base AI, Pro AI,
Base Data, Pro Data and Custom plans.

summaryfalsebool This parameter enables summary key generation in web
search results. This is required for summarizer to be enabled.

  You can also optimise your search query by using search operators.

 #### # Local Search API

 This table lists the query parameters supported by the Local Search API. Some are required, but
    most are optional.

 ParameterRequiredTypeDefaultDescriptionidstruelist[string] Unique identifier for the location. Ids can not be empty.
Maximum of 20 ids per request. The parameter can be repeated
to query for multiple ids.

search_langfalsestringen The search language preference.

The 2 or more character language code for which the search
results are provided. For a list of possible values, see
Language Codes.

ui_langfalsestringen-US User interface language preferred in response.

Usually of the format <language_code>-<country_code>. For more,
see RFC 9110.
For a list of supported values, see
UI Language Codes.

unitsfalsestring The measurement units. If not provided, units are derived
from search country.

Possible values are:
- metric: The standardized measurement system
- imperial: The British Imperial system of units.

 