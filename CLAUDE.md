# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a lightweight Vercel reverse proxy application that routes traffic to Databricks instances. It's part of the ad-cloud-platform monorepo under `applications/xdp/ui/vercel-proxy/`.

## Purpose

This proxy serves as an intermediary layer between clients and Databricks cloud instances, providing:
- Path-based routing to Databricks endpoints
- CORS header management
- URL rewriting for different path prefixes

## Architecture

The application uses Vercel's edge network infrastructure with:
- **vercel.json**: Configuration-based routing without custom server code
- **Rewrites**: Maps URL paths to Databricks instance endpoints
- **Headers**: Applies CORS policies for cross-origin requests

### Routing Configuration

All routing is handled declaratively in `vercel.json`:
- `/a/*` and `/b/*` paths route to the same Databricks instance
- Catch-all route `/:path*` forwards all other requests
- Target: `https://dbc-4fabc9a4-3e18.cloud.databricks.com`

## Commands

### Installation
```bash
npm install
```

### Deployment
```bash
# Deploy to Vercel (development/preview)
vercel

# Deploy to production
vercel --prod
```

### Local Development
Note: This is a Vercel-specific configuration project with no local development server. Testing requires deployment to Vercel's platform.

## Important Notes

- **No custom code**: This proxy runs entirely on Vercel's configuration-based routing
- **http-proxy-middleware dependency**: Listed but not actively used (configuration-only proxy)
- **CORS enabled**: Wildcard CORS headers allow all origins
- **Path preservation**: Original paths are maintained when proxying to Databricks