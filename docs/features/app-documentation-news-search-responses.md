# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/news-search/responses](https://api-dashboard.search.brave.com/app/documentation/news-search/responses)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/news-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/news-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/news-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/news-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/news-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/news-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/news-search/api-changelog)[Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave News Search API

 ## Response Objects

 #### # NewsSearchApiResponse

  Top level response model for successful News Search API requests.     The API can also respond back with an error response based on invalid subscription keys and rate limit events.

 FieldTypeRequiredDescriptiontype"news"true The type of search API result. The value is always news.

query[Query](https://api-dashboard.search.brave.com#Query)true News search query string.

resultslist [ [NewsResult](https://api-dashboard.search.brave.com#NewsResult) ]true The list of news results for the given query.

#### # Query

  A model representing information gathered around the requested query.

 FieldTypeRequiredDescriptionoriginalstringtrue The original query that was requested.

alteredstringfalse The altered query by the spellchecker. This is the query that is used to search if any.

cleanedstringfalse The cleaned normalized query by the spellchecker. This is the query that is used to search if any.

spellcheck_offboolfalse Whether the spellchecker is enabled or disabled.

show_strict_warningboolfalse The value is true if the lack of results is due to a strict safesearch setting. Adult content relevant to the query was found, but was blocked by safesearch.

#### # NewsResult

  A model representing a news result for the requested query.

 FieldTypeRequiredDescriptiontypenews_resulttrue The type of news search API result. The value is always news_result.

urlstringtrue The source URL of the news article.

titlestringtrue The title of the news article.

descriptionstringfalse The description for the news article.

agestringfalse A human readable representation of the page age.

page_agestringfalse The page age found from the source web page.

page_fetchedstringfalse The ISO date time when the page was last fetched. The format is YYYY-MM-DDTHH:MM:SSZ.

breakingboolfalse Whether the result includes breaking news.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false The thumbnail for the news article.

meta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false Aggregated information on the URL associated with the news search result.

extra_snippetslist [ [string](https://api-dashboard.search.brave.com#string) ]false A list of extra alternate snippets for the news search result.

#### # Thumbnail

  Aggregated details representing the news thumbnail.

 FieldTypeRequiredDescriptionsrcstringtrue The served URL of the thumbnail associated with the news article.

originalstringfalse The original URL of the thumbnail associated with the news article.

#### # MetaUrl

  Aggregated information about a URL.

 FieldTypeRequiredDescriptionschemestringfalse The protocol scheme extracted from the URL.

netlocstringfalse The network location part extracted from the URL.

hostnamestringfalse The lowercased domain name extracted from the URL.

faviconstringfalse The favicon used for the URL.

pathstringfalse The hierarchical path of the URL useful as a display string.

 