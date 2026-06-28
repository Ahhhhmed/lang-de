# German Text Highlighting Strategy for Learning Assistance

This document defines the visual highlighting strategy used when generating or annotating German texts for reading practice. It covers both **light mode** and **dark mode** values.

All highlight colours are exposed as CSS custom properties (see the variable reference below). Inline `<span>` styles must use `var(--hl-xxx)` — **never hardcode hex values** in published HTML, so that dark mode works automatically.

---

## 🎨 Style Specification

| Concept | Target / Rule | CSS Variable(s) | Light Value | Dark Value |
| :--- | :--- | :--- | :--- | :--- |
| **Masculine Noun** | Noun with *der* gender | `--hl-masc` | `#1a73e8` | `#60a5fa` |
| **Feminine Noun** | Noun with *die* gender | `--hl-fem` | `#d93025` | `#f87171` |
| **Neuter Noun** | Noun with *das* gender | `--hl-neut` | `#188038` | `#4ade80` |
| **Plural Noun** | Noun in plural form | `--hl-plur` | `#a142f4` | `#c084fc` |
| **Verb Parts** | Verb stems, auxiliaries, participles, reflexives | `--hl-verb` (color + border) | `#4b0082` | `#a78bfa` |
| **Separable Prefix (Attached)** | Prefix part of a compound verb when not split | `--hl-verb` (border only) | `#4b0082` | `#a78bfa` |
| **Separable Prefix (Split)** | Prefix at the end of a clause | `--hl-verb` (color + border) | `#4b0082` | `#a78bfa` |
| **Inseparable Prefix** | `ver-`, `be-`, `emp-`, `ent-` | `--hl-insep-color`, `--hl-insep-border` | `#5f6368` / `#9aa0a6` | `#9ca3af` / `#6b7280` |
| **Dative Phrase** | Whole phrase governing Dativ | `--hl-dat-border` | `#8ab4f8` | `#93c5fd` |
| **Accusative Phrase** | Whole phrase governing Akkusativ | `--hl-akk-border` | `#81c995` | `#86efac` |
| **Declension Ending** | Suffix on articles and adjectives | *(no colour — opacity only)* | — | — |
| **Subordinating Conjunction** | Conjunction triggering verb-last order | `--hl-conj-bg`, `--hl-conj-color` | `#ffe082` / `#111827` | `#4a3500` / `#fde68a` |
| **Subordinated Verb** | Conjugated verb at end of subordinate clause | `--hl-subord-border` | `#fbc02d` | `#fcd34d` |
| **Noun Gender Suffix** | `-ung`, `-heit`, `-keit`, `-schaft`, `-in` | *(no colour — opacity only)* | — | — |
| **Vowel / Umlaut Mutation** | Changed letter in present tense, plural, or participle | `--hl-fem` (shared) | `#d93025` | `#f87171` |

---

## 🎨 CSS Variables Quick Reference

Add these to both `:root` and `html[data-theme="dark"]` in every page that uses highlighting. See `html_templates.md` — they are already included in the design token block.

```css
/* === GRAMMAR HIGHLIGHTING — LIGHT MODE (:root) === */
--hl-masc:          #1a73e8;   /* der-nouns — blue */
--hl-fem:           #d93025;   /* die-nouns + mutation — red */
--hl-neut:          #188038;   /* das-nouns — green */
--hl-plur:          #a142f4;   /* plural nouns — purple */
--hl-verb:          #4b0082;   /* verbs + separable prefixes — indigo */
--hl-insep-color:   #5f6368;   /* inseparable prefix text — grey */
--hl-insep-border:  #9aa0a6;   /* inseparable prefix underline */
--hl-dat-border:    #8ab4f8;   /* dative phrase underline — light blue */
--hl-akk-border:    #81c995;   /* accusative phrase underline — light green */
--hl-conj-bg:       #ffe082;   /* subordinating conjunction background — amber */
--hl-conj-color:    #111827;   /* subordinating conjunction text */
--hl-subord-border: #fbc02d;   /* subordinated verb double-underline */

/* === GRAMMAR HIGHLIGHTING — DARK MODE (html[data-theme="dark"]) === */
--hl-masc:          #60a5fa;   /* der-nouns — lighter blue */
--hl-fem:           #f87171;   /* die-nouns + mutation — lighter red */
--hl-neut:          #4ade80;   /* das-nouns — lighter green */
--hl-plur:          #c084fc;   /* plural nouns — lighter purple */
--hl-verb:          #a78bfa;   /* verbs + separable prefixes — violet */
--hl-insep-color:   #9ca3af;   /* inseparable prefix text — lighter grey */
--hl-insep-border:  #6b7280;   /* inseparable prefix underline */
--hl-dat-border:    #93c5fd;   /* dative phrase underline */
--hl-akk-border:    #86efac;   /* accusative phrase underline */
--hl-conj-bg:       #4a3500;   /* subordinating conjunction background — dark amber */
--hl-conj-color:    #fde68a;   /* subordinating conjunction text — light amber */
--hl-subord-border: #fcd34d;   /* subordinated verb double-underline */
```

---

## 🛠 Inline Span Patterns

Use these exact patterns in inline `style` attributes. All colours must go through CSS variables.

