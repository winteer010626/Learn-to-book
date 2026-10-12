# Learn-to-book

A reusable Doubao skill: **textbook-to-handout** — turn uploaded textbook materials (photos, scans, CSV, thread links) into a well-formatted, error-free Word study handout (vocabulary, phrases, grammar, text/task answers, speaking templates, writing frameworks).

## Usage

1. Build a JSON spec (see `references/spec_example.json`).
2. Run:

```bash
python scripts/build_handout.py spec.json out.docx
```

## Structure

- `SKILL.md` — workflow and hard requirements
- `scripts/build_handout.py` — data-driven Word generator
- `references/handout-structure.md` — handout structure and layout spec
- `references/quality-checklist.md` — omission and zero-error checklists
- `references/spec_example.json` — spec example
