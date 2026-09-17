# Vecmap Modifier Prototype

A browser-based bitmap tracing, SVG fixing, collage, trimming, and visual-effects workstation.

> Packaging note: `#Vecmap Mod FN.html` is copied byte-for-byte to `index.html`.

## Tool Architecture

Two top-level areas:

1. **Bitmap Autotracer**
2. **IMG Collager**

### Bitmap Autotracer subtabs

- Image Tracer
- SVG Fixer

### IMG Collager subtabs

- IMG Collager
- Bitmap Trimmer
- Visual Effects

The global reset clears all five working tool states while preserving theme and site-network mode.

## 1. Image Tracer

Converts bitmap images into optimized silhouette-style SVG contours.

The source describes:

- two dominant output colors: background + foreground,
- silhouette processing,
- multiple trace engines,
- maximum 10 images per trace batch.

Trace output can be previewed and downloaded as SVG.

### Trace Engines / External Runtimes

The source references engines such as:

- ImageTracer.js 1.2.6
- Potrace
- VTracer / `@neplex/vectorizer`

Some engine choices explicitly require the app's internet mode to be ON.

Relevant external runtime URLs include:

```text
https://cdn.jsdelivr.net/npm/imagetracerjs@1.2.6/imagetracer_v1.2.6.min.js
https://cdn.jsdelivr.net/gh/kilobtye/potrace@master/potrace.js
https://esm.sh/@neplex/vectorizer
```

## 2. SVG Fixer

SVG-only repair/analysis workspace.

The source supports a maximum of:

```text
3 SVG Fixer slots
```

Tools/workflows in the source include analysis and repair for areas such as:

- curves/arcs,
- extrema,
- inflection points,
- overlap,
- path efficiency,
- bounding paths,
- per-shape/global operations,
- reset to original SVG,
- fixed SVG preview/export.

The source also includes OCR-oriented workflows for selected shapes/multiple shapes.

### OCR / CV Runtimes

Referenced external runtimes include:

```text
https://cdn.jsdelivr.net/npm/tesseract.js@5/dist/tesseract.min.js
https://docs.opencv.org/4.x/opencv.js
```

## 3. IMG Collager

Creates square image collages.

The source describes:

- up to 16 images,
- no-crop fitting,
- drag/swap ordering,
- configurable 0–25 px gaps,
- transparent background support,
- 3000 × 3000 export.

## 4. Bitmap Trimmer

Batch crop/trim workspace for same-ratio images.

Features include:

- imported image set,
- sample/selection workflow,
- crop guides,
- ratio controls,
- slicers,
- synchronized/parallel crop behavior,
- output preview,
- batch export.

## 5. Visual Effects

Per-image and batch effects workspace.

The source includes:

- effect presets,
- per-image state,
- batch/default state,
- transforms,
- flip operations,
- editable censorship geometry,
- working preview,
- output-per-image preview,
- single/batch export.

The UI specifies a maximum of:

```text
9 images
```

for same-aspect-ratio Visual Effects batches.

## Session Autosave

Vecmap Modifier stores working state in IndexedDB.

Implementation identifiers:

```text
Database: MediaModifierV2AutotracerSession
Version: 1
Store: session
Key: latest
```

## External Styling Resource

Google Fonts / Inter:

```text
https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap
```

The source loads this non-blockingly.

## Network Control

The interface contains its own site-level network toggle/status.

This controls whether online-required engines/features are allowed by the application; it does not disable network access for the browser/device itself.

## Other External Runtime URLs

The unchanged source also references:

```text
https://cdn.jsdelivr.net/npm/imagetracerjs@1.2.6/imagetracer_v1.2.6.min.js
https://cdn.jsdelivr.net/gh/kilobtye/potrace@master/potrace.js
https://cdn.jsdelivr.net/npm/tesseract.js@5/dist/tesseract.min.js
https://docs.opencv.org/4.x/opencv.js
https://esm.sh/@neplex/vectorizer
```

These engine-specific resources require internet when selected.

## External Creator Link

```text
https://www.instagram.com/ervinf.dsg
```

## Browser APIs

Important capabilities include:

- Canvas 2D
- SVG DOM / DOMParser / XMLSerializer
- File API
- Blob / Object URLs
- IndexedDB
- dynamic script/module loading
- WebAssembly/worker-based runtimes where required
- pointer events
- browser downloads / ZIP workflows

## Running Locally

Open:

```text
index.html
```

Some tools can operate with local/browser-native logic. Online trace/OCR/vectorizer engines need their external runtime resources.

Optional server:

```bash
python -m http.server 8080
```

## GitHub Pages

The application is a static frontend suitable for GitHub Pages. Internet-dependent engines remain subject to their external CDN availability.

## Project Structure

```text
.
├── index.html
├── README.md
└── .gitignore
```

## Copyright

The source footer states:

```text
©2026 Ervin Faristiyanto. All rights reserved.
```

No new project-wide `LICENSE` file is added.
