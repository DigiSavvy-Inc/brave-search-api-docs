# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/image-search/responses](https://api-dashboard.search.brave.com/app/documentation/image-search/responses)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/image-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/image-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/image-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/image-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/image-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/image-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/image-search/api-changelog)[How to Guides](https://api-dashboard.search.brave.com/app/documentation/image-search/guides)[Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Image Search API

 ## Response Objects

 #### # ImageSearchApiResponse

  Top level response model for successful Image Search API requests.     The API can also respond back with an error response based on invalid subscription keys and rate limit events.

 FieldTypeRequiredDescriptiontype"images"true The type of search API result. The value is always images.

query[Query](https://api-dashboard.search.brave.com#Query)true Image search query string.

resultslist [ [ImageResult](https://api-dashboard.search.brave.com#ImageResult) ]true The list of image results for the given query.

extra[Extra](https://api-dashboard.search.brave.com#Extra)true Additional information about the image search results.

#### # Query

  A model representing information gathered around the requested query.

 FieldTypeRequiredDescriptionoriginalstringtrue The original query that was requested.

alteredstringfalse The altered query by the spellchecker. This is the query that is used to search.

spellcheck_offboolfalse Whether the spellchecker is enabled or disabled.

show_strict_warningstringfalse The value is true if the lack of results is due to a strict safesearch setting. Adult content relevant to the query was found, but was blocked by safesearch.

#### # ImageResult

  A model representing an image result for the requested query.

 FieldTypeRequiredDescriptiontypeimage_resulttrue The type of image search API result. The value is always image_result.

titlestringfalse The title of the image.

urlstringfalse The original page URL where the image was found.

sourcestringfalse The source domain where the image was found.

page_fetchedstringfalse The ISO date time when the page was last fetched. The format is YYYY-MM-DDTHH:MM:SSZ.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false The thumbnail for the image.

properties[Properties](https://api-dashboard.search.brave.com#Properties)false Metadata for the image.

meta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false Aggregated information on the URL associated with the image search result.

confidence"low" | "medium" | "high"false The confidence level for the image result.

#### # Thumbnail

  Aggregated details representing the image thumbnail.

 FieldTypeRequiredDescriptionsrcstringfalse The served URL of the image.

widthintfalse The width of the image.

heightintfalse The height of the image.

#### # Properties

  Metadata on an image.

 FieldTypeRequiredDescriptionurlstringfalse The image URL.

placeholderstringfalse The lower resolution placeholder image URL.

widthintfalse The width of the image.

heightintfalse The height of the image.

#### # MetaUrl

  Aggregated information about a URL.

 FieldTypeRequiredDescriptionschemestringfalse The protocol scheme extracted from the URL.

netlocstringfalse The network location part extracted from the URL.

hostnamestringfalse The lowercased domain name extracted from the URL.

faviconstringfalse The favicon used for the URL.

pathstringfalse The hierarchical path of the URL useful as a display string.

#### # Extra

  Additional information about the image search results.

 FieldTypeRequiredDescriptionmight_be_offensivebooleantrue Indicates whether the image search results might contain offensive content.

 