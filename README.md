[README.md](https://github.com/user-attachments/files/31381386/README.md)
# portfolio# Donghee (Joy) Chae — personal site

Single-file static site for GitHub Pages. No build step, no dependencies.

## Publishing

1. Create a repository named `<your-github-username>.github.io` (e.g. `joychae.github.io`).
2. Upload `index.html`, the `img/` folder, and your CV PDF to the repository root.
3. Settings → Pages → Source: `main` branch, `/ (root)` → Save.
4. Live in a few minutes at `https://<your-github-username>.github.io`.

To use a project repo instead (e.g. `github.com/joychae/site`), the URL becomes
`https://joychae.github.io/site/` — everything still works because all paths are relative.

## Adding images

Every photo slot is a dashed placeholder that describes what to shoot and prints the exact
filename underneath. Drop a file at that path and the placeholder is replaced automatically
on the next page load — no code change needed.

Recommended: JPG for photos, PNG for figures and plots. Keep each file under ~600 KB.
Landscape 4:3 works best for figures, 16:9 for the wide slots, 4:5 for the portrait.

### Image slots

**Profile**
- `img/profile/portrait.jpg` — you at the bench or the flow cytometer (4:5)

**Devices**
- `img/devices/inhalation-housing.jpg` — the murine inhalation exposure housing you designed
- `img/devices/vbg-adapter.jpg` — Rhino render + printed prototype

**Research — Channel 01, immunomodulation**
- `img/research/msc-efferocytosis-schematic.png`
- `img/research/flow-dotplot.png` — FlowJo gating; the single most persuasive figure on the site
- `img/research/tcell-suppression.png`
- `img/research/bystander-scheme.png`
- `img/research/ucmsc-culture.jpg`
- `img/research/adipocyte-oro.png`

**Research — Channel 02, nanomaterials**
- `img/research/scintillator-scheme.png`
- `img/research/tem-particles.png`
- `img/research/dls-distribution.png`
- `img/research/emission-spectrum.png`
- `img/research/msn-synthesis.png`
- `img/research/ferroptosis-viability.png`
- `img/research/cartam-scheme.png`
- `img/research/intron-knockin.png`

**Research — Channel 03, computational**
- `img/research/adc-modules.png`
- `img/research/adc-heatmap.png`
- `img/research/il2-workflow.png`
- `img/research/docking-pose.png`
- `img/research/tme-remodel.png`

**Research — Channel 04, environmental**
- `img/research/pb-crosspresentation.png`
- `img/research/lysotracker.png`
- `img/research/pcb-endpoints.png`
- `img/research/exposure-assessment.png`

**Posters**
- `img/posters/isct-2026.jpg`
- `img/posters/kbiox-2025.jpg`
- `img/posters/presenting.jpg`

**Skills** (shown inside the skill pop-ups)
- `img/skills/efferocytosis.png`, `cfse.png`, `culture.jpg`, `panel-design.png`,
  `cytoflex.jpg`, `flowjo.png`, `elisa.jpg`, `synthesis-bench.jpg`, `dls.png`,
  `confocal.png`, `r-analysis.png`, `docking.png`, `rhino.png`

**Outreach & life**
- `img/outreach/korus70.jpg`, `img/outreach/simtomi.jpg`, `img/outreach/teaching.jpg`
- `img/life/truss.jpg`, `img/life/volunteer.jpg`

## CV PDF

Put the exported CV at the repository root as `Donghee_Chae_CV.pdf`.
The footer link already points there.

## Editing the site in the browser (Ctrl + E)

You never share a password with anyone to do this. Editing happens on your own machine, in your
own browser.

1. Open your site (locally or the published URL) and press **Ctrl + E** (**Cmd + E** on Mac).
   A purple toolbar appears at the bottom.
2. **Text** — click any sentence and type. Everything with a dashed purple outline is editable.
3. **Photos** — click a dashed photo box. A dialog opens with two options:
   - *Choose a file* — the image is added immediately, resized to 1400px wide and compressed.
     Good for trying things out.
   - *Type a path* like `img/research/flow-dotplot.png` — better for the published site, because
     the image lives as a separate file instead of being embedded in the HTML.
   The same dialog has **Remove photo** to take one back out.
4. **Blocks** — every section has a `+ Add` button in edit mode (publication, award, post,
   research project, photo slot, entry). Each block has its own **Delete** button.
5. **Ctrl + S** saves a draft to this browser so a refresh does not lose your work.
6. When you are finished, click **Download index.html**. Replace the file in your GitHub
   repository with the downloaded one and the site updates.

### Important

The draft in step 5 lives only in that browser. Nothing is published until you download the file
and upload it to GitHub. If you edit on your laptop and then open the site on your phone, the
phone will show the last published version.

If you embed many photos as files rather than paths, `index.html` gets large. Past roughly 5 MB
the draft can no longer be saved locally — a message tells you. At that point switch to the path
method and upload images to `img/` on GitHub instead.

## Editing the site by hand (optional)

You never need to share a password with anyone to do this — not your Google account, not your
GitHub account. Editing happens inside your own logged-in GitHub session.

### The easy way: edit in the browser

1. Go to your repository on github.com and click `index.html`.
2. Click the pencil icon (top right) — this opens the file editor.
3. Change the text, scroll to the bottom, and click **Commit changes**.
4. Wait about a minute and refresh your site. Done.

Use `Ctrl+F` / `Cmd+F` in the editor to find the sentence you want to change.

### Adding a photo

1. Open the folder you want, e.g. `img/research`.
2. **Add file → Upload files**, drag your image in, and name it exactly as the placeholder
   said (e.g. `flow-dotplot.png`).
3. Commit. The dashed box is replaced by your image automatically.

### Where each thing lives in index.html

| What you want to change | Where to look |
| --- | --- |
| Name, tagline, email at the top | near the top, inside `<header class="hero">` |
| About paragraphs | `<section id="about">` |
| Education, teaching, awards | the matching `<section id="...">` |
| Publications and presentations | `<section id="publications">` / `id="presentations"` |
| Research projects and their figures | the `THEMES` object in the `<script>` at the bottom |
| Skill cards and their pop-ups | the `SKILLS` list, just after `THEMES` |

### Adding a research project

Inside `THEMES`, find the channel you want and add one entry to its `projects` list:

```js
{ t:"Project title",
  where:"Lab, University · PI: Name · dates",
  status:"In progress",
  body:["First paragraph.","Second paragraph."],
  mine:"What you personally did.",
  chips:["Method","Method","Method"],
  figs:[["img/research/filename.png","What to shoot or plot","<b>Fig 1.</b> Caption."]]
},
```

Keep the commas and quotation marks exactly as shown. If the page ever goes blank after an
edit, it is almost always a missing comma or quote — GitHub keeps every previous version, so
open the **History** tab and revert.

### Safer option while you learn

Make changes on a branch instead of `main`: in the editor, choose *Create a new branch for
this commit*. The live site only updates when you merge that branch into `main`.

## Editing content

All research content lives in the `THEMES` object near the bottom of `index.html`, and the
skills list in `SKILLS` right after it. Adding a project means adding one object to the
`projects` array of a theme — title, where, status, body paragraphs, "what I did", method
chips, and figure slots.

## Before publishing

- Confirm the TOEFL figure if you add it to the site.
- Do not upload patient-identifiable photos from hospital volunteering.
- Check with your PI before posting unpublished figures from lab projects.
