# Gabriele Bovina Portfolio

Personal portfolio built with Astro and deployed through GitHub Actions to [zela2000.org](https://zela2000.org).

This repo is static and data-driven. Most of the visible content lives in `src/data/`, so you can update copy, links, sections, and project data without changing the component structure.

## Stack

- Astro 6
- Tailwind CSS 4
- TypeScript
- GitHub Actions for deploys and dependency updates

## Local Development

Use Corepack to run the pinned pnpm version:

```bash
corepack pnpm install
corepack pnpm dev
```

Build the site locally with:

```bash
corepack pnpm build
```

The build output lands in `dist/`.

## Configuration

The main content and metadata live here:

- `src/data/personal.json` - name, bio, socials, contact info, and hero copy
- `src/data/site.json` - SEO metadata, tagline, footer attribution, and services cards
- `src/data/menu.json` - section navigation labels
- `src/data/projects.json` - project cards and hero slider content
- `src/data/expertise.json` - expertise section cards
- `src/data/skills.json` - skills and icon references

The site is configured for the custom domain with these values:

- `SITE_URL=https://zela2000.org`
- `BASE_PATH=/`

Current profile data:

- Name: `Gabriele Bovina`
- GitHub handle: `ZELA2000`
- Public email: `gabrielebovina@outlook.it`

## Deploy on GitHub Pages

This repo is meant to deploy from GitHub Actions, not from a branch.

1. In repository settings, set GitHub Pages source to `GitHub Actions`.
2. Open **Actions** and run the workflow named **Deploy to GitHub Pages**.
3. Keep `SITE_URL` and `BASE_PATH` aligned with the custom domain. For this project they should stay at `https://zela2000.org` and `/`.

The workflow resolves the site URL and base path, builds `dist/`, and uploads the Pages artifact.

## Update Dependencies

The workflow **Update Dependencies** refreshes direct dependencies, pins the pnpm packageManager version, runs a security audit, and updates the README timestamp.

Run it from **Actions** whenever you want to refresh the dependency tree.

## Asset Generation

The build process also refreshes generated assets when needed:

- fonts under `public/fonts/`
- generated icons under `public/images/icons/`
- fetched GitHub images for projects when `GITHUB_USER` and `GITHUB_TOKEN` are available

## Editing Notes

- Update content in `src/data/` first. Most copy changes do not require component edits.
- `corepack pnpm` is the safest way to run local commands in this workspace.
- `update-deps.yml` is the place to change dependency update behavior.
- If you add or remove sections, update `src/data/menu.json` to keep the navigation in sync.
