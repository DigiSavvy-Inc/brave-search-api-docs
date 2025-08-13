# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/spellcheck/responses](https://api-dashboard.search.brave.com/app/documentation/spellcheck/responses)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [Get Started](https://api-dashboard.search.brave.com/app/documentation/spellcheck/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/spellcheck/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/spellcheck/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/spellcheck/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/spellcheck/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/spellcheck/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/spellcheck/api-changelog)[General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Spellcheck API

 ## Response Objects

 #### # SpellCheckSearchApiResponse

  Top level response model for successful Spellcheck API requests.     The API can also respond back with an error response based on invalid subscription keys and rate limit events.

 FieldTypeRequiredDescriptiontype"spellcheck"true The type of search api result. The value is always spellcheck.

query[Query](https://api-dashboard.search.brave.com#Query)true Spellcheck search query string. Only the original query is returned.

resultslist [ [SpellCheckResult](https://api-dashboard.search.brave.com#SpellCheckResult) ]true The list of spell-checked results for given query.

#### # Query

  A model representing information gathered around the requested query.

 FieldTypeRequiredDescriptionoriginalstringtrue The original query that was requested.

#### # SpellCheckResult

  Spell-checked query result.

 FieldTypeRequiredDescriptionquerystringtrue The spellcheck-corrected query.

 