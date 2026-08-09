---
name: resume-publisher
description: Use when converting a reviewed structured Resume Model (preferred) or finalized Markdown resume into a polished DOCX file for job applications.
---

# Resume Publisher

## Overview

Turn a reviewed Resume Model into a clean, ATS-friendly Word DOCX deliverable. `schemas/resume-model.schema.json` is preferred; Markdown remains a compatibility input. The publisher is a renderer and must never rewrite facts, infer fields, or strengthen claims.

## Workflow

1. Validate the Resume Model (preferred) or parse the Markdown compatibility input. Reject missing name, empty sections, empty headings, or empty bullet text rather than guessing fields.
2. Run the delivery checklist in `references/delivery_checklist.md`.
3. Apply the layout rules in `references/resume_layout_rules.md`.
4. Generate DOCX with `scripts/build_resume_docx.py`.
5. Inspect the final document visually before saying it is ready to submit.

## Quick Start

Use the script from the skill directory:

```bash
python scripts/build_resume_docx.py path/to/tailored-resume.json --outdir path/to/output
```

Optional flags:

```bash
python scripts/build_resume_docx.py resume.md --basename "姓名-岗位方向"
python scripts/build_resume_docx.py resume.md --photo path/to/headshot.jpg
```

The skill generates DOCX only. Any later format conversion should be handled outside this skill.

## Output Contract

Create one file:

- `<姓名>-<岗位方向>.docx`

Use the DOCX as the editable deliverable. Keep source files unchanged unless the user asks for content edits. When an application exists, place the emitted immutable DOCX under its application directory and record the exact path before marking it submitted.

## Publishing Rules

- Prefer one to two pages for early-career technical resumes.
- Use simple typography, clear section headings, compact spacing, and real text.
- Do not use skill bars, radar charts, decorative icons, or image-only resume layouts.
- Do not add a headshot by default for technical/ATS-oriented submissions. Add one only when the employer expects it, the platform asks for it, or the user explicitly requests it.
- Do not add metrics, tools, titles, project scope, or claims. The model's `claim_ids` are traceability metadata, not license to create prose.
- Remove Markdown-only artifacts from the deliverable, including horizontal rules, raw `#`, raw `**`, and code fences.
- Keep links as visible text when they are useful for ATS parsing.

## Common Mistakes

| Mistake | Fix |
|---|---|
| Rewriting the resume while exporting | Only format unless content editing is requested. |
| Making a flashy visual template | Use ATS-friendly text layout. |
| Shipping DOCX without visual review | Render or open-check the document first. |
| Trying to automate non-DOCX export from the skill | Generate DOCX only. |
| Letting Chinese text use random fallback fonts | Use the declared Windows/macOS/Linux CJK fallback chain. |
