# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

PermaDown Detector is a static single-page application that monitors website availability. It's built with vanilla HTML, JavaScript, and Bulma CSS, designed for deployment to Arweave.

## Architecture

- **Single file architecture**: All HTML, CSS, and JavaScript are contained in `index.html`
- **No build process**: The application is purely static with no compilation or bundling required
- **CDN dependencies**: Bulma CSS is loaded from Arweave, Font Awesome from cdnjs

## How It Works

The app checks website status by attempting to load favicon images from each monitored site. Due to browser CORS restrictions, this is the most reliable method for a purely static client-side application:

1. Creates an `Image` object for each site's favicon
2. If the image loads successfully, the site is considered "up"
3. If loading fails or times out (5 seconds), the site is marked as "down"

## Monitored Sites

Sites are configured in the `websites` array in the JavaScript section. Each site object contains:
- `name`: Display name
- `url`: Main site URL
- `logo`: Primary logo URL
- `fallbackLogo`: Backup logo if primary fails
- `checkUrl`: URL used for availability check (typically favicon)

## Development

To test locally, serve the file with any static server:
```bash
npx serve .
# or
python3 -m http.server 8000
```

## Deployment

The app is designed for Arweave deployment. Simply upload `index.html` to Arweave - no build step required.

## Limitations

- CORS restrictions prevent true HTTP status checks from the browser
- Favicon-based checking may give false positives if a site blocks favicon requests but is otherwise operational
- Some sites may have CDN caching that masks actual outages
