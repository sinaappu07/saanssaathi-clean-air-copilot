# SaansSaathi — Netlify package

This package serves the static page from `dist/` and the AI backend as a Netlify Function at `/api/chat`. The page uses the Clean-Air AI branding. The server function calls Google's Gemini Interactions API; its key is read from a Netlify environment secret and is not placed in the HTML.

## Deploy from your GitHub repository

1. Put all files in this folder at the **root** of your GitHub repository. Keep `index.html`, `netlify.toml`, and `netlify/functions/chat.mjs` in the shown locations.
2. In Netlify, choose **Add new project → Import an existing project**, connect GitHub, and select the repository.
3. Keep the base directory at the repository root. The included `netlify.toml` sets the build command to copy `index.html` into `dist`, publishes `dist`, and places the function outside the published folder.
4. Deploy the site. Netlify will show a live `*.netlify.app` URL.
5. Create a Gemini API key using Google AI Studio. Then open the Netlify site's **Project configuration → Environment variables**, add `GEMINI_API_KEY`, paste the key, and mark it **Contains secret values**. Make sure its scope includes **Functions**.
6. Trigger a new deploy so the function receives the secret. Then open the site, load a city in the Copilot, and ask a question.

The `/api/chat` function is public so site visitors can use it. Set usage limits and monitor the provider account. Do not put the key in GitHub, HTML, `netlify.toml`, or this README. If account setup asks for adult consent, ask a parent/guardian to handle that step.

## Local preview

For local development, copy `.env.example` to `.env`, place your own key in `.env`, and use Netlify Dev to preview Functions. `.env` is ignored by Git. Never commit it.

```text
GEMINI_API_KEY=your_key_here
```

Official references:

- [Deploy from a Git repository](https://docs.netlify.com/start/quickstarts/deploy-from-repository/)
- [Netlify Functions](https://docs.netlify.com/build/functions/get-started/)
- [Function environment variables](https://docs.netlify.com/build/functions/environment-variables/)
- [Netlify function routing](https://docs.netlify.com/build/functions/configuration/)
- [Gemini API](https://ai.google.dev/gemini-api/docs/get-started)
- [Open-Meteo Geocoding](https://open-meteo.com/en/docs/geocoding-api) and [Air Quality](https://open-meteo.com/en/docs/air-quality-api)
