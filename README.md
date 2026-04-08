# Fastify Proxy Server

This server uses Fastify to:

- Proxy API requests from `/api/*` to an upstream server.
- Serve static frontend files from the `public/` directory.

## 1. Requirements

- Node.js 18+ (Node.js 20 recommended)
- npm

## 2. Installation

```bash
npm install
```

## 3. Run Locally

```bash
npm run dev
```

The server runs on:

```text
http://localhost:3001
```

## 4. How It Works

### Proxy API

- Proxy prefix: `/api`
- Current upstream: `https://s40lp1.ucc.cit.tum.de`
- Since `rewritePrefix: ""`:

```text
/api/foo/bar  ->  https://s40lp1.ucc.cit.tum.de/foo/bar
```

The server also rewrites several headers (`host`, `origin`, `referer`) for upstream compatibility.

### Serve static

- Static root: `public/`
- Prefix: `/`

The prebuilt frontend assets in `public/` are served directly.

## 5. Quick Configuration

You can update constants in `app-constant.ts`:

- `UPSTREAM_URL`: target backend URL
- `PORT`: local server port

## 6. Main Structure

```text
.
|- server.ts         # Fastify app (proxy + static)
|- app-constant.ts   # UPSTREAM_URL and PORT configuration
|- public/           # Prebuilt frontend assets
|- package.json
```