### Noun Genders
```html
<!-- Masculine (der) -->
<span style="color:var(--hl-masc); font-weight:bold;">Tisch</span>

<!-- Feminine (die) -->
<span style="color:var(--hl-fem); font-weight:bold;">Tür</span>

<!-- Neuter (das) -->
<span style="color:var(--hl-neut); font-weight:bold;">Bett</span>

<!-- Plural -->
<span style="color:var(--hl-plur); font-weight:bold;">Möbel</span>
```

### Verbs
```html
<!-- Verb part (stem, auxiliary, participle, reflexive) -->
<span style="color:var(--hl-verb); font-weight:bold; border-bottom:2px dotted var(--hl-verb);">hat</span>

<!-- Separable prefix — attached form -->
<span style="border-bottom:1px dashed var(--hl-verb);">um</span>ziehen

<!-- Separable prefix — split (at clause end) -->
... lädt ... <span style="color:var(--hl-verb); font-style:italic; border-bottom:2px dotted var(--hl-verb);">ein</span>

<!-- Inseparable prefix -->
<span style="color:var(--hl-insep-color); border-bottom:1px dotted var(--hl-insep-border);">ver</span>kaufen
```

### Case Phrases
```html
<!-- Dative phrase -->
<span style="border-bottom:2px solid var(--hl-dat-border); padding-bottom:1px;">in einer WG</span>

<!-- Accusative phrase -->
<span style="border-bottom:2px solid var(--hl-akk-border); padding-bottom:1px;">auf den Tisch</span>
```

### Declension & Mutation
```html
<!-- Declension ending (no colour — works in both themes unchanged) -->
ein<span style="font-weight:bold; font-style:italic; opacity:0.75;">er</span>

<!-- Noun gender suffix -->
Wohn<span style="font-style:italic; opacity:0.6;">ung</span>

<!-- Vowel / umlaut mutation (shares --hl-fem) -->
s<span style="color:var(--hl-fem); font-weight:bold;">ie</span>ht
```

### Clause Structure
```html
<!-- Subordinating conjunction -->
<span style="background-color:var(--hl-conj-bg); color:var(--hl-conj-color); padding:0 4px; border-radius:3px; font-weight:bold;">weil</span>

<!-- Subordinated verb (verb-last in subordinate clause) -->
<span style="font-style:italic; border-bottom:2px double var(--hl-subord-border);">bin</span>
```

---

## 🛠 Guidelines for Nested Styling

When applying these rules, styles will often overlap. Apply nesting logically:

1. **Case Phrase Outer Boundary**: Dativ and Akkusativ must be marked separately — blue underline for Dativ, green for Akkusativ. The underline wraps the *entire* phrase.
2. **Inflection Suffixes**: Inside the phrase, article and adjective suffixes get their bold/italic styling.
3. **Noun Gender**: Inside the phrase, the noun stem gets its gender colour via `var(--hl-masc/fem/neut/plur)`.
4. **Verbs in Participles**: A verb phrase is wrapped in the verb style (dotted underline via `var(--hl-verb)`), but internal prefixes or mutations get their respective nested styles.

### Nested HTML Example

```html
<!-- Dative phrase: possessive + adjective with dative endings + masculine noun -->
<span style="border-bottom:2px solid var(--hl-dat-border); padding-bottom:1px;">
  mit mein<span style="font-weight:bold; font-style:italic; opacity:0.75;">em</span>
  gross<span style="font-weight:bold; font-style:italic; opacity:0.75;">en</span>
  <span style="color:var(--hl-masc); font-weight:bold;">Bruder</span>
</span>
```

---

## 📖 Complete Annotated Example

**Source Text:**
> "Ich wohne in einer WG am Stadtrand. Gestern bin ich umgezogen. Weil ich viele Möbel habe, hat mir mein Bruder geholfen."

**Annotated HTML:**
```html
Ich wohne
<span style="border-bottom:2px solid var(--hl-dat-border); padding-bottom:1px;">in ein<span style="font-weight:bold; font-style:italic; opacity:0.75;">er</span> <span style="color:var(--hl-fem); font-weight:bold;">Wohn-gemein-<span style="font-style:italic; opacity:0.6;">schaft</span></span></span>
<span style="border-bottom:2px solid var(--hl-dat-border); padding-bottom:1px;">am <span style="color:var(--hl-masc); font-weight:bold;">Stadtrand</span></span>.
Gestern
<span style="color:var(--hl-verb); font-weight:bold; border-bottom:2px dotted var(--hl-verb);">bin</span> ich
<span style="color:var(--hl-verb); font-weight:bold; border-bottom:2px dotted var(--hl-verb);"><span style="border-bottom:1px dashed var(--hl-verb);">um</span>gez<span style="color:var(--hl-fem); font-weight:bold;">o</span>gen</span>.
<span style="background-color:var(--hl-conj-bg); color:var(--hl-conj-color); padding:0 4px; border-radius:3px; font-weight:bold;">Weil</span> ich viele
<span style="color:var(--hl-plur); font-weight:bold;">Möbel</span>
<span style="font-style:italic; border-bottom:2px double var(--hl-subord-border);">habe</span>,
<span style="color:var(--hl-verb); font-weight:bold; border-bottom:2px dotted var(--hl-verb);">hat</span> mir mein
<span style="color:var(--hl-masc); font-weight:bold;">Bruder</span>
<span style="color:var(--hl-verb); font-weight:bold; border-bottom:2px dotted var(--hl-verb);">geh<span style="color:var(--hl-fem); font-weight:bold;">o</span>lfen</span>.
```
