# Context Engineering — Knowledge Base

## What this repo is

A self-contained knowledge base website for Context Engineering content built by Impetus. It covers how context engineering works across cloud platforms (AWS, Databricks, Snowflake, Azure) and is used for partner meetings, internal reference, and demos.

The site is a **single HTML file** (`index.html`) that works locally (open in browser) and deploys to GitHub Pages without a build step.

---

## Why this was built

Impetus has developed Context Engineering capabilities around three pillars:
- **Context Studio** — BUILD phase: authors, curates, and governs semantic context
- **Knowledge Graph** — STORE phase: the living semantic store (entities, metrics, ontologies, policies, lineage)
- **Context Fiber** — RUN phase: discovers, ranks, filters, and delivers context to AI agents at runtime

This site documents how these pillars map onto customer cloud stacks, what gaps exist in native cloud tooling, and how Impetus fills them.

---

## Site structure

```
ce-knowledge-base/
└── index.html          ← entire site: shell + all content + JS routing
```

Everything lives in `index.html`. There are no external dependencies, no build tools, no server required.

### Navigation model
- **Top nav**: Platforms · Concepts · Use Cases
- **Sidebar**: slides in from the left when a top nav item is clicked; hidden by default so competitor platform names are not visible during presentations
- **Breadcrumb**: always shows current location when sidebar is closed
- **Content panels**: `<div id="page-xxx" class="page">` — show/hide via JS

### Adding a new page (two steps)
1. Add a `<div class="sidebar-item">` entry in the relevant sidebar section with `onclick="loadPage('xxx', ['Nav','Path','Label'], this)"`
2. Add a `<div id="page-xxx" class="page">` block in the content area with the page content

No other changes needed.

---

## Content that exists today

### Platforms → AWS
| Page | ID | Status |
|---|---|---|
| Level 1 Stack | `aws-level1` | ✓ Live |
| Competitive Positioning | `aws-competitive` | ✓ Live |
| Architecture | `aws-arch` | Placeholder |
| Use Cases | `aws-usecases` | Placeholder |

### Platforms → Databricks, Snowflake, Azure
All placeholders — sidebar groups exist, content not yet written.

### Concepts (all placeholders)
Business Glossary · Semantic Model (OSI) · ODPS / ODCS · Ontology · Knowledge Graph · Policy Bindings · Data Lineage

### Use Cases (all placeholders)
Amazon UK Delivery · BFSI — CET1 Capital Adequacy

---

## Key content context

### The Amazon UK delivery example
The primary worked example used throughout the AWS content. Sarah asks: *"Where is my order and when will it arrive?"*

Key terms in Amazon's internal dictionary:
- `DEL` — Delivered: requires photo proof + postcode match + doorstep scan. NOT just a status string.
- `ATT` — Attempted: photo taken but postcode mismatch or no safe place
- `SAF` — Safe place: delivered to neighbour or safe location with photo
- `EDD` — Estimated Delivery Date: `order_date + processing_days + transit_days + weekend_adjustment`

AWS Level 1 mapping (what AWS can do natively, and the gaps):
- Business Glossary → AWS Glue Data Catalog (has column names/types, NOT business definitions)
- Semantic Model → Amazon QuickSight Q topics (has EDD metric but locked inside QuickSight, not callable by Bedrock Agent)
- Knowledge Graph → Amazon Neptune (stores graph but nodes have no OWL class bindings)

### The competitive positioning argument
If Amazon ships a native "Context" service, it closes the RUN and STORE gaps (governed metrics, semantic graph bindings, single API). It does NOT close the BUILD phase gaps: no visual authoring tool, no Golden Gatekeeper before release, no ACE feedback loop, no ODCS breach alerts, no PBAC manager, not portable across clouds.

**One-liner**: Amazon Context closes RUN and STORE. Impetus owns BUILD — and without a governed build phase, what you store and serve is still ungoverned.

---

## Design conventions

- **Theme**: light, clean — white cards on `#F0F4F8` background
- **Font**: Segoe UI / system-ui for prose; Courier New for diagrams
- **Diagrams**: `<div class="diagram">` with `white-space: pre` and colored `<span>` tags
- **Color classes**: `.c-blue` `.c-green` `.c-red` `.c-amber` `.c-purple` `.c-orange` `.c-gray` `.c-dark` `.c-query`
- **Layout classes**: `.section` `.two-col` `.gaps-row` `.gap-card.closes` `.gap-card.remains` `.compare` table
- **No external CSS frameworks, no JS libraries** — everything is vanilla

---

## Pending content to build

Priority order based on partner meetings scheduled:
1. **Databricks** — Level 1 Stack and Competitive Positioning (same structure as AWS)
2. **Concepts → Business Glossary** — the Amazon dictionary example with machine-readable YAML
3. **Concepts → Semantic Model** — EDD formula in OSI format
4. **Use Cases → Amazon UK Delivery** — full end-to-end walkthrough across all 8 semantic components
5. **Snowflake** — Level 1 Stack
6. **Azure** — Level 1 Stack

---

## Related files (outside this repo)

The AWS content originated from a longer session building a PPT deck. Related files live at:
- `/Users/inbravo/GitHub/my-agent-foundry/[aws]-[ce-for-agents]-[2026-06]/ppt/` — PPT versions of the same content
- `/Users/inbravo/GitHub/my-agent-foundry/[aws]-[ce-for-agents]-[2026-06]/code/` — Python scripts that built the PPTs
- `/Users/inbravo/GitHub/my-agent-foundry/[aws]-[ce-for-agents]-[2026-06]/aws_context_stack.html` — earlier standalone HTML version (two-tab format, superseded by this repo)

---

## GitHub Pages deployment

To publish: push to `main` branch, enable GitHub Pages from repo Settings → Pages → Source: `main` / `/ (root)`. The site will be live at `https://inbravo.github.io/ce-knowledge-base/`.
