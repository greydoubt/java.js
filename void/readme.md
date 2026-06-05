# 1. Configure the target
```
// void.json
{ "target": "node" }
```
# 2. Install the server dependency (Node.js only)

Node.js requires @hono/node-server as an additional dependency. Bun and Deno use their built-in HTTP servers.
```
npm install @hono/node-server
```
# 3. Develop
```
npx vite dev
```
The dev server runs your Hono routes in Node.js through Vite's SSR module loading. You get the same hot-reload experience as the Cloudflare target, but without workerd.


# 4. Build and run
```
npx vite build
node dist/ssr/index.js
```

For Bun:
```
bunx vite build
bun dist/ssr/index.js
```
For Deno:
```
deno run -A npm:vite build
deno run -A dist/ssr/index.js
```


The server listens on PORT (env variable) or 3000 by default.


# Build Output

The build produces two entry points:
```
dist/
  ssr/
    app.js       ← Hono app with static asset middleware (default export)
    index.js     ← imports app.js and starts the HTTP server
  client/        ← static assets (pages mode only)
    assets/
      ...

```

index.js: imports app.js and starts the server
