# Presentation Extension

Load this reference only when the user explicitly asks to generate, update, or export a presentation artifact such as HTML, deck, PPT, report page, read-through page, or slide-style output.

## Source Principle

Wiki Markdown is the truth source. Presentation files are generated products.

Do not use files in `presentation/` or `presentation/exports/` as knowledge sources for ordinary query, ingestion, or maintenance.

## Output Locations

- Main HTML output: `presentation/*.html`
- Optional exports such as PDF, DOCX, or PPTX: `presentation/exports/`

Only create exports when the user explicitly asks for them.

## Before Generating

Confirm or infer:

- Source wiki page or pages.
- Desired output type: deck, report, article, brief, poster, or other.
- Output path.
- Style source.
- Whether exports are required.

If the target knowledge base has a style registry, use only existing active styles declared by that registry. Do not invent new modes, registries, or styles unless the user asks to create them.

If no style system exists and the user has not specified a style, ask for style direction before generating.

## Guardrails

- Do not add scripts, compilers, or build systems automatically.
- Do not modify external style directories while generating output.
- Do not overwrite a source wiki page with generated HTML.
- Do not update dashboards by scanning generated outputs unless the local rules say to do so.
- Keep generated artifacts human-facing and isolated from knowledge retrieval.
