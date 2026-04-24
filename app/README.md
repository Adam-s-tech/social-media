# Social Media AI — Next.js App

This is the Next.js front-end for the **Social Media AI** pipeline.

For full documentation (installation, API keys, usage), see the **[root README](../README.md)**.

## Running the app

Make sure you have created a `.env` file at the **project root** (one level up) with your API keys.  
See [../docs/API_KEYS.md](../docs/API_KEYS.md) for instructions.

```bash
# From the project root:
cd app
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Pages

| Page | URL | Description |
|---|---|---|
| Dashboard | `/` | Global stats and recent videos |
| Creators | `/creators` | Manage competitor Instagram accounts |
| Configs | `/configs` | Manage pipeline configurations |
| Run | `/run` | Launch the pipeline with real-time progress |
| Videos | `/videos` | Browse analysed videos and generated concepts |

## Tech stack

- **Next.js 16** (App Router) + **TypeScript**
- **Tailwind CSS** + **shadcn/ui**
- API routes in `src/app/api/`
- Core pipeline logic in `src/lib/`
