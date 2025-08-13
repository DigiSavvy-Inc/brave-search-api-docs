# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/video-search/responses](https://api-dashboard.search.brave.com/app/documentation/video-search/responses)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/video-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/video-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/video-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/video-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/video-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/video-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/video-search/api-changelog)[News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Video Search API

 ## Response Objects

 #### # VideoSearchApiResponse

  Top level response model for successful Video Search API requests.     The API can also respond back with an error response based on invalid subscription keys and rate limit events.

 FieldTypeRequiredDescriptiontype"videos"true The type of search API result. The value is always video.

query[Query](https://api-dashboard.search.brave.com#Query)true Video search query string.

resultslist [ [VideoResult](https://api-dashboard.search.brave.com#VideoResult) ]true The list of video results for the given query.

extra[Extra](https://api-dashboard.search.brave.com#Extra)true Additional information about the video search results.

#### # Query

  A model representing information gathered around the requested query.

 FieldTypeRequiredDescriptionoriginalstringtrue The original query that was requested.

alteredstringfalse The altered query by the spellchecker. This is the query that is used to search if any.

cleanedstringfalse The cleaned noramlized query by the spellchecker. This is the query that is used to search if any.

spellcheck_offboolfalse Whether the spellchecker is enabled or disabled.

show_strict_warningstringfalse The value is true if the lack of results is due to a strict safesearch setting. Adult content relevant to the query was found, but was blocked by safesearch.

#### # VideoResult

  A model representing a video result for the requested query.

 FieldTypeRequiredDescriptiontypevideo_resulttrue The type of video search API result. The value is always video_result.

urlstringtrue The source URL of the video.

titlestringtrue The title of the video.

descriptionstringfalse The description for the video.

agestringfalse A human readable representation of the page age.

page_agestringfalse The page age found from the source web page.

page_fetchedstringfalse The ISO date time when the page was last fetched. The format is YYYY-MM-DDTHH:MM:SSZ.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false The thumbnail for the video.

video[VideoData](https://api-dashboard.search.brave.com#VideoData)false Metadata for the video.

meta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false Aggregated information on the URL associated with the video search result.

#### # Thumbnail

  Aggregated details representing the video thumbnail.

 FieldTypeRequiredDescriptionsrcstringtrue The served URL of the thumbnail associated with the video.

originalstringfalse The original URL of the thumbnail associated with the video.

#### # VideoData

  A model representing metadata gathered for a video.

 FieldTypeRequiredDescriptiondurationstringfalse A time string representing the duration of the video.

viewsintfalse The number of views of the video.

creatorstringfalse The creator of the video.

publisherstringfalse The publisher of the video.

requires_subscriptionboolfalse Whether the video requires a subscription.

tagslist [ string ]false A list of tags relevant to the video.

author[Profile](https://api-dashboard.search.brave.com#Profile)false A list of profiles associated with the video.

#### # Profile

  A profile of an entity associated with the video.

 FieldTypeRequiredDescriptionnamestringtrue The name of the profile.

long_namestringfalse The long name of the profile.

urlstringtrue The original URL where the profile is available.

imgstringfalse The served image URL representing the profile.

#### # MetaUrl

  Aggregated information about a URL.

 FieldTypeRequiredDescriptionschemestringfalse The protocol scheme extracted from the URL.

netlocstringfalse The network location part extracted from the URL.

hostnamestringfalse The lowercased domain name extracted from the URL.

faviconstringfalse The favicon used for the URL.

pathstringfalse The hierarchical path of the URL useful as a display string.

#### # Extra

  Additional information about the video search results.

 FieldTypeRequiredDescriptionmight_be_offensivebooleantrue Indicates whether the video search results might contain offensive content.

 