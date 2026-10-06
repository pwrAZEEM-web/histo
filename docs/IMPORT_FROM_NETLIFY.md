# Import the HistoAtlas site from Netlify into this repo

The live site (<https://histo-atlas.netlify.app/>) currently exists **only
on Netlify**. This guide moves it into GitHub and wires up automatic
deploys. There are 4 steps; two need clicks in the Netlify dashboard
(only the site owner can do those), the rest happens here.

## Step 1 — Download your deployed files from Netlify (you, ~2 min)

Netlify keeps every successful deploy and lets you download it as a ZIP
([official docs: "Download a deploy"](https://docs.netlify.com/deploy/manage-deploys/manage-deploys-overview/)):

1. Go to [app.netlify.com](https://app.netlify.com/) → open the
   `histo-atlas` site → **Deploys** tab.
2. Click the latest **Published** deploy to open its detail page.
3. In the page header click **Download**, wait for the ZIP to generate,
   then click **Download ready**.
4. Attach the ZIP file here in the chat (or upload it to this repo).

> Tip: if the project was created with Netlify's AI builder from a prompt,
> check the project's dashboard page first for a code view or GitHub
> export option — that would give you the *original source* instead of the
> built output, which is even better. Either way, attach what you get.

## Step 2 — The code gets committed here (agent)

Once the ZIP is attached, the agent will:

1. Unpack and organize it into clean source
   (`index.html` + assets, or the framework project if that's what it is).
2. Add `netlify.toml` with the verified build command + publish directory.
3. Update this README with real dev instructions.
4. Open a pull request into `main` for review.

## Step 3 — Link the Netlify site to this repo (you, ~3 min)

This turns on continuous deployment: every push to `main` redeploys the
live site automatically
([docs: "Link a Git repository"](https://docs.netlify.com/build/git-workflows/repo-permissions-linking/)):

1. Netlify dashboard → `histo-atlas` site →
   **Project configuration → Developer settings → Continuous deployment →
   Repository** → **Link repository**.
2. Choose **GitHub** → select `pwrAZEEM-web/histo`
   (grant the Netlify GitHub App access if asked).
3. Set the production branch to **`main`**.
4. Under **Build settings** in the same section, enter the values from the
   import PR (for a static site this is typically: build command empty,
   publish directory = site root — see
   [docs: "Build configuration overview"](https://docs.netlify.com/build/configure-builds/overview/)).
5. Save and trigger a deploy (pushing/merging the import PR does this).

Prefer the terminal? The same linking can be done with the
[Netlify CLI](https://docs.netlify.com/api-and-cli-guides/cli-guides/get-started-with-cli/):

```bash
npm install -g netlify-cli
netlify login
git clone https://github.com/pwrAZEEM-web/histo.git
cd histo
netlify link   # pick the histo-atlas site
```

## Step 4 — Verify (both, ~2 min)

- [ ] Merging the import PR triggers a Netlify production deploy.
- [ ] <https://histo-atlas.netlify.app/> still serves the full site.
- [ ] Opening a test PR produces a Netlify Deploy Preview URL.
- [ ] `main` is the only branch Netlify publishes from (unless you enable
      branch deploys).

## FAQ

**Will linking delete or break the live site?**
Linking only connects Git pushes to new deploys; your current published
deploy stays live until the first Git-triggered build succeeds. If a build
fails, Netlify keeps serving the previous working deploy.

**The ZIP has minified `assets/index-*.js` — is that a problem?**
No for hosting: the site runs exactly as before. For *editing*, original
source (Step 1 tip) is nicer. Either is committable and deployable.

**Can we use a custom domain later?**
Yes — anytime via Site configuration → Domain management. No repo changes needed.
