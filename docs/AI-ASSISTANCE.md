# Record of AI assistance

Required by the Final Project brief: material AI assistance, validation work,
rejected or revised outputs, and known limitations. Kept current as the build
proceeds. The Solution Design Report carries the summary; this file carries the
detail.

## Boundaries in force

From §8.5 of the Solution Design Report.

**Permitted** — proposing component code, test scaffolding, schema drafts,
interface stubs and documentation; explaining failures; drafting the
deterministic comparison logic in A6; reviewing code against the requirements.

**Not permitted** — authoring the answer key; real client material or protected
health information in any prompt; accepting generated code that crosses the
disposition boundary without line-by-line human review.

## Log

### Step 1 — seeded corpus

**Model-drafted.** The three demand letters and all 25 exhibit files in
`corpus/`. The deterministic segmentation rule and the `statements.tsv` files
derived from it. `PLANTING-LOG.md`. The key templates `key-statements.csv` and
`key-defects.csv` — structure and statement text only, with every judgment
column left empty.

**Human-authored.** The answer key itself: every value in the `classification`,
`support`, `exhibit`, `page` and `passage` columns, and every row of
`key-defects.csv`.

**Decisions taken against the draft.** _(to be completed as the key is authored
— record here anything in the corpus that turned out wrong, ambiguous, or
different from what the planting log claims.)_

**Known limitation.** The corpus letters are written one sentence per line so
that segmentation is deterministic and the key can be authored against stable
identifiers. A production system would need real sentence segmentation. This is
a simplification of the prototype, not of the design, and it is recorded in
`corpus/README.md`.
