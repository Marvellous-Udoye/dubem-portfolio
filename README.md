# Dubem Portfolio

A static portfolio site for Onyilimba Dubemchukwu Fidelis, based on the Stratopreter/Webflow export.

The site is served as plain HTML, CSS, JavaScript, images, and videos. It is not a React/Vite app, so there is no build step.

## Project Structure

```text
.
├── files/              # CSS, JavaScript libraries, and bundled template assets
├── syntax/             # Main site pages and media
│   ├── index.html      # Home page
│   ├── project.html    # Project page placeholder/export
│   ├── videos/         # Hero video assets
│   └── team/           # Team/profile media
├── package.json        # Local static server scripts
├── package-lock.json
└── vercel.json         # Vercel rewrite config
```

## Local Development

Install dependencies:

```powershell
npm install
```

Start the local static server:

```powershell
npm run dev
```

Open:

```text
http://localhost:3000/syntax/
```

The root path is also configured for deployment through `vercel.json`, but locally `serve` may redirect `/syntax/index.html` to `/syntax/`.

## Deployment

This project can be deployed on Vercel as a static site.

Recommended Vercel web settings:

```text
Framework Preset: Other
Install Command: npm install
Build Command: leave empty
Output Directory: .
```

`vercel.json` rewrites the deployed root URL to the main page:

```json
{
  "rewrites": [
    {
      "source": "/",
      "destination": "/syntax/index.html"
    }
  ]
}
```

## Notes

- Do not commit `node_modules`; it is ignored in `.gitignore`.
- The exported template originally referenced several Webflow/CDN paths as local folders. The main page has been patched to load bundled local libraries from `files/` where available and valid `https://` CDN URLs where needed.
- If a page is blank, check the browser console and Network tab for `404` errors first. Most issues will be caused by a missing or incorrectly rewritten asset path.
