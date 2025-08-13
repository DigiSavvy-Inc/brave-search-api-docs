# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/image-search/guides](https://api-dashboard.search.brave.com/app/documentation/image-search/guides)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Get Started](https://api-dashboard.search.brave.com/app/documentation/image-search/get-started)[Query Parameters](https://api-dashboard.search.brave.com/app/documentation/image-search/query)[Request Headers](https://api-dashboard.search.brave.com/app/documentation/image-search/request-headers)[Response Headers](https://api-dashboard.search.brave.com/app/documentation/image-search/response-headers)[Response Objects](https://api-dashboard.search.brave.com/app/documentation/image-search/responses)[Codes](https://api-dashboard.search.brave.com/app/documentation/image-search/codes)[API Changelog](https://api-dashboard.search.brave.com/app/documentation/image-search/api-changelog)[How to Guides](https://api-dashboard.search.brave.com/app/documentation/image-search/guides)[Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [Pricing](https://api-dashboard.search.brave.com/app/plans)    [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # A simple guide to handle missing and small image results

 ##### Brave Search Image API

 There are two limitations of the Brave Search Image API:

We’ve worked around the very same limitations to build our image
search vertical at search.brave.com/images.
This guide is a simpler version of the same approach.

Our project structure will be this:

```
index.js
public/
    images.html
    styles.css
```

To get started, let’s create a folder for our image search page as well
as create the files we will need later on:

```
mkdir img-search && cd img-search
mkdir public
touch public/images.html
touch public/styles.css
```

We’ll use a simple node.js express server to call
the API. So let’s go ahead and install it as a dependency (our only one).

```
npm install express --save
```

The following index.js is our server, and will be handling the API calls.
It has to be done through a server environment so that there are no
Cross-Origin Resource Sharing (CORS)
issues.

#### index.js

```
const express = require('express');
const app = express();
const port = 4000;

app.use(express.static('public'));

const API_KEY = '<YOUR_API_KEY>';
const API_PATH = 'https://api.search.brave.com/res/v1/images/search';

app.get('/api/images', async (req, res) => {
  try {
    const params = new URLSearchParams({
      q: req.query.q,
      count: 20,
      search_lang: 'en',
      country: 'us',
      spellcheck: 1,
    });
    const response = await fetch(`${API_PATH}?${params}`, {
      headers: {
        'x-subscription-token': API_KEY,
        accept: 'application/json',
      },
    });
    const data = await response.json();
    res.json(data);
    return;
  } catch (err) {
    console.log(err);
  }
  res.status(500).send('Internal Server Error');
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```

Now that we have our server, let’s focus on the client side scripts needed
to load image outside of the DOM, to learn if they exist, and what the
width and height is.

#### public/images.html

