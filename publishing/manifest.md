# Publishing Manifest

This file is the **source of truth** for every page on the docs website.

To publish changes, follow the two-step workflow in [`README.md`](README.md):
1. Edit entries here.
2. Regenerate affected HTML pages and update `docs/index.html`.

---

## Manifest Entries

### `intensivkurs-nenad/index.html`

```
title:        Intensivkurs Nenad Notizen
type:         app
status:       published
output:       docs/intensivkurs-nenad/index.html
action_label: Öffnen
description:  Digitalisierte A2/B1-Kursnotizen mit Suche, Sidebar-Navigation und zuschaltbarer Grammatik-Markierung.
source:
  - raw_notes/Intensivkurs Nenad/IntensivkursNenad.html
  - raw_notes/Intensivkurs Nenad/images/
```

---

### `stories/ein-ruhiger-morgen-in-zuerich.html`

```
title:        Ein ruhiger Morgen in Zürich
type:         story
status:       published
output:       docs/stories/ein-ruhiger-morgen-in-zuerich.html
action_label: Lesen
description:  Kurzer A2/B1-Lesetext mit zuschaltbaren Grammatikmarkierungen und getrennten Dativ-/Akkusativ-Hinweisen.
source:       (agent-generated — no source file)
```

---

## Status Reference

| Status | Meaning |
| :--- | :--- |
| `published` | HTML file is live and up to date with the manifest entry |
| `draft` | Entry describes a page that has not yet been generated |
| `outdated` | Source material has changed; HTML needs to be regenerated |
