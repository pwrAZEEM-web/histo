# HistoAtlas — the 57 histology slides

Oral-exam companion · Histology III

**Live site:** <https://histo-atlas.netlify.app/>

All **57 exam slides** in one place — each with what it is, how to spot it,
theoretical background, mechanisms, histological appearance, embryology,
an interactive ID checklist, staining notes, plus the labeled handout plates.

## Status

🚧 **Source import in progress.** The site currently lives only on Netlify.
This repo is being set up to hold the site's code and deploy it automatically:

- Production branch: `main` (Netlify watches this branch)
- Every push to `main` → Netlify rebuilds and redeploys the live site
- Every pull request → a Netlify Deploy Preview with its own URL

## Getting the code into this repo

Follow **`docs/IMPORT_FROM_NETLIFY.md`** — it takes ~5 minutes:

1. **You:** download a ZIP of the deployed site from the Netlify dashboard
   (Deploys → latest published deploy → **Download**) and attach it here.
2. **Me (the agent):** organize it into proper source, add `netlify.toml`
   with the correct build settings, and open a PR.
3. **You:** link the Netlify site to this repo for continuous deployment
   (Project configuration → Developer settings → Continuous deployment →
   Repository → **Link repository**).

## Local development

_Final instructions land here once the source is imported. Expected:_

```bash
# static site (no build step)
npx serve .
# or, if the import reveals a Vite/React project:
npm install
npm run dev
```

## License / notes

Personal study companion built from course notes and seminar handouts.
Content is for exam preparation, not medical advice.
