# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/general/api-versioning](https://api-dashboard.search.brave.com/app/documentation/general/api-versioning)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [API Versioning](https://api-dashboard.search.brave.com/app/documentation/general/api-versioning)[Privacy Notice](https://api-dashboard.search.brave.com/app/documentation/general/privacy-policy)[Terms of Service](https://api-dashboard.search.brave.com/app/documentation/general/terms-of-service)[Security](https://api-dashboard.search.brave.com/app/documentation/general/security)[Status Updates](https://api-dashboard.search.brave.com/app/documentation/general/status-updates)[Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # API Versioning

  The Brave Search API is evolving rapidly, with new iterations released
all the time. However, we know that changing an existing API can be an
unwelcome change, and that API developers can quickly lose flexibility
as users start consuming their API. A common way to mitigate this is to
add some form of versioning to the published API so users can fully
rely on the API’s behavior. When you’re ready for an API change, you’ll
then have an easy upgrade path forward provided by the API developers.

With Brave Search you can expect two types of versioning schemes.

## 1. Versioning in Request URL

The first is a major version of the format v1 that is prefixed to the
API URL. An example URL will look something like this /v1/web/search.
As a user you can expect this version to be rarely changed, but we
reserve the right to do so. These will only be used when there is a
major API redesign, which should happen only rarely, and naturally
would warrant a major upgrade.

## 2. Versioning in Request Header

We believe in making incremental changes which are easier to digest
and iterate upon for an API user. These are smaller, backwards
incompatible changes, which require an upgrade path and are dated with
the format YYYY-MM-DD. An API request for a product always points to
the latest version available. The API behavior can be locked to a
specific version by providing a version header named Api-Version as
part of the request. An example version header will look something
like Api-Version: 2023-01-01.

Changes made to the API can be backwards compatible or incompatible.
To learn more about which changes are considered backwards compatible
or incompatible, read below.

## Backwards compatible changes

Brave Search considers the following changes to be backwards compatible,
and they will not require action from the API user:

## Backwards incompatible changes

Brave Search considers the following changes to be backwards
incompatible, and they will require action from the API user
(provided the API user has updated to the new API version):

 