# German Text Highlighting Strategy for Learning Assistance

This document defines the visual highlighting strategy to be used by agents when generating or annotating German texts for reading practice. The goal is to help A1/A2 learners visually parse sentence structure, identify word types, recognize grammatical gender, and track declension markers.

---

## 🎨 Style Specification

All styling must be applied using inline HTML `<span>` tags with `style` attributes to ensure compatibility with Markdown-rendered HTML.

| Concept | Target / Rule | CSS Styling | HTML Example | Rendered Example |
| :--- | :--- | :--- | :--- | :--- |
| **Masculine Noun** | Noun with *der* gender | `color: #1a73e8; font-weight: bold;` | `<span style="color:#1a73e8; font-weight:bold;">Tisch</span>` | <span style="color:#1a73e8; font-weight:bold;">Tisch</span> |
| **Feminine Noun** | Noun with *die* gender | `color: #d93025; font-weight: bold;` | `<span style="color:#d93025; font-weight:bold;">Tür</span>` | <span style="color:#d93025; font-weight:bold;">Tür</span> |
| **Neuter Noun** | Noun with *das* gender | `color: #188038; font-weight: bold;` | `<span style="color:#188038; font-weight:bold;">Bett</span>` | <span style="color:#188038; font-weight:bold;">Bett</span> |
| **Plural Noun** | Noun in plural form | `color: #a142f4; font-weight: bold;` | `<span style="color:#a142f4; font-weight:bold;">Möbel</span>` | <span style="color:#a142f4; font-weight:bold;">Möbel</span> |
| **Verb Parts** | Verb stems, auxiliaries, participles, reflexives | `color: #4b0082; font-weight: bold; border-bottom: 2px dotted #4b0082;` | `<span style="color:#4b0082; font-weight:bold; border-bottom:2px dotted #4b0082;">hat</span> ... <span style="color:#4b0082; font-weight:bold; border-bottom:2px dotted #4b0082;">geholfen</span>` | <span style="color:#4b0082; font-weight:bold; border-bottom:2px dotted #4b0082;">hat</span> ... <span style="color:#4b0082; font-weight:bold; border-bottom:2px dotted #4b0082;">geholfen</span> |
| **Separable Prefix (Attached)** | Prefix part of a compound verb when not split | `border-bottom: 1px dashed #4b0082;` | `<span style="border-bottom:1px dashed #4b0082;">um</span>ziehen` | <span style="border-bottom:1px dashed #4b0082;">um</span>ziehen |
| **Separable Prefix (Split)** | Prefix at the end of a clause | `color: #4b0082; font-style: italic; border-bottom: 2px dotted #4b0082;` | `... lädt ... <span style="color:#4b0082; font-style:italic; border-bottom:2px dotted #4b0082;">ein</span>` | ... lädt ... <span style="color:#4b0082; font-style:italic; border-bottom:2px dotted #4b0082;">ein</span> |
| **Inseparable Prefix** | `ver-`, `be-`, `emp-`, `ent-` | `border-bottom: 1px dotted #9aa0a6; color: #5f6368;` | `<span style="border-bottom:1px dotted #9aa0a6; color:#5f6368;">ver</span>kaufen` | <span style="border-bottom:1px dotted #9aa0a6; color:#5f6368;">ver</span>kaufen |
| **Dative Phrase** | Whole prepositional or object phrase governing Dativ. Keep visually distinct from Akkusativ. | `border-bottom: 2px solid #8ab4f8; padding-bottom: 1px;` | `<span style="border-bottom:2px solid #8ab4f8; padding-bottom:1px;">in einer WG</span>` | <span style="border-bottom:2px solid #8ab4f8; padding-bottom:1px;">in einer WG</span> |
| **Accusative Phrase** | Whole prepositional or object phrase governing Akkusativ. Keep visually distinct from Dativ. | `border-bottom: 2px solid #81c995; padding-bottom: 1px;` | `<span style="border-bottom:2px solid #81c995; padding-bottom:1px;">auf den Tisch</span>` | <span style="border-bottom:2px solid #81c995; padding-bottom:1px;">auf den Tisch</span> |
| **Declension Ending** | Suffix on articles and adjectives (`-e`, `-en`, `-em`, `-er`, `-es`) | `font-weight: bold; font-style: italic; opacity: 0.75;` | `ein<span style="font-weight:bold; font-style:italic; opacity:0.75;">er</span>` | ein<span style="font-weight:bold; font-style:italic; opacity:0.75;">er</span> |
| **Subordinating Conjunction** | Conjunction triggering verb-last order | `background-color: #ffe082; padding: 0 4px; border-radius: 3px; font-weight: bold;` | `<span style="background-color:#ffe082; padding:0 4px; border-radius:3px; font-weight:bold;">weil</span>` | <span style="background-color:#ffe082; padding:0 4px; border-radius:3px; font-weight:bold;">weil</span> |
| **Subordinated Verb** | Conjugated verb at the end of a subordinate clause | `font-style: italic; border-bottom: 2px double #fbc02d;` | `<span style="font-style:italic; border-bottom:2px double #fbc02d;">bin</span>` | <span style="font-style:italic; border-bottom:2px double #fbc02d;">bin</span> |
| **Noun Gender Suffix** | `-ung`, `-heit`, `-keit`, `-schaft`, `-in` | `font-style: italic; opacity: 0.6;` | `Wohn<span style="font-style:italic; opacity:0.6;">ung</span>` | Wohn<span style="font-style:italic; opacity:0.6;">ung</span> |
| **Vowel / Umlaut Mutation** | Changed letter in present tense, plural, or participle | `color: #d93025; font-weight: bold;` | `s<span style="color:#d93025; font-weight:bold;">ie</span>ht` | s<span style="color:#d93025; font-weight:bold;">ie</span>ht |

