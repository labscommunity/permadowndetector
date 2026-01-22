# PermaDown Detector

A decentralized website status monitoring application permanently deployed on Arweave. Check if major services are up or down in real-time.

## Features

- Real-time status monitoring for major websites
- Dark theme UI inspired by Downdetector
- Summary dashboard with up/down counts
- Alert banner when services are experiencing issues
- Manual refresh capability
- Fully static - no server required

## Monitored Services

- Google
- YouTube
- Amazon
- Netflix
- X (Twitter)
- Verizon
- Downdetector

## How It Works

The application checks website availability by attempting to load favicon images from each monitored service. This client-side approach works around browser CORS restrictions while providing a reliable indicator of service availability.

- If the favicon loads successfully, the service is marked as **Operational**
- If loading fails or times out (5 seconds), the service is marked as **Down or Unreachable**

## Tech Stack

- Vanilla HTML, CSS, and JavaScript
- [Bulma CSS](https://bulma.io/) (loaded from Arweave)
- [Font Awesome](https://fontawesome.com/) icons

## Local Development

Serve the project with any static file server:

```bash
# Using npx
npx serve .

# Using Python
python3 -m http.server 8000
```

Then open `http://localhost:3000` (or `http://localhost:8000` for Python).

## Deployment

This application is designed for deployment to [Arweave](https://arweave.org) for permanent, decentralized hosting. Simply upload `index.html` to Arweave - no build step required.

## Limitations

- CORS restrictions prevent true HTTP status code checks from the browser
- Favicon-based checking may produce false positives if a site blocks favicon requests but is otherwise operational
- CDN caching may mask actual outages in some cases

## License

MIT
