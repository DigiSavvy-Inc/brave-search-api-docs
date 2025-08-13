# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/summarizer-search/responses](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/responses)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/responses)[Code Samples](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/code-samples)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/api-changelog)[AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Summarizer Search API

 ## Response Objects

 #### # SummarizerSearchApiResponse

  Top level response model for successful Summarizer Search API requests. The response will include the summarized content or answer based on the key. The API can also respond back with an error response based on the incompleted summarization request, invalid subscription keys, and rate limit events. Access to Summarizer requires a subscription to Pro AI plan.

 FieldTypeRequiredDescriptiontype"summarizer"true The type of summarizer search API result. The value is always summarizer.

statusstringtrue The current status of summarizer for the given key. The value can be either failed or complete.

titlestringfalse The title for the summary.

summarylist [ [SummaryMessage](https://api-dashboard.search.brave.com#SummaryMessage) ]false Details for the summary message.

enrichments[SummaryEnrichments](https://api-dashboard.search.brave.com#SummaryEnrichments)false Enrichments that can be added to the summary message.

followupslist [ string ]false Followup queries relevant to the current query.

entities_infosdict [ string, [SummaryEntityInfo](https://api-dashboard.search.brave.com#SummaryEntityInfo) ]false Details on the entities in the summary message.

#### # SummaryMessage

  The summary message.

 FieldTypeRequiredDescriptiontypestringtrue The type of subset of a summary message. The value can be token
(a text excerpt from the summary), enum_item (a summary entity),
enum_start (describes the beginning of summary entities, which
means the following item(s) in the summary list will be entities),
enum_end (the end of summary entities) or inline_reference (an inline
reference to the summary, requires inline_references query param to be set).

data[SummaryEntity](https://api-dashboard.search.brave.com#SummaryEntity) | SummaryInlineReferencefalse The summary entity or the explanation for the type field. For type
enum_start the value can be ol or ul, which means an ordered
list or an unordered list of entities follows respectively. For type
enum_end there is no value. For type token the value is a
text excerpt. For type enum_item the value is the
SummaryEntity
response model. For type inline_reference the value is the
SummaryInlineReference
response model.

#### # TextLocation

  Index-based location in a text.

 FieldTypeRequiredDescriptionstartinttrue The 0-based index, where the important part of the text starts.

endinttrue The 0-based index, where the important part of the text ends.

#### # SummaryEntity

  An entity in the summary message.

 FieldTypeRequiredDescriptionuuidstringtrue A unique identifier for the entity.

namestringtrue The name of the entity.

urlstringfalse The URL where further details on the entity can be found.

textstringfalse A text message describing the entity.

imageslist [ [SummaryImage](https://api-dashboard.search.brave.com#SummaryImage) ]false The image associated with the entity.

highlightlist [ [TextLocation](https://api-dashboard.search.brave.com#TextLocation) ]false The location of the entity in the summary message.

#### # SummaryInlineReference

  An inline reference to the summary.

 FieldTypeRequiredDescriptiontypestringtrue The type of inline reference. The value is always inline_reference.

urlstringtrue The URL that is being referenced.

start_indexinttrue The start index of the inline reference in the summary message.

end_indexinttrue The end index of the inline reference in the summary message.

numberinttrue The ordinal number of the inline reference.

faviconstringfalse The favicon of the URL that is being referenced.

snippetstringfalse The reference text snippet.

#### # Thumbnail

  Aggregated details representing a picture thumbnail.

 FieldTypeRequiredDescriptionsrcstringtrue The served URL of the picture thumbnail.

originalstringfalse The original URL of the image.

#### # ImageProperties

  Metadata on an image.

 FieldTypeRequiredDescriptionurlstringtrue The image URL.

#### # Image

  A model describing an image.

 FieldTypeRequiredDescriptionthumbnail[Thumbnail](https://api-dashboard.search.brave.com#Thumbnail)true The thumbnail associated with the image.

urlstringfalse The URL of the image.

properties[ImageProperties](https://api-dashboard.search.brave.com#ImageProperties)false Metadata on the image.

#### # SummaryImage (Image)

  An image associated with the summary.

 FieldTypeRequiredDescriptiontextstringfalse Text associated with the image.

#### # SummaryEnrichments

  Enrichments associated with the summary message.

 FieldTypeRequiredDescriptionrawstringtrue The raw summary message.

imageslist [ [SummaryImage](https://api-dashboard.search.brave.com#SummaryImage) ]false The images associated with the summary.

qalist [ [SummaryAnswer](https://api-dashboard.search.brave.com#SummaryAnswer) ]false The answers in the summary message.

entitieslist [ [SummaryEntity](https://api-dashboard.search.brave.com#SummaryEntity) ]false The entities in the summary message.

contextlist [ [SummaryContext](https://api-dashboard.search.brave.com#SummaryContext) ]false References based on which the summary was built.

#### # SummaryAnswer

  The answer if the query is a question.

 FieldTypeRequiredDescriptionanswerstringtrue The answer text.

scorefloatfalse A score associated with the answer.

highlight[TextLocation](https://api-dashboard.search.brave.com#TextLocation)false The location of the answer in the summary message.

#### # MetaUrl

  Aggregated information about a URL.

 FieldTypeRequiredDescriptionschemestringfalse The protocol scheme extracted from the URL.

netlocstringfalse The network location part extracted from the URL.

hostnamestringfalse The lowercased domain name extracted from the URL.

faviconstringfalse The favicon used for the URL.

pathstringfalse The hierarchical path of the URL useful as a display string.

#### # SummaryContext

  A reference for the summary.

 FieldTypeRequiredDescriptiontitlestringtrue The title of the reference.

urlstringtrue The URL where the reference can be found.

meta_url[MetaUrl](https://api-dashboard.search.brave.com#MetaUrl)false Details on the URL associated with the reference.

#### # SummaryEntityInfo

  Details on the entity in the summary message.

 FieldTypeRequiredDescriptionproviderstringfalse The name of the provider.

descriptionstringfalse Description of the entity.

 