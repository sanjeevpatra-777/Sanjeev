---
name: rebrand
description: Rebrand a converted DITA file by replacing the brand name "Microsoft" with "New Microsoft" in text content only, leaving markup untouched. Use whenever the user runs /rebrand with a base document name, or asks to rebrand, rename, or apply a terminology/brand-name change to a DITA file. Reads output/<name>-output.dita and writes output/<name>-rebranded.dita.
---

# Rebrand a DITA File (Microsoft → New Microsoft)

You are a Brand Compliance Specialist for an enterprise documentation team,
experienced in safe, precise find-and-replace inside structured XML content
without disturbing markup.

## Task

Replace every occurrence of the old brand name **"Microsoft"** with the new brand
name **"New Microsoft"** in the DITA file produced by the `convert` skill.
`$ARGUMENTS` is the base document name. Read `output/$ARGUMENTS-output.dita`, apply
the replacement, and write a new rebranded file. **The original converted file
must remain untouched** — read it, never overwrite it.

## Context

This is a single, fixed terminology change for a proof-of-concept demo:
"Microsoft" becomes "New Microsoft" everywhere it appears as a standalone word or
as part of a compound term (e.g. "Microsoft Project Management Tool" becomes
"New Microsoft Project Management Tool"). The rebranded file is consumed by a
downstream validation skill, so the output must stay structurally identical to
the input.

## Replacement rules (MUST / MUST NOT)

- MUST replace only whole-word occurrences of "Microsoft" with "New Microsoft";
  do not partially match inside unrelated words. Treat a word boundary as the
  edge of the token so an already-prefixed "New Microsoft" is not matched again.
- MUST only replace text inside element **text content**; MUST NOT modify element
  names, attribute names, or attribute values (ids, hrefs). If "Microsoft" appears
  inside an `id`, `href`, or any other attribute, leave it exactly as-is.
- MUST NOT alter the XML structure in any way — the rebranded file must be
  byte-for-byte identical to the input except for the replaced text (same
  ordering, whitespace, indentation, DOCTYPE, and XML declaration).
- MUST count the total number of replacements made.
- MUST verify at the end that zero standalone occurrences of "Microsoft" remain
  that are not already part of "New Microsoft" — i.e. do not double-replace
  "New Microsoft" into "New New Microsoft". If any bare "Microsoft" (in text
  content) survives, the residual check FAILS.
- MUST NOT use Python scripts; perform the replacement by reading and rewriting
  the file directly.

## Output

- **Output file:** `output/$ARGUMENTS-rebranded.dita`.
- **Console report:** the total replacement count, a residual-term check result
  (**PASS** if no bare "Microsoft" remains in text content, **FAIL** otherwise),
  and the output file path.

## Example invocation

```
/rebrand Sample_Doc_for_DITA_Conversion
```

## Input to process

$ARGUMENTS
