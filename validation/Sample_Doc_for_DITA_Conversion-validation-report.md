# DITA Validation Report

| Field | Value |
|---|---|
| **Document** | Sample_Doc_for_DITA_Conversion |
| **Validated file** | `output/Sample_Doc_for_DITA_Conversion-rebranded.dita` |
| **Source compared** | `input/Sample_Doc_for_DITA_Conversion.docx` |
| **Date** | 2026-07-05 |
| **Stage** | Validation (stage 3 of 3: convert → rebrand → validate) |

## Results

| # | Check | Status | Details |
|---|---|---|---|
| 1 | Output file exists and is non-empty | ✅ PASS | File present, 3,921 bytes. |
| 2 | XML is well-formed | ✅ PASS | Parsed with an XML reader (external DTD ignored); no errors. |
| 3 | DOCTYPE declaration present and correct | ✅ PASS | Line 1 XML declaration; line 2 `<!DOCTYPE topic PUBLIC "-//OASIS//DTD DITA Topic//EN" "topic.dtd">`. |
| 4 | Root element is a valid DITA topic type | ✅ PASS | Root element is `<topic>`. |
| 5 | Root element has a non-empty `id` | ✅ PASS | `id="sample-doc-for-dita-conversion"`. |
| 6 | `<title>` present and first child of root | ✅ PASS | First child is `<title>New Microsoft Project Management Tool - Setup Guide and System Design</title>`. |
| 7 | Body element matching topic type present | ✅ PASS | `<body>` present, correctly paired. |
| 8 | Every source heading has a `<section>/<title>` | ✅ PASS | Source has 1 Heading 1 + 9 Heading 2. DITA maps Heading 1 → topic `<title>` and all 9 Heading 2 → 9 `<section>` titles (Introduction and Overview, Prerequisites, Procedure, System Architecture, Data Design, Interface Design, UI Mockups, Stakeholder List, Project Milestones). |
| 9 | All bullet/numbered lists preserved with matching item counts | ✅ PASS | Source: 2 bullet lists (2 + 4 = 6 items) and 2 numbered lists (2 + 1 = 3 items). DITA: 2 `<ul>` (6 `<li>`) + 2 `<ol>` (3 `<li>`) = 9 items. Counts match exactly. |
| 10 | Procedure section represented as an ordered list of steps | ✅ PASS | "Procedure: Creating a New Project" section contains an `<ol>` with 2 `<li>` steps. |
| 11 | All source tables present, correct column counts and header rows | ✅ PASS | Both source tables present. Table 1 = 2 columns (`tgroup cols="2"`, `<thead>` Entity / Key Attributes); Table 2 = 3 columns (`tgroup cols="3"`, `<thead>` Stakeholder / Role / Responsibilities). 5 `<row>` total matches 5 source `<w:tr>`. |
| 12 | Tables appear in their original document position | ✅ PASS | Table 1 sits inside the "Data Design" section; Table 2 sits inside the "Stakeholder List" section — same positions as the source. Neither drifted to the end. |
| 13 | Figures represented as `<fig>` with titles and `<image>` references | ✅ PASS | 2 `<fig>` elements, each with a `<title>` (Figure 1 / Figure 2 captions) and an `<image href="images/figure-N.png"/>`. |
| 14 | No empty elements | ✅ PASS | No empty element pairs detected. |
| 15 | Rebranding complete — no standalone "Microsoft" remains | ✅ PASS | 0 occurrences of "Microsoft" not preceded by "New "; no "New New Microsoft" double-replacements. |

## Verdict

### ✅ PASS

| Status | Count |
|---|---:|
| PASS | 15 |
| WARN | 0 |
| FAIL | 0 |

All 15 checks passed. The rebranded DITA file is structurally conformant, content-faithful to the source Word document (headings, lists, tables, and figures all preserved in original order), and the Microsoft → New Microsoft rebranding is complete. The file is ready for downstream publishing.
