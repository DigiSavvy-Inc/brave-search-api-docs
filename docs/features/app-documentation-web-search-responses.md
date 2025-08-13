# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/web-search/responses](https://api-dashboard.search.brave.com/app/documentation/web-search/responses)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/web-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/web-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/web-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/web-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/web-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/web-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/web-search/api-changelog)[Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Web Search API

 ## Response Objects

 #### # WebSearchApiResponse

  Top level response model for successful Web Search API requests.     The response will include the relevant keys based on the plan subscribed,     query relevance or applied     result_filter as a     query parameter. The API can also respond back with an error response     based on invalid subscription keys and rate limit events.

 FieldTypeRequiredDescriptiontype"search"true The type of web search API result. The value is always search.

discussions[Discussions](https://api-dashboard.search.brave.com#Discussions)false Discussions clusters aggregated from forum posts that are relevant to the query.

faq[FAQ](https://api-dashboard.search.brave.com#FAQ)false Frequently asked questions that are relevant to the search query.

infobox[GraphInfobox](https://api-dashboard.search.brave.com#GraphInfobox)false Aggregated information on an entity showable as an infobox.

locations[Locations](https://api-dashboard.search.brave.com#Locations)false Places of interest (POIs) relevant to location sensitive queries.

mixed[MixedResponse](https://api-dashboard.search.brave.com#MixedResponse)false Preferred ranked order of search results.

news[News](https://api-dashboard.search.brave.com#News)false News results relevant to the query.

query[Query](https://api-dashboard.search.brave.com#Query)false Search query string and its modifications that are used for search.

videos[Videos](https://api-dashboard.search.brave.com#Videos)false Videos relevant to the query.

web[Search](https://api-dashboard.search.brave.com#Search)false Web search results relevant to the query.

summarizer[Summarizer](https://api-dashboard.search.brave.com#Summarizer)false Summary key to get summary results for the query.

rich[RichCallbackInfo](https://api-dashboard.search.brave.com#RichCallbackInfo)false Callback information for rich results.

#### # LocalPoiSearchApiResponse

  Top level response model for successful Local Search API request to get extra information for locations. The response will include a list of location results corresponding to the ids in the request. The API can also respond back with an error response in cases like too many ids being requested, invalid subscription keys, and rate limit events. Access to Local Search API requires a subscription to a Pro plan.

 FieldTypeRequiredDescriptiontype"local_pois"true The type of local POI search API result. The value is always local_pois.

resultslist [ [LocationResult](https://api-dashboard.search.brave.com#LocationResult) ]false Location results matching the ids in the request.

#### # LocalDescriptionsSearchApiResponse

  Top level response model for successful Local Search API request to get AI generated description for locations. The response includes a list of generated descriptions corresponding to the ids in the request. The API can also respond back with an error response in cases like too many ids being requested, invalid subscription keys, and rate limit events. Access to Local Search API requires a subscription to a Pro plan.

 FieldTypeRequiredDescriptiontype"local_descriptions"true The type of local description search API result. The value is always local_descriptions.

resultslist [ [LocationDescription](https://api-dashboard.search.brave.com#LocationDescription) ]false Location descriptions matching the ids in the request.

#### # Query

  A model representing information gathered around the requested query.

 FieldTypeRequiredDescriptionoriginalstringtrue The original query that was requested.

show_strict_warningboolfalse Whether there is more content available for query, but the response was restricted due to safesearch.

alteredstringfalse The altered query for which the search was performed.

safesearchboolfalse Whether safesearch was enabled.

is_navigationalboolfalse Whether the query is a navigational query to a domain.

is_geolocalboolfalse Whether the query has location relevance.

local_decisionstringfalse Whether the query was decided to be location sensitive.

local_locations_idxintfalse The index of the location.

is_trendingboolfalse Whether the query is trending.

is_news_breakingboolfalse Whether the query has news breaking articles relevant to it.

ask_for_locationboolfalse Whether the query requires location information for better results.

language[Language](https://api-dashboard.search.brave.com#Language)false The language information gathered from the query.

spellcheck_offboolfalse Whether the spellchecker was off.

countrystringfalse The country that was used.

bad_resultsboolfalse Whether there are bad results for the query.

should_fallbackboolfalse Whether the query should use a fallback.

latstringfalse The gathered location latitutde associated with the query.

longstringfalse The gathered location longitude associated with the query.

postal_codestringfalse The gathered postal code associated with the query.

citystringfalse The gathered city associated with the query.

statestringfalse The gathered state associated with the query.

header_countrystringfalse The country for the request origination.

more_results_availableboolfalse Whether more results are available for the given query.

custom_location_labelstringfalse Any custom location labels attached to the query.

reddit_clusterstringfalse Any reddit cluster associated with the query.

#### # Discussions

  A model representing a discussion cluster relevant to the query.

 FieldTypeRequiredDescriptiontype"search"true The type identifying a discussion cluster. Currently the value is always search.

resultslist [ [DiscussionResult](https://api-dashboard.search.brave.com#DiscussionResult) ]true A list of discussion results.

mutated_by_gogglesbooltrue Whether the discussion results are changed by a Goggle. The value is false by default.

#### # DiscussionResult (SearchResult)

  A discussion result. These are forum posts and discussions that are relevant to the search query.

 FieldTypeRequiredDescriptiontype"discussion"true The discussion result type identifier. The value is always discussion.

data[ForumData](https://api-dashboard.search.brave.com#ForumData)false The enriched aggregated data for the relevant forum post.

#### # ForumData

  Defines a result from a discussion forum.

 FieldTypeRequiredDescriptionforum_namestringtrue The name of the forum.

num_answersintfalse The number of answers to the post.

scorestringfalse The score of the post on the forum.

titlestringfalse The title of the post on the forum.

questionstringfalse The question asked in the forum post.

top_commentstringfalse The top-rated comment under the forum post.

#### # FAQ

  Frequently asked questions relevant to the search query term.

 FieldTypeRequiredDescriptiontype"faq"true The FAQ result type identifier. The value is always faq.

resultslist [ [QA](https://api-dashboard.search.brave.com#QA) ]true A list of aggregated question answer results relevant to the query.

#### # QA

  A question/answer result.

 FieldTypeRequiredDescriptionquestionstringtrue The question being asked.

answerstringtrue The answer to the question.

titlestringtrue The title of the post.

urlstringtrue The URL pointing to the post.

meta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false Aggregated information about the URL.

#### # MetaUrl

  Aggregated information about a URL.

 FieldTypeRequiredDescriptionschemestringtrue The protocol scheme extracted from the URL.

netlocstringtrue The network location part extracted from the URL.

hostnamestringfalse The lowercased domain name extracted from the URL.

faviconstringtrue The favicon used for the URL.

pathstringtrue The hierarchical path of the URL useful as a display string.

#### # Search

  A model representing a collection of web search results.

 FieldTypeRequiredDescriptiontype"search"true A type identifying web search results. The value is always search.

resultslist [ [SearchResult](https://api-dashboard.search.brave.com#SearchResult) ]true A list of search results.

family_friendlybooltrue Whether the results are family friendly.

#### # SearchResult (Result)

  Aggregated information on a web search result, relevant to the query.

 FieldTypeRequiredDescriptiontype"search_result"true A type identifying a web search result. The value is always search_result.

subtype"generic"true A sub type identifying the web search result type.

is_livebooltrue Whether the web search result is currently live. Default value is false.

deep_results[DeepResult](https://api-dashboard.search.brave.com#DeepResult)false Gathered information on a web search result.

schemaslist [ list ]false A list of schemas (structured data) extracted from the page. The schemas try to follow schema.org and will return anything we can extract from the HTML that can fit into these models.

meta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false Aggregated information on the URL associated with the web search result.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false The thumbnail of the web search result.

agestringfalse A string representing the age of the web search result.

languagestringtrue The main language on the web search result.

location[LocationResult](https://api-dashboard.search.brave.com#LocationResult)false The location details if the query relates to a restaurant.

video[VideoData](https://api-dashboard.search.brave.com#VideoData)false The video associated with the web search result.

movie[MovieData](https://api-dashboard.search.brave.com#MovieData)false The movie associated with the web search result.

faq[FAQ](https://api-dashboard.search.brave.com#FAQ)false Any frequently asked questions associated with the web search result.

qa[QAPage](https://api-dashboard.search.brave.com#QAPage)false Any question answer information associated with the web search result page.

book[Book](https://api-dashboard.search.brave.com#Book)false Any book information associated with the web search result page.

rating[Rating](https://api-dashboard.search.brave.com#Rating)false Rating found for the web search result page.

article[Article](https://api-dashboard.search.brave.com#Article)false An article found for the web search result page.

product[Product](https://api-dashboard.search.brave.com#Product)|[Review](https://api-dashboard.search.brave.com#Review)false The main product and a review that is found on the web search result page.

product_clusterlist [ [Product](https://api-dashboard.search.brave.com#Product)|[Review](https://api-dashboard.search.brave.com#Review) ]false A list of products and reviews that are found on the web search result page.

cluster_typestringfalse A type representing a cluster. The value can be product_cluster.

clusterlist [ [Result](https://api-dashboard.search.brave.com#Result) ]false A list of web search results.

creative_work[CreativeWork](https://api-dashboard.search.brave.com#CreativeWork)false Aggregated information on the creative work found on the web search result.

music_recording[MusicRecording](https://api-dashboard.search.brave.com#MusicRecording)false Aggregated information on music recording found on the web search result.

review[Review](https://api-dashboard.search.brave.com#Review)false Aggregated information on the review found on the web search result.

software[Software](https://api-dashboard.search.brave.com#Software)false Aggregated information on a software product found on the web search result page.

recipe[Recipe](https://api-dashboard.search.brave.com#Recipe)false Aggregated information on a recipe found on the web search result page.

organization[Organization](https://api-dashboard.search.brave.com#Organization)false Aggregated information on a organization found on the web search result page.

content_typestringfalse The content type associated with the search result page.

extra_snippetslist [ [string](https://api-dashboard.search.brave.com#string) ]false A list of extra alternate snippets for the web search result.

#### # Result

  A model representing a web search result.

 FieldTypeRequiredDescriptiontitlestringtrue The title of the web page.

urlstringtrue The URL where the page is served.

is_source_localbooltrue is_source_bothbooltrue descriptionstringfalse A description for the web page.

page_agestringfalse A date representing the age of the web page.

page_fetchedstringfalse A date representing when the web page was last fetched.

profile[Profile](https://api-dashboard.search.brave.com#Profile)false A profile associated with the web page.

languagestringfalse A language classification for the web page.

family_friendlybooltrue Whether the web page is family friendly.

#### # AbstractGraphInfobox (Result)

  Shared aggregated information on an entity from a knowledge graph.

 FieldTypeRequiredDescriptiontype"infobox"true The infobox result type identifier. The value is always infobox.

positioninttrue The position on a search result page.

labelstringfalse Any label associated with the entity.

categorystringfalse Category classification for the entity.

long_descstringfalse A longer description for the entity.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false The thumbnail associated with the entity.

attributeslist [ list [ [string](https://api-dashboard.search.brave.com#string) ] ]false A list of attributes about the entity.

profileslist [ [Profile](https://api-dashboard.search.brave.com#Profile) ] | list [ [DataProvider](https://api-dashboard.search.brave.com#DataProvider) ]false The profiles associated with the entity.

website_urlstringfalse The official website pertaining to the entity.

ratingslist [ [Rating](https://api-dashboard.search.brave.com#Rating) ]false Any ratings given to the entity.

providerslist [ [DataProvider](https://api-dashboard.search.brave.com#DataProvider) ]false A list of data sources for the entity.

distance[Unit](https://api-dashboard.search.brave.com#Unit)false A unit representing quantity relevant to the entity.

imageslist [ [Thumbnail](https://api-dashboard.search.brave.com#Thumbnail) ]false A list of images relevant to the entity.

movie[MovieData](https://api-dashboard.search.brave.com#MovieData)false Any movie data relevant to the entity. Appears only when the result is a movie.

#### # GenericInfobox (AbstractGraphInfobox)

  Aggregated information on a generic entity from a knowledge graph.

 FieldTypeRequiredDescriptionsubtype"generic"true The infobox subtype identifier. The value is always generic.

found_in_urlslist [ string ]false List of URLs where the entity was found.

#### # EntityInfobox (AbstractGraphInfobox)

  Aggregated information on an entity from a knowledge graph.

 FieldTypeRequiredDescriptionsubtype"entity"true The infobox subtype identifier. The value is always entity.

#### # QAInfobox (AbstractGraphInfobox)

  A question answer infobox.

 FieldTypeRequiredDescriptionsubtype"code"true The infobox subtype identifier. The value is always code.

data[QAPage](https://api-dashboard.search.brave.com#QAPage)true The question and relevant answer.

meta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false Detailed information on the page containing the question and relevant answer.

#### # InfoboxWithLocation (AbstractGraphInfobox)

  An infobox with location.

 FieldTypeRequiredDescriptionsubtype"location"true The infobox subtype identifier. The value is always location.

is_locationbooltrue Whether the entity a location.

coordinateslist [ float ]false The coordinates of the location.

zoom_levelinttrue The map zoom level.

location[LocationResult](https://api-dashboard.search.brave.com#LocationResult)false The location result.

#### # InfoboxPlace (AbstractGraphInfobox)

  An infobox for a place, such as a business.

 FieldTypeRequiredDescriptionsubtype"place"true The infobox subtype identifier. The value is always place.

location[LocationResult](https://api-dashboard.search.brave.com#LocationResult)true The location result.

#### # GraphInfobox

  Aggregated information on an entity shown as an infobox.

 FieldTypeRequiredDescriptiontype"graph"true The type identifier for infoboxes. The value is always graph.

results[GenericInfobox](https://api-dashboard.search.brave.com#GenericInfobox)|[QAInfobox](https://api-dashboard.search.brave.com#QAInfobox)|[InfoboxPlace](https://api-dashboard.search.brave.com#InfoboxPlace)|[InfoboxWithLocation](https://api-dashboard.search.brave.com#InfoboxWithLocation)|[EntityInfobox](https://api-dashboard.search.brave.com#EntityInfobox)true A list of infoboxes associated with the query.

#### # QAPage

  Aggreated result from a question answer page.

 FieldTypeRequiredDescriptionquestionstringtrue The question that is being asked.

answer[Answer](https://api-dashboard.search.brave.com#Answer)true An answer to the question.

#### # Answer

  A response representing an answer to a question on a forum.

 FieldTypeRequiredDescriptiontextstringtrue The main content of the answer.

authorstringfalse The name of the author of the answer.

upvoteCountintfalse Number of upvotes on the answer.

downvoteCountintfalse The number of downvotes on the answer.

#### # Thumbnail

  Aggregated details representing a picture thumbnail.

 FieldTypeRequiredDescriptionsrcstringtrue The served URL of the picture thumbnail.

originalstringfalse The original URL of the image.

#### # LocationWebResult (Result)

  A model representing a web result related to a location.

 FieldTypeRequiredDescriptionmeta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)true Aggregated information about the URL.

#### # LocationResult (Result)

  A result that is location relevant.

 FieldTypeRequiredDescriptiontype"location_result"true Location result type identifier. The value is always location_result.

idstringfalse A Temporary id associated with this result, which can be used to retrieve extra information about the location. It remains valid for 8 hours…

provider_urlstringtrue The complete URL of the provider.

coordinateslist [ float ]false A list of coordinates associated with the location. This is a lat long represented as a floating point.

zoom_levelinttrue The zoom level on the map.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false The thumbnail associated with the location.

postal_address[PostalAddress](https://api-dashboard.search.brave.com#PostalAddress)false The postal address associated with the location.

opening_hours[OpeningHours](https://api-dashboard.search.brave.com#OpeningHours)false The opening hours, if it is a business, associated with the location .

contact[Contact](https://api-dashboard.search.brave.com#Contact)false The contact of the business associated with the location.

price_rangestringfalse A display string used to show the price classification for the business.

rating[Rating](https://api-dashboard.search.brave.com#Rating)false The ratings of the business.

distance[Unit](https://api-dashboard.search.brave.com#Unit)false The distance of the location from the client.

profileslist [ [DataProvider](https://api-dashboard.search.brave.com#DataProvider) ]false Profiles associated with the business.

reviews[Reviews](https://api-dashboard.search.brave.com#Reviews)false Aggregated reviews from various sources relevant to the business.

pictures[PictureResults](https://api-dashboard.search.brave.com#PictureResults)false A bunch of pictures associated with the business.

action[Action](https://api-dashboard.search.brave.com#Action)false An action to be taken.

serves_cuisinelist [ string ]false A list of cuisine categories served.

categorieslist [ string ]false A list of categories.

icon_categorystringfalse An icon category.

results[LocationWebResult](https://api-dashboard.search.brave.com#LocationWebResult)false Web results related to this location.

timezonestringfalse IANA timezone identifier.

timezone_offsetstringfalse The utc offset of the timezone.

#### # LocationDescription

  AI generated description of a location result.

 FieldTypeRequiredDescriptiontype"local_description"true The type of a location description. The value is always local_description.

idstringtrue A Temporary id of the location with this description.

descriptionstringfalse AI generated description of the location with the given id.

#### # Locations

  A model representing location results.

 FieldTypeRequiredDescriptiontype"locations"true Location type identifier. The value is always locations.

resultslist [ [LocationResult](https://api-dashboard.search.brave.com#LocationResult) ]true An aggregated list of location sensitive results.

#### # MixedResponse

  The ranking order of results on a search result page.

 FieldTypeRequiredDescriptiontype"mixed"true The type representing the model mixed. The value is always mixed.

mainlist [ [ResultReference](https://api-dashboard.search.brave.com#ResultReference) ]false The ranking order for the main section of the search result page.

toplist [ [ResultReference](https://api-dashboard.search.brave.com#ResultReference) ]false The ranking order for the top section of the search result page.

sidelist [ [ResultReference](https://api-dashboard.search.brave.com#ResultReference) ]false The ranking order for the side section of the search result page.

#### # ResultReference

  The ranking order of results on a search result page.

 FieldTypeRequiredDescriptiontypestringtrue The type of the result.

indexintfalse The 0th based index where the result should be placed.

allbooltrue Whether to put all the results from the type at specific position.

#### # Videos

  A model representing video results.

 FieldTypeRequiredDescriptiontypevideostrue The type representing the videos. The value is always videos.

resultslist [ [VideoResult](https://api-dashboard.search.brave.com#VideoResult) ]true A list of video results.

mutated_by_gogglesboolfalse Whether the video results are changed by a Goggle. The value is false by default.

#### # News

  A model representing news results.

 FieldTypeRequiredDescriptiontypenewstrue The type representing the news. The value is always news.

resultslist [ [NewsResult](https://api-dashboard.search.brave.com#NewsResult) ]true A list of news results.

mutated_by_gogglesboolfalse Whether the news results are changed by a Goggle. The value is false by default.

#### # NewsResult (Result)

  A model representing news results.

 FieldTypeRequiredDescriptionmeta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false The aggregated information on the URL representing a news result.

sourcestringfalse The source of the news.

breakingbooltrue Whether the news result is currently a breaking news.

is_livebooltrue Whether the news result is currently live.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false The thumbnail associated with the news result.

agestringfalse A string representing the age of the news article.

extra_snippetslist [ [string](https://api-dashboard.search.brave.com#string) ]false A list of extra alternate snippets for the news search result.

#### # PictureResults

  A model representing a list of pictures.

 FieldTypeRequiredDescriptionviewMoreUrlstringfalse A URL to view more pictures.

resultslist [ [Thumbnail](https://api-dashboard.search.brave.com#Thumbnail) ]true A list of thumbnail results.

#### # Action

  A model representing an action to be taken.

 FieldTypeRequiredDescriptiontypestringtrue The type representing the action.

urlstringtrue A URL representing the action to be taken.

#### # PostalAddress

  A model representing a postal address of a location.

 FieldTypeRequiredDescriptiontype"PostalAddress"true The type identifying a postal address. The value is always PostalAddress.

countrystringfalse The country associated with the location.

postalCodestringfalse The postal code associated with the location.

streetAddressstringfalse The street address associated with the location.

addressRegionstringfalse The region associated with the location. This is usually a state.

addressLocalitystringfalse The address locality or subregion associated with the location.

displayAddressstringtrue The displayed address string.

#### # OpeningHours

  Opening hours of a bussiness at a particular location.

 FieldTypeRequiredDescriptioncurrent_daylist [ [DayOpeningHours](https://api-dashboard.search.brave.com#DayOpeningHours) ]false The current day opening hours. Can have two sets of opening hours.

dayslist [ list [ [DayOpeningHours](https://api-dashboard.search.brave.com#DayOpeningHours) ] ]false The opening hours for the whole week.

#### # DayOpeningHours

  A model representing the opening hours for a particular day for a business at a particular location.

 FieldTypeRequiredDescriptionabbr_namestringtrue A short string representing the day of the week.

full_namestringtrue A full string representing the day of the week.

opensstringtrue A 24 hr clock time string for the opening time of the business on a particular day.

closesstringtrue A 24 hr clock time string for the closing time of the business on a particular day.

#### # Contact

  A model representing contact information for an entity.

 FieldTypeRequiredDescriptionemailstringfalse The email address.

telephonestringfalse The telephone number.

#### # DataProvider

  A model representing the data provider associated with the entity.

 FieldTypeRequiredDescriptiontype"external"true The type representing the source of data. This is usually external.

namestringtrue The name of the data provider. This can be a domain.

urlstringtrue The URL where the information is coming from.

long_namestringfalse The long name for the data provider.

imgstringfalse The served URL for the image data.

#### # Profile

  A profile of an entity.

 FieldTypeRequiredDescriptionnamestringtrue The name of the profile.

long_namestringtrue The long name of the profile.

urlstringfalse The original URL where the profile is available.

imgstringfalse The served image URL representing the profile.

#### # Unit

  A model representing a unit of measurement.

 FieldTypeRequiredDescriptionvaluefloattrue The quantity of the unit.

unitsstringtrue The name of the unit associated with the quantity.

#### # MovieData

  Aggregated data for a movie result.

 FieldTypeRequiredDescriptionnamestringfalse Name of the movie.

descriptionstringfalse A short plot summary for the movie.

urlstringfalse A URL serving a movie profile page.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false A thumbnail for a movie poster.

releasestringfalse The release date for the movie.

directorslist [ [Person](https://api-dashboard.search.brave.com#Person) ]false A list of people responsible for directing the movie.

actorslist [ [Person](https://api-dashboard.search.brave.com#Person) ]false A list of actors in the movie.

rating[Rating](https://api-dashboard.search.brave.com#Rating)false Rating provided to the movie from various sources.

durationstringfalse The runtime of the movie. The format is HH:MM:SS.

genrelist [ string ]false List of genres in which the movie can be classified.

querystringfalse The query that resulted in the movie result.

#### # Thing

  A model describing a generic thing.

 FieldTypeRequiredDescriptiontype"thing"true A type identifying a thing. The value is always thing.

namestringtrue The name of the thing.

urlstringfalse A URL for the thing.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false Thumbnail associated with the thing.

#### # Person (Thing)

  A model describing a person entity.

 FieldTypeRequiredDescriptiontype"person"true A type identifying a person. The value is always person.

emailstringfalse Email address of the person.

#### # Rating

  The rating associated with an entity.

 FieldTypeRequiredDescriptionratingValuefloattrue The current value of the rating.

bestRatingfloattrue Best rating received.

reviewCountintfalse The number of reviews associated with the rating.

profile[Profile](https://api-dashboard.search.brave.com#Profile)false The profile associated with the rating.

is_tripadvisorbooltrue Whether the rating is coming from Tripadvisor.

#### # Book

  A model representing a book result.

 FieldTypeRequiredDescriptiontitlestringtrue The title of the book.

authorlist [ [Person](https://api-dashboard.search.brave.com#Person) ]true The author of the book.

datestringfalse The publishing date of the book.

price[Price](https://api-dashboard.search.brave.com#Price)false The price of the book.

pagesintfalse The number of pages in the book.

publisher[Person](https://api-dashboard.search.brave.com#Person)false The publisher of the book.

rating[Rating](https://api-dashboard.search.brave.com#Rating)false A gathered rating from different sources associated with the book.

#### # Price

  A model representing the price for an entity.

 FieldTypeRequiredDescriptionpricestringtrue The price value in a given currency.

price_currencystringtrue The current of the price value.

#### # Article

  A model representing an article.

 FieldTypeRequiredDescriptionauthorlist [ [Person](https://api-dashboard.search.brave.com#Person) ]false The author of the article.

datestringfalse The date when the article was published.

publisher[Organization](https://api-dashboard.search.brave.com#Organization)false The name of the publisher for the article.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false A thumbnail associated with the article.

isAccessibleForFreeboolfalse Whether the article is free to read or is behind a paywall.

#### # ContactPoint (Thing)

  A way to contact an entity.

 FieldTypeRequiredDescriptiontype"contact_point"true A type string identifying a contact point. The value is always contact_point.

telephonestringfalse The telephone number of the entity.

emailstringfalse The email address of the entity.

#### # Organization (Thing)

  An entity responsible for another entity.

 FieldTypeRequiredDescriptiontype"organization"true A type string identifying an organization. The value is always organization.

contact_pointslist [ [ContactPoint](https://api-dashboard.search.brave.com#ContactPoint) ]false A list of contact points for the organization.

#### # HowTo

  Aggregated information on a how to.

 FieldTypeRequiredDescriptiontextstringtrue The how to text.

namestringfalse A name for the how to.

urlstringfalse A URL associated with the how to.

imagelist [ [string](https://api-dashboard.search.brave.com#string) ]false A list of image URLs associated with the how to.

#### # Recipe

  Aggregated information on a recipe.

 FieldTypeRequiredDescriptiontitlestringtrue The title of the recipe.

descriptionstringtrue The description of the recipe.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)true A thumbnail associated with the recipe.

urlstringtrue The URL of the web page where the recipe was found.

domainstringtrue The domain of the web page where the recipe was found.

faviconstringtrue The URL for the favicon of the web page where the recipe was found.

timestringfalse The total time required to cook the recipe.

prep_timestringfalse The preparation time for the recipe.

cook_timestringfalse The cooking time for the recipe.

ingredientsstringfalse Ingredients required for the recipe.

instructionslist [ [HowTo](https://api-dashboard.search.brave.com#HowTo) ]false List of instructions for the recipe.

servingsintfalse How many people the recipe serves.

caloriesintfalse Calorie count for the recipe.

rating[Rating](https://api-dashboard.search.brave.com#Rating)false Aggregated information on the ratings associated with the recipe.

recipeCategorystringfalse The category of the recipe.

recipeCuisinestringfalse The cuisine classification for the recipe.

video[VideoData](https://api-dashboard.search.brave.com#VideoData)false Aggregated information on the cooking video associated with the recipe.

#### # Product

  A model representing a product.

 FieldTypeRequiredDescriptiontype"Product"true A string representing a product type. The value is always product.

namestringtrue The name of the product.

categorystringfalse The category of the product.

pricestringtrue The price of the product.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)true A thumbnail associated with the product.

descriptionstringfalse The description of the product.

offerslist [ [Offer](https://api-dashboard.search.brave.com#Offer) ]false A list of offers available on the product.

rating[Rating](https://api-dashboard.search.brave.com#Rating)false A rating associated with the product.

#### # Offer

  An offer associated with a product.

 FieldTypeRequiredDescriptionurlstringtrue The URL where the offer can be found.

priceCurrencystringtrue The currency in which the offer is made.

pricestringtrue The price of the product currently on offer.

#### # Review

  A model representing a review for an entity.

 FieldTypeRequiredDescriptiontype"review"true A string representing review type. This is always review.

namestringtrue The review title for the review.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)true The thumbnail associated with the reviewer.

descriptionstringtrue A description of the review (the text of the review itself).

rating[Rating](https://api-dashboard.search.brave.com#Rating)true The ratings associated with the review.

#### # Reviews

  The reviews associated with an entity.

 FieldTypeRequiredDescriptionresultslist [ [TripAdvisorReview](https://api-dashboard.search.brave.com#TripAdvisorReview) ]true A list of trip advisor reviews for the entity.

viewMoreUrlstringtrue A URL to a web page where more information on the result can be seen.

reviews_in_foreign_languagebooltrue Any reviews available in a foreign language.

#### # TripAdvisorReview

  A model representing a Tripadvisor review.

 FieldTypeRequiredDescriptiontitlestringtrue The title of the review.

descriptionstringtrue A description seen in the review.

datestringtrue The date when the review was published.

rating[Rating](https://api-dashboard.search.brave.com#Rating)true A rating given by the reviewer.

author[Person](https://api-dashboard.search.brave.com#Person)true The author of the review.

review_urlstringtrue A URL link to the page where the review can be found.

languagestringtrue The language of the review.

#### # CreativeWork

  A creative work relevant to the query. An example can be enriched metadata for an app.

 FieldTypeRequiredDescriptionnamestringtrue The name of the creative work.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)true A thumbnail associated with the creative work.

rating[Rating](https://api-dashboard.search.brave.com#Rating)false A rating that is given to the creative work.

#### # MusicRecording

  Result classified as a music label or a song.

 FieldTypeRequiredDescriptionnamestringtrue The name of the song or album.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false A thumbnail associated with the music.

rating[Rating](https://api-dashboard.search.brave.com#Rating)false The rating of the music.

#### # Software

  A model representing a software entity.

 FieldTypeRequiredDescriptionnamestringfalse The name of the software product.

authorstringfalse The author of software product.

versionstringfalse The latest version of the software product.

codeRepositorystringfalse The code repository where the software product is currently available or maintained.

homepagestringfalse The home page of the software product.

datePublisherstringfalse The date when the software product was published.

is_npmboolfalse Whether the software product is available on npm.

is_pypiboolfalse Whether the software product is available on pypi.

starsintfalse The number of stars on the repository.

forksintfalse The numbers of forks of the repository.

ProgrammingLanguagestringfalse The programming language spread on the software product.

#### # DeepResult

  Aggregated deep results from news, social, videos and images.

 FieldTypeRequiredDescriptionnewslist [ [NewsResult](https://api-dashboard.search.brave.com#NewsResult) ]false A list of news results associated with the result.

buttonslist [ [ButtonResult](https://api-dashboard.search.brave.com#ButtonResult) ]false A list of buttoned results associated with the result.

videoslist [ [VideoResult](https://api-dashboard.search.brave.com#VideoResult) ]false Videos associated with the result.

imageslist [ [Image](https://api-dashboard.search.brave.com#Image) ]false Images associated with the result.

#### # VideoResult (Result)

  A model representing a video result.

 FieldTypeRequiredDescriptiontype"video_result"true The type identifying the video result. The value is always video_result.

video[VideoData](https://api-dashboard.search.brave.com#VideoData)true Meta data for the video.

meta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false Aggregated information on the URL.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false The thumbnail of the video.

agestringfalse A string representing the age of the video.

#### # VideoData

  A model representing metadata gathered for a video.

 FieldTypeRequiredDescriptiondurationstringfalse A time string representing the duration of the video. The format can be HH:MM:SS or MM:SS.

viewsstringfalse The number of views of the video.

creatorstringfalse The creator of the video.

publisherstringfalse The publisher of the video.

thumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)false A thumbnail associated with the video.

tagslist [ string ]false A list of tags associated with the video.

author[Profile](https://api-dashboard.search.brave.com#Profile)false Author of the video.

requires_subscriptionboolfalse Whether the video requires a subscription to watch.

#### # ButtonResult

  A result which can be used as a button.

 FieldTypeRequiredDescriptiontype"button_result"true A type identifying button result. The value is always button_result.

titlestringtrue The title of the result.

urlstringtrue The URL for the button result.

#### # Image

  A model describing an image.

 FieldTypeRequiredDescriptionthumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)true The thumbnail associated with the image.

urlstringfalse The URL of the image.

properties[ImageProperties](https://api-dashboard.search.brave.com#ImageProperties)false Metadata on the image.

#### # Language

  A model representing a language.

 FieldTypeRequiredDescriptionmainstringtrue The main language seen in the string.

#### # ImageProperties

  Metadata on an image.

 FieldTypeRequiredDescriptionurlstringtrue The original image URL.

resizedstringtrue The URL for a better quality resized image.

placeholderstringtrue The placeholder image URL.

heightintfalse The image height.

widthintfalse The image width.

formatstringfalse The image format.

content_sizestringfalse The image size.

#### # Summarizer

  Details on getting the summary.

 FieldTypeRequiredDescriptiontype"summarizer"true The value is always summarizer.

keystringtrue The key for the summarizer API.

#### # RichCallbackInfo

  Callback information for rich results.

 FieldTypeRequiredDescriptiontype"rich"true The value is always rich.

hint[RichCallbackHint](https://api-dashboard.search.brave.com#RichCallbackHint)false The hint for the rich result.

#### # RichCallbackHint

  The hint for the rich result.

 FieldTypeRequiredDescriptionverticalstringtrue The name of the vertical of the rich result.

callback_keystringtrue The callback key for the rich result.

 