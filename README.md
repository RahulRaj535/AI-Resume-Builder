# AI Resume Builder

An AI-powered resume builder designed and developed as a final year project.
It lets users create, customize, preview, download, and share professional
resumes through a React and Vite interface.

## Developer

**Rahul Raj**

B.Tech in Computer Science and Engineering (Artificial Intelligence)<br>
Motihari College of Engineering

Phone: [+91 74799 85407](tel:+917479985407)<br>
Email: [ranjanrahul5279@gmail.com](mailto:ranjanrahul5279@gmail.com)

## Deployment

The project is ready for free deployment on Cloudflare Pages. See
[DEPLOYMENT.md](DEPLOYMENT.md) for the GitHub, build, and environment-variable
setup.

## Features

- Resume creation and live preview
- Personal details, experience, education, and skills
- AI-assisted professional summaries
- Custom resume theme colors
- Printable and shareable resume pages
- Optional local mode without external services

## Local setup

```bash
npm install
copy .env.example .env
npm run dev
```

All external services are optional for local development:

- Without `VITE_CLERK_PUBLISHABLE_KEY`, the app uses a local guest account.
- Without `VITE_API_BASE_URL`, resume data is stored in browser `localStorage`.
- Without `VITE_GOOGLE_AI_API_KEY`, AI generation buttons are disabled.
- Without `VITE_BASE_URL`, share links use the current browser origin.

To use the hosted integrations, fill in the corresponding values in `.env`.
The frontend expects a Strapi `user-resumes` collection with create, read,
update, and delete access.

Every `VITE_*` value is bundled into client-side JavaScript. Use only
browser-safe credentials with restricted permissions. A production application
should proxy privileged Strapi and Gemini requests through a backend.