---

## 🛠 Guidelines for Nested Styling

When applying these rules, styles will often overlap. Apply nesting logically:

1.  **Case Phrase Outer Boundary**: Dativ and Akkusativ must be marked separately. Use solid light-blue only for Dativ and solid light-green only for Akkusativ. The underline must wrap the *entire* phrase.
2.  **Inflection Suffixes**: Inside the phrase, article and adjective suffixes get their bold/italic styling.
3.  **Noun Gender**: Inside the phrase, the noun stem gets its gender color.
4.  **Verbs in Participles**: A verb phrase (e.g. *umgezogen*) is wrapped in the verb style (dotted indigo), but internal prefixes or mutations get their respective nested styles.

### Nested HTML Example:
```html
<!-- Dative phrase containing: possessive article with dative ending, adjective with dative ending, masculine noun -->
<span style="border-bottom:2px solid #8ab4f8; padding-bottom:1px;">
  mit mein<span style="font-weight:bold; font-style:italic; opacity:0.75;">em</span> 
  gross<span style="font-weight:bold; font-style:italic; opacity:0.75;">en</span> 
  <span style="color:#1a73e8; font-weight:bold;">Bruder</span>
</span>
```
**Rendered result:**
<span style="border-bottom:2px solid #8ab4f8; padding-bottom:1px;">mit mein<span style="font-weight:bold; font-style:italic; opacity:0.75;">em</span> gross<span style="font-weight:bold; font-style:italic; opacity:0.75;">en</span> <span style="color:#1a73e8; font-weight:bold;">Bruder</span></span>

---

## 📖 Complete Annotated Example

**Source Text:**
> "Ich wohne in einer WG am Stadtrand. Gestern bin ich umgezogen. Weil ich viele Möbel habe, hat mir mein Bruder geholfen."

**Annotated HTML:**
```html
Ich wohne 
<span style="border-bottom:2px solid #8ab4f8; padding-bottom:1px;">in ein<span style="font-weight:bold; font-style:italic; opacity:0.75;">er</span> <span style="color:#d93025; font-weight:bold;">Wohn-gemein-<span style="font-style:italic; opacity:0.6;">schaft</span></span></span> 
<span style="border-bottom:2px solid #8ab4f8; padding-bottom:1px;">am <span style="color:#1a73e8; font-weight:bold;">Stadtrand</span></span>. 
Gestern 
<span style="color:#4b0082; font-weight:bold; border-bottom:2px dotted #4b0082;">bin</span> ich 
<span style="color:#4b0082; font-weight:bold; border-bottom:2px dotted #4b0082;"><span style="border-bottom: 1px dashed #4b0082;">um</span>gez<span style="color:#d93025; font-weight:bold;">o</span>gen</span>. 
<span style="background-color:#ffe082; padding:0 4px; border-radius:3px; font-weight:bold;">Weil</span> ich viele 
<span style="color:#a142f4; font-weight:bold;">Möbel</span> 
<span style="font-style:italic; border-bottom:2px double #fbc02d;">habe</span>, 
<span style="color:#4b0082; font-weight:bold; border-bottom:2px dotted #4b0082;">hat</span> mir mein 
<span style="color:#1a73e8; font-weight:bold;">Bruder</span> 
<span style="color:#4b0082; font-weight:bold; border-bottom:2px dotted #4b0082;">geh<span style="color:#d93025; font-weight:bold;">o</span>lfen</span>.
```
