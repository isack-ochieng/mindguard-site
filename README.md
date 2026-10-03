# MindGuard Public Website

Standalone public advertising and privacy website for **MindGuard**.

This repository is intentionally separate from the MindGuard Android/Flutter application repository.

## Repository purpose

This repo contains only public-facing web content:

- marketing homepage;
- product/how-it-works information;
- privacy policy;
- static assets; and
- Cloudflare Pages deployment configuration.

It does **not** contain the Android application source code.

## Structure

```text
mindguard-site/
├── site/
│   ├── index.html
│   ├── privacy/
│   │   └── index.html
│   ├── assets/
│   │   └── logo.svg
│   ├── styles.css
│   ├── _headers
│   ├── _redirects
│   ├── robots.txt
│   └── sitemap.xml
├── README.md
└── LICENSE
```

## Local preview

This is a static site and does not require a build system.

From the repository root, use any static-file server, for example:

```bash
python -m http.server 8080 --directory site
```

Then open:

```text
http://localhost:8080/
http://localhost:8080/privacy
```

## Cloudflare Pages

Create a new **Cloudflare Pages** project and connect this repository.

Recommended configuration:

| Setting | Value |
|---|---|
| Production branch | `main` |
| Root directory | `/` |
| Framework preset | None / Other |
| Build command | `exit 0` |
| Build output directory | `site` |

No Node.js installation and no `npm run build` step are required.

The public URLs will be:

```text
https://mindguard.pages.dev/
https://mindguard.pages.dev/privacy
```

## Custom domain

A custom domain can later be attached from Cloudflare Pages without changing the site structure.

If the custom domain replaces `mindguard.pages.dev`, update the canonical URL, Open Graph URL, robots.txt, and sitemap.xml accordingly.

## Privacy policy maintenance

The privacy policy must remain synchronized with the actual Android application's behaviour and Google Play Data safety declarations. Update `site/privacy/index.html` whenever permissions, third-party services, data practices, retention, or other material privacy characteristics change.

## Deployment isolation

This repository is independent from the Android application repository. Do not add the website as a subdirectory of the application repository if strict separation is required.
