# Free Deployment with Cloudflare Pages

## 1. Push the project to your own GitHub repository

Create an empty repository in your GitHub account, then replace the current
remote with your repository URL:

```bash
git remote set-url origin https://github.com/YOUR_USERNAME/AI-Resume-Builder.git
git add .
git commit -m "Prepare AI Resume Builder for deployment"
git push -u origin main
```

Do not commit a `.env` file or API keys.

## 2. Create the Cloudflare Pages project

1. Sign in at <https://dash.cloudflare.com/>.
2. Open **Workers & Pages**.
3. Select **Create application**, then **Pages**.
4. Select **Import an existing Git repository**.
5. Connect GitHub and choose your `AI-Resume-Builder` repository.
6. Use these build settings:

| Setting | Value |
| --- | --- |
| Production branch | `main` |
| Build command | `npm run build` |
| Build output directory | `dist` |

No environment variables are required for the free standalone version.

## 3. Deploy

Select **Save and Deploy**. Cloudflare will provide a free URL similar to:

```text
https://ai-resume-builder.pages.dev
```

Each new push to `main` will automatically deploy the latest version.

## Optional integrations

Add variables under **Settings > Environment variables** only when needed:

| Variable | Purpose |
| --- | --- |
| `VITE_CLERK_PUBLISHABLE_KEY` | Clerk authentication |
| `VITE_API_BASE_URL` | Strapi server URL |
| `VITE_STRAPI_API_KEY` | Restricted Strapi API token |
| `VITE_GOOGLE_AI_API_KEY` | Gemini generation features |
| `VITE_BASE_URL` | Final `pages.dev` or custom-domain URL |

Without these variables, the deployed app uses a local guest account and saves
resumes in that visitor's browser using `localStorage`.

## Important limitations

- Browser-local resumes are available only on the same browser and device.
- Shared resume links cannot access another user's browser-local data.
- All `VITE_*` values are visible in the browser bundle. Do not expose
  unrestricted or privileged API keys.
- When enabling Clerk, add the deployed domain in the Clerk dashboard.
- When enabling Strapi, allow the deployed domain in Strapi's CORS settings.
