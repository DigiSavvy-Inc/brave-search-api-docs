# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/summarizer-search/code-samples](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/code-samples)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/responses)[Code Samples](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/code-samples)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/summarizer-search/api-changelog)[AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # A simple guide to use the Brave Search Summarizer API

 ##### Example using Python

 Ensure Python version 3 is installed on your machine. Install the
required Python dependencies for rate limiting and issuing HTTP requests:

```
pip install aiohttp aiolimiter
```

Copy the Python script below to a file named summarizer.py. Make sure
you are subscribed to the Pro AI plan.
Change the value of the API_KEY variable to your generated
API key in the script, and then run the script to get
summarized results for the given query.

```
python summarizer.py
```

Here’s the summarizer.py module:

```
import asyncio
import json
import logging
from urllib.parse import urljoin

from aiohttp import ClientSession, ClientTimeout, TCPConnector
from aiolimiter import AsyncLimiter

# Configure logger
logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s",
    datefmt="%Y-%m-%d %H:%M:%S",
)
log = logging.getLogger(__name__)

# Request rate and concurrency
API_MAX_CONCURRENT_REQUESTS = 1
API_RPS = 1
API_RATE_LIMIT = AsyncLimiter(API_RPS, 1)
API_TIMEOUT = 20

# Brave Search API Key
API_KEY = "your_api_key"

# Brave Search API host
API_HOST = "https://api.search.brave.com"

# Brave Search API subpaths
API_PATH = {
    "web": urljoin(API_HOST, "res/v1/web/search"),
    "summarizer_search": urljoin(API_HOST, "res/v1/summarizer/search"),
}

# Create request headers for specific endpoints
API_HEADERS = {
    "web": {"X-Subscription-Token": API_KEY, "Api-Version": "2023-10-11"},
    "summarizer": {"X-Subscription-Token": API_KEY, "Api-Version": "2024-04-23"},
}

# Create web search request params
API_PARAMS_WEB = {
    "q": "what is the second highest mountain",
    "summary": 1,
}

async def get_summary(session: ClientSession) -> None:
    # Fetch web search results so we can get a summary key
    async with session.get(
        API_PATH["web"],
        params=API_PARAMS_WEB,
        headers=API_HEADERS["web"],
    ) as response:
        log.info("Querying url: [%s]", response.url)
        # print(await response.text())
        data = await response.json()
        status = response.status

    if status != 200:
        log.error(
            "Failure getting web search results \n%s",
            json.dumps(data, indent=2),
        )
        return

    # Get the summary key from web search results
    summary_key = data.get("summarizer", {}).get("key")

    if not summary_key:
        log.error("Failure: Getting summary key")
        return

    log.info("Summarizer Key: [%s]", summary_key)

    # Fetch summary all in one
    log.info("Requesting summarizer search in blocking mode")
    async with session.get(
        url=API_PATH["summarizer_search"],
        params={"key": summary_key, "entity_info": 1},
        headers=API_HEADERS["summarizer"],
    ) as response:
        log.info("Querying url: [%s]", response.url)
        data = await response.json()
        status = response.status

        log.info(json.dumps(data, indent=2))

async def main():
    async with API_RATE_LIMIT:
        async with ClientSession(
            connector=TCPConnector(limit=API_MAX_CONCURRENT_REQUESTS),
            timeout=ClientTimeout(API_TIMEOUT),
        ) as session:
            await get_summary(session=session)

asyncio.run(main())
```

 