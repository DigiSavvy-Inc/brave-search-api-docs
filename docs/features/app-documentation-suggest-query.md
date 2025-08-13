# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/suggest/query](https://api-dashboard.search.brave.com/app/documentation/suggest/query)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Get Started](https://api-dashboard.search.brave.com/app/documentation/suggest/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/suggest/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/suggest/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/suggest/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/suggest/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/suggest/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/suggest/api-changelog)[Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Suggest API

 ## Query Parameters

 #### # Suggest Search API

 This table lists the query parameters supported by the Suggest Search API. Some are required,
    but most are optional.

 ParameterRequiredTypeDefaultDescriptionqtruestring The user’s suggest search query term. Query can not be empty. The max       query length is 400 characters, and the word limit is 50.

countryfalsestringUS The suggest search query country, where potentially the results could         come from.

The country string is limited to 2 character country codes of         supported countries. This is a just a hint for calculating         suggest responses.

For a list of supported supported values, see         Country Codes.

langfalsestringen The suggest search language preference, where potentially the results       could come from.

The 2 or more character language code for which the suggest search       results are provided. This is a just a hint for calculating suggest       responses.

For a list of possible values, see       Language Codes.

countfalseint5 The number of suggestion search results returned in response.       The actual number of results delivered may be less than requested.       Minimum is 1, maximum is 20. The default is 5.

richfalseboolfalse Whether to enhance suggestions with rich results. This requires a paid       autosuggest subscription.

 