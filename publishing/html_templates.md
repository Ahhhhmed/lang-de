# HTML Templates & Style Guide

This document is the single source of truth for the visual design and HTML structure of every page in `docs/`.

All new pages **must** use the design tokens, boilerplate, and component patterns defined here. Never introduce ad-hoc colours, fonts, or structural patterns outside this guide.

For German grammar highlighting inside body text, see [`highlighting_strategy.md`](highlighting_strategy.md).

---

## Table of Contents

1. [Design Tokens (CSS Variables)](#1-design-tokens)
2. [Page Shell (Boilerplate)](#2-page-shell)
3. [Topbar Component](#3-topbar-component)
4. [Index Artifact List](#4-index-artifact-list)
5. [Section & Section Header](#5-section--section-header)
6. [Story / Reading Text Block](#6-story--reading-text-block)
7. [Callout Boxes](#7-callout-boxes)
8. [Footer](#8-footer)
9. [Theme Toggle Script](#9-theme-toggle-script)
10. [Page Type Templates](#10-page-type-templates)
11. [File Placement Rules](#11-file-placement-rules)

---

## 1. Design Tokens

Paste the following `<style>` block into every page's `<head>`. Do not change token names or values — consistency across pages depends on this.

```css
:root {
    /* Backgrounds */
    --bg-primary:    #f6f7f9;
    --bg-secondary:  #ffffff;
    --bg-tertiary:   #eef2f6;

    /* Text */
    --text-primary:   #111827;
    --text-secondary: #536072;
    --text-muted:     #7b8794;

    /* Borders & Accents */
    --border-color:  #d9e0e8;
    --accent:        #2563eb;
    --accent-hover:  #1d4ed8;
    --accent-soft:   #dbeafe;

    /* Status colours */
    --good:    #15803d;
    --warning: #b45309;

    /* Shadows */
    --shadow: 0 12px 32px rgb(17 24 39 / 0.08);

    /* Grammar Highlighting */
    --hl-masc:          #1a73e8;
    --hl-fem:           #d93025;
    --hl-neut:          #188038;
    --hl-plur:          #a142f4;
    --hl-verb:          #4b0082;
    --hl-insep-color:   #5f6368;
    --hl-insep-border:  #9aa0a6;
    --hl-dat-border:    #8ab4f8;
    --hl-akk-border:    #81c995;
    --hl-conj-bg:       #ffe082;
    --hl-conj-color:    #111827;
    --hl-subord-border: #fbc02d;
}

html[data-theme="dark"] {
    --bg-primary:    #0d1117;
    --bg-secondary:  #151b23;
    --bg-tertiary:   #1f2937;

    --text-primary:   #f3f4f6;
    --text-secondary: #a7b0bd;
    --text-muted:     #7d8794;

    --border-color:  #2f3a48;
    --accent:        #60a5fa;
    --accent-hover:  #93c5fd;
    --accent-soft:   #172554;

    --good:    #4ade80;
    --warning: #fbbf24;

    --shadow: 0 18px 44px rgb(0 0 0 / 0.35);

    /* Grammar Highlighting */
    --hl-masc:          #60a5fa;
    --hl-fem:           #f87171;
    --hl-neut:          #4ade80;
    --hl-plur:          #c084fc;
    --hl-verb:          #a78bfa;
    --hl-insep-color:   #9ca3af;
    --hl-insep-border:  #6b7280;
    --hl-dat-border:    #93c5fd;
    --hl-akk-border:    #86efac;
    --hl-conj-bg:       #4a3500;
    --hl-conj-color:    #fde68a;
    --hl-subord-border: #fcd34d;
}
```

> **Fonts:** Always load Inter (body) and Outfit (headings) from Google Fonts. Copy the `<link>` tags from the page shell below — do not use system fonts.

---

## 2. Page Shell

Every page starts with exactly this shell. Replace `<!-- TITLE -->` and `<!-- PAGE CONTENT -->`.

```html
<!DOCTYPE html>
<html lang="de" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><!-- TITLE --> – Deutsch Lernen</title>
    <meta name="description" content="<!-- META DESCRIPTION -->">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Outfit:wght@400;500;600;700;800&display=swap" rel="stylesheet">

    <style>
        /* === DESIGN TOKENS === */
        :root {
            --bg-primary:    #f6f7f9;
            --bg-secondary:  #ffffff;
            --bg-tertiary:   #eef2f6;
            --text-primary:   #111827;
            --text-secondary: #536072;
            --text-muted:     #7b8794;
            --border-color:  #d9e0e8;
            --accent:        #2563eb;
            --accent-hover:  #1d4ed8;
            --accent-soft:   #dbeafe;
            --good:    #15803d;
            --warning: #b45309;
            --shadow: 0 12px 32px rgb(17 24 39 / 0.08);
            /* Grammar Highlighting */
            --hl-masc:#1a73e8; --hl-fem:#d93025; --hl-neut:#188038; --hl-plur:#a142f4;
            --hl-verb:#4b0082; --hl-insep-color:#5f6368; --hl-insep-border:#9aa0a6;
            --hl-dat-border:#8ab4f8; --hl-akk-border:#81c995;
            --hl-conj-bg:#ffe082; --hl-conj-color:#111827; --hl-subord-border:#fbc02d;
        }
        html[data-theme="dark"] {
            --bg-primary:    #0d1117;
            --bg-secondary:  #151b23;
            --bg-tertiary:   #1f2937;
            --text-primary:   #f3f4f6;
            --text-secondary: #a7b0bd;
            --text-muted:     #7d8794;
            --border-color:  #2f3a48;
            --accent:        #60a5fa;
            --accent-hover:  #93c5fd;
            --accent-soft:   #172554;
            --good:    #4ade80;
            --warning: #fbbf24;
            --shadow: 0 18px 44px rgb(0 0 0 / 0.35);
            /* Grammar Highlighting */
            --hl-masc:#60a5fa; --hl-fem:#f87171; --hl-neut:#4ade80; --hl-plur:#c084fc;
            --hl-verb:#a78bfa; --hl-insep-color:#9ca3af; --hl-insep-border:#6b7280;
            --hl-dat-border:#93c5fd; --hl-akk-border:#86efac;
            --hl-conj-bg:#4a3500; --hl-conj-color:#fde68a; --hl-subord-border:#fcd34d;
        }

        /* === BASE === */
        *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            min-height: 100vh;
            font-family: 'Inter', sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            transition: background-color 0.2s, color 0.2s;
        }

        a { color: inherit; }

        h1, h2, h3, h4, .font-display { font-family: 'Outfit', sans-serif; }

        h1 { font-size: clamp(1.75rem, 4vw, 3rem); line-height: 1.1; }
        h2 { font-size: 1.35rem; }
        h3 { font-size: 1.1rem; }

        /* === LAYOUT === */
        .page {
            width: min(980px, calc(100% - 32px));
            margin: 0 auto;
            padding: 28px 0 48px;
        }

        /* === THEME TOGGLE ICON === */
        .icon-sun { display: none; }
        html[data-theme="light"] .icon-moon { display: none; }
        html[data-theme="light"] .icon-sun  { display: block; }

        @media (max-width: 560px) {
            .page { width: min(100% - 24px, 980px); padding-top: 18px; }
        }

        /* === PAGE-SPECIFIC STYLES BELOW === */
    </style>
</head>
<body>
    <div class="page">
        <!-- TOPBAR (see Section 3) -->

        <main>
            <!-- PAGE CONTENT -->
        </main>

        <!-- FOOTER (see Section 8) -->
    </div>

    <!-- THEME TOGGLE SCRIPT (see Section 9) -->
</body>
</html>
```

---

## 3. Topbar Component

All inner pages (anything that is not `docs/index.html`) use the topbar with a back link to the index.

```html
<style>
    .topbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 20px;
        padding-bottom: 22px;
        border-bottom: 1px solid var(--border-color);
        margin-bottom: 28px;
    }

    .nav-link {
        color: var(--accent);
        font-size: 0.9rem;
        font-weight: 600;
        text-decoration: none;
    }
    .nav-link:hover { text-decoration: underline; }

    .btn-theme {
        width: 40px;
        height: 40px;
        border-radius: 8px;
        border: 1px solid var(--border-color);
        background-color: var(--bg-secondary);
        color: var(--text-primary);
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        outline: none;
        box-shadow: var(--shadow);
    }
    .btn-theme:hover { border-color: var(--accent); }
</style>

<header class="topbar">
    <a href="../" class="nav-link">← Zurück zur Übersicht</a>
    <button class="btn-theme" onclick="toggleTheme()" aria-label="Theme umschalten">
        <svg class="icon-moon" width="20" height="20" fill="currentColor" viewBox="0 0 24 24"><path d="M12 3a9 9 0 1 0 9 9c0-.46-.04-.92-.1-1.36a5.38 5.38 0 0 1-4.4 2.26 5.4 5.4 0 0 1-4.14-9.5c.3-.08.58-.14.88-.16-.42-.16-.86-.24-1.24-.24z"/></svg>
        <svg class="icon-sun"  width="20" height="20" fill="currentColor" viewBox="0 0 24 24"><path d="M12 7a5 5 0 1 0 0 10 5 5 0 0 0 0-10zm0-5a1 1 0 0 1 1 1v2a1 1 0 0 1-2 0V3a1 1 0 0 1 1-1zm0 16a1 1 0 0 1 1 1v2a1 1 0 0 1-2 0v-2a1 1 0 0 1 1-1zM5.64 5.64a1 1 0 0 1 1.41 0l1.42 1.42a1 1 0 0 1-1.42 1.42L5.64 7.05a1 1 0 0 1 0-1.41zm11.31 11.31a1 1 0 0 1 1.42 0l1.41 1.41a1 1 0 0 1-1.41 1.42l-1.41-1.42a1 1 0 0 1 0-1.41zM2 12a1 1 0 0 1 1-1h2a1 1 0 0 1 0 2H3a1 1 0 0 1-1-1zm16 0a1 1 0 0 1 1-1h2a1 1 0 0 1 0 2h-2a1 1 0 0 1-1-1zM7.05 18.36a1 1 0 0 1 0 1.42l-1.42 1.41a1 1 0 0 1-1.41-1.41l1.42-1.42a1 1 0 0 1 1.41 0zm11.31-11.3a1 1 0 0 1 0-1.42l1.42-1.41a1 1 0 0 1 1.41 1.41l-1.42 1.42a1 1 0 0 1-1.41 0z"/></svg>
    </button>
</header>
```

**Index page topbar** (for `docs/index.html` only — no back link, shows brand instead):

```html
<header class="topbar">
    <div class="brand">
        <div class="eyebrow">Deutsch Notizen</div>
        <h1>Artefakte</h1>
    </div>
    <!-- btn-theme as above -->
</header>
```

Additional CSS for the index topbar:
```css
.brand    { display: flex; flex-direction: column; gap: 5px; }
.eyebrow  { font-size: 0.76rem; font-weight: 800; letter-spacing: 0.12em;
            text-transform: uppercase; color: var(--accent); }
```

---

## 4. Index Artifact List

Used only in `docs/index.html`. Each row is driven by the manifest fields.

```html
<style>
    .section {
        padding: 26px 0;
        border-top: 1px solid var(--border-color);
    }
    .section-header {
        display: flex;
        align-items: baseline;
        justify-content: space-between;
        gap: 18px;
        margin-bottom: 14px;
    }
    .section-note { color: var(--text-muted); font-size: 0.86rem; }

    .artifact-list {
        border: 1px solid var(--border-color);
        border-radius: 8px;
        overflow: hidden;
        background: var(--bg-secondary);
    }
    .artifact-row {
        display: grid;
        grid-template-columns: 150px minmax(0, 1fr) 138px;
        gap: 18px;
        align-items: center;
        padding: 17px 18px;
        text-decoration: none;
        border-top: 1px solid var(--border-color);
    }
    .artifact-row:first-child { border-top: 0; }
    .artifact-row:hover       { background: var(--bg-tertiary); }

    .artifact-type   { color: var(--text-muted); font-size: 0.78rem; font-weight: 800;
                       letter-spacing: 0.08em; text-transform: uppercase; }
    .artifact-title  { display: block; font-weight: 700; color: var(--text-primary); margin-bottom: 4px; }
    .artifact-desc   { color: var(--text-secondary); line-height: 1.55; font-size: 0.93rem; }
    .artifact-action { justify-self: end; color: var(--accent); font-size: 0.88rem; font-weight: 700; }

    @media (max-width: 820px) {
        .artifact-row    { grid-template-columns: 1fr; gap: 8px; }
        .artifact-action { justify-self: start; }
    }
</style>

<!-- One .artifact-row per manifest entry with status: published -->
<!-- type value → display label: app→App, story→Story, reference→Referenz -->
<section class="section" aria-labelledby="artifact-heading">
    <div class="section-header">
        <h2 id="artifact-heading">Artefaktliste</h2>
        <span class="section-note">sortiert nach Nutzung</span>
    </div>
    <div class="artifact-list">
        <a href="<!-- output path relative to docs/ -->" class="artifact-row">
            <span class="artifact-type"><!-- type label --></span>
            <span>
                <span class="artifact-title"><!-- title --></span>
                <span class="artifact-desc"><!-- description --></span>
            </span>
            <span class="artifact-action"><!-- action_label --></span>
        </a>
        <!-- repeat for each published entry -->
    </div>
</section>
```

---

## 5. Section & Section Header

Use `.section` to divide page content into visually distinct blocks. Every section needs an `aria-labelledby` pointing to its heading id.

```html
<style>
    .section {
        padding: 26px 0;
        border-top: 1px solid var(--border-color);
    }
    .section-header {
        display: flex;
        align-items: baseline;
        justify-content: space-between;
        gap: 18px;
        margin-bottom: 14px;
    }
    .section-note { color: var(--text-muted); font-size: 0.86rem; }
</style>

<section class="section" aria-labelledby="section-id">
    <div class="section-header">
        <h2 id="section-id">Abschnittstitel</h2>
        <span class="section-note">Optionaler Hinweis</span>
    </div>
    <!-- section body -->
</section>
```

---

## 6. Story / Reading Text Block

For annotated German reading texts. The `.story-body` class sets comfortable line-height and font-size for long-form reading. Inline grammar highlights are applied using `<span>` tags per [`highlighting_strategy.md`](highlighting_strategy.md).

```html
<style>
    .story-body {
        font-size: 1.05rem;
        line-height: 1.9;
        color: var(--text-primary);
        background: var(--bg-secondary);
        border: 1px solid var(--border-color);
        border-radius: 8px;
        padding: 24px 28px;
    }
    .story-body p { margin-bottom: 1.1em; }
    .story-body p:last-child { margin-bottom: 0; }

    /* When grammar highlighting is active, keep colours theme-aware.
       Never use hardcoded hex here — always use design token variables. */
    .story-text.is-highlighted,
    .story-body.is-highlighted {
        color: var(--text-primary);
        background: var(--bg-secondary);
        border: 1px solid var(--border-color);
        border-radius: 8px;
        padding: 18px;
    }

    .story-meta {
        display: flex;
        gap: 12px;
        flex-wrap: wrap;
        margin-bottom: 16px;
        font-size: 0.82rem;
        color: var(--text-muted);
    }
    .story-badge {
        background: var(--bg-tertiary);
        border: 1px solid var(--border-color);
        border-radius: 4px;
        padding: 2px 8px;
        font-weight: 600;
        letter-spacing: 0.05em;
        text-transform: uppercase;
    }

    /* Toggle button for grammar highlights */
    .btn-toggle {
        display: inline-flex;
        align-items: center;
        gap: 8px;
        padding: 7px 14px;
        border-radius: 6px;
        border: 1px solid var(--border-color);
        background: var(--bg-secondary);
        color: var(--text-primary);
        font-size: 0.88rem;
        font-weight: 600;
        cursor: pointer;
    }
    .btn-toggle:hover { border-color: var(--accent); color: var(--accent); }
    .btn-toggle.active { background: var(--accent-soft); border-color: var(--accent); color: var(--accent); }

    /* Layout shell with sidebar and content */
    .story-shell {
        display: grid;
        grid-template-columns: 230px minmax(0, 1fr);
        gap: 22px;
        align-items: start;
        border-top: 1px solid var(--border-color);
        padding-top: 26px;
    }
    .story-controls {
        border: 1px solid var(--border-color);
        background: var(--bg-secondary);
        border-radius: 8px;
        padding: 16px;
        position: sticky;
        top: 20px;
    }
    .toggle-container {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 12px;
        color: var(--text-secondary);
        font-size: 0.88rem;
        font-weight: 650;
    }

    /* Toggle Switch */
    .switch {
        position: relative;
        display: inline-block;
        width: 44px;
        height: 24px;
        flex: 0 0 auto;
    }
    .switch input { opacity: 0; width: 0; height: 0; }
    .slider {
        position: absolute;
        cursor: pointer;
        inset: 0;
        background-color: var(--border-color);
        transition: 0.2s;
        border-radius: 24px;
    }
    .slider:before {
        position: absolute;
        content: "";
        width: 18px;
        height: 18px;
        left: 3px;
        bottom: 3px;
        background-color: #fff;
        transition: 0.2s;
        border-radius: 50%;
    }
    input:checked + .slider { background-color: var(--accent); }
    input:checked + .slider:before { transform: translateX(20px); }

    /* Comprehensive Legend Styling */
    .legend {
        display: grid;
        gap: 9px;
        margin-top: 18px;
        color: var(--text-secondary);
        font-size: 0.83rem;
    }
    .legend-group-title {
        font-size: 0.7rem;
        font-weight: 800;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--text-muted);
        margin-top: 14px;
        margin-bottom: 4px;
        border-bottom: 1px solid var(--border-color);
        padding-bottom: 3px;
    }
    .legend-group-title:first-of-type { margin-top: 8px; }
    .legend-item {
        display: flex;
        align-items: center;
        gap: 8px;
    }
    .legend-swatch {
        width: 16px;
        height: 16px;
        border-radius: 3px;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        flex: 0 0 auto;
        font-size: 0.65rem;
        font-weight: bold;
    }
    .legend-swatch.masc      { background: var(--hl-masc); }
    .legend-swatch.fem       { background: var(--hl-fem); }
    .legend-swatch.neut      { background: var(--hl-neut); }
    .legend-swatch.plur      { background: var(--hl-plur); }
    .legend-swatch.verb {
        background: transparent;
        color: var(--hl-verb);
        border-bottom: 2px dotted var(--hl-verb);
        border-radius: 0;
    }
    .legend-swatch.pref-sep {
        background: transparent;
        border-bottom: 1px dashed var(--hl-verb);
        border-radius: 0;
    }
    .legend-swatch.pref-insep {
        background: transparent;
        color: var(--hl-insep-color);
        border-bottom: 1px dotted var(--hl-insep-border);
        border-radius: 0;
    }
    .legend-swatch.dativ {
        background: transparent;
        border-bottom: 2.5px solid var(--hl-dat-border);
        border-radius: 0;
        height: 12px;
    }
    .legend-swatch.akkusativ {
        background: transparent;
        border-bottom: 2.5px solid var(--hl-akk-border);
        border-radius: 0;
        height: 12px;
    }
    .legend-swatch.conj {
        background: var(--hl-conj-bg);
        color: var(--hl-conj-color);
        border-radius: 3px;
        font-size: 0.6rem;
        padding: 0 2px;
    }
    .legend-swatch.sub-verb {
        background: transparent;
        border-bottom: 2px double var(--hl-subord-border);
        border-radius: 0;
        height: 12px;
    }
    .legend-swatch.ending {
        background: transparent;
        font-style: italic;
        font-weight: bold;
        opacity: 0.75;
        color: var(--text-primary);
    }
    .legend-swatch.suffix {
        background: transparent;
        font-style: italic;
        opacity: 0.6;
        color: var(--text-primary);
    }
    .legend-swatch.mutation {
        background: transparent;
        color: var(--hl-fem);
        font-weight: bold;
    }

    @media (max-width: 760px) {
        .story-shell { grid-template-columns: 1fr; }
        .story-controls { position: static; }
    }
</style>

<div class="story-meta">
    <span class="story-badge">A2/B1</span>
    <span class="story-badge">Lesetext</span>
</div>

<section class="story-shell" aria-label="Story mit Markierungen">
    <aside class="story-controls">
        <div class="toggle-container">
            <span>Grammatik markieren</span>
            <label class="switch">
                <input type="checkbox" id="highlightToggle" onchange="toggleHighlight()">
                <span class="slider"></span>
            </label>
        </div>
        <div class="legend" aria-label="Markierungslegende">
            <div class="legend-group-title">Nomen & Plural</div>
            <div class="legend-item"><span class="legend-swatch masc"></span><span>Maskulin (der)</span></div>
            <div class="legend-item"><span class="legend-swatch fem"></span><span>Feminin (die)</span></div>
            <div class="legend-item"><span class="legend-swatch neut"></span><span>Neutral (das)</span></div>
            <div class="legend-item"><span class="legend-swatch plur"></span><span>Plural</span></div>
            
            <div class="legend-group-title">Verben & Präfixe</div>
            <div class="legend-item"><span class="legend-swatch verb">V</span><span>Verb / Partizip</span></div>
            <div class="legend-item"><span class="legend-swatch pref-sep">um</span><span>Trennbares Präfix</span></div>
            <div class="legend-item"><span class="legend-swatch pref-insep">be</span><span>Untrennbares Präfix</span></div>
            
            <div class="legend-group-title">Kasus (Phrasen)</div>
            <div class="legend-item"><span class="legend-swatch dativ"></span><span>Dativ-Phrase</span></div>
            <div class="legend-item"><span class="legend-swatch akkusativ"></span><span>Akkusativ-Phrase</span></div>
            
            <div class="legend-group-title">Nebensätze</div>
            <div class="legend-item"><span class="legend-swatch conj">weil</span><span>Konjunktion</span></div>
            <div class="legend-item"><span class="legend-swatch sub-verb">ist</span><span>Nebensatz-Verb</span></div>
            
            <div class="legend-group-title">Endungen & Details</div>
            <div class="legend-item"><span class="legend-swatch ending">-er</span><span>Deklinationsendung</span></div>
            <div class="legend-item"><span class="legend-swatch suffix">-ung</span><span>Nomen-Suffix</span></div>
            <div class="legend-item"><span class="legend-swatch mutation">ä</span><span>Vokalwechsel (Umlaut)</span></div>
        </div>
    </aside>

    <article class="story-card">
        <div class="story-kicker">Story</div>
        <h2 class="story-title"><!-- Story-Titel --></h2>
        <p class="story-body" id="storyText">
            <!-- Text content goes here -->
        </p>
    </article>
</section>
```

---

## 7. Callout Boxes

Use for grammar notes, tips, or warnings inside a page.

```html
<style>
    .callout {
        border-left: 3px solid var(--border-color);
        background: var(--bg-secondary);
        border-radius: 0 6px 6px 0;
        padding: 14px 18px;
        margin: 16px 0;
        font-size: 0.93rem;
        line-height: 1.6;
    }
    .callout-note { border-left-color: var(--accent); }
    .callout-tip  { border-left-color: var(--good); }
    .callout-warn { border-left-color: var(--warning); }
    .callout-label {
        font-weight: 700;
        font-size: 0.78rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        margin-bottom: 6px;
        color: var(--text-muted);
    }
</style>

<!-- Note -->
<div class="callout callout-note">
    <div class="callout-label">Hinweis</div>
    <!-- content -->
</div>

<!-- Tip -->
<div class="callout callout-tip">
    <div class="callout-label">Tipp</div>
    <!-- content -->
</div>

<!-- Warning -->
<div class="callout callout-warn">
    <div class="callout-label">Achtung</div>
    <!-- content -->
</div>
```

---

## 8. Footer

Paste at the bottom of every page, inside `.page`, after `<main>`.

```html
<style>
    footer {
        border-top: 1px solid var(--border-color);
        padding-top: 22px;
        color: var(--text-muted);
        font-size: 0.84rem;
    }
</style>

<footer>
    <p>Erstellt für strukturierte Deutschpraxis – Stand: <!-- Month Year --></p>
</footer>
```

---

## 9. Theme Toggle Script

Paste at the end of `<body>` on every page. Reads from `localStorage` so the user's preference persists across pages.

```html
<script>
    const storedTheme = localStorage.getItem("theme") || "dark";
    document.documentElement.setAttribute("data-theme", storedTheme);

    function toggleTheme() {
        const current = document.documentElement.getAttribute("data-theme");
        const next    = current === "dark" ? "light" : "dark";
        document.documentElement.setAttribute("data-theme", next);
        localStorage.setItem("theme", next);
    }
</script>
```

---

## 10. Page Type Templates

### Type: `story`
File location: `docs/stories/<slug>.html`
Structure:
1. Page shell with topbar (back link → `../`)
2. `<h1>` story title
3. Story meta badges (level, type)
4. Optional: grammar toggle button(s)
5. `.story-body` with annotated paragraphs
6. Optional: callout boxes for grammar notes
7. Footer

### Type: `app`
File location: `docs/<app-name>/index.html`
Structure: Custom — can have sidebar, search, etc. Must still use the design tokens and fonts. Back link in topbar required.

### Type: `reference`
File location: `docs/reference/<slug>.html` *(if a reference ever needs to be a published HTML page)*
Structure:
1. Page shell with topbar (back link)
2. `<h1>` title
3. Sections using `.section` + `.section-header`
4. Tables using standard HTML `<table>` with border-color tokens
5. Footer

---

## 11. File Placement Rules

| Content type | Location in `docs/` |
| :--- | :--- |
| Index / home | `docs/index.html` |
| Story / reading text | `docs/stories/<slug>.html` |
| Interactive app | `docs/<app-name>/index.html` |
| Reference page (HTML) | `docs/reference/<slug>.html` |

Slugs must be lowercase, hyphen-separated, and in German (e.g. `ein-ruhiger-morgen-in-zuerich`).

All paths in `docs/index.html` are relative to `docs/` (e.g. `href="stories/ein-ruhiger-morgen-in-zuerich.html"`).
All back-links from inner pages point to `../` (one level up to `docs/`).
