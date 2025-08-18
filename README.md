# Render deployment (minimal)

This directory contains a minimal setup for deploying the Smart Classroom server on Render.

Files included
- `index.js`: thin bootstrap that imports the root `index.js`
- `package.json`: minimal package manifest for Render
- `render.yaml`: service definition pointing to `render_deploy/index.js`
- `Procfile`: herokuish process file

Deploy
1. Push this repo to GitHub
2. In Render, create a Web Service from this repo
3. Render will read `render_deploy/render.yaml` (auto) or you can set:
   - Build Command: `npm ci`
   - Start Command: `node render_deploy/index.js`
4. Environment variables required at minimum:
   - `MONGO_URI` (your cluster)
   - `ANTHROPIC_KEY` (if using Claude; otherwise mock path will run)
   - `PORT` (optional, defaults to 10000)
   - `NODE_VERSION=18.20.5`

Notes
- The service serves the `public/` directory via the root server.
- No duplication of assets; this bootstrap simply runs the main server entry. 