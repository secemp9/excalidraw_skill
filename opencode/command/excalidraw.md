---
description: Generate Excalidraw diagrams for Obsidian (.md files with full JSON)
---

<task>
Generate Excalidraw diagrams as Obsidian-compatible `.md` files. Analyze the user's content, choose the best diagram type, generate complete Excalidraw JSON with all elements/arrows/text, wrap in Obsidian format, and save to the current working directory.
</task>

<userMessage>$ARGUMENTS</userMessage>


# Excalidraw Diagram Generator for Obsidian

## Overview

This skill generates Excalidraw diagrams from text content, producing Obsidian-compatible `.md` files that render natively in the Obsidian Excalidraw plugin. The generated JSON follows the exact Excalidraw schema used by the excalidraw.com editor and the obsidian-excalidraw-plugin.

## Workflow

1. **Analyze content** -- identify concepts, relationships, and hierarchy in the user's input
2. **Choose diagram type** -- select the best diagram type based on the content (see Diagram Type Selection Guide below)
3. **Generate Excalidraw JSON** -- build the full JSON structure with all elements, arrows, and text
4. **Wrap in Obsidian format** -- produce the complete `.md` file with Excalidraw frontmatter
5. **Save to current working directory** -- write the file automatically
6. **Report to user** -- confirm save location and explain how to view the diagram

## Output Format -- STRICT

Every generated file MUST follow this exact structure. Do not deviate.

```
---
excalidraw-plugin: parsed
tags: [excalidraw]
---
==!!== Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ==!!== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'

# Excalidraw Data

## Text Elements
%%
## Drawing
```json
{Complete JSON data here}
```
%%
```

**Critical rules for the output format:**
- Frontmatter MUST include `excalidraw-plugin: parsed` and `tags: [excalidraw]`
- The warning message MUST be present and complete (use the unicode warning sign)
- The JSON block MUST be enclosed between `%%` markers
- The `## Text Elements` section MUST be left empty -- the Excalidraw plugin auto-fills it from JSON data
- Do NOT use any frontmatter keys other than `excalidraw-plugin` and `tags`

**IMPORTANT:** In the actual output file, replace `==!!==` with the real warning emoji character followed by a space. The warning line should read:
`==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'`

## Minimal Complete Example (Quick Start)

Here is a complete, copy-paste-ready `.md` file containing a simple 3-box flowchart:

```
---
excalidraw-plugin: parsed
tags: [excalidraw]
---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'

# Excalidraw Data

## Text Elements
%%
## Drawing
```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://github.com/zsviczian/obsidian-excalidraw-plugin",
  "elements": [
    {
      "id": "box1",
      "type": "rectangle",
      "x": 100,
      "y": 100,
      "width": 160,
      "height": 50,
      "angle": 0,
      "strokeColor": "#1971c2",
      "backgroundColor": "#a5d8ff",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "groupIds": [],
      "frameId": null,
      "index": "a0",
      "roundness": { "type": 3 },
      "seed": 100000001,
      "version": 1,
      "versionNonce": 200000001,
      "isDeleted": false,
      "boundElements": [
        { "id": "box1-text", "type": "text" },
        { "id": "arrow1", "type": "arrow" }
      ],
      "updated": 1700000000000,
      "link": null,
      "locked": false
    },
    {
      "id": "box1-text",
      "type": "text",
      "x": 105,
      "y": 105,
      "width": 150,
      "height": 25,
      "angle": 0,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "groupIds": [],
      "frameId": null,
      "index": "a1",
      "roundness": null,
      "seed": 100000002,
      "version": 1,
      "versionNonce": 200000002,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1700000000000,
      "link": null,
      "locked": false,
      "text": "Start",
      "rawText": "Start",
      "originalText": "Start",
      "fontSize": 20,
      "fontFamily": 5,
      "textAlign": "center",
      "verticalAlign": "middle",
      "containerId": "box1",
      "autoResize": true,
      "lineHeight": 1.25
    },
    {
      "id": "box2",
      "type": "rectangle",
      "x": 100,
      "y": 250,
      "width": 160,
      "height": 50,
      "angle": 0,
      "strokeColor": "#2f9e44",
      "backgroundColor": "#b2f2bb",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "groupIds": [],
      "frameId": null,
      "index": "a4",
      "roundness": { "type": 3 },
      "seed": 100000005,
      "version": 1,
      "versionNonce": 200000005,
      "isDeleted": false,
      "boundElements": [
        { "id": "box2-text", "type": "text" },
        { "id": "arrow1", "type": "arrow" }
      ],
      "updated": 1700000000000,
      "link": null,
      "locked": false
    },
    {
      "id": "box2-text",
      "type": "text",
      "x": 105,
      "y": 255,
      "width": 150,
      "height": 25,
      "angle": 0,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "groupIds": [],
      "frameId": null,
      "index": "a5",
      "roundness": null,
      "seed": 100000006,
      "version": 1,
      "versionNonce": 200000006,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1700000000000,
      "link": null,
      "locked": false,
      "text": "End",
      "rawText": "End",
      "originalText": "End",
      "fontSize": 20,
      "fontFamily": 5,
      "textAlign": "center",
      "verticalAlign": "middle",
      "containerId": "box2",
      "autoResize": true,
      "lineHeight": 1.25
    },
    {
      "id": "arrow1",
      "type": "arrow",
      "x": 180,
      "y": 150,
      "width": 0,
      "height": 100,
      "angle": 0,
      "strokeColor": "#1e1e1e",
      "backgroundColor": "transparent",
      "fillStyle": "solid",
      "strokeWidth": 2,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "groupIds": [],
      "frameId": null,
      "index": "a6",
      "roundness": { "type": 2 },
      "seed": 100000007,
      "version": 1,
      "versionNonce": 200000007,
      "isDeleted": false,
      "boundElements": null,
      "updated": 1700000000000,
      "link": null,
      "locked": false,
      "points": [[0, 0], [0, 100]],
      "startBinding": {
        "elementId": "box1",
        "fixedPoint": [0.5, 1],
        "mode": "orbit"
      },
      "endBinding": {
        "elementId": "box2",
        "fixedPoint": [0.5, 0],
        "mode": "orbit"
      },
      "startArrowhead": null,
      "endArrowhead": "arrow",
      "elbowed": false
    }
  ],
  "appState": {
    "gridSize": null,
    "viewBackgroundColor": "#ffffff"
  },
  "files": {}
}
```
%%
```

This example demonstrates: two rectangles with bound text, one arrow with bindings connecting them, proper cross-referencing between elements, and the correct Obsidian wrapper format. For details on each property, see the reference sections below.

## Diagram Type Selection Guide

| Type | When to Use | Layout Approach |
|------|-------------|-----------------|
| **Flowchart** | Step-by-step processes, workflows, decision trees, task sequences | Connect steps with arrows showing flow direction |
| **Mind Map** | Concept expansion, topic classification, brainstorming, idea exploration | Radiate branches outward from a central core node |
| **Hierarchy** | Org structures, content grading, system decomposition, taxonomies | Top-down or left-to-right tree of parent-child nodes |
| **Relationship** | Dependencies, interactions, connections between entities | Lines and arrows between shapes showing how things connect |
| **Comparison** | Contrasting 2 or more options, viewpoints, pros/cons | Side-by-side columns or table-style layout |
| **Timeline** | Event progression, project milestones, historical sequences, model evolution | Horizontal or vertical time axis with key points and events |
| **Matrix** | Two-dimensional classification, priority sorting, risk assessment | X and Y axes creating quadrants or a coordinate plane |
| **Freeform** | Scattered content, brainstorming dumps, initial info gathering, mixed content | Free placement of blocks and arrows wherever they fit |
| **Entity Relationship** | Database schemas, data models, cardinality relationships | Entities with connecting arrows using cardinality arrowheads |
| **Network** | System architecture, infrastructure, communication flows | Nodes representing systems/services with connection lines |
| **Bar Chart** | Quantitative comparisons, survey results, performance metrics | Vertical bars with labeled axes, auto-colored series |
| **Line Chart** | Trends over time, continuous data, multi-series comparisons | Connected dots along an axis with guides and legend |
| **Radar Chart** | Multi-dimensional comparisons, skill assessments, feature scoring (needs 3+ axes) | Polygonal overlay on radial axes with labels |

If the user does not specify a type, analyze the content and pick the most appropriate one. Explain the choice in the final report.

**Chart generation note:** When creating bar/line/radar charts, compose them from native Excalidraw elements (rectangles for bars, line elements for line charts, closed polylines for radar polygons, text for labels). Excalidraw's built-in chart system uses exactly these primitives -- there is no special "chart" element type.

## Design Rules

### Typography

- **Default font:** use `fontFamily: 5` (Excalifont, the handwriting-style font) for the sketch aesthetic
- **Line height:** all text uses `lineHeight: 1.25`
- **Font size guide:**
  - Title: 28-36px (`FONT_SIZES.xl` = 36, `FONT_SIZES.lg` = 28)
  - Subtitle / section headers: 20px (`FONT_SIZES.md` = 20)
  - Body text / descriptions: 16px (`FONT_SIZES.sm` = 16)
- **Quote handling:** replace any double quotes `"` inside text content with single quotes or escaped quotes to avoid JSON parsing issues

#### Available Font Families (complete list from source)

| fontFamily Value | Name | Style |
|------------------|------|-------|
| `1` | Virgil | Legacy hand-drawn font |
| `2` | Helvetica | Clean sans-serif |
| `3` | Cascadia | Monospace / code font |
| `5` | **Excalifont** | Default hand-drawn font (recommended) |
| `6` | Nunito | Rounded sans-serif ("Normal" font) |
| `7` | Lilita One | Bold display font |
| `8` | Comic Shanns | Comic-style monospace ("Code" font) |
| `9` | Liberation Sans | Standard sans-serif |
| `10` | Assistant | Clean sans-serif |

**Note:** Value `4` is reserved/unused. For the classic Excalidraw hand-drawn look, always use `5` (Excalifont). Use other fonts when the user explicitly requests a different style.

### Font-Specific Line Heights

Each font family has its own optimal line height. While `1.25` works as a universal default, these are the exact values from the source:

| Font Family | lineHeight |
|-------------|-----------|
| Excalifont (5) | `1.25` |
| Virgil (1) | `1.25` |
| Comic Shanns (8) | `1.25` |
| Nunito (6) | `1.25` |
| Helvetica (2) | `1.15` |
| Cascadia (3) | `1.2` |
| Lilita One (7) | `1.15` |
| Liberation Sans (9) | `1.15` |
| Assistant (10) | `1.25` |

### Font Metrics (from FONT_METADATA)

For precise text positioning and vertical alignment, each font has specific metric values:

| Font (ID) | unitsPerEm | ascender | descender | lineHeight |
|-----------|-----------|----------|-----------|------------|
| Excalifont (5) | 1000 | 886 | -374 | 1.25 |
| Nunito (6) | 1000 | 1011 | -353 | 1.25 |
| Lilita One (7) | 1000 | 923 | -220 | 1.15 |
| Comic Shanns (8) | 1000 | 750 | -250 | 1.25 |
| Virgil (1) | 1000 | 886 | -374 | 1.25 |
| Helvetica (2) | 2048 | 1577 | -471 | 1.15 |
| Cascadia (3) | 2048 | 1900 | -480 | 1.2 |
| Liberation Sans (9) | 2048 | 1854 | -434 | 1.15 |
| Assistant (10) | 2048 | 1021 | -287 | 1.25 |

**Vertical offset formula** (used internally for text rendering):
```
fontSizeEm = fontSize / unitsPerEm
lineGap = (lineHeightPx - fontSizeEm * ascender + fontSizeEm * descender) / 2
verticalOffset = fontSizeEm * ascender + lineGap
```

These metrics are primarily useful when you need pixel-perfect text positioning.

### Font Fallback Chain

Each font family has a specific fallback chain for characters not covered by the primary font:

| Primary Font | Fallback Chain |
|-------------|---------------|
| Excalifont (5) | Xiaolai (CJK) -> sans-serif -> Segoe UI Emoji |
| Virgil (1) | Xiaolai (CJK) -> sans-serif -> Segoe UI Emoji |
| Nunito (6) | sans-serif -> Segoe UI Emoji |
| Lilita One (7) | sans-serif -> Segoe UI Emoji |
| Helvetica (2) | sans-serif -> Segoe UI Emoji |
| Liberation Sans (9) | sans-serif -> Segoe UI Emoji |
| Assistant (10) | sans-serif -> Segoe UI Emoji |
| Cascadia (3) | monospace -> Segoe UI Emoji |
| Comic Shanns (8) | monospace -> Segoe UI Emoji |

**Xiaolai** (font ID 100) is a hand-drawn CJK font that maintains the sketch aesthetic for Chinese, Japanese, and Korean text. It's automatically loaded when CJK characters are detected.

### Layout and Spacing

- **Canvas:** Excalidraw supports infinite canvas. For typical diagrams, keep elements within a reasonable area (e.g. 1200x800 pixels). Larger diagrams can extend beyond this -- Obsidian will auto-scroll.
- **Spacing:** maintain comfortable spacing between elements -- minimum 40-60px gaps between shapes
- **Visual hierarchy:** use different colors, sizes, and shapes to distinguish information levels
- **Coordinate system:** top-left corner is (0, 0), x increases rightward, y increases downward. **Negative coordinates are fully supported** -- the canvas is infinite in all directions. Elements can be placed at negative x/y values.
- **Grid:** default grid size is 20px with 5 steps. Set `gridSize: null` for freeform placement or `gridSize: 20` for snapping

**Grid rendering details:**
- Bold grid lines: `#dddddd` (every `gridStep` cells, default every 5 = every 100px)
- Regular grid lines: `#e5e5e5` (dashed pattern)
- Regular lines hidden when `gridSize * zoom < 10px` (too dense to see)
- Bold line width: `min(1/zoom, 4)` px
- Regular line width: `min(1/zoom, 1)` px

- **Centering tip:** for a well-centered diagram, start the first element at approximately (100, 100) and expand rightward/downward. Obsidian will auto-scroll to fit the content.

### Color Palette -- Excalidraw Built-in Colors

Excalidraw has a built-in color palette. Use these for consistent, professional diagrams:

**Editor Default Picks (top row of color picker):**

| Category | Colors |
|----------|--------|
| **Default Stroke** | `#1e1e1e` (black), `#e03131` (red), `#2f9e44` (green), `#1971c2` (blue), `#f08c00` (yellow) |
| **Default Background** | `transparent`, `#ffc9c9` (light red), `#b2f2bb` (light green), `#a5d8ff` (light blue), `#ffec99` (light yellow) |

These are the 5 most-used colors shown in the top row of the Excalidraw color picker. Use them for quick, harmonious diagrams.

**Stroke Colors (full saturation):**

| Color | Hex | Use For |
|-------|-----|---------|
| Black | `#1e1e1e` | Default stroke, body text |
| Red | `#e03131` | Errors, warnings, critical paths |
| Pink | `#c2255c` | Accents, highlights |
| Grape | `#9c36b5` | Categories, grouping |
| Violet | `#6741d9` | Special elements |
| Indigo | `#3b5bdb` | Headers, primary elements |
| Blue | `#1971c2` | Links, connections, primary |
| Cyan | `#0c8599` | Secondary elements |
| Teal | `#099268` | Success, positive paths |
| Green | `#2f9e44` | Completion, approved items |
| Yellow | `#f08c00` | Warnings, attention |
| Orange | `#e8590c` | Important highlights |

**Background Fill Colors (light tones for fills):**

| Color | Hex | Pairs With |
|-------|-----|------------|
| Light Red | `#ffc9c9` | Red stroke |
| Light Pink | `#fcc2d7` | Pink stroke |
| Light Grape | `#eebefa` | Grape stroke |
| Light Violet | `#d0bfff` | Violet stroke |
| Light Indigo | `#bac8ff` | Indigo stroke |
| Light Blue | `#a5d8ff` | Blue stroke |
| Light Cyan | `#99e9f2` | Cyan stroke |
| Light Teal | `#96f2d7` | Teal stroke |
| Light Green | `#b2f2bb` | Green stroke |
| Light Yellow | `#ffec99` | Yellow stroke |
| Light Orange | `#ffd8a8` | Orange stroke |
| White | `#ffffff` | Any stroke |
| Transparent | `"transparent"` | No fill |

**Choosing background shades:** For medium-tone backgrounds, use shade 2 from the Complete Color Palette table below. For light backgrounds, use shade 0 or 1. The Background Fill Colors table above lists the most commonly used light fills (shade 1 values).

### Complete Color Palette -- All Shades

The `COLOR_PALETTE` from Excalidraw source defines 5 shades per color (index 0 = lightest, 4 = darkest). Here are the exact hex values used internally:

| Color | Shade 0 (lightest) | Shade 1 | Shade 2 | Shade 3 | Shade 4 (darkest) |
|-------|----|----|----|----|-----|
| Gray | `#f8f9fa` | `#e9ecef` | `#ced4da` | `#868e96` | `#343a40` |
| Red | `#fff5f5` | `#ffc9c9` | `#ff8787` | `#fa5252` | `#e03131` |
| Pink | `#fff0f6` | `#fcc2d7` | `#f783ac` | `#e64980` | `#c2255c` |
| Grape | `#f8f0fc` | `#eebefa` | `#da77f2` | `#be4bdb` | `#9c36b5` |
| Violet | `#f3f0ff` | `#d0bfff` | `#9775fa` | `#7950f2` | `#6741d9` |
| Indigo | `#edf2ff` | `#bac8ff` | `#748ffc` | `#4c6ef5` | `#3b5bdb` |
| Blue | `#e7f5ff` | `#a5d8ff` | `#4dabf7` | `#228be6` | `#1971c2` |
| Cyan | `#e3fafc` | `#99e9f2` | `#3bc9db` | `#15aabf` | `#0c8599` |
| Teal | `#e6fcf5` | `#96f2d7` | `#38d9a9` | `#12b886` | `#099268` |
| Green | `#ebfbee` | `#b2f2bb` | `#69db7c` | `#40c057` | `#2f9e44` |
| Yellow | `#fff9db` | `#ffec99` | `#ffd43b` | `#fab005` | `#f08c00` |
| Orange | `#fff4e6` | `#ffd8a8` | `#ffa94d` | `#fd7e14` | `#e8590c` |
| Bronze | `#f8f1ee` | `#eaddd7` | `#d2bab0` | `#a18072` | `#846358` |

**Usage pattern:** Use shade 4 (darkest) for stroke colors, shade 0-2 (lightest) for background fills. The stroke and background picker defaults in Excalidraw use these exact values.

Special values: `"transparent"` for no fill, `#1e1e1e` for black, `#ffffff` for white.

Use a harmonious color scheme. Do not use more than 5-6 distinct colors in a single diagram. Pair stroke colors with their corresponding light background fills.

## JSON Structure

The top-level JSON object must follow this exact schema:

```json
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://github.com/zsviczian/obsidian-excalidraw-plugin",
  "elements": [],
  "appState": {
    "theme": "light",
    "gridSize": null,
    "viewBackgroundColor": "#ffffff"
  },
  "files": {}
}
```

**Schema fields:**
- `type` -- always `"excalidraw"`
- `version` -- always `2` (current schema version)
- `source` -- use the obsidian plugin URL for Obsidian files

**`source` field behavior:** The `source` field is purely informational -- it does NOT affect rendering or element behavior. However, the Obsidian plugin uses it for version detection: if the saved version is <= 1.8.16, legacy text wrapping behavior is applied to ellipse and diamond containers via `customData.legacyTextWrap: true`. For new diagrams, always use a recent version URL or the standard plugin source URL.

- `elements` -- array of all element objects (shapes, text, arrows, lines, frames)
- `appState` -- editor state: `theme` (`"light"` or `"dark"`), `gridSize` (null or 20), and `viewBackgroundColor`
- `files` -- object mapping fileId to image data (empty `{}` unless embedding images)

**Additional appState properties that are persisted to file:**

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `gridStep` | number | `5` | Grid subdivision steps within each grid cell |
| `gridModeEnabled` | boolean | `false` | Whether grid snapping is active |
| `lockedMultiSelections` | object | `{}` | Map of locked multi-selection group IDs |

---

## All Element Types

Excalidraw supports these element types:

| Type | Description | Key Extra Properties |
|------|-------------|---------------------|
| `"rectangle"` | Rectangular shape | Standard shape props |
| `"ellipse"` | Oval / circle | Standard shape props |
| `"diamond"` | Diamond / rhombus | Standard shape props |
| `"text"` | Text label | `fontSize`, `fontFamily`, `text`, `textAlign`, `verticalAlign`, `containerId` |
| `"arrow"` | Arrow connector | `points`, `startBinding`, `endBinding`, `startArrowhead`, `endArrowhead`, `elbowed` |
| `"line"` | Line / polyline | `points`, `startArrowhead`, `endArrowhead`, `polygon` |
| `"freedraw"` | Freehand drawing | `points`, `pressures`, `simulatePressure` |
| `"frame"` | Visual frame / container | `name` (string label for the frame) |
| `"image"` | Embedded image | `fileId`, `status`, `scale`, `crop` |
| `"embeddable"` | Embedded URL (YouTube, etc.) | URL in `link` field |

For diagram generation, focus on: `rectangle`, `ellipse`, `diamond`, `text`, `arrow`, `line`, and `frame`.

**Note:** The `"selection"` element type exists internally for drag-selection rectangles but is not used in saved files.

---

## Element Base Template -- All Required Fields

EVERY element MUST include ALL of these base fields. Missing fields cause rendering failures:

```json
{
  "id": "unique-id-string",
  "type": "rectangle",
  "x": 100,
  "y": 100,
  "width": 200,
  "height": 50,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a1",
  "roundness": { "type": 3 },
  "seed": 123456789,
  "version": 2,
  "versionNonce": 987654321,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1751928342106,
  "link": null,
  "locked": false
}
```

### Field Reference

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier. Use descriptive names: `"title"`, `"box1"`, `"arrow-1-to-2"` |
| `type` | string | Element type (see table above) |
| `x`, `y` | number | Position of the element's top-left corner in canvas coordinates |
| `width`, `height` | number | Dimensions in pixels. Min value: 1 |
| `angle` | number | Rotation in radians. `0` = no rotation. Use `Math.PI / 4` for 45 degrees, etc. |
| `strokeColor` | string | Border/outline color as hex string |
| `backgroundColor` | string | Fill color as hex string, or `"transparent"` |
| `fillStyle` | string | How the fill is rendered (see Fill Styles below) |
| `strokeWidth` | number | Border thickness: `1` (thin), `2` (bold/default), `4` (extra bold) |
| `strokeStyle` | string | Border pattern (see Stroke Styles below) |
| `roughness` | number | Hand-drawn roughness level (see Roughness below) |
| `opacity` | number | 0-100. Default 100 (fully opaque) |
| `groupIds` | string[] | Array of group IDs this element belongs to |
| `frameId` | string\|null | ID of the frame this element is inside, or null |
| `index` | string | Fractional index for z-ordering (see Index Conventions) |
| `roundness` | object\|null | Corner rounding algorithm (see Roundness below) |
| `seed` | number | Random seed for rough.js rendering. Use unique random 9+ digit integers |
| `version` | number | Version counter. Excalidraw internally starts at 2 for new elements. Use `1` or `2` |
| `versionNonce` | number | Random nonce, unique per element. Use random 9+ digit integers |
| `isDeleted` | boolean | Always `false` for new elements |
| `boundElements` | array\|null | Array of `{ "id": "...", "type": "text" }` or `{ "id": "...", "type": "arrow" }` objects. Use `null` when no bindings exist (preferred over `[]`) |
| `updated` | number | Timestamp in milliseconds |
| `link` | string\|null | URL hyperlink, or null |
| `locked` | boolean | Whether the element is locked from editing |

**Element size validation:** Excalidraw logs an error if `x`, `y`, `width`, or `height` exceeds `±1,000,000` (1e6). Keep coordinates and dimensions within this range.

**Canvas rendering limits:**
- Safari mobile max canvas area: `16,777,216 px²` (equivalent to ~4096x4096)
- Safari max canvas dimension: `32,767px`
- When exporting very large diagrams, the export scale is automatically reduced to fit within these limits
- For best compatibility, keep diagram total area under 4000x4000px at 1x scale

### Bindable Element Types

Not all elements can have arrows bound to them. The following types support arrow bindings (are "bindable"):
- `rectangle`
- `ellipse`
- `diamond`
- `text` (standalone text, not contained)
- `image`
- `frame`
- `embeddable`
- `iframe`

Non-bindable types: `arrow`, `line`, `freedraw` -- arrows cannot bind to these.

### Fillable vs Non-Fillable Elements

Not all elements support `backgroundColor` fill:

| Fillable (supports backgroundColor) | NOT Fillable |
|--------------------------------------|-------------|
| `rectangle` | `freedraw` |
| `diamond` | `text` |
| `ellipse` | `image` |
| `arrow` | `frame` |
| `line` | `embeddable` |

For non-fillable elements, `backgroundColor` should be `"transparent"`.

### Valid Text Containers

Only these element types can contain bound text:
- `rectangle`
- `ellipse`
- `diamond`
- `arrow` (for labeled arrows)

---

## Style Properties -- Complete Reference

### Fill Styles (`fillStyle`)

| Value | Description |
|-------|-------------|
| `"solid"` | Solid color fill (default, most common) |
| `"hachure"` | Diagonal line hatching (hand-drawn look) |
| `"cross-hatch"` | Cross-hatched lines (denser hand-drawn look) |
| `"zigzag"` | Zigzag line fill pattern (available in newer versions) |

### Stroke Styles (`strokeStyle`)

| Value | Description |
|-------|-------------|
| `"solid"` | Continuous line (default) |
| `"dashed"` | Dashed line pattern |
| `"dotted"` | Dotted line pattern |

**Exact dash array values:**
- **Dashed:** `[8, 8 + strokeWidth]` -- e.g., strokeWidth=2 produces `[8, 10]` (8px dash, 10px gap)
- **Dotted:** `[1.5, 6 + strokeWidth]` -- e.g., strokeWidth=2 produces `[1.5, 8]` (1.5px dot, 8px gap)
- **Solid:** no dash array (continuous line)

For dashed/dotted strokes, rough.js multi-stroke wobble is disabled and strokeWidth is internally increased by `0.5px` to compensate visually.

### Roughness Levels (`roughness`)

| Value | Name | Description |
|-------|------|-------------|
| `0` | Architect | Clean, precise lines with no roughness |
| `1` | Artist | Slightly rough, natural hand-drawn look (default) |
| `2` | Cartoonist | Very rough, exaggerated hand-drawn style |

**Adaptive roughness for small elements:** Roughness is automatically reduced for small shapes to prevent excessive wobble:
- Elements >= 20px min side AND >= 50px max side: full roughness applied
- Elements < 10px max side: roughness divided by 3
- Elements 10-20px: roughness divided by 2
- Capped at maximum 2.5 after reduction

This means very small shapes always look cleaner regardless of the roughness setting.

**Continuous path rendering:** For shapes with smooth SVG paths (rounded rectangles, rounded diamonds, elbow arrows), rough.js is told to preserve exact vertex positions (`preserveVertices: true`). This prevents roughjs from jittering the control points, ensuring curves remain smooth. For sharp-cornered shapes and elements with `roughness < 2` (Cartoonist), vertices are always preserved. Only Cartoonist roughness on non-rounded shapes allows full vertex randomization.

### Stroke Width (`strokeWidth`)

| Value | Name |
|-------|------|
| `1` | Thin |
| `2` | Bold (default) |
| `4` | Extra Bold |

### Roundness (`roundness`)

| Value | Name | Use For |
|-------|------|---------|
| `{ "type": 1 }` | Legacy | Legacy rectangles only. Differs from type 2/3 -- avoid using for new elements |
| `{ "type": 2 }` | Proportional Radius | Lines, diamonds -- 25% of largest side |
| `{ "type": 3 }` | Adaptive Radius | Rectangles (default) -- fixed 32px radius, like CSS border-radius |
| `null` | Sharp | No rounding -- sharp corners |

**Which roundness to use per element type:**
- **Rectangles:** `{ "type": 3 }` for rounded, `null` for sharp
- **Diamonds:** `{ "type": 2 }` for rounded, `null` for sharp
- **Ellipses:** always `null` (inherently rounded)
- **Lines/Arrows:** `{ "type": 2 }` for curved segments, `null` for straight segments

**Adaptive radius cutoff behavior (type 3):**
- If the smaller dimension is <= 128px: uses proportional mode = `minSide * 0.25`
- If the smaller dimension is > 128px: uses fixed 32px radius
- The cutoff threshold is `DEFAULT_ADAPTIVE_RADIUS / DEFAULT_PROPORTIONAL_RADIUS` = `32 / 0.25` = 128px
- This means small rectangles get proportionally rounded corners, while large rectangles get a consistent 32px radius

**Diamond double-radius:** Diamonds use TWO separate radii — one for the vertical diagonal and one for the horizontal diagonal, each calculated from their respective diagonal length.

### Text Alignment

**`textAlign`:**
| Value | Description |
|-------|-------------|
| `"left"` | Left-aligned (default for standalone text) |
| `"center"` | Center-aligned (default for text in containers) |
| `"right"` | Right-aligned |

**`verticalAlign`:**
| Value | Description |
|-------|-------------|
| `"top"` | Top-aligned |
| `"middle"` | Vertically centered (default for text in containers) |
| `"bottom"` | Bottom-aligned |

---

## Text Elements

Text elements include all base fields plus these text-specific properties:

```json
{
  "type": "text",
  "text": "Display text here",
  "rawText": "Display text here",
  "fontSize": 20,
  "fontFamily": 5,
  "textAlign": "left",
  "verticalAlign": "top",
  "containerId": null,
  "originalText": "Display text here",
  "autoResize": true,
  "lineHeight": 1.25
}
```

| Field | Type | Description |
|-------|------|-------------|
| `text` | string | The rendered text content. Use `\n` for line breaks |
| `rawText` | string | Same as `text` for generated content |
| `fontSize` | number | Font size in pixels. Predefined sizes: 16, 20, 28, 36. Min: 1 |
| `fontFamily` | number | Font family ID (see Font Families table above) |
| `textAlign` | string | `"left"`, `"center"`, or `"right"` |
| `verticalAlign` | string | `"top"`, `"middle"`, or `"bottom"` |
| `containerId` | string\|null | ID of the parent container shape, or null for standalone text |
| `originalText` | string | Same as `text` for generated content |
| `autoResize` | boolean | Whether the text auto-resizes. `true` for generated content |
| `lineHeight` | number | Line height multiplier. Use `1.25` for Excalifont (default). See Font-Specific Line Heights table for other fonts |

**No inline formatting:** Excalidraw text elements do NOT support inline rich text (no bold, italic, markdown, or mixed styles within a single element). Each text element has one `fontSize`, one `fontFamily`, and one `strokeColor`. To mix styles, create separate text elements positioned adjacent to each other.

**Width/Height for text:** calculate approximate dimensions based on font size and character count:
- Width: approximately `fontSize * 0.6 * maxLineLength` (this ratio works well for Excalifont; wider fonts like Nunito/Helvetica may need `0.65-0.7`)
- Height: approximately `fontSize * lineHeight * numberOfLines`
- These are approximations -- Excalidraw internally uses canvas `measureText()` for exact sizing. The restore function auto-corrects text dimensions on load, so approximate values work.

### Text Container Dimension Formulas

When placing text inside a container shape, the maximum text width depends on the container type. These formulas come directly from the source code:

| Container Type | Max Text Width | Max Text Height |
|----------------|---------------|-----------------|
| **Rectangle** | `containerWidth - PADDING * 2` (i.e. width - 10) | `containerHeight - PADDING * 2` |
| **Ellipse** | `(containerWidth / 2) * sqrt(2) - PADDING * 2` (~70.7% of width - 10) | `(containerHeight / 2) * sqrt(2) - PADDING * 2` |
| **Diamond** | `containerWidth / 2 - PADDING * 2` (50% of width - 10) | `containerHeight / 2 - PADDING * 2` |
| **Arrow** | `containerWidth * 0.7` (70% of arrow length) | Based on font size |

Where `PADDING` = 5 (the `BOUND_TEXT_PADDING` constant).

**Minimum container dimensions:** when text is bound to a container, the container auto-sizes. The minimum width for an arrow label is `fontSize * 11` divided by the label width fraction.

### Reverse Calculation: Container Size from Text Size

When you know the text dimensions and need to calculate the minimum container size:

| Container Type | Min Container Width | Min Container Height |
|----------------|--------------------|--------------------|
| **Rectangle** | `textWidth + PADDING * 2` (textWidth + 10) | `textHeight + PADDING * 2` |
| **Ellipse** | `round(((textWidth + PADDING * 2) / sqrt(2)) * 2)` (~1.414x wider) | `round(((textHeight + PADDING * 2) / sqrt(2)) * 2)` |
| **Diamond** | `2 * (textWidth + PADDING * 2)` (2x wider) | `2 * (textHeight + PADDING * 2)` |
| **Arrow** | `textWidth + PADDING * 8 * 2` (textWidth + 80) | Based on text height |

**Arrow label minimum width:** `fontSize * ARROW_LABEL_FONT_SIZE_TO_MIN_WIDTH_RATIO` where `ARROW_LABEL_FONT_SIZE_TO_MIN_WIDTH_RATIO = 11`. So for fontSize 20, minimum arrow label width = 220px.

### Container Coordinate Offsets for Text Positioning

When positioning text inside a container, the text origin is offset from the container origin:

| Container Type | X Offset | Y Offset |
|----------------|----------|----------|
| **Rectangle** | `PADDING` (5px) | `PADDING` (5px) |
| **Ellipse** | `(width/2) * (1 - sqrt(2)/2)` + PADDING | `(height/2) * (1 - sqrt(2)/2)` + PADDING |
| **Diamond** | `width/4` + PADDING | `height/4` + PADDING |

### Multi-line Text

- Use `\n` in the `text`, `rawText`, and `originalText` fields for line breaks
- Width should accommodate the longest line
- Height should be `fontSize * lineHeight * numberOfLines`
- Text wrapping happens automatically in containers based on the max width formulas above
- For standalone text with `autoResize: true`, the element auto-sizes to fit content
- For standalone text with `autoResize: false`, text wraps to the element's width

### CJK and International Text Support

Excalidraw has full Unicode text wrapping support with special rules for CJK (Chinese, Japanese, Korean) characters:
- **CJK characters** (Han, Hiragana, Katakana, Hangul): break allowed before and after each character
- **CJK opening punctuation** (`（「【〈《` etc.): no break between opening punctuation and following character
- **CJK closing punctuation** (`）」】〉》。，、？！` etc.): no break between preceding character and closing punctuation
- **CJK currency symbols** (`￥￦￡￠＄`): break before, not after
- **Emoji sequences**: multi-codepoint emojis (ZWJ sequences, flags, skin tones) are never split
- Text is NFC-normalized before wrapping
- Tabs are replaced with 8 spaces
- **RTL (Right-to-Left) text**: Excalidraw detects RTL scripts (Arabic, Hebrew) by checking if the first directional character in the text is RTL. RTL text is properly handled for display and wrapping.

---

## Arrow and Line Elements

### Arrow Element

Arrows include all base fields plus these properties:

```json
{
  "type": "arrow",
  "points": [[0, 0], [200, 0]],
  "startBinding": null,
  "endBinding": null,
  "startArrowhead": null,
  "endArrowhead": "arrow",
  "elbowed": false
}
```

| Field | Type | Description |
|-------|------|-------------|
| `points` | number[][] | Array of [x, y] coordinate pairs relative to element's x, y. First point is always [0, 0] |
| `startBinding` | object\|null | Binding to the start shape |
| `endBinding` | object\|null | Binding to the end shape |
| `startArrowhead` | string\|null | Arrowhead at the start (see Arrowhead Types) |
| `endArrowhead` | string\|null | Arrowhead at the end (see Arrowhead Types) |
| `elbowed` | boolean | If true, creates an elbow (right-angle) arrow |

### Line Element

Lines are similar to arrows but use `type: "line"`:

```json
{
  "type": "line",
  "points": [[0, 0], [200, 0]],
  "startArrowhead": null,
  "endArrowhead": null,
  "polygon": false
}
```

The `polygon` field (boolean) controls whether the line forms a closed polygon (last point connects back to first point). Lines can also have arrowheads.

Points within `20px` (`LINE_POLYGON_POINT_MERGE_DISTANCE`) of each other are merged when forming a polygon. A closed polygon requires at least 4 points.

**Polygon rendering differences:**
- `polygon: false` (open line): rendered as an open path with no fill, even if backgroundColor is set. Hit testing only checks proximity to line segments.
- `polygon: true` (closed polygon): rendered as a closed, filled shape. The `backgroundColor` and `fillStyle` are applied (hachure, cross-hatch, solid, or zigzag fill). Hit testing checks if points are inside the enclosed area.
- **Toggle behavior:** When closing a line into a polygon, if the last point is within 20px of the first point, it snaps to the first point's position. Otherwise, a new closing point is appended at the first point's coordinates.

### Points Array

The `points` array defines the path of arrows and lines:
- First point is ALWAYS `[0, 0]` (relative to the element's x, y position)
- Subsequent points are relative offsets from the element's x, y
- For a straight horizontal arrow 200px long: `[[0, 0], [200, 0]]`
- For an L-shaped path: `[[0, 0], [200, 0], [200, 100]]`
- For multi-segment paths, add intermediate points

### Arrowhead Types (complete list from source)

| Value | Description | Visual |
|-------|-------------|--------|
| `"arrow"` | Standard arrow tip | Default, most common |
| `"triangle"` | Filled triangle | Solid triangular arrowhead |
| `"triangle_outline"` | Outlined triangle | Hollow triangular arrowhead |
| `"bar"` | Perpendicular bar | Flat end bar |
| `"circle"` | Filled circle | Solid dot |
| `"circle_outline"` | Outlined circle | Hollow dot |
| `"diamond"` | Filled diamond | Solid diamond shape |
| `"diamond_outline"` | Outlined diamond | Hollow diamond shape |
| `null` | No arrowhead | Plain line end |

**Cardinality Arrowheads (for ER diagrams):**

| Value | Description | Notation |
|-------|-------------|----------|
| `"cardinality_one"` | Exactly one | `\|` |
| `"cardinality_many"` | Many | `>` (crow's foot) |
| `"cardinality_one_or_many"` | One or many | `\|>` |
| `"cardinality_exactly_one"` | Exactly one (strict) | `\|\|` |
| `"cardinality_zero_or_one"` | Zero or one | `o\|` |
| `"cardinality_zero_or_many"` | Zero or many | `o>` |

### Arrow Types (shape of the path)

Arrows can follow different path algorithms controlled by properties:
- **Sharp arrows:** straight line segments with sharp corners at points
- **Round arrows:** curved path through points (when `roundness: { "type": 2 }`)
- **Elbow arrows:** right-angle orthogonal routing (`"elbowed": true`)

### Elbow Arrows

For elbow arrows (right-angle routing), set `"elbowed": true` on the arrow element. Elbow arrows automatically route around obstacles with 90-degree turns.

**Elbow arrow rules:**
- `roundness` MUST be `null` (elbow arrows don't support curved corners)
- `angle` MUST be `0` (elbow arrows cannot be rotated)
- Points should form right-angle segments (each consecutive pair differs in only x OR y, not both)

```json
{
  "type": "arrow",
  "elbowed": true,
  "points": [[0, 0], [100, 0], [100, 100], [200, 100]],
  "roundness": null,
  "startArrowhead": null,
  "endArrowhead": "arrow"
}
```

**Advanced elbow arrow properties (when `elbowed: true`):**

| Property | Type | Description |
|----------|------|-------------|
| `fixedSegments` | array\|null | Array of user-pinned segments: `{start: [x,y], end: [x,y], index: number}`. Controls which segments the user has manually positioned. |
| `startIsSpecial` | boolean\|null | When true, the 3rd point is used as the 2nd to temporarily hide the first segment. |
| `endIsSpecial` | boolean\|null | When true, the 3rd-from-end point is used as the 2nd-from-end to temporarily hide the last segment. |

Elbow arrows use an A* pathfinding algorithm on a grid to route orthogonal paths around obstacles. The routing respects headings: RIGHT `[1,0]`, DOWN `[0,1]`, LEFT `[-1,0]`, UP `[0,-1]`.

**Elbow arrow corner radius:** Fixed at `16px` for all elbow arrow turns. The actual corner radius is `min(16, distance_to_next_point/2, distance_to_prev_point/2)`. Corners are rendered as quadratic bezier curves for smooth right-angle turns.

### Arrow Width and Height Calculation

For arrow and line elements, the `width` and `height` fields MUST match the bounding box of the `points` array:
- `width` = max x value in points - min x value in points (the absolute x spread)
- `height` = max y value in points - min y value in points (the absolute y spread)

Example: For `points: [[0, 0], [150, -50], [300, 0]]`:
- width = 300 - 0 = 300
- height = 0 - (-50) = 50

If width or height calculates to 0 (e.g. a perfectly horizontal arrow), use `0` (not `1`).

**Minimum arrow size:** arrows shorter than 20px (`MINIMUM_ARROW_SIZE`) are considered too small. The editor auto-completes them at 20px on touch devices. Design arrows to be at least 20px for reliable rendering.

### Arrow Positioning Recipe

When connecting shapes with arrows, follow this recipe to calculate the arrow's `x`, `y`, and `points`:

**For a vertical arrow (top-to-bottom):**
1. Arrow `x` = source shape center X = `sourceX + sourceWidth / 2`
2. Arrow `y` = source shape bottom edge = `sourceY + sourceHeight`
3. Arrow `points` = `[[0, 0], [0, gap]]` where `gap` = distance to target shape top edge
4. Arrow `width` = `0`, `height` = `gap`

**For a horizontal arrow (left-to-right):**
1. Arrow `x` = source shape right edge = `sourceX + sourceWidth`
2. Arrow `y` = source shape center Y = `sourceY + sourceHeight / 2`
3. Arrow `points` = `[[0, 0], [gap, 0]]` where `gap` = distance to target shape left edge
4. Arrow `width` = `gap`, `height` = `0`

**For a diagonal arrow:**
1. Arrow `x` = approximate start position (near source shape edge)
2. Arrow `y` = approximate start position
3. Arrow `points` = `[[0, 0], [deltaX, deltaY]]` where delta = offset to target
4. Arrow `width` = `|deltaX|`, `height` = `|deltaY|`

**Important:** When bindings are set (`startBinding`/`endBinding`), Excalidraw auto-adjusts arrow endpoints on load. The coordinates only need to be approximately correct -- the binding system will snap them to the shape edges. The `fixedPoint` in the binding determines exactly where the arrow connects.

---

## Arrow Bindings

To connect an arrow to shapes, use `startBinding` and `endBinding`. Both the arrow AND the target shape must reference each other:

### Arrow side:

```json
{
  "id": "arrow1",
  "type": "arrow",
  "startBinding": {
    "elementId": "box1",
    "focus": 0,
    "gap": 5,
    "fixedPoint": null
  },
  "endBinding": {
    "elementId": "box2",
    "focus": 0,
    "gap": 5,
    "fixedPoint": null
  }
}
```

### Shape side (add arrow to `boundElements`):

```json
{
  "id": "box1",
  "type": "rectangle",
  "boundElements": [
    { "id": "arrow1", "type": "arrow" }
  ]
}
```

```json
{
  "id": "box2",
  "type": "rectangle",
  "boundElements": [
    { "id": "arrow1", "type": "arrow" }
  ]
}
```

### Binding Fields

There are two binding formats. Both work -- Excalidraw's restore function normalizes them:

**Format 1 -- PointBinding (legacy, works for all arrows):**

| Field | Type | Description |
|-------|------|-------------|
| `elementId` | string | ID of the shape being bound to |
| `focus` | number | Where the arrow connects on the shape edge. `0` = center, `-1` to `1` range. Negative = towards left/top, positive = towards right/bottom |
| `gap` | number | Pixel gap between arrow endpoint and shape edge. Default: `5` |
| `fixedPoint` | [number, number]\|null | Fixed connection point as [x, y] ratio (0-1) on the shape. `null` for automatic |

```json
{
  "elementId": "box1",
  "focus": 0,
  "gap": 5,
  "fixedPoint": null
}
```

**Format 2 -- FixedPointBinding (modern, used by `convertToExcalidrawElements` and elbow arrows):**

| Field | Type | Description |
|-------|------|-------------|
| `elementId` | string | ID of the shape being bound to |
| `fixedPoint` | [number, number] | Connection point as [x, y] ratio (0-1) on the shape. `[0.5, 0]` = top center, `[1, 0.5]` = right center, `[0.5, 1]` = bottom center, `[0, 0.5]` = left center |
| `mode` | string | Binding mode: `"orbit"`, `"inside"`, or `"skip"` |

```json
{
  "elementId": "box1",
  "fixedPoint": [0.5, 1],
  "mode": "orbit"
}
```

**Common fixedPoint values:**
- `[0.5, 0]` -- top center of shape
- `[1, 0.5]` -- right center of shape
- `[0.5, 1]` -- bottom center of shape
- `[0, 0.5]` -- left center of shape
- `[0, 0]` -- top-left corner
- `[1, 1]` -- bottom-right corner

**fixedPoint normalization:** Values exactly equal to `0.5` are internally nudged to `0.5001` (offset by `EPSILON = 0.0001`) to avoid floating-point precision issues in arrow heading calculations. This is automatic -- you can use exact `0.5` values in generated JSON and they will be normalized on load.

**Binding modes:**
- `"orbit"` -- arrow connects around the outside of the shape (default, most common)
- `"inside"` -- arrow connects to the inside edge of the shape
- `"skip"` -- binding is skipped

### Binding Gap

The visual gap between an arrow endpoint and the bound shape's edge:
- **Standard arrows:** `5px + (strokeWidth / 2)`
- **Elbow arrows:** `5px + (strokeWidth / 2)`

**CRITICAL:** When binding arrows to shapes, you MUST update BOTH:
1. The arrow's `startBinding`/`endBinding` with the shape's ID
2. The shape's `boundElements` array with `{ "id": "arrowId", "type": "arrow" }`

If either side is missing, the binding will not work.

### Binding Detection Priority

When an arrow endpoint is near multiple shapes, Excalidraw selects which shape to bind to:
1. Tests all non-deleted bindable elements from front to back (z-order)
2. Stops at the first element with a non-transparent background (blocks elements behind it)
3. If multiple candidates overlap, prefers the **smallest** shape (by area: `width² + height²`)
4. Elements that are already bound to the same arrow are deprioritized

---

## Bound Text in Shapes (Text Containers)

To place text inside a shape, you need TWO elements with cross-references:

### Step 1: Shape element with boundElements reference

```json
{
  "id": "box1",
  "type": "rectangle",
  "x": 100,
  "y": 100,
  "width": 200,
  "height": 60,
  "boundElements": [
    { "id": "box1-text", "type": "text" }
  ]
}
```

### Step 2: Text element with containerId

```json
{
  "id": "box1-text",
  "type": "text",
  "x": 105,
  "y": 105,
  "width": 190,
  "height": 50,
  "text": "Box Label",
  "rawText": "Box Label",
  "originalText": "Box Label",
  "fontSize": 20,
  "fontFamily": 5,
  "textAlign": "center",
  "verticalAlign": "middle",
  "containerId": "box1",
  "autoResize": true,
  "lineHeight": 1.25
}
```

**Valid text container shapes:** `rectangle`, `ellipse`, `diamond`, `arrow` (for labeled arrows)

**Text container rules:**
- The text element's `containerId` MUST match the shape's `id`
- The shape's `boundElements` MUST include `{ "id": "textId", "type": "text" }`
- Only ONE text element per container shape
- For text in containers: use `textAlign: "center"` and `verticalAlign: "middle"` by default
- Bound text padding: 5px on each side (so text width = container width - 10)
- For arrows with labels, the label width is approximately 70% of arrow length

### Labeled Arrows

To add a label to an arrow, bind a text element to it:

```json
{
  "id": "arrow1",
  "type": "arrow",
  "boundElements": [{ "id": "arrow1-label", "type": "text" }],
  "points": [[0, 0], [300, 0]]
}
```

```json
{
  "id": "arrow1-label",
  "type": "text",
  "containerId": "arrow1",
  "text": "connects to",
  "textAlign": "center",
  "verticalAlign": "middle"
}
```

---

## Frame Elements

Frames visually group elements together with a labeled border:

```json
{
  "id": "frame1",
  "type": "frame",
  "x": 50,
  "y": 50,
  "width": 400,
  "height": 300,
  "name": "My Frame",
  "strokeColor": "#bbb",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "fillStyle": "solid",
  "roughness": 0,
  "roundness": null,
  "backgroundColor": "transparent"
}
```

**Frame rules:**
- Frame name font size: 14px, line height: 1.25
- Frame stroke color: `#bbb` (light gray)
- Frame corner radius: 8px
- Frame roughness: always `0` (clean lines, not hand-drawn)
- Child elements must have `"frameId": "frame1"` set to the frame's ID

**Element ordering for frames:** Frame children MUST come BEFORE the frame element in the `elements` array:

```json
{
  "elements": [
    { "id": "child1", "frameId": "frame1", "type": "rectangle" },
    { "id": "child2", "frameId": "frame1", "type": "text" },
    { "id": "frame1", "type": "frame", "name": "My Frame" },
    { "id": "other-element", "frameId": null, "type": "rectangle" }
  ]
}
```

This ordering is critical for correct rendering and clipping.

### Complete Frame Example

```json
[
  {
    "id": "svc-api",
    "type": "rectangle",
    "x": 70,
    "y": 70,
    "width": 160,
    "height": 50,
    "frameId": "frame-backend",
    "strokeColor": "#1971c2",
    "backgroundColor": "#a5d8ff",
    "fillStyle": "solid",
    "strokeWidth": 2,
    "strokeStyle": "solid",
    "roughness": 1,
    "opacity": 100,
    "angle": 0,
    "groupIds": [],
    "roundness": { "type": 3 },
    "seed": 111111111,
    "version": 1,
    "versionNonce": 222222222,
    "isDeleted": false,
    "boundElements": [{ "id": "svc-api-text", "type": "text" }],
    "updated": 1751928342106,
    "link": null,
    "locked": false,
    "index": "a0"
  },
  {
    "id": "svc-api-text",
    "type": "text",
    "x": 75,
    "y": 75,
    "width": 150,
    "height": 25,
    "frameId": "frame-backend",
    "containerId": "svc-api",
    "text": "API Service",
    "rawText": "API Service",
    "originalText": "API Service",
    "fontSize": 20,
    "fontFamily": 5,
    "textAlign": "center",
    "verticalAlign": "middle",
    "autoResize": true,
    "lineHeight": 1.25,
    "strokeColor": "#1e1e1e",
    "backgroundColor": "transparent",
    "fillStyle": "solid",
    "strokeWidth": 2,
    "strokeStyle": "solid",
    "roughness": 1,
    "opacity": 100,
    "angle": 0,
    "groupIds": [],
    "roundness": null,
    "seed": 333333333,
    "version": 1,
    "versionNonce": 444444444,
    "isDeleted": false,
    "boundElements": null,
    "updated": 1751928342106,
    "link": null,
    "locked": false,
    "index": "a1"
  },
  {
    "id": "svc-db",
    "type": "ellipse",
    "x": 280,
    "y": 60,
    "width": 140,
    "height": 70,
    "frameId": "frame-backend",
    "strokeColor": "#2f9e44",
    "backgroundColor": "#b2f2bb",
    "fillStyle": "solid",
    "strokeWidth": 2,
    "strokeStyle": "solid",
    "roughness": 1,
    "opacity": 100,
    "angle": 0,
    "groupIds": [],
    "roundness": null,
    "seed": 555555555,
    "version": 1,
    "versionNonce": 666666666,
    "isDeleted": false,
    "boundElements": [{ "id": "svc-db-text", "type": "text" }],
    "updated": 1751928342106,
    "link": null,
    "locked": false,
    "index": "a2"
  },
  {
    "id": "svc-db-text",
    "type": "text",
    "x": 310,
    "y": 78,
    "width": 80,
    "height": 25,
    "frameId": "frame-backend",
    "containerId": "svc-db",
    "text": "Database",
    "rawText": "Database",
    "originalText": "Database",
    "fontSize": 20,
    "fontFamily": 5,
    "textAlign": "center",
    "verticalAlign": "middle",
    "autoResize": true,
    "lineHeight": 1.25,
    "strokeColor": "#1e1e1e",
    "backgroundColor": "transparent",
    "fillStyle": "solid",
    "strokeWidth": 2,
    "strokeStyle": "solid",
    "roughness": 1,
    "opacity": 100,
    "angle": 0,
    "groupIds": [],
    "roundness": null,
    "seed": 777777777,
    "version": 1,
    "versionNonce": 888888888,
    "isDeleted": false,
    "boundElements": null,
    "updated": 1751928342106,
    "link": null,
    "locked": false,
    "index": "a3"
  },
  {
    "id": "frame-backend",
    "type": "frame",
    "x": 50,
    "y": 30,
    "width": 400,
    "height": 120,
    "name": "Backend Services",
    "strokeColor": "#bbb",
    "backgroundColor": "transparent",
    "fillStyle": "solid",
    "strokeWidth": 2,
    "strokeStyle": "solid",
    "roughness": 0,
    "opacity": 100,
    "angle": 0,
    "groupIds": [],
    "frameId": null,
    "roundness": null,
    "seed": 999999999,
    "version": 1,
    "versionNonce": 101010101,
    "isDeleted": false,
    "boundElements": null,
    "updated": 1751928342106,
    "link": null,
    "locked": false,
    "index": "a4"
  }
]
```

Key points demonstrated:
- All child elements (`svc-api`, `svc-api-text`, `svc-db`, `svc-db-text`) have `"frameId": "frame-backend"`
- Children appear BEFORE the frame element in the array
- The frame element itself has `"frameId": null` (frames don't nest)
- Bound text elements also need `frameId` set to the same frame
- Frame has `roughness: 0` and `strokeColor: "#bbb"` per frame style rules

**Frame name colors by theme:**
- Light theme: `#999999`
- Dark theme: `#7a7a7a`

**Frame opacity stacking:** When elements are inside a frame, their effective opacity is calculated as:
```
effectiveOpacity = (frameOpacity * elementOpacity) / 10000
```
For example, a frame with opacity 50 containing an element with opacity 80 renders at `(50 * 80) / 10000 = 0.4` (40% opacity).

**Magic frames** (`type: "magicframe"`): Same as regular frames but with a distinct stroke color (`#7affd7` in light theme). Used for AI-driven code generation in the Excalidraw editor. For diagram generation, use regular `"frame"` type instead.

---

## Groups

To visually group elements together (without a frame border), use `groupIds`:

```json
[
  {
    "id": "elem1",
    "groupIds": ["group-a"],
    "type": "rectangle"
  },
  {
    "id": "elem2",
    "groupIds": ["group-a"],
    "type": "text"
  }
]
```

- All elements in the same group share the same group ID string in their `groupIds` array
- Elements can belong to multiple groups (nested groups): `"groupIds": ["inner-group", "outer-group"]`
- Groups are ordered from innermost to outermost in the array

---

## Freedraw Elements

For freehand-drawn elements (sketches, underlines, decorations):

```json
{
  "type": "freedraw",
  "points": [[0, 0], [5, 2], [10, 1], [15, 5], [20, 3]],
  "pressures": [],
  "simulatePressure": true
}
```

| Field | Type | Description |
|-------|------|-------------|
| `points` | number[][] | Array of [x, y] points defining the path |
| `pressures` | number[] | Pressure values per point (empty array if simulated) |
| `simulatePressure` | boolean | If true, pressure is simulated for natural look |

**Freedraw rendering parameters** (passed to perfect-freehand library):
- `size`: `strokeWidth * 4.25` (visual stroke size)
- `thinning`: `0.6` (how much the stroke thins at fast speeds)
- `smoothing`: `0.5` (how smooth the stroke path is)
- `streamline`: `0.5` (how much lag the stroke has)
- `easing`: ease-out sine function
- `simulatePressure`: from element (true when no real pressure data, e.g., mouse input)

---

## Dark Mode Support

To generate a dark-mode diagram, change the `appState.viewBackgroundColor`:

```json
{
  "appState": {
    "gridSize": null,
    "viewBackgroundColor": "#121212"
  }
}
```

**Important:** Setting `"theme": "dark"` in appState does NOT automatically transform element colors in the JSON. It only applies a CSS filter (`invert(93%) hue-rotate(180deg)`) at render time in the editor. For generated diagrams, you must manually choose appropriate colors for the background. The theme setting affects how the Excalidraw editor displays the diagram, not the stored color values.

For dark mode diagrams:
- Use `viewBackgroundColor: "#121212"` or `"#1e1e1e"` or `"#000000"`
- Light-colored strokes work better: use shade 0-2 colors for strokes instead of shade 4
- Background fills can use shade 3-4 (darker) colors
- Text colors should be light: `"#ffffff"` or `"#e9ecef"`

The Excalidraw dark mode filter applies `invert(93%) hue-rotate(180deg)` to colors, but when generating JSON directly, just use appropriate colors for the chosen background.

### Dark Mode Color Transformation (Exact Formula)

When applying dark mode programmatically (not via CSS), colors are transformed in two steps:

**Step 1 -- Invert at 93%:**
```
invertedR = R * 0.07 + (255 - R) * 0.93
invertedG = G * 0.07 + (255 - G) * 0.93
invertedB = B * 0.07 + (255 - B) * 0.93
```

**Step 2 -- Hue Rotate 180 degrees:** Apply a 3x3 rotation matrix on the inverted RGB values.

**Color brightness detection:** Excalidraw uses the YIQ formula to determine if a color is "dark":
```
yiq = (R * 299 + G * 587 + B * 114) / 1000
isDark = yiq < 160
```

For generated diagrams, it's simpler to just pick appropriate colors directly rather than computing the transform. Use light strokes on dark backgrounds.

### Canvas Background Quick Picks

The Excalidraw editor offers these preset background colors:
`#ffffff`, `#f8f9fa`, `#f5faff`, `#fffce8`, `#fdf8f6`

These can be used as `viewBackgroundColor` in `appState` for subtle tinted backgrounds.

## Custom Data

Every element supports an optional `customData` field for storing arbitrary metadata:

```json
{
  "id": "box1",
  "type": "rectangle",
  "customData": {
    "source": "auto-generated",
    "category": "process-step",
    "priority": 1
  }
}
```

This field is preserved through save/load cycles and can be used by scripts and plugins. It does not affect rendering.

---

## Element ID and Index Conventions

### Element IDs
- Use descriptive strings: `"title"`, `"box1"`, `"step-3"`, `"arrow-1-to-2"`, `"label-step3"`
- Each ID must be unique across all elements in the diagram
- Keep IDs short but meaningful

### Index (Fractional Indexing for Z-Order)
- The `index` field controls element stacking order (z-index) using fractional indexing
- Uses lexicographic ordering where lower strings = further back, higher strings = further forward
- Use alphanumeric codes in sequence: `"a0"`, `"a1"`, `"a2"`, ... `"a9"`, `"aA"`, `"aB"`, ... `"aZ"`, `"aa"`, `"ab"`, etc.
- Elements are rendered in index order (bottom to top)
- To insert between two elements: use a value between their indices (e.g., between `"a1"` and `"a2"`, use `"a1V"`)
- Excalidraw auto-repairs invalid/missing indices on load via `syncInvalidIndices()`, so approximate values work
- **Ordering rules enforced on load:**
  - Group members must be contiguous in the elements array (grouped together)
  - Bound text elements must immediately follow their container element
  - Frame children must come before the frame element

### Seed and VersionNonce
- `seed`: random integer, typically 5-9 digits (e.g. `Math.floor(Math.random() * 100000)` or larger). Controls rough.js hand-drawn rendering variation
- `versionNonce`: random integer, typically 9+ digits (e.g. `Math.floor(Math.random() * 1000000000)`). Used for version conflict resolution
- Each element MUST have unique values for both fields
- Different seeds produce different hand-drawn line variations for the same element

---

## Complete Element Examples

### Rectangle with Text Inside

```json
[
  {
    "id": "box1",
    "type": "rectangle",
    "x": 100,
    "y": 100,
    "width": 200,
    "height": 60,
    "angle": 0,
    "strokeColor": "#1971c2",
    "backgroundColor": "#a5d8ff",
    "fillStyle": "solid",
    "strokeWidth": 2,
    "strokeStyle": "solid",
    "roughness": 1,
    "opacity": 100,
    "groupIds": [],
    "frameId": null,
    "index": "a0",
    "roundness": { "type": 3 },
    "seed": 1234567890,
    "version": 1,
    "versionNonce": 9876543210,
    "isDeleted": false,
    "boundElements": [{ "id": "box1-text", "type": "text" }],
    "updated": 1751928342106,
    "link": null,
    "locked": false
  },
  {
    "id": "box1-text",
    "type": "text",
    "x": 105,
    "y": 105,
    "width": 190,
    "height": 25,
    "angle": 0,
    "strokeColor": "#1e1e1e",
    "backgroundColor": "transparent",
    "fillStyle": "solid",
    "strokeWidth": 2,
    "strokeStyle": "solid",
    "roughness": 1,
    "opacity": 100,
    "groupIds": [],
    "frameId": null,
    "index": "a1",
    "roundness": null,
    "seed": 2345678901,
    "version": 1,
    "versionNonce": 8765432109,
    "isDeleted": false,
    "boundElements": null,
    "updated": 1751928342106,
    "link": null,
    "locked": false,
    "text": "Start Process",
    "rawText": "Start Process",
    "fontSize": 20,
    "fontFamily": 5,
    "textAlign": "center",
    "verticalAlign": "middle",
    "containerId": "box1",
    "originalText": "Start Process",
    "autoResize": true,
    "lineHeight": 1.25
  }
]
```

### Arrow Connecting Two Boxes

```json
{
  "id": "arrow-1-to-2",
  "type": "arrow",
  "x": 300,
  "y": 130,
  "width": 100,
  "height": 0,
  "angle": 0,
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a2",
  "roundness": { "type": 2 },
  "seed": 3456789012,
  "version": 2,
  "versionNonce": 7654321098,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1751928342106,
  "link": null,
  "locked": false,
  "points": [[0, 0], [100, 0]],
  "startBinding": {
    "elementId": "box1",
    "focus": 0,
    "gap": 5,
    "fixedPoint": null
  },
  "endBinding": {
    "elementId": "box2",
    "focus": 0,
    "gap": 5,
    "fixedPoint": null
  },
  "startArrowhead": null,
  "endArrowhead": "arrow",
  "elbowed": false
}
```

### Diamond (Decision Node)

```json
{
  "id": "decision1",
  "type": "diamond",
  "x": 150,
  "y": 200,
  "width": 150,
  "height": 100,
  "angle": 0,
  "strokeColor": "#e8590c",
  "backgroundColor": "#ffd8a8",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a3",
  "roundness": { "type": 2 },
  "seed": 4567890123,
  "version": 2,
  "versionNonce": 6543210987,
  "isDeleted": false,
  "boundElements": [{ "id": "decision1-text", "type": "text" }],
  "updated": 1751928342106,
  "link": null,
  "locked": false
}
```

### Standalone Text (Title)

```json
{
  "id": "title",
  "type": "text",
  "x": 100,
  "y": 20,
  "width": 400,
  "height": 45,
  "angle": 0,
  "strokeColor": "#1971c2",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "groupIds": [],
  "frameId": null,
  "index": "a0",
  "roundness": null,
  "seed": 5678901234,
  "version": 2,
  "versionNonce": 5432109876,
  "isDeleted": false,
  "boundElements": null,
  "updated": 1751928342106,
  "link": null,
  "locked": false,
  "text": "System Architecture Overview",
  "rawText": "System Architecture Overview",
  "fontSize": 36,
  "fontFamily": 5,
  "textAlign": "left",
  "verticalAlign": "top",
  "containerId": null,
  "originalText": "System Architecture Overview",
  "autoResize": true,
  "lineHeight": 1.25
}
```

---

## Default Element Properties (from Excalidraw source)

When creating elements, these are the defaults the editor uses:

```json
{
  "strokeColor": "#1e1e1e",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 1,
  "opacity": 100,
  "locked": false
}
```

---

## File Naming Convention

- **Format:** `[topic].[diagram-type].md`
- **Use lowercase, hyphen-separated English names**
- **Examples:**
  - `content-creation-flow.flowchart.md`
  - `business-model.relationship.md`
  - `project-timeline.timeline.md`
  - `system-architecture.hierarchy.md`
  - `feature-comparison.comparison.md`
  - `brainstorm-ideas.mindmap.md`
  - `database-schema.er-diagram.md`
  - `infrastructure.network.md`

## Post-Generation Report

After saving the file, report the following to the user:

1. **Confirmation** -- the diagram has been generated and saved
2. **File path** -- the exact save location (absolute path)
3. **How to view** -- open the file in Obsidian, click the MORE OPTIONS menu (three dots), and select "Switch to Excalidraw View"
4. **Design rationale** -- which diagram type was chosen and why
5. **Element count** -- how many shapes, arrows, and text elements were generated
6. **Adjustment offer** -- ask if the user wants any layout, color, or content changes

## Common Pitfalls to Avoid

- Do NOT forget the `%%` markers around the Drawing section
- Do NOT add content to the `## Text Elements` section -- leave it empty
- Do NOT use duplicate element IDs -- every ID must be unique
- Do NOT forget `boundElements` when binding text to shapes or arrows to shapes -- BOTH sides must reference each other
- Do NOT use raw double quotes inside text values -- use single quotes or escaped characters
- Do NOT omit any required fields from elements -- missing fields cause rendering failures
- Do NOT use `excalidraw-plugin: raw` -- always use `parsed`
- Do NOT forget to set `frameId` on child elements when using frames
- Do NOT place frame children AFTER the frame element in the elements array -- children come first
- Do NOT use `"roundness": { "type": 3 }` on diamonds or ellipses -- use `{ "type": 2 }` for diamonds, `null` for ellipses
- Do NOT forget the `points` array on arrow and line elements -- first point must be `[0, 0]`
- Do NOT set `containerId` on a text element without also adding the text to the container's `boundElements`
- Do NOT use `fontFamily` values of `4` -- it is reserved/unused
- Do NOT forget to calculate `width` and `height` of arrows/lines from the points array (width = max x spread, height = max y spread). A value of `0` IS valid for one axis (e.g. a perfectly horizontal arrow has height=0)

## Common Style Recipes

Quick reference for frequently needed style combinations:

**Dashed border with solid fill:**
```json
{ "strokeStyle": "dashed", "backgroundColor": "#a5d8ff", "fillStyle": "solid" }
```

**Borderless filled shape (background zone):**
```json
{ "strokeColor": "transparent", "backgroundColor": "#b2f2bb", "fillStyle": "solid", "roughness": 0 }
```
Note: `strokeColor` can be set to `"transparent"` to hide the border while keeping a visible fill.

**Ghost/watermark element (semi-transparent):**
```json
{ "opacity": 30, "backgroundColor": "#a5d8ff", "fillStyle": "solid" }
```

**Clean technical drawing (no hand-drawn wobble):**
```json
{ "roughness": 0, "strokeWidth": 1, "roundness": { "type": 3 } }
```

**Bold highlighted box:**
```json
{ "strokeWidth": 4, "strokeColor": "#e03131", "backgroundColor": "#ffc9c9", "fillStyle": "solid" }
```

**Line with arrowhead on one end:**
```json
{ "type": "line", "startArrowhead": null, "endArrowhead": "arrow", "points": [[0, 0], [200, 0]] }
```
Yes, `type: "line"` elements can have arrowheads too -- they don't need to be `type: "arrow"`.

**Self-referencing arrow** (arrow that starts and ends on the same shape):
Set both `startBinding.elementId` and `endBinding.elementId` to the same shape ID. Use multi-point `points` to create a loop path, e.g.:
```json
{ "points": [[0, 0], [0, -80], [120, -80], [120, 0]], "elbowed": true }
```

**Arrow label positioning:**
Arrow labels (text bound to an arrow) automatically appear at the arrow's midpoint. The label position is not configurable in JSON -- it is computed at render time from the arrow's path geometry.

## Layout Patterns and Recipes

### Flowchart Pattern

Standard flowchart layout with top-to-bottom flow:

1. Place start node (rounded rectangle or ellipse) at top center
2. Decision nodes use diamonds, process nodes use rectangles
3. Connect with arrows, default `endArrowhead: "arrow"`
4. Use elbow arrows (`elbowed: true`) for clean right-angle routing
5. Space nodes 100-150px apart vertically, 200-250px horizontally for branches
6. Yes/No labels on decision arrows using labeled arrows
7. Group related elements with frames or groupIds
8. Use `fixedPoint: [0.5, 1]` (bottom) for start bindings and `fixedPoint: [0.5, 0]` (top) for end bindings in vertical flows
9. The Excalidraw editor has built-in flowchart creation: Ctrl+ArrowKey on a selected element creates linked child nodes with elbow arrows automatically

**Built-in flowchart constants:** `VERTICAL_OFFSET = 100px`, `HORIZONTAL_OFFSET = 100px` between nodes. The editor's flowchart tool (Ctrl+ArrowKey) uses these exact values.

### Mind Map Pattern

Radial layout expanding from center:

1. Central topic in a large ellipse or rounded rectangle at canvas center (e.g. x:400, y:300)
2. Main branches radiate outward at equal angles
3. Use arrows from center to first-level nodes
4. Sub-branches continue outward from first-level nodes
5. Color-code branches (each main branch gets a unique stroke/fill color pair)
6. Decrease font size at each level: 28 → 20 → 16
7. Use `roughness: 1` for organic, hand-drawn feel

### Timeline Pattern

Horizontal timeline with events:

1. Draw a horizontal line element as the time axis (long line with `points: [[0, 0], [1000, 0]]`)
2. Place event markers as small circles (ellipse elements) along the line
3. Alternate event descriptions above and below the line to avoid crowding
4. Connect descriptions to markers with short vertical arrows
5. Add date labels below each marker
6. Use color coding for event categories

### Hierarchy / Org Chart Pattern

Top-down tree structure:

1. Root node centered at top
2. Children equally spaced below, connected with arrows pointing downward
3. Standard spacing: 200px horizontal between siblings, 120px vertical between levels
4. Use elbow arrows for clean connections
5. Group each level's nodes together
6. Use frames to delineate departments or sections

### Entity Relationship Diagram Pattern

Database schema visualization:

1. Entity boxes as rectangles with entity name as title text
2. Attribute lists as multi-line text inside each rectangle
3. Connect related entities with arrows
4. Use cardinality arrowheads: `"cardinality_one"`, `"cardinality_many"`, `"cardinality_zero_or_one"`, `"cardinality_zero_or_many"`, `"cardinality_one_or_many"`, `"cardinality_exactly_one"`
5. Place relationship labels on arrows using labeled arrows
6. Space entities 300-400px apart

### Bar Chart Pattern

Creating a bar chart from data:

1. Define constants: `BAR_WIDTH` (30-50px), `BAR_GAP` (12-20px), `CHART_HEIGHT` (250-300px), `SLOT_WIDTH` (44-60px)
2. Draw X and Y axes as line elements
3. For each data point, create a rectangle with:
   - `x = startX + (index * SLOT_WIDTH)`
   - `y = axisY - (value / maxValue * CHART_HEIGHT)`
   - `width = BAR_WIDTH`, `height = value / maxValue * CHART_HEIGHT`
   - `fillStyle: "hachure"` for single series, `"solid"` for multi-series
4. Add rotated text labels below each bar (use `angle` ~5.5-5.9 radians for ~30-degree tilt)
5. Add Y-axis labels (0 and max value)
6. Add a title text above the chart
7. For multi-series: group bars within each slot, use distinct colors per series, add a legend
8. Color selection: use `getSeriesColors` approach -- pick maximally-distant colors from the palette

**Built-in chart engine constants** (used when Excalidraw generates charts from spreadsheet data):

| Constant | Value | Used For |
|----------|-------|----------|
| `CARTESIAN_BAR_HEIGHT` | `304` px | Total bar chart area height |
| `CARTESIAN_BASE_SLOT_WIDTH` | `44` px | Base width per data point slot |
| `CARTESIAN_BAR_SLOT_EXTRA_PER_SERIES` | `22` px | Extra width added per additional series |
| `CARTESIAN_GAP` | `14` px | Gap between bars |
| `CARTESIAN_LABEL_ROTATION` | `5.87 rad` (~-24°) | X-axis label rotation angle |
| `CARTESIAN_LINE_SLOT_WIDTH` | `48` px | Slot width for line charts |
| `CARTESIAN_LINE_HEIGHT` | `320` px | Total line chart area height |
| `RADAR_GRID_LEVELS` | `4` | Number of concentric grid rings |
| `RADAR_LABEL_OFFSET` | `24` px | Label distance from outermost ring |

Chart elements use: `fillStyle: "hachure"`, `strokeWidth: 1`, `fontFamily: 5`, `roughness: 1`, `roundness: null`.

### Line Chart Pattern

Creating a line chart from data:

1. Draw X and Y axes as line elements
2. For each data series, create a line element with points at each data value:
   - Each point: `[index * SLOT_WIDTH, -(value / maxValue * CHART_HEIGHT)]` (relative to line start)
3. Add ellipse "dots" at each data point (small circles, ~8x8px, `fillStyle: "solid"`)
4. Add dotted vertical guide lines from x-axis to max value at each x position
5. Add rotated category labels, y-axis value labels, and chart title
6. For multi-series: use distinct strokeColors per line, add a legend

### Radar / Spider Chart Pattern

Creating a radar chart for multi-dimensional comparison (needs 3+ axes):

1. Calculate angles: `angle[i] = (2 * PI * i / numAxes) - PI/2` (start from top)
2. Calculate point positions: `x = centerX + cos(angle) * (value / maxValue * radius)`, `y = centerY + sin(angle) * (value / maxValue * radius)`
3. Draw radial spokes as dotted line elements from center to each axis
4. Draw series polygons as closed line elements (`polygon: true`) connecting data points
5. Position axis labels outside the chart at each spoke end
6. Add a title above and legend below for multi-series
7. Use distinct strokeColors per series polygon

### Comparison / Side-by-Side Pattern

Comparing options, features, or approaches:

1. Create a title text at the top
2. Draw vertical divider lines between columns
3. Place column headers in colored rectangles at the top of each column
4. List items as text elements or small rectangles below each header
5. Use consistent colors per column (e.g. green for pros, red for cons)
6. Optional: add a horizontal line separating the header row from content

### Network / Architecture Diagram Pattern

System architecture and infrastructure visualization:

1. Use rectangles for servers/services, ellipses for databases, diamonds for load balancers/routers
2. Group related services using frames with descriptive names (e.g., "Frontend", "Backend", "Data Layer")
3. Connect with arrows showing data flow direction; use labeled arrows for protocols/ports
4. Place external-facing services at the top, internal services in the middle, data stores at the bottom
5. Use color coding: blue for compute, green for databases, orange for external services, gray for infrastructure
6. Space major components 300-400px apart; keep related services within 150-200px of each other
7. Add a title and optional legend explaining color/shape meanings
8. Use `strokeStyle: "dashed"` for optional/future connections

### Relationship / Dependency Map Pattern

Showing connections between entities:

1. Place entities as rectangles or ellipses, sized proportionally to importance
2. Connect with arrows; use `strokeWidth: 1` for weak connections, `strokeWidth: 4` for strong dependencies
3. Bidirectional relationships: use arrows with `startArrowhead: "arrow"` and `endArrowhead: "arrow"`
4. Add labeled arrows for relationship descriptions
5. Use color to indicate relationship type (e.g., green for positive, red for conflicting, blue for informational)
6. For hub-and-spoke layouts, place the central entity at the center and radiate connections outward
7. Space entities 200-300px apart; avoid crossing arrows where possible

### Matrix / Quadrant Pattern

Two-dimensional classification with labeled axes:

1. Draw two perpendicular line elements forming crosshairs at the center of the diagram
2. Horizontal axis: `points: [[-400, 0], [400, 0]]` with arrowheads at both ends (`startArrowhead: "arrow"`, `endArrowhead: "arrow"`)
3. Vertical axis: `points: [[0, -300], [0, 300]]` with arrowheads at both ends
4. Label each axis end with standalone text (e.g., "Low Effort" / "High Effort" on horizontal, "Low Impact" / "High Impact" on vertical)
5. Label each quadrant with a title in a larger font (e.g., 28px) at the top of each quadrant
6. Place items as small rectangles or ellipses in the appropriate quadrant
7. Use distinct background colors per quadrant for visual separation (e.g., light green for "Do First", light red for "Avoid")
8. Optional: add a frame around the entire matrix

### Freeform / Brainstorm Pattern

Unstructured content organization:

1. Start with the most important items near the center of the canvas
2. Place items as rectangles, ellipses, or standalone text without strict alignment
3. Use arrows sparingly -- only to show clear relationships
4. Vary element sizes to indicate importance (larger = more important)
5. Use color to create visual clusters of related items
6. Add rough grouping with dashed-stroke rectangles or frames around clusters
7. Use `roughness: 2` (Cartoonist) for an informal, brainstorming aesthetic
8. No strict spacing rules -- let the layout feel organic and natural

---

## Arrowhead Sizing Reference

Arrowhead visual size scales with `strokeWidth`:
- **Arrowhead size** = `strokeWidth * 6` (minimum 14px)
- **Arrow angle**: 25 degrees for `"arrow"`, 20 degrees for `"triangle"`, 15 degrees for `"diamond"`
- Arrowheads render proportionally -- thicker arrows get larger arrowheads automatically

This means for `strokeWidth: 2`, arrowheads are 14px (minimum). For `strokeWidth: 4`, arrowheads are 24px.

### Arrowhead Shape Construction

How each arrowhead type is geometrically constructed:

| Arrowhead | Shape | Fill |
|-----------|-------|------|
| `"arrow"` | Two lines from tip backward to wings | No fill (open) |
| `"triangle"` | Filled triangle polygon (3 vertices) | Filled with strokeColor |
| `"triangle_outline"` | Triangle polygon (3 vertices) | Filled with backgroundColor |
| `"diamond"` | Diamond polygon (4 vertices) | Filled with strokeColor |
| `"diamond_outline"` | Diamond polygon (4 vertices) | Filled with backgroundColor |
| `"circle"` | Circle at endpoint | Filled with strokeColor |
| `"circle_outline"` | Circle at endpoint | Filled with backgroundColor |
| `"bar"` | Perpendicular line at endpoint | No fill |
| `"cardinality_one"` | Single perpendicular line | No fill |
| `"cardinality_many"` | Two lines to tip (crow's foot) | No fill |
| `"cardinality_one_or_many"` | Crow's foot + perpendicular line (offset -0.25) | No fill |
| `"cardinality_exactly_one"` | Two perpendicular lines (offsets -0.5 and 0) | No fill |
| `"cardinality_zero_or_one"` | Circle outline (scale 0.8) + perpendicular line (offset -0.5) | Circle: backgroundColor |
| `"cardinality_zero_or_many"` | Crow's foot + circle outline (scale 0.8, offset 1.5) | Circle: backgroundColor |

**Arrowhead roughness:** Capped at `Math.min(1, roughness)` for standard arrowheads and `Math.min(0.5, roughness)` for circles -- ensuring arrowheads are always cleaner than the arrow body.

---

## Style Properties That Get Copied

When users copy/paste styles between elements in the Excalidraw editor, these properties are transferred. This defines what constitutes an element's "style":

- `backgroundColor`
- `strokeWidth`
- `strokeColor`
- `strokeStyle`
- `fillStyle`
- `opacity`
- `roughness`
- `roundness`
- `fontSize` (text only)
- `fontFamily` (text only)
- `textAlign` (text only)
- `lineHeight` (text only)
- `startArrowhead` (arrows only)
- `endArrowhead` (arrows only)

---

## Element Restore and Normalization

Excalidraw's `restoreElements()` function normalizes elements on load, handling missing/legacy fields. This means:

1. **Missing fields are auto-filled** -- if you omit optional fields, restore adds defaults
2. **Legacy properties are migrated:**
   - `strokeSharpness: "round"` → `roundness: { type: 2 }` (lines/diamonds) or `{ type: 3 }` (rectangles)
   - `strokeSharpness: "sharp"` → `roundness: null`
   - `boundElementIds: [...]` → `boundElements: [{ id, type }]`
   - Old arrowhead names: `"dot"` → `"circle"`, `"crowfoot_one"` → `"cardinality_one"`, `"crowfoot_many"` → `"cardinality_many"`, `"crowfoot_one_or_many"` → `"cardinality_one_or_many"`
3. **Bindings are repaired** -- broken references are cleaned up
4. **Frame membership is validated** -- `frameId` pointing to non-existent frames is set to `null`
5. **Duplicate IDs are deduplicated** -- only the first element with a given ID is kept

This means generated diagrams are somewhat forgiving of minor errors, but it's best to include all fields correctly to avoid any restoration surprises.

### AppState Restore Behavior

When loading a file, `restoreAppState()` applies these normalizations:
- **Grid clamping:** `gridSize` and `gridStep` are clamped to `[1, 100]` (rounded to integer)
- **Zoom normalization:** Clamped to `[0.1, 30]` with 6 decimal places. Legacy raw-number zoom is migrated to `{value: N}` format
- **Tool validation:** Active tools are validated against an allow-list. Disallowed tools (`eraser`, `laser`, `magicframe`) are replaced with `"selection"`
- **State reset:** `cursorButton` resets to `"up"`, `editingFrame` resets to `null`, `lastActiveTool` resets to `null`
- **Legacy migration:** `isSidebarDocked` -> `defaultSidebarDockedPreference`

### Auto-Corrected vs. Must-Be-Correct Properties

When Excalidraw loads a file, some properties are automatically fixed, while others must be correct in the JSON:

**Auto-corrected on load (approximate values OK):**
- Text `width` and `height` -- recalculated from text content, font, and container
- Arrow/line `width` and `height` -- reconciled from `points` array bounding box
- Fractional `index` values -- invalid indices are regenerated via `syncInvalidIndices()`
- `version` and `versionNonce` -- defaults applied if missing
- Missing base properties -- filled with defaults (strokeColor, backgroundColor, etc.)
- `roundness` -- migrated from legacy `strokeSharpness`
- Arrowhead names -- legacy names normalized (e.g., `"dot"` -> `"circle"`)

**Must be correct (not auto-corrected):**
- `startBinding`/`endBinding` on arrows AND `boundElements` on shapes -- BOTH sides must reference each other
- `containerId` on text AND `boundElements` on the container shape -- BOTH sides must match
- `frameId` on children -- must reference an existing frame element
- Element ordering in the array -- frame children must come before the frame element
- `points` array on arrows/lines -- first point must be `[0, 0]`; the path determines the arrow shape
- `type` field -- must be a valid element type string

---

## Element Type Conversion Rules

In the Excalidraw editor, elements can be converted between types using Tab/Shift+Tab. Understanding these rules helps when designing diagrams:

**Generic shapes** cycle in order: `rectangle` -> `diamond` -> `ellipse` -> `rectangle`

**Linear elements** cycle in order: `line` -> `sharp arrow` -> `curved arrow` -> `elbow arrow` -> `line`

**Cross-category conversion is NOT allowed** -- you cannot convert a rectangle to an arrow or vice versa.

**Conversion details:**
- When converting between generic shapes, bound text font size auto-shrinks to fit the new container dimensions
- Converting to `diamond` switches roundness from `ADAPTIVE_RADIUS` to `PROPORTIONAL_RADIUS`
- Converting to elbow arrow: line points are sanitized (colinear points dropped, micro-jogs collapsed)
- Bound arrows on a shape are NOT preserved during linear element conversion

---

## Editor Default State (What Users Start With)

When the Excalidraw editor starts fresh, these defaults are applied. Generated diagrams that match these defaults will look most natural:

| Property | Default Value | Notes |
|----------|--------------|-------|
| `currentItemRoundness` | `"round"` | Elements default to rounded corners |
| `currentItemArrowType` | `"round"` | Arrows default to curved (round) path, not sharp |
| `currentItemEndArrowhead` | `"arrow"` | New arrows have an arrowhead at the end |
| `currentItemStartArrowhead` | `null` | No arrowhead at the start |
| `currentItemFontFamily` | `5` (Excalifont) | Hand-drawn font |
| `currentItemFontSize` | `20` | Medium font size |
| `currentItemTextAlign` | `"left"` | Left-aligned text |
| `currentItemFillStyle` | `"solid"` | Solid fill |
| `currentItemStrokeWidth` | `2` | Bold stroke |
| `currentItemRoughness` | `1` | Artist roughness |
| `viewBackgroundColor` | `"#ffffff"` | White canvas |
| `gridSize` | `20` | 20px grid (but grid mode is OFF by default) |
| `isBindingEnabled` | `true` | Arrow binding is enabled |

---

## Element Property Constraints (from Editor UI)

These constraints are enforced in the Excalidraw editor's properties panel:

| Property | Min Value | Step Size | Notes |
|----------|-----------|-----------|-------|
| `fontSize` | `4` (UI) / `1` (schema) | 4 | Steps in increments of 4 |
| `width`, `height` | `1` | 10 | Steps in increments of 10 |
| `x`, `y` | unlimited | 10 | Negative values fully supported |
| `angle` | 0 | 15 degrees | Stored in radians; displayed as degrees; wraps at 360 |
| `opacity` | 0 | slider | 0 = invisible, 100 = fully opaque |

**Angle restrictions:**
- Elbow arrows cannot have their angle changed (always 0)
- Frame-like elements cannot have their angle changed
- Bound text inherits container's angle (except for arrow labels which are always 0)

---

## Embeddable Elements

Embeddable elements display embedded web content (iframes). Supported URL patterns:

| Service | URL Patterns |
|---------|-------------|
| YouTube | `youtube.com/watch`, `youtu.be/`, `youtube.com/embed/` |
| Vimeo | `vimeo.com/`, `player.vimeo.com/video/` |
| Figma | `figma.com/file/`, `figma.com/design/` |
| GitHub Gists | `gist.github.com/` |
| Twitter/X | `twitter.com/`, `x.com/` |
| Google Maps | `google.*/maps`, `maps.google.*` |
| Google Drive | `drive.google.com/file/` |
| Val.town | `val.town/` |
| GIPHY | `giphy.com/gifs/`, `giphy.com/clips/` |

To create an embeddable element, use `type: "embeddable"` and set the URL in the `link` field. The element renders as an iframe in the Excalidraw editor.

**Default aspect ratios for embeddable elements:**

| Service | Width x Height |
|---------|---------------|
| YouTube | 560 x 315 (shorts: 315 x 560) |
| Vimeo | 560 x 315 |
| Google Drive | 560 x 315 |
| Figma | 550 x 550 |
| GitHub Gist | 550 x 720 |
| Twitter/X | 480 x 480 |
| Reddit | 480 x 480 |
| Default (other) | 560 x 840 |

---

## Image Elements

Image elements embed raster images into the diagram:

```json
{
  "type": "image",
  "fileId": "abc123def456",
  "status": "saved",
  "scale": [1, 1],
  "crop": null
}
```

| Field | Type | Description |
|-------|------|-------------|
| `fileId` | string | Reference to the file data in the top-level `files` object |
| `status` | string | `"saved"` for loaded images, `"pending"` for loading |
| `scale` | [number, number] | Horizontal and vertical scale factors. `[1, 1]` = normal, `[-1, 1]` = flipped horizontally |
| `crop` | object\|null | Crop region (see below), or null for no cropping |

**Crop object structure** (when `crop` is not null):
```json
{
  "crop": {
    "x": 0,
    "y": 0,
    "width": 100,
    "height": 100,
    "naturalWidth": 200,
    "naturalHeight": 200
  }
}
```
- `x`, `y`: top-left corner of the crop region within the original image
- `width`, `height`: dimensions of the visible crop area
- `naturalWidth`, `naturalHeight`: original uncropped image dimensions

The corresponding file data goes in the top-level `files` object:

```json
{
  "files": {
    "abc123def456": {
      "mimeType": "image/png",
      "id": "abc123def456",
      "dataURL": "data:image/png;base64,iVBORw0KGgo...",
      "created": 1690295874454,
      "lastRetrieved": 1690295874454
    }
  }
}
```

**Max file size:** 4MB (4 * 1024 * 1024 bytes). Default max image dimension: 1440 pixels.

**Supported image MIME types:** `image/png`, `image/jpeg`, `image/svg+xml`, `image/gif`, `image/webp`, `image/bmp`, `image/x-icon`, `image/avif`, `image/jfif`, `application/octet-stream`

**Image placeholder rendering:**
- When `fileId` is `null` or `status` is `"pending"`: a gray image icon placeholder is displayed (background: `#E7E7E7` light / `#2E2E2E` dark)
- When `status` is `"error"`: a "no entry" error icon is displayed instead
- Placeholder icon size: `min(elementMinSide, min(elementMinSide * 0.4, 100))`, centered in the element
- **SVG export:** Image elements with no loaded file data are silently skipped (not included in SVG output)
- Image `scale` is NOT applied while the image is pending (prevents mirror-flip of placeholder icons)

---

## Minimum Element Sizes

- **Shapes** (rectangle, ellipse, diamond): minimum `width` and `height` of `1`
- **Text**: minimum `fontSize` of `1`
- **Lines/Arrows**: must have at least 2 points in the `points` array; a single-point arrow is valid but renders as a dot
- **Invisible elements**: elements with both `width` and `height` below `0.1px` (`INVISIBLY_SMALL_ELEMENT_SIZE`) are considered "invisibly small" and may be automatically cleaned up

---

## Interaction and Sizing Constants

Key constants from the Excalidraw source that affect element behavior:

| Constant | Value | Description |
|----------|-------|-------------|
| `BOUND_TEXT_PADDING` | `5` px | Padding between container edge and bound text |
| `ARROW_LABEL_WIDTH_FRACTION` | `0.7` (70%) | Max label width relative to arrow length |
| `ARROW_LABEL_FONT_SIZE_TO_MIN_WIDTH_RATIO` | `11` | Min arrow label width = fontSize * 11 |
| `BASE_BINDING_GAP` | `5` px | Base gap between arrow endpoint and bound shape |
| `BASE_ARROW_MIN_LENGTH` | `10` px | Minimum arrow length for bindings |
| `MINIMUM_ARROW_SIZE` | `20` px | Minimum arrow size for reliable rendering |
| `LINE_POLYGON_POINT_MERGE_DISTANCE` | `20` px | Distance below which endpoints merge to close a polygon |
| `INVISIBLY_SMALL_ELEMENT_SIZE` | `0.1` px | Elements smaller than this may be auto-cleaned |
| `MIN_WIDTH_OR_HEIGHT` | `1` px | Minimum dimension for shapes |
| `MIN_FONT_SIZE` | `1` px (schema) / `4` px (UI) | Minimum font size |
| `TEXT_AUTOWRAP_THRESHOLD` | `36` px | Drag distance before text is considered fixed-width |
| `DRAGGING_THRESHOLD` | `10` px | Minimum drag distance to start a drag operation |
| `SNAP_DISTANCE` | `8` px | Threshold for object snapping (divided by zoom) |
| `DEFAULT_ADAPTIVE_RADIUS` | `32` px | Fixed border-radius for rectangles with roundness type 3 |
| `DEFAULT_PROPORTIONAL_RADIUS` | `0.25` (25%) | Proportional border-radius for diamonds/lines |
| `BASE_PADDING` (elbow arrows) | `40` px | Grid padding around obstacles for elbow arrow routing |
| `ELEMENT_TRANSLATE_AMOUNT` | `1` px | Arrow key nudge distance |
| `ELEMENT_SHIFT_TRANSLATE_AMOUNT` | `5` px | Shift+arrow key nudge distance |
| `SHIFT_LOCKING_ANGLE` | `Math.PI / 12` (15°) | Angle increment for shift-locked rotation/drawing |

---

## Programmatic Element Creation (Skeleton API)

The `convertToExcalidrawElements()` function accepts simplified "skeleton" elements and fills in all required properties. Key behaviors:

**Default dimensions when unspecified:**
- Shapes (rectangle, ellipse, diamond): `100 x 100` px
- Shapes with a label but no width: width auto-sizes to fit label text
- Lines/arrows: `100 x 0` px (horizontal by default)
- Images: `100 x 100` px

**Label binding:** Providing a `label: { text: "..." }` on a shape skeleton automatically creates a bound text element with `textAlign: "center"`, `verticalAlign: "middle"`, and `strokeColor` inherited from the container.

**Arrow binding:** Providing `start: { type: "rectangle" }` or `end: { type: "ellipse", id: "existing-id" }` on an arrow skeleton creates bound shapes at computed positions (or binds to existing elements by ID).

**Frame auto-sizing:** Frame skeletons with `children: ["id1", "id2"]` auto-calculate their x/y/width/height from the bounding box of child elements, plus 10px padding on all sides.

**ID regeneration:** By default, all element IDs are regenerated. Cross-references (bindings, containerId, frameId) are automatically updated to use the new IDs.

---

## JSON Validation Rules

For a valid Excalidraw JSON file:
1. `type` must be `"excalidraw"`
2. `elements` must be an array (can be empty)
3. Each element must have a valid `type` field
4. `appState` is optional but recommended
5. `files` is optional (defaults to `{}`)
6. `version` should be `2`
7. The `source` field is informational and does not affect functionality

---

## Named Connection Points for Arrow Bindings

When connecting arrows to shapes, these named positions map to specific `fixedPoint` [x, y] ratios:

| Named Position | fixedPoint Value | Description |
|----------------|-----------------|-------------|
| **top** | `[0.5, 0]` | Center of top edge |
| **bottom** | `[0.5, 1]` | Center of bottom edge |
| **left** | `[0, 0.5]` | Center of left edge |
| **right** | `[1, 0.5]` | Center of right edge |
| **top-left** | `[0, 0]` | Top-left corner |
| **top-right** | `[1, 0]` | Top-right corner |
| **bottom-left** | `[0, 1]` | Bottom-left corner |
| **bottom-right** | `[1, 1]` | Bottom-right corner |
| **center** | `[0.5, 0.5]` | Center of element (rarely used) |

**Tip:** When creating flowcharts with top-to-bottom flow, use `fixedPoint: [0.5, 1]` (bottom) for `startBinding` and `fixedPoint: [0.5, 0]` (top) for `endBinding` to ensure arrows connect at the bottom of the source and top of the target.

---

## Grid Layout Strategy

When laying out many elements in a grid pattern (e.g. comparison tables, feature matrices):

1. **Choose columns:** decide how many columns per row
2. **Calculate cell size:** determine width and height for each cell, plus gap between cells
3. **Position formula:**
   - `x = startX + (columnIndex * (cellWidth + gap))`
   - `y = startY + (rowIndex * (cellHeight + gap))`
4. **Recommended values:**
   - Cell gap: 20-40px
   - Cell width: 150-250px
   - Cell height: 60-100px
5. **Add headers:** place header text/shapes in the first row
6. **Add borders:** optionally wrap each column or the entire grid in a frame

---

## Element Array Ordering Summary

The order of elements in the `elements` array matters for rendering. Follow these rules:

1. **Z-order:** elements later in the array render on top of earlier elements
2. **Frame children first:** all elements with a given `frameId` MUST appear before the frame element itself
3. **Group members contiguous:** elements sharing a `groupId` should be adjacent in the array
4. **Bound text follows container:** a text element with `containerId` should appear immediately after its container
5. **Index field consistency:** the `index` field values should be in ascending order matching the array order

**Recommended element ordering in the array:**
```
1. Background shapes (large rectangles, decorative elements)
2. Frame children (grouped by frame)
3. Frame elements
4. Main shapes (rectangles, ellipses, diamonds) with their bound text immediately after
5. Arrows and lines (on top of shapes)
6. Standalone labels and titles (topmost)
```

---

## Shape Tool Keyboard Shortcuts (Reference)

These are the keyboard shortcuts users use in the Excalidraw editor. Useful context for understanding tool names:

| Key | Tool |
|-----|------|
| `R` | Rectangle |
| `D` | Diamond |
| `O` | Ellipse (Oval) |
| `A` | Arrow |
| `L` | Line |
| `P` | Pencil / Freedraw |
| `T` | Text |
| `F` | Frame |
| `E` | Eraser |
| `H` | Hand (panning) |
| `K` | Laser pointer |
| `V` | Selection |

### Editor Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl/Cmd+S` | Save scene |
| `Ctrl/Cmd+Z` | Undo |
| `Ctrl/Cmd+Shift+Z` or `Ctrl/Cmd+Y` | Redo |
| `Ctrl/Cmd+D` | Duplicate selection |
| `Ctrl/Cmd+G` | Group selection |
| `Ctrl/Cmd+Shift+G` | Ungroup |
| `Ctrl/Cmd+A` | Select all |
| `Ctrl/Cmd+C` / `Ctrl/Cmd+X` / `Ctrl/Cmd+V` | Copy / Cut / Paste |
| `Ctrl/Cmd+Alt+C` | Copy styles |
| `Ctrl/Cmd+Alt+V` | Paste styles |
| `Ctrl/Cmd+[` | Send backward |
| `Ctrl/Cmd+]` | Bring forward |
| `Ctrl/Cmd+Shift+[` | Send to back |
| `Ctrl/Cmd+Shift+]` | Bring to front |
| `Ctrl/Cmd+K` | Add hyperlink |
| `Ctrl/Cmd+Shift+L` | Toggle element lock |
| `Ctrl/Cmd+'` | Toggle grid mode |
| `Ctrl/Cmd+F` | Search menu |
| `Shift+H` | Flip horizontal |
| `Shift+V` | Flip vertical |
| `Shift+1` | Zoom to fit all |
| `Shift+2` | Zoom to fit selection in viewport |
| `Shift+3` | Zoom to fit selection |
| `Ctrl/Cmd+0` | Reset zoom |
| `Ctrl/Cmd++` / `Ctrl/Cmd+-` | Zoom in / Zoom out |
| `Alt+Z` | Toggle zen mode |
| `Alt+R` | Toggle view mode |
| `Alt+S` | Toggle snap mode |
| `Shift+Alt+C` | Copy as PNG |
| `Shift+Alt+D` | Toggle dark/light theme |
| `Q` | Toggle tool lock |
| `Delete` | Delete selected |

These shortcuts are informational for users -- they don't affect JSON generation.

---

## Mermaid Diagram Integration

Excalidraw supports converting Mermaid diagram definitions into native Excalidraw elements. Supported Mermaid diagram types:

`flowchart`, `graph`, `sequenceDiagram`, `classDiagram`, `stateDiagram`, `stateDiagram-v2`, `erDiagram`, `journey`, `gantt`, `pie`, `quadrantChart`, `requirementDiagram`, `gitGraph`, `C4Context`, `mindmap`, `timeline`, `zenuml`, `sankey`, `xychart`, `block`

When generating diagrams, you can use Mermaid syntax as an intermediate representation and then convert to Excalidraw elements. However, for the Obsidian file format, generate the Excalidraw JSON directly.

---

## Rendering Pipeline (How Elements Are Drawn)

Understanding the render pipeline helps create better diagrams:

1. **Background:** canvas is filled with `viewBackgroundColor`
2. **Grid:** rendered if `gridSize` is set (dotted lines with bold lines every N steps)
3. **Non-iframe elements:** rendered in array order with frame clipping applied
4. **Embeddable/iframe elements:** rendered on top of everything else
5. **Frame labels:** rendered as text above each frame

**Frame clipping:** elements inside a frame are visually clipped to the frame's boundary. Elements that extend beyond the frame are cut off visually but their full data is preserved.

**Dark mode rendering:** when `theme` is `"dark"`, a CSS filter `invert(93%) hue-rotate(180deg)` is applied to all elements. SVG exports handle this by wrapping elements in a filter group.

---

## SVG Export Details

When Excalidraw exports to SVG:

1. **Fonts are inlined:** font face declarations with woff2 data are embedded directly in the SVG `<defs>` section
2. **Frames create clip paths:** each frame generates a `<clipPath>` element; frame children are wrapped in a `<g clip-path="...">` group
3. **Scene embedding:** optionally, the full Excalidraw JSON is base64-encoded and embedded in the SVG metadata for round-trip import
4. **Element rendering:** each element is converted to SVG nodes (rect, ellipse, path, text, image, etc.) with proper transforms
5. **Background:** the canvas background is rendered as the first `<rect>` element

This means generated diagrams will render correctly when exported from Obsidian, since all fonts and styling are self-contained in the SVG.

---

## Library Format (.excalidrawlib)

Excalidraw libraries use a separate file format for reusable element collections:

```json
{
  "type": "excalidrawlib",
  "version": 2,
  "source": "https://excalidraw.com",
  "libraryItems": [
    {
      "id": "item-id",
      "status": "published",
      "elements": [],
      "created": 1690295874454,
      "name": "Item Name"
    }
  ]
}
```

| Field | Type | Description |
|-------|------|-------------|
| `type` | string | Always `"excalidrawlib"` |
| `version` | number | Always `2` |
| `status` | string | `"published"` or `"unpublished"` |
| `elements` | array | Array of ExcalidrawElement objects composing this library item |
| `created` | number | Epoch timestamp in milliseconds |
| `name` | string | Display name of the library item |

**Library restrictions:** Elements of type `iframe`, `embeddable`, and `image` cannot be saved to library items.

---

## MIME Types

| Usage | MIME Type |
|-------|----------|
| Excalidraw file | `application/vnd.excalidraw+json` |
| Excalidraw clipboard | `application/vnd.excalidraw.clipboard+json` |
| Excalidraw library | `application/vnd.excalidrawlib+json` |
| SVG export | `image/svg+xml` |
| PNG export | `image/png` |

---

## Clipboard Format

When copying Excalidraw elements to clipboard, the JSON format differs slightly from the file format:

```json
{
  "type": "excalidraw/clipboard",
  "elements": [...],
  "files": {...}
}
```

Note: `type` is `"excalidraw/clipboard"` (not `"excalidraw"`), and there is no `appState` or `version` field.

---

## Zoom Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `MIN_ZOOM` | `0.1` (10%) | Minimum zoom level |
| `MAX_ZOOM` | `30` (3000%) | Maximum zoom level |
| `ZOOM_STEP` | `0.1` | Zoom increment per step |

Zoom is normalized: `clamp(round(zoom, 6), 0.1, 30)`.

## Export Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `EXPORT_SCALES` | `[1, 2, 3]` | Available export scale multipliers |
| `DEFAULT_EXPORT_PADDING` | `10` px | Padding around exported content |
| `MAX_DECIMALS_FOR_SVG_EXPORT` | `2` | Decimal precision in SVG coordinates |
| `MAX_ALLOWED_FILE_BYTES` | `4,194,304` (4MB) | Maximum file size for embedded images |
| `DEFAULT_MAX_IMAGE_WIDTH_OR_HEIGHT` | `1440` px | Default max dimension for images |

---

## Snapping Behavior

When elements are dragged or resized in the Excalidraw editor, they snap to other elements:

- **Point snaps:** element corners and centers snap to other elements' corners and centers
- **Gap snaps:** elements snap to maintain equal spacing between neighbors
- **Snap distance:** default visual snap threshold for alignment
- **Grid snapping:** when grid is enabled, elements snap to grid intersections

This doesn't affect JSON generation directly, but understanding snapping explains why users expect well-aligned elements. When generating diagrams, align elements to consistent grid-like positions (multiples of 20px work well with the default grid).

### Snap Algorithm Details

- **Snap distance:** `SNAP_DISTANCE / zoom` = `8 / zoom` pixels (snaps get tighter when zoomed in)
- **Point snapping:** Element corners and centers snap to other elements' corners and centers along horizontal/vertical axes
- **Gap snapping:** When three or more elements are in a row, dragging one will snap to maintain equal spacing with its neighbors. Gap directions: center_horizontal, center_vertical, side_left, side_right, side_top, side_bottom
- **Snap enable logic:** When `objectsSnapModeEnabled` is on, holding Ctrl/Cmd temporarily DISABLES snapping. When off, Ctrl/Cmd temporarily ENABLES snapping (only if grid mode is also off)
- **Single arrows are excluded** from object snapping (to allow free binding behavior)

---

## Troubleshooting Generated Diagrams

If a generated diagram doesn't render correctly in Obsidian:

1. **Blank canvas / nothing visible:**
   - Check that `excalidraw-plugin: parsed` is in the frontmatter (not `raw`)
   - Verify the `%%` markers surround the Drawing section
   - Ensure the JSON is valid (no trailing commas, unclosed brackets, unescaped quotes)
   - Check that `"isDeleted": false` on all elements

2. **Elements missing or invisible:**
   - Verify `opacity` is not `0`
   - Check `width` and `height` are > 0 for shapes (elements with both = 0 are auto-cleaned)
   - Ensure `strokeColor` is not `"transparent"` on unfilled elements
   - For text: check `text` field is not empty

3. **Arrows not connecting to shapes:**
   - Verify BOTH sides are linked: arrow's `startBinding`/`endBinding` AND shape's `boundElements`
   - Check `elementId` in bindings matches the actual shape `id`
   - Ensure target shapes are bindable types (not arrows, lines, or freedraw)

4. **Text not appearing inside shapes:**
   - Check text's `containerId` matches shape's `id`
   - Check shape's `boundElements` includes `{ "id": "textId", "type": "text" }`
   - Only ONE text element per container

5. **Frame children not clipped:**
   - Ensure frame children appear BEFORE the frame element in the array
   - Check `frameId` on children matches the frame's `id`

6. **JSON parse errors:**
   - Replace double quotes inside text values with single quotes
   - Ensure no literal newlines in string values (use `\n` instead)
   - Check for duplicate keys in objects

7. **Elements stacked wrong:**
   - Verify `index` values are in ascending lexicographic order
   - Ensure bound text elements follow their containers in the array

## Obsidian Plugin Features

The Obsidian Excalidraw plugin extends the base Excalidraw editor with additional capabilities:

- **LaTeX/MathJax support:** Equations can be rendered as SVG and embedded in diagrams
- **PDF integration:** PDF pages can be embedded and annotated
- **Script engine:** Users can write custom JavaScript scripts that automate diagram operations (100+ community scripts available)
- **SVG to Excalidraw conversion:** Import SVG files and convert them to native Excalidraw elements
- **OCR:** Optical character recognition for extracting text from images within diagrams
- **Transclusion:** Obsidian notes can be transcluded (embedded) within Excalidraw drawings
- **23 language localizations:** Full internationalization support

These features are available through the Obsidian UI but don't affect the JSON format. Generated `.md` files are fully compatible with all plugin features.

### Obsidian-Specific Format Details

The Obsidian Excalidraw plugin has some format differences from vanilla Excalidraw:

- **Compressed format:** Files can use ` ```compressed-json ` instead of ` ```json ` for smaller file sizes. Data is LZ-string compressed.
- **Bracket encoding:** Obsidian encodes `[` as `&#91;` in JSON to prevent creating phantom links in Obsidian's graph view. The plugin's JSON parser reverses this on load.
- **Link format:** Supports Obsidian `[[wikilinks|alias]]` syntax in addition to standard `[alias](url)`. Links prefixed with `!` are transclusions (embedded content).
- **Font family 4:** Historically used for the "Assistant" font or custom fonts in Obsidian. Now unused in vanilla Excalidraw -- always use font family 5 (Excalifont) instead.
- **rawText property:** Obsidian adds a `rawText` field to text elements containing the original markdown before parsing. Vanilla Excalidraw deletes this field during restore.

For generated diagrams, use the standard `parsed` format with ` ```json ` blocks. The plugin handles both formats transparently.

### Obsidian Extended Markdown Sections

The full Obsidian Excalidraw `.md` file can contain additional sections beyond the basic format:

**`## Element Links` section** (plugin version 2.0.26+):
Stores non-text element hyperlinks in format: `elementId: linkURL` (one per line, separated by blank lines). Previously, links were stored inline with text element blocks.

**`## Embedded Files` section:**
Stores references to embedded Obsidian files with these formats:
- Wiki-link: `elementId: ![[filename.ext]] {colorMap}` -- where the optional `{colorMap}` is a JSON object for SVG color replacement (e.g., `{"#000000":"#ff0000"}`)
- URL: `elementId: https://example.com/image.png`
- LaTeX: `elementId: $$equation$$`

**Checkbox parsing:**
When enabled in plugin settings, Markdown checkboxes in text elements are converted:
- `- [ ]` -> custom "todo" character
- `- [x]` -> custom "done" character

**Null property repair:**
The plugin automatically repairs null values that would break rendering: `x: null` -> `0`, `y: null` -> `0`, `fontSize: null` -> `20`, `binding.focus: null` -> `0`.

**Deleted elements preservation:**
Deleted elements (`isDeleted: true`) are filtered out of the working set but preserved on disk for collaboration/versioning. They are re-appended during save.
