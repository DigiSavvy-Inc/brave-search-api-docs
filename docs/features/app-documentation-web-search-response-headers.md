# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/web-search/response-headers](https://api-dashboard.search.brave.com/app/documentation/web-search/response-headers)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/web-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/web-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/web-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/web-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/web-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/web-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/web-search/api-changelog)[Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Web Search API

 ## Response Headers

 #### Global

 This table lists the response headers supported by the Web Search API.

 HeaderNameDescriptionX-RateLimit-LimitRate Limit Rate limits associated with the requested plan.

An example rate limit X-RateLimit-Limit: 1, 15000 means     1 request per second and 15000 requests per month.

X-RateLimit-PolicyRate Limit Policy Rate limit policies currently associated with the requested plan.

An example policy X-RateLimit-Policy: 1;w=1, 15000;w=2592000 means     a limit of 1 request over a 1 second window and 15000 requests over     a month window. The windows are always given in seconds.

X-RateLimit-RemainingRate Limit Remaining Remaining quota units associated with the expiring limits.

An example remaining limit X-RateLimit-Remaining: 1, 1000     indicates the API is able to be accessed once during the current     second, and 1000 times over the current month.

Note: Only successful requests are counted and billed.

X-RateLimit-ResetRate Limit Reset The number of seconds until the quota associated with the expiring     limits resets.

An example reset limit X-RateLimit-Reset: 1, 1419704 means a     single request can be done again in a second and in 1419704 seconds     the full monthly quota associated with the plan will be available again.

 