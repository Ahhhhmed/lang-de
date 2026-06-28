# Publishing

This folder controls how content from the learning workspace gets published to the **docs website** (`/docs`).

The website is an HTML mini-site served statically. All pages share a common visual language described in [`html_templates.md`](html_templates.md). The German highlighting conventions used inside doc pages are defined in [`highlighting_strategy.md`](highlighting_strategy.md).

---

## Two-Step Publishing Workflow

### Step 1 — Update the manifest

Edit [`manifest.md`](manifest.md) to reflect the desired state of the docs site:

- **Adding a new page**: add a new entry with `status: draft`, fill in all fields, point `source` to the originating file(s).
- **Updating a page**: change its `status` to `outdated` if the source has changed and the HTML needs regenerating.
- **Removing a page**: delete the entry and delete the corresponding file in `docs/`.
- **Updating the index**: the index card for each page is driven by the manifest fields (`title`, `description`, `action_label`, `type`). Update those here, then apply in Step 2.

### Step 2 — Publish

Bring `docs/` into line with the manifest:

1. For every entry with `status: draft` or `status: outdated` — generate or regenerate the HTML file at the path given in `output`, following the templates in [`html_templates.md`](html_templates.md).
2. Update `docs/index.html` so its artifact list matches the set of `status: published` entries in the manifest (same order, same metadata).
3. Mark updated entries as `status: published` in the manifest.

> Publishing is always done by an agent reading the manifest and the templates. Never edit `docs/` pages directly without updating the manifest first.

---

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [`manifest.md`](manifest.md) | Source-of-truth for all published docs — tracks source files, output paths, and status |
| [`html_templates.md`](html_templates.md) | HTML/CSS style guide and copy-paste templates for all page types |
| [`highlighting_strategy.md`](highlighting_strategy.md) | German grammar highlighting colour spec used inside doc pages |
