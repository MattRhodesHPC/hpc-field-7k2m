# Homestead Paving Co. — Field Forms (hosted site)

These files are ready to host on GitHub Pages so tablets and workstations open the forms from one web address instead of passed-around files.

**What's here:** `index.html` (home page with links to the three forms), the three form files, and `sw.js` (caches the forms on each device so they still open with no signal — saved days already queue locally and upload when back online).

## Put it on GitHub Pages

1. Create a GitHub account if needed, then a **new repository** — name it something non-obvious (e.g. `hpc-field-7k2m`), and make it **Private** if you have GitHub Pro (see security note below); otherwise Public works.
2. Click **uploading an existing file** (or Add file → Upload files) and drag in everything in this folder: `index.html`, `sw.js`, and the three `HPC_*.html` files. Commit.
3. Go to **Settings → Pages** → under "Build and deployment," Source: **Deploy from a branch**, Branch: **main** / **(root)** → Save.
4. After a minute the site is live at `https://YOURUSERNAME.github.io/REPONAME/`.

## Add the flow URL + key

If you haven't already pasted `flowUrl` / `apiKey` (and `officePin` in the office file) into the CONFIG blocks, you can do it right on GitHub: open the file → pencil icon (Edit) → paste → Commit. Every device picks up changes the next time it loads the page — no re-distributing files ever again.

## On the tablets

Open the site in Chrome → menu (⋮) → **Add to Home screen**. It behaves like an app: full screen, works offline, and the foreman's saved days, language choice, and job stay on the device.

## Security — read this

Anyone who views the page source can see the flow URL and API key, and with those they can read/write your five SharePoint lists. That was equally true of the passed-around files, but a **public** GitHub repo is searchable and gets scanned by bots, which meaningfully raises the odds of someone finding it. So, in order of preference:

1. **Private repo + GitHub Pro** (~$4/mo): the published site still works for your crews, but the source code isn't browsable or indexed on GitHub.
2. Public repo with an unguessable repo name, and don't link the site anywhere public.

Either way: if you ever suspect the key leaked, change it in the flow's "Check secret key" condition and in the two CONFIG blocks — takes two minutes and locks everyone else out. The flow can only touch the one SharePoint site you pointed it at.

## Updating the forms later

Replace a file on GitHub (Add file → Upload files → drag the new version → Commit). The service worker fetches network-first, so devices get the new version on their next load; offline devices keep the last cached copy until they're back in signal.
