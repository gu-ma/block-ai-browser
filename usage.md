---
draft: true # Do not publish
---

# How to Use This Browser AI Block

This block is a reusable teaching unit about **running AI models directly in the browser**.

It combines short conceptual notes with runnable HTML/JavaScript demos so learners can move from explanation to hands-on experimentation quickly.

> [!WARNING]
> This template auto-generates `README.md` from `index.md` on push (via GitHub Actions).
> The workflow may create one extra bot commit after your push.
> Before your next push, run `git pull` to avoid non-fast-forward errors.

## README Sync Workflow (GitHub + Quartz)

This template uses a GitHub Actions workflow to keep `README.md` synchronized from `index.md`.

- `index.md` is the source of truth for content.
- On push, the workflow copies `index.md` to `README.md`.
- Frontmatter is removed from `README.md` so GitHub displays it cleanly.
- The workflow commits this update automatically with `github-actions[bot]`.

### What this means for your Git routine

After you push your changes, the workflow may create one additional commit.
Before your next push, run:

```bash
git pull
```

This avoids "branch is behind" / non-fast-forward errors.

## Structure

- **index.md**: main block overview and teaching roadmap
- **content/**: sequenced lesson notes for the block
- **samples/**: runnable HTML/JS demos
- **resources/**: optional supplementary materials, links, or assets
- **class-notes/**: instructor-specific notes or adaptations

## Recommended Teaching Workflow

1. Start with the overview in `index.md`
2. Work through the content notes in order
3. Run the matching demos from `samples/`
4. Ask students to modify the demos during the hands-on tasks

## Running the Samples Locally

Use a local static server from the block root:

```bash
python -m http.server 8000
```

Then visit the sample in a browser such as Chrome or Edge:

```text
http://localhost:8000/samples/01-transformersjs-sentiment-demo.html
```

Why local-first:

- avoids `file://` loading problems
- makes model downloads and paths easier to debug
- works better for browser inference experiments
- keeps the workflow simple for classroom editing

## GitHub Pages vs Local

- **Local** is the primary teaching path
- **GitHub Pages** is useful later for sharing a stable demo URL

If you publish samples online, keep paths relative and test browser compatibility carefully.

## Teaching Notes

- Prefer recent Chrome or Edge for WebGPU demos
- Be explicit about first-load delays and model download size
- Encourage learners to compare browser latency, privacy, and offline advantages against API-based workflows
- Remind students that WebLLM demos depend heavily on device GPU/CPU capability

---

Keep this block focused on practical browser-AI literacy: model loading, async flows, UX constraints, and tool selection.
