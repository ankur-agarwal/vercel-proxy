# Vercel Proxy for Databricks

This project sets up a reverse proxy using Vercel to route traffic to a Databricks instance based on path.

## Routes

- `/a/*` -> Routes to Databricks instance
- `/b/*` -> Routes to Databricks instance

## Development

1. Install dependencies:
```bash
npm install
```

2. Deploy to Vercel:
```bash
vercel
```

## Production Deployment

```bash
vercel --prod
``` 