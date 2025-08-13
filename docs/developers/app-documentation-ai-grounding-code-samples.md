# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/ai-grounding/code-samples](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/code-samples)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Get Started](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/responses)[Code Samples](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/code-samples)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/ai-grounding/api-changelog)[Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # A simple guide to use the Brave AI Grounding API

 ##### Example using Python

 Ensure Python version 3 is installed on your machine. Install the
required Python dependencies for openai SDK:

```
pip install openai
```

Copy the Python script below to a file named brave_ai_grounding.py. Make sure
you are subscribed to the AI Grounding plan.
Change the value of the API_KEY variable to your generated
API key in the script, and then run the script to get results for the given query.

```
python brave_ai_grounding.py
```

Here’s the brave_ai_grounding.py module:

```
#!/usr/bin/env python

import asyncio
import json

from openai import AsyncOpenAI

client = AsyncOpenAI(
    api_key="<YOUR_BRAVE_SEARCH_API_KEY>",  # Replace with your Brave Search API key
    base_url="https://api.search.brave.com/res/v1",
)

async def main() -> None:
    streaming = True
    enable_research = False  # Set this to `True` to enable Deep Research
    print_raw_messages = False  # Set this to `True` to print raw API messages

    # Blocking example
    if not streaming:
        print(
            await client.chat.completions.create(
                messages=[
                    {
                        "role": "user",
                        "content": "albums from lady gaga",
                    }
                ],
                model="brave",
                stream=False,
                extra_body={
                    "country": "us",
                    "language": "en",
                    "enable_entities": False,  # Default
                    "enable_citations": True,  # Default
                    "enable_research": enable_research,
                },
            )
        )
        return

    # Streaming example
    async for data in await client.chat.completions.create(
        messages=[
            {
                "role": "user",
                "content": "albums from lady gaga",
            }
        ],
        model="brave",
        stream=streaming,
        extra_body={
            "country": "us",
            "language": "en",
            "enable_entities": False,
            "enable_citations": True,  # Default
            "enable_research": enable_research,
        },
    ):
        if print_raw_messages:
            print(data.model_dump_json(), flush=True)
        elif choices := data.choices:
            if delta := choices[0].delta.content:
                if delta.startswith("<citation>") and delta.endswith("</citation>"):
                    # Attributes: start_index, end_index, number, url, favicon, snippet.
                    citation = json.loads(
                        delta.removeprefix("<citation>").removesuffix("</citation>")
                    )
                    print(
                        f"[{citation['number']}]({citation['url']})", end="", flush=True
                    )
                elif delta.startswith("<enum_item>") and delta.endswith("</enum_item>"):
                    # Attributes: uuid, name, href, extra_text, original_tokens, instance_of, images, citations.
                    item = json.loads(
                        delta.removeprefix("<enum_item>").removesuffix("</enum_item>")
                    )
                    print("*", item["original_tokens"], end="", flush=True)
                elif delta.startswith("<enum_start>") and delta.endswith(
                    "</enum_start>"
                ):
                    pass
                elif delta.startswith("<enum_end>") and delta.endswith("</enum_end>"):
                    pass
                elif delta.startswith("<usage>") and delta.endswith("</usage>"):
                    # Attributes: tokens, cost, model.
                    usage = json.loads(
                        delta.removeprefix("<usage>").removesuffix("</usage>")
                    )
                    print("\n\nUsage:", usage)
                else:
                    print(delta, end="", flush=True)

if __name__ == "__main__":
    asyncio.run(main())
```

 