# EcoTime Capsule: 1900 vs 2026 Earth

Split-screen, Uzbek-language climate comparison with independently controlled Three.js globes, a React + Tailwind frontend, Express REST API, and MongoDB/Mongoose schema. The server serves bundled fallback records if MongoDB is not configured.

## Run locally

```sh
cp .env.example .env
npm install
npm run dev
```

Open `http://localhost:5173`. The API listens at `http://localhost:4000`; check `/api/health` and read `/api/earth/1900`, `/api/earth/2026`, or `/api/earth`.

### Open with VS Code Live Server (Go Live)

The workspace recommends the Live Server extension and points its web root to the built `dist/` folder. Build once with `pnpm run build` (or `npm run build` where npm is installed), then open the project `index.html` and click **Go Live**. Live Server will open the optimized static build on port 5500. Rebuild after editing source files so `dist/` receives the latest changes. The page includes local data fallbacks, so the visual comparison still works without starting the API.

To persist records, start MongoDB, set `MONGODB_URI` in `.env`, then run `npm run db:seed`. The API falls back to checked-in records while the database is offline. For deployment, build the static client with `npm run build`, serve `dist/` from a CDN/static host, and deploy the Express API separately with an allowlisted `CLIENT_ORIGIN` and managed MongoDB. Add rate limiting, request logging, TLS, and secret management at the deployment edge.

## Data interpretation

The visual year 2026 uses the latest completed global observation year available at the time of this project: 2025. Its data-year badge prevents incomplete 2026 figures being presented as a finished annual average. CO₂ is atmospheric concentration (ppm), not annual emissions. Temperature is the surface-temperature anomaly against 1850–1900, not an absolute global temperature. The 1900 forest share is explicitly a historical estimate because a directly comparable global measurement series does not exist that far back. Values are supplied as reference snapshots; update them from the linked source publications before making decisions or republishing as a current scientific dataset.

The globe canvas now loads NASA's Blue Marble: Next Generation global base map (January 2004) and overlays soft, illustrative cloud bands. A procedural map remains as an offline fallback. The texture is modern Earth imagery used as a realistic geographic backdrop; it is not a reconstructed 1900 satellite image, and the warm color grade on the 2026 globe is illustrative rather than a measured global smog layer. Credit the texture to NASA Earth Observatory when republishing.
# earth
