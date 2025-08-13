# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/web-search/request-headers](https://api-dashboard.search.brave.com/app/documentation/web-search/request-headers)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/web-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/web-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/web-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/web-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/web-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/web-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/web-search/api-changelog)[Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) ###### Brave Web Search API

 ## Request Headers

 #### # Web Search API Request Headers

 This table lists the request headers supported by the Web Search API. Most are optional, but
    note that sending more information in headers (such as client location) will improve search
    results.

 HeaderRequiredNameDescriptionAcceptfalseAccept The default supported media type is application/json

Accept-EncodingfalseAccept Encoding The supported compression type is gzip.

Api-VersionfalseWeb Search API Version The Brave Web Search API version to use. This is denoted by     the format YYYY-MM-DD. The latest version is used by default,    and the previous ones can be found in the    API Changelog.

Cache-ControlfalseCache Control Search will return cached web search results by default.     To prevent caching, set the Cache-Control header to no-cache.     This is currently done as best effort.

User-AgentfalseUser Agent The user agent of the client sending the request. Search can     utilize the user agent to provide a different experience depending     on the client sending the request.

The user agent should follow the commonly used browser     agent strings on each platform. For more information on     curating user agents, see RFC 9110.

User agent string examples by platform:

X-Loc-LatfalseLatitude The latitude of the client’s geographical location in degrees,     to provide relevant local results. The latitiude must be greater     than or equal to -90.0 degrees and less than or equal to +90.0 degrees.

X-Loc-LongfalseLongitude The longitude of the client’s geographical location in degrees,   to provide relevant local results. The longitude must be greater   than or equal to -180.0 degrees and less than or equal to +180.0 degrees.

X-Loc-TimezonefalseTimezone The IANA timezone for the client’s device, for example     America/New_York.

For complete list of IANA timezones and location mappings see     IANA Database and     Geonames Database.

X-Loc-CityfalseCity Name The generic name of the client city.

X-Loc-StatefalseState Code The code representing the client’s state/region, can be up to     3 characters long.

The region is the first-level subdivision (the broadest or least specific)     of the ISO 3166-2 code.

X-Loc-State-NamefalseState Name The name of the client’s state/region.

The region is the first-level subdivision (the broadest or least specific)     of the ISO 3166-2 code.

X-Loc-CountryfalseCountry Code The two letter code for the client’s country.

For a list of country codes, see     ISO 3166-1 alpha-2

X-Loc-Postal-CodefalsePostal Code The postal code of the client’s location.

X-Subscription-TokentrueAuthentication token The secret token for the subscribed plan to authenticate the request.   Can be obtained from API Keys.

 #### # Local Search API Request Headers

 This table lists the request headers supported by the Local Search API, most of which are
    optional.

 HeaderRequiredNameDescriptionAcceptfalseAccept The default supported media type is application/json

Accept-EncodingfalseAccept Encoding The supported compression type is gzip.

Api-VersionfalseWeb Search API Version The Brave Web Search API version to use. This is denoted by     the format YYYY-MM-DD. The latest version is used by default,    and the previous ones can be found in the    API Changelog.

Cache-ControlfalseCache Control Search will return cached web search results by default.     To prevent caching, set the Cache-Control header to no-cache.     This is currently done as best effort.

User-AgentfalseUser Agent The user agent of the client sending the request. Search can     utilize the user agent to provide a different experience depending     on the client sending the request.

The user agent should follow the commonly used browser     agent strings on each platform. For more information on     curating user agents, see RFC 9110.

User agent string examples by platform:

X-Subscription-TokentrueAuthentication token The secret token for the subscribed plan to authenticate the request.   Can be obtained from API Keys.

 