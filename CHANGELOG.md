# Changelog

All notable changes to the Data Center Mechanical Design Kickoff Tool.

## [1.0.0] — 2026-11-11

### Added
- Initial public release, prepared for GitHub Pages hosting from `index.html` at the repository root.
- Visible version number and last-updated date in the header and footer (v1.0.0, 11 November 2026).
- In-app privacy and local-storage notice: documents are extracted locally in the browser, local save is per-browser only and is not a shared project database.
- `.nojekyll` so GitHub Pages serves the site as plain static files.
- `README.md` documenting purpose, features, local run, GitHub Pages deployment, Google Sites iframe embed, third-party libraries, and privacy.
- Responsive improvements: deliverables table scrolls horizontally on small screens, toolbar buttons wrap / expand on mobile.

### Preserved (unchanged from the supplied tool)
- Document intake and browser extraction for PDF, DOCX, XLSX, XLS, CSV, TXT and text-based IFC.
- Candidate detection, source references, and accept-into-design-basis review.
- Design basis, system strategy, equipment schedule, preliminary cooling / airflow / chilled-water / pump calculations, coordination checklist, and risk & decision log.
- Local save (`localStorage`), JSON export, CSV document-register export, and print / PDF.