```
<html>
  <head>
    <title>Image Search</title>
    <link rel="stylesheet" href="/styles.css" />
  </head>
  <body>
    <script lang="javascript">
      async function fetchImages(query) {
        const params = new URLSearchParams({ q: query });
        const response = await fetch(`/api/images?${params}`);
        return await response.json();
        return data;
      }

      function renderImages(images) {
        const imagesContainer = document.getElementById('images');
        imagesContainer.innerHTML = '';
        images.forEach(({ image }) => {
          const figElement = document.createElement('figure');

          const imgElement = document.createElement('img');
          imgElement.src = image.thumbnail.src;
          imgElement.alt = image.title;
          imgElement.width = image.thumbnail.width;
          imgElement.height = image.thumbnail.height;

          const figCaptionElement = document.createElement('figcaption');
          figCaptionElement.innerHTML =
            `<div class="dimensions">${image.thumbnail.width} x ${image.thumbnail.height}</div>` +
            image.title;

          figElement.appendChild(imgElement);
          figElement.appendChild(figCaptionElement);

          imagesContainer.appendChild(figElement);
        });
      }

      function loadImage(result) {
        return new Promise((resolve, reject) => {
          const img = new Image();
          img.crossOrigin = 'anonymous';
          img.onload = (e) => {
            if (e.target) {
              const image = e.target;
              const width = image.naturalWidth;
              const height = image.naturalHeight;

              // Filter images that are too small
              if (width < 275 || height < 275) {
                console.error('[Img] Image too small', result);
                reject(result);
                return;
              }

              // Fill missing info; use the size the image will be scaled into instead of actual size
              result.thumbnail.width = width;
              result.thumbnail.height = height;

              resolve(result);
            } else {
              console.error('[Img] onLoad returned no image', result);
              reject(result);
            }
          };
          img.onerror = (e) => {
            console.error('[Img] onError loading img', e);
            reject(result);
          };
          img.onabort = (e) => {
            console.error('[Img] onAbort loading img', e);
            reject(result);
          };
          img.src = result.thumbnail.src;
        });
      }

      async function load(query) {
        // Load images from API
        const response = await fetchImages(query);
        const loadedImages = [];
        let i = 0;
        const count = 5;
        const initialPromises = [];

        // Load the first 5 images in parallel
        for (let i = 0; i < count; i++) {
          initialPromises.push(async () => {
            const result = response.results[i];
            try {
              const image = await loadImage(result);
              loadedImages.push({
                image,
              });
            } catch (err) {
              // pass
            }
          });
        }

        // Wait for the first 5 images to resolve
        await Promise.all(initialPromises);

        // Load images sequentially until there is 5 results, then show them.
        while (loadedImages.length < 5 || i >= response.results.length) {
          const result = response.results[i];
          try {
            const image = await loadImage(result);
            loadedImages.push({
              image,
            });
          } catch (err) {
            // pass
          }
          i++;
        }

        renderImages(loadedImages);
      }
    </script>
    <div id="search">
      <input type="text" id="query" value="" onchan />
      <button onclick="load(document.getElementById('query').value)">Search</button>
    </div>
    <div id="images"></div>
  </body>
</html>
```

The approach here, is to load images outside of the DOM, 5 at a time
(which you can configure), and images that we manage successfully, and
are larger than a given size (width > 275 || height > 275 in the example),
we show in the DOM.

Lastly, we need some styles to make sure what we see does not look too bad:

### styles.css

```
#images {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  max-width: 1000px;
  margin: 2rem auto;
  justify-content: center;
}
#search {
  display: flex;
  gap: 1rem;
  align-items: center;
  width: 600px;
  margin: auto;
}
#search input {
  width: 100%;
  padding: 10px 20px;
  border-radius: 12px;
  outline: none;
  border: solid 1px #d3d3d3;
  background: #f3f3f3;
}
button {
  cursor: pointer;
  padding: 10px 20px;
  border-radius: 12px;
  outline: none;
  border: solid 1px #d3d3d3;
  background: #f3f3f3;
}
button:hover {
  background: #111;
  color: #fff;
}
figure {
  border: solid 1px #d3d3d3;
  display: flex;
  flex-flow: column;
  padding: 5px 5px 10px 5px;
  max-width: 220px;
  gap: 1rem;
  border-radius: 12px;
  margin: 0;
}

img {
  max-width: 220px;
  max-height: 150px;
  object-fit: contain;
  border-radius: 12px;
}

figcaption {
  display: flex;
  text-align: center;
  font-family: sans-serif;
  font-size: 14px;
  flex-direction: column;
  gap: 5px;
  align-items: center;
}
figcaption .dimensions {
  font-size: 12px;
  color: blue;
  background: #e7e7fc;
  padding: 5px 10px;
  border-radius: 12px;
  width: fit-content;
}
```

And we’re ready to go. You can now run the project:

```
node index.js
```

Open localhost:4000/images.html in the browser, and start searching.

 ![Image Search Client](https://cdn.search.brave.com/search-api/web/v1/client/_app/immutable/assets/img-search-client.Yjc8cU7X.png) 