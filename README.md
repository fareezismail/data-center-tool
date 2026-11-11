# Data Center Mechanical Design Kickoff Tool

**Version 1.0.1 · Last updated 11 November 2026**

A browser-based, client-side workspace to help mechanical engineers establish a preliminary data center design basis from architectural and project documents.

Live site (GitHub Pages, once deployed): `https://fareezismail.github.io/data-center-tool/`

> This tool is a design-management and preliminary-calculation aid. It does **not** establish code compliance, equipment selection, reliability certification, final load, or construction-ready design. Verify all extracted data against the signed / current source document and coordinate with the architect, owner, utilities, vendors, AHJ and engineer of record. Every extracted value is an unverified proposal until a mechanical engineer confirms it.

## What it does

- **Document intake** — upload architectural / project documents and extract searchable text in the browser. Supported: PDF, DOCX, XLSX, XLS, CSV, TXT, and text-based IFC. Native Revit (.rvt), DWG, Navisworks, point-cloud and scanned-PDF files are not directly interpreted — export schedules / views to PDF, XLSX, CSV, IFC or searchable PDF first.
- **Suggested data** — rule-based candidate detection maps recognisable values (IT load, rack density / count, gross area, PUE/WUE, outdoor design conditions, ceiling / plenum heights, air temperatures, phasing) to design-basis fields, with source file, snippet and confidence. Accept a candidate only after review.
- **Design basis** — project, location, facility type, phase, IT load, area, rack data, outdoor conditions, site / architectural constraints, OPR, sustainability targets, phasing and assumptions, with accepted-evidence traceability.
- **System strategy** — heat-rejection architecture, white-space air system, liquid-cooling strategy, redundancy, water approach, IAQ, controls / BMS, maintainability.
- **Equipment schedule** — concept-level mechanical equipment rows (tag, type, capacity / duty). Placeholder capacities are not selected equipment.
- **Preliminary calculations** (screening-level only):
  - IT heat load + cooling duty (kW / refrigeration tons, with design margin)
  - Airflow screening (ρ·Cp·ΔT)
  - Chilled-water flow screening (ρ·Cp·ΔT)
  - Hydronic pump input screening (ρgQH/η)
- **Coordination** — mechanical coordination checklist and a risk / decision / RFI log.
- **Save / export / print** — save in this browser, export project data to JSON, export the document register to CSV, print / save to PDF.

## How to run locally

No build step, no backend, no install.

```bash
# Option 1 — open the file directly
open index.html

# Option 2 — serve over HTTP (recommended, so file downloads / printing behave normally)
python3 -m http.server 8000
# then open http://localhost:8000/
```

## How it is deployed (GitHub Pages)

1. This repository's `index.html` is at the repo root, with all CSS/JS inline — there are no local file-path dependencies and no build step.
2. GitHub Pages is enabled from the `main` branch, root folder (`/`).
3. `.nojekyll` is included so GitHub Pages serves the site as plain static files.
4. The public URL is `https://fareezismail.github.io/data-center-tool/`

## Embedding in Google Sites

Google Sites does not run custom HTML directly. Use **Insert → Embed → Embed code** and paste an iframe pointing at the Pages URL:

```html
<iframe src="https://fareezismail.github.io/data-center-tool/" width="100%" height="1200" style="border:0" title="Data Center Mechanical Design Kickoff"></iframe>
```

- The app is a single static page with no frame-busting code, so it works in an iframe.
- Give the embed plenty of height (1200px or more) — the tool has five tabs and long panels.
- Test the embedded page on desktop and mobile: the layout stacks to one column below 800px.

## Privacy — read this before uploading documents

- **Documents are not transmitted to an external service.** Extraction runs locally in the browser using `FileReader` / `ArrayBuffer`. No document content is sent to a server by this app.
- **Third-party libraries (code only, loaded on demand from cdnjs):**
  | Library | Version | Used for | URL |
  |---|---|---|---|
  | pdf.js | 3.11.174 | PDF text extraction | `https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js` (+ `pdf.worker.min.js`) |
  | Mammoth | 1.8.0 | DOCX text extraction | `https://cdnjs.cloudflare.com/ajax/libs/mammoth/1.8.0/mammoth.browser.min.js` |
  | SheetJS (xlsx) | 0.18.5 | XLSX / XLS sheet extraction | `https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js` |
  
  These load JavaScript code only. They do not receive your documents. Plain TXT, CSV and IFC work without any of them. Internet access is required the first time a PDF / Word / Excel file is extracted; afterwards the libraries are cached by the browser.
- **No analytics, no tracking, no backend, no accounts.** The app makes no `fetch` / `XMLHttpRequest` calls of its own.
- **Local storage is not a shared project database.** "Save project locally" writes to `localStorage` key `dcMechanicalDesign` in *that browser on that device only*. Data saved by one user is **not** automatically accessible to other users, other browsers, or other devices. To share a project, use **Export project data (JSON)** and send that file, or re-upload the source documents on the other machine.

## Repository layout

```
data-center-tool/
├── index.html      # the whole app (inline CSS + JS, GitHub Pages entry point)
├── README.md       # this file
├── CHANGELOG.md    # version history
└── .nojekyll       # serve as plain static files on GitHub Pages
```

## Browser support

Modern desktop and mobile browsers (Chrome, Edge, Firefox, Safari). File upload, `localStorage`, printing and downloads must be allowed by the browser / iframe host.

## Changelog

See [CHANGELOG.md](CHANGELOG.md).
