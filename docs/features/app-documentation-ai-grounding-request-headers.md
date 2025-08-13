# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/ai-grounding/request-headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/request-headers)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Get Started](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/responses)[Code Samples](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/code-samples)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/api-changelog)[Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave AI Grounding API

 ## Request Headers

 #### AI Grounding API Request Headers

 This table lists the request headers supported by all the AI Grounding API endpoints, most of
    which are optional.

 HeaderRequiredNameDescriptionAcceptfalseAccept The default supported media type is application/json

Accept-EncodingfalseAccept Encoding The supported compression type is gzip.

Api-VersionfalseWeb Search API Version The Brave Web Search API version to use. This is denoted by     the format YYYY-MM-DD. The latest version is used by default,    and the previous ones can be found in the    API Changelog.

Cache-ControlfalseCache Control Search will return cached web search results by default.     To prevent caching, set the Cache-Control header to no-cache.     This is currently done as best effort.

User-AgentfalseUser Agent The user agent of the client sending the request. Search can     utilize the user agent to provide a different experience depending     on the client sending the request.

The user agent should follow the commonly used browser     agent strings on each platform. For more information on     curating user agents, see RFC 9110.

User agent string examples by platform:

X-Subscription-TokentrueAuthentication token The secret token for the subscribed plan to authenticate the request.   Can be obtained from API Keys.

 