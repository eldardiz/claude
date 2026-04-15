---
name: axamo-site-audit
description: |
  Full website audit system for Axamo client projects. Use this skill whenever a client URL is provided and an audit, analysis, brief, or pre-project review is needed. Also trigger when Eldar says things like "analyze this site", "what's wrong with their site", "pull together a brief", "what can we improve", "audit before the call", or "give me talking points on their website". Produces a structured .xlsx file with four sheets: Overview (area scores), SEO & AEO (gaps + recommendations), Design & Dev (bugs + redesign direction), and Copy (current vs. suggested). Orange + white color scheme matching Axamo's brand standards.
---

# Axamo Site Audit

Produces a full client website audit as a structured .xlsx file. Four sheets, orange + white, ready to send to clients or use internally before a sales/strategy call.

## Process

### 1. Fetch the site

Use `web_fetch` on the homepage first, then any key subpages (e.g. /services, /about, /pricing, /contact, /blog). Collect:

- Page titles and meta descriptions (or absence of them)
- Navigation structure and any broken links (href="#", href="/")
- All copy: hero headline, subhead, section headers, CTA text, testimonials, FAQ
- Social proof: client logos, testimonials (check for placeholder images)
- Schema markup (look for <script type="application/ld+json"> in the HTML)
- Blog structure and internal linking patterns
- Any obvious dev bugs: broken form labels, missing images, placeholder text

### 2. Score the site across four layers

For each area below, assign a score 1–5 and a priority (High / Medium / Low):

- SEO: page titles, meta descriptions, schema markup, internal linking, keyword targeting
- AEO: FAQPage schema, structured data, AI-readable content, entity definition
- Design: visual identity, social proof quality, section-level consistency, mobile feel
- Dev: broken links, form issues, missing images, nav errors
- Copy: hero claim, service descriptions, CTA language, process section, testimonials

### 3. Build the .xlsx

Use `openpyxl`. Four sheets, orange + white color scheme. Exact spec below.

---

## Color Palette

| Token        | Hex       | Use                        |
|--------------|-----------|----------------------------|
| ORANGE       | E05C1B    | Section headers, title bar |
| LIGHT_ORANGE | FFE5D6    | Column headers background  |
| WHITE        | FFFFFF    | Data rows (even)           |
| LIGHT_GRAY   | F5F5F5    | Data rows (odd, alt)       |
| ORANGE_TEXT  | C0390B    | Column header text         |
| DARK         | 222222    | Data cell text             |

All fonts: Arial. Thin borders on all data cells (color: DDDDDD).

---

## Sheet 1: Overview

Title row (merged A1:C1): "[CLIENT NAME] — WEBSITE ANALYSIS", white text on orange, size 14, height 36.
Subtitle row (merged A2:C2): "Prepared by Axamo · [domain]", gray text (#777777), light gray bg, height 22.
Empty spacer row (height 10).

Section header: "AREA SCORES  (1 = needs major work · 5 = solid)"
Column headers: Area | Score | Priority

Score rows (alternating white/light-gray):
- SEO — Page Titles & Meta
- SEO — Schema Markup
- SEO — Internal Linking
- AEO — FAQ Schema
- AEO — Blog Content Depth
- Design — Visual Identity
- Design — Social Proof
- Dev — Broken Links / Bugs
- Copy — Hero & Positioning
- Copy — Services Section

Column widths: A=28, B=52, C=18

---

## Sheet 2: SEO & AEO

Title row: "SEO & AEO — GAPS & RECOMMENDATIONS"

Two sections:

**CURRENT GAPS** — columns: Issue | Detail | Impact
**RECOMMENDATIONS** — columns: Action | Detail | Priority

Populate based on what was found during the crawl. Standard gaps to check for:
- Missing/generic page titles
- No meta descriptions
- No Organization schema
- No FAQPage schema despite FAQ section existing
- No BreadcrumbList
- Blog with no internal links to service pages
- No case study or results page
- No keyword targeting for core service term

Column widths: A=28, B=50, C=22. Row height: 42.

---

## Sheet 3: Design & Dev

Title row: "DESIGN & DEV — ISSUES & DIRECTION"

Two sections:

**BUGS & DEV ISSUES** — columns: Issue | Detail | Fix
**DESIGN DIRECTION — REDESIGN SCOPE** — columns: Section | Current State | Improvement Direction

Dev bugs to check:
- Nav links routing to "/" or "#"
- CTA/learn more buttons linking to "#"
- Form option labels not rendering (CMS binding issues)
- Placeholder images in testimonials
- Missing alt text

Design direction covers: Hero, Social Proof, Testimonials, Process section, FAQ section, Blog layout, Overall aesthetic.

Column widths: A=28, B=50, C=22. Row heights: 42 (bugs), 52 (design rows).

---

## Sheet 4: Copy

Title row: "COPY — CURRENT VS. SUGGESTED"

Section header: "COPY REVIEW"
Columns: Element | Current Copy | Issue / Suggested Direction

Copy elements to review:
- Hero headline (watch for unsupported "#1" claims, generic positioning)
- Hero subhead / CTA (watch for "FREE" framing on premium-priced services)
- Each service description (process vs. outcome language)
- Process/steps section (internal descriptions vs. buyer outcomes)
- Why us section (weak constructions, gerund-heavy phrasing)
- Testimonials (vague praise vs. specific proof)

Column widths: A=22, B=40, C=40. Row heights: 52.

---

## Python boilerplate

```python
from openpyxl import Workbook
from openpyxl.styles import Font, PatternFill, Alignment, Border, Side
from openpyxl.utils import get_column_letter

wb = Workbook()

ORANGE      = "E05C1B"
LIGHT_ORANGE = "FFE5D6"
WHITE       = "FFFFFF"
LIGHT_GRAY  = "F5F5F5"
ORANGE_TEXT = "C0390B"
DARK        = "222222"

def fill(hex): return PatternFill("solid", start_color=hex, end_color=hex)
def thin_border():
    s = Side(style="thin", color="DDDDDD")
    return Border(left=s, right=s, top=s, bottom=s)

def title_row(ws, text, subtitle):
    ws.merge_cells("A1:C1")
    ws["A1"] = text
    ws["A1"].font = Font(name="Arial", bold=True, size=13, color="FFFFFF")
    ws["A1"].fill = fill(ORANGE)
    ws["A1"].alignment = Alignment(horizontal="left", vertical="center", indent=2)
    ws.row_dimensions[1].height = 34

def section_header(ws, row, label):
    ws.merge_cells(f"A{row}:C{row}")
    ws[f"A{row}"] = label
    ws[f"A{row}"].font = Font(name="Arial", bold=True, size=10, color="FFFFFF")
    ws[f"A{row}"].fill = fill(ORANGE)
    ws[f"A{row}"].alignment = Alignment(horizontal="left", vertical="center", indent=2)
    ws.row_dimensions[row].height = 24

def col_headers(ws, row, labels):
    for i, label in enumerate(labels):
        col = ["A","B","C"][i]
        c = ws[f"{col}{row}"]
        c.value = label
        c.font = Font(name="Arial", bold=True, size=9, color=ORANGE_TEXT)
        c.fill = fill(LIGHT_ORANGE)
        c.alignment = Alignment(horizontal="left", vertical="center", indent=1)
        c.border = thin_border()
    ws.row_dimensions[row].height = 20

def data_row(ws, row, vals, alt=False, height=42):
    bg = LIGHT_GRAY if alt else WHITE
    for i, val in enumerate(vals):
        col = ["A","B","C"][i]
        c = ws[f"{col}{row}"]
        c.value = val
        c.font = Font(name="Arial", size=9, color=DARK)
        c.fill = fill(bg)
        c.alignment = Alignment(horizontal="left", vertical="top", wrap_text=True, indent=1)
        c.border = thin_border()
    ws.row_dimensions[row].height = height
```

---

## Output

Save to `/home/claude/[clientname]_site_audit.xlsx`, then copy to `/mnt/user-data/outputs/` and call `present_files`.

File naming: lowercase, underscores, `_site_audit.xlsx` suffix. Example: `spacebar_site_audit.xlsx`.

---

## Copy standards (applied across all sheets)

- No em dashes anywhere
- No filler phrases ("in order to", "at its core", "it's worth noting")
- Issue descriptions: direct, specific, one clear sentence
- Recommendations: action-first, outcome-linked
- Copy suggestions: outcome-led, buyer-aware, no AI-isms

## Scope note

This skill covers B2B agency and SaaS client websites. The four-layer framework (SEO, AEO, Design/Dev, Copy) is Axamo's standard pre-project audit methodology. Always fetch live data — never write copy or scores from assumption.
