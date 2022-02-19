# Payload Search Plugin

[![NPM](https://img.shields.io/npm/v/payload-plugin-search)](https://www.npmjs.com/package/payload-plugin-search)

A plugin for [Payload CMS](https://github.com/payloadcms/payload) to create extremely fast search results from your existing documents.

Core features:
  - Creates a `search` collection that:
    - Automatically creates, syncs, and deletes search results related to your documents
    - Serves search results extremely quickly by saving only search-critical data that you define
    - Allows you to sort search results by priority
## Installation

```bash
  yarn add payload-plugin-search
  # OR
  npm i payload-plugin-search
```

## Basic Usage

In the `plugins` array of your [Payload config](https://payloadcms.com/docs/configuration/overview), call the plugin with [options](#options):

```js
import { buildConfig } from 'payload/config';
import search from 'payload-search';

const config = buildConfig({
  collections: [
    {
      slug: 'pages',
      fields: []
    }
  ],
  plugins: [
    search({
      collections: ['pages'],
      defaultPriorities: {
        pages: 10
      }
    })
  ]
});

export default config;
```

### Options

- `collections`
    An array of collections slugs to enable sync-to-search. Enabled collections receive a `beforeChange` and `afterDelete` hook that creates, syncs, and deleted the document to its related search document as it changes over time, and also an `afterDelete` hook that deletes.

- `searchOverrides`

    Override anything on the search collection by sending a [Payload Collection Config](https://payloadcms.com/docs/configuration/collections).

    ```
    searchOverrides: {
      slug: 'search-results'
    }
    ```
  ## TypeScript

  All types can be directly imported:
  ```js
  import {
    SearchConfig,
   } from 'payload-plugin-search/dist/types';
  ```

  ## Screenshots

  <!-- ![screenshot 1](https://github.com/trouble/payload-plugin-search/blob/main/images/screenshot-1.jpg?raw=true) -->
