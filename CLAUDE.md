# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A meme search web app that lets users search a tagged collection of GIFs (Giphy) and images (Imgur) by keyword. Clicking a result copies its URL to the clipboard. Hosted on Firebase Hosting.

## Architecture

This is a no-build static site. All application logic lives in `public/index.html` as inline JavaScript.

- **Data source**: Meme metadata (IDs + tags) is fetched at page load from a Google Apps Script endpoint. The response is cached in `localStorage` for instant subsequent loads.
- **Meme format**: Each meme is either a `gif` (Giphy media URL) or `image` (Imgur URL), paired with a tags array for search.
- **Search**: Triggered on Enter keypress; filters memes whose tags array includes the search text (exact substring match via `Array.includes`).

## Deployment

```
firebase deploy
```

Firebase project: `the-meme-hub` (configured in `.firebaserc`). The `public/` directory is served as-is.
