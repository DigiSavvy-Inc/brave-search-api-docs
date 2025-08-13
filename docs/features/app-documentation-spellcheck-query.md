# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/spellcheck/query](https://api-dashboard.search.brave.com/app/documentation/spellcheck/query)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [Get Started](https://api-dashboard.search.brave.com/app/documentation/spellcheck/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/spellcheck/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/spellcheck/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/spellcheck/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/spellcheck/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/spellcheck/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/spellcheck/api-changelog)[General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Spellcheck API

 ## Query Parameters

 #### # Spellcheck API Query Parameters

 This table lists the query parameters supported by the Spellcheck API. Some are required, but
    most are optional.

 ParameterRequiredTypeDefaultDescriptionqtruestring The user’s spellcheck search query. Query can not be empty.         Maximum of 400 characters and 50 words in the query.

countryfalsestringUS The spellcheck search query country, where potentially the results         could come from. The country string is limited to 2 character country         codes of supported countries. This is a just a hint for calculating         spellcheck responses.

For a list of supported supported values, see         Country Codes.

langfalsestringen The spell check search language preference, where potentially the         results could come from.

The 2 or more character language code for which the spell check         search results are provided. This is a just a hint for calculating         spell check responses.

For a list of possible values, see         Language Codes.

 