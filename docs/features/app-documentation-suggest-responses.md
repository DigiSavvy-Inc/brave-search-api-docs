# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/suggest/responses](https://api-dashboard.search.brave.com/app/documentation/suggest/responses)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Get Started](https://api-dashboard.search.brave.com/app/documentation/suggest/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/suggest/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/suggest/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/suggest/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/suggest/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/suggest/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/suggest/api-changelog)[Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Suggest API

 ## Response Objects

 #### # SuggestSearchApiResponse

  Top level response model for successful Suggest Search API requests.     The API can also respond back with an error response based on invalid subscription keys and rate limit events.

 FieldTypeRequiredDescriptiontype"suggest"true The type of search api result. The value is always suggest.

query[Query](https://api-dashboard.search.brave.com#Query)true Suggest search query string. Only the original query is returned.

resultslist [ [SuggestResult](https://api-dashboard.search.brave.com#SuggestResult) ]true The list of suggestions for the given query.

#### # Query

  A model representing information gathered around the requested query.

 FieldTypeRequiredDescriptionoriginalstringtrue The original query that was requested.

#### # SuggestResult

  Suggestions for a query.

 FieldTypeRequiredDescriptionquerystringtrue Suggested query completion.

is_entityboolfalse Whether the suggested enriched query is an entity.

titlestringfalse The suggested query enriched title.

descriptionstringfalse The suggested query enriched description.

imgstringfalse The suggested query enriched image URL.

 