# Throughline

**Assertion-to-exhibit traceability for personal-injury demand packages.**

Every factual statement in a demand letter is supposed to trace to a passage in
an attached exhibit. Nothing in a law office records whether it does.

Throughline takes a drafted demand package — the letter and its exhibit set —
and reports, for every statement in that letter, whether it is supported by an
attached exhibit, which passage supports it, and what could not be established.
It proposes; people decide. It does not draft, assess whether evidence is
sufficient, value a claim, or comment on an offer. Its claims are about whether
two texts correspond, never about the case.

CEN 4010, Principles of Software Engineering — Florida Atlantic University.
Final Project. Author: Mark Cunningham.

---

## Why this exists

A mid-size personal-injury office assembles roughly thirty demand packages a
month. A paralegal drafts the letter by reading back through several hundred
pages of medical records, bills, and correspondence, then checks the letter
against those exhibits by hand, under deadline. The attorney reviews and signs —
but spot-checks rather than verifies, because volume permits nothing else.

The link between a statement and the passage supporting it exists only in the
memory of whoever last read both. When that person stops reading, it is gone.
And because nothing counts defects, the office cannot say how often one reaches
a carrier. A failure that cannot be measured cannot be managed.

The full problem analysis, requirements baseline, architecture, and design are
in the Solution Design Report. This repository is the prototype that implements
a bounded slice of it and produces evidence about its own behavior.

## Architecture in one page

Nine pipeline stages and four shared controls. Two commitments shape it.

**Proposal and decision are separate.** Stages A1 through A7 create and hold
candidate information. Only A8 may write a disposition, and only with a named
human actor. No pipeline stage has an interface that writes one, so the rule is
structural and therefore testable rather than merely asserted.

**Generative and deterministic work are separated.** A3 and A4 use a model and
carry model risk. A6 uses none: a mismatch between `$4,820` in a letter and
`$4,280` in the bill it cites is a string comparison; a specials total that does
not equal the sum of its lines is arithmetic. Those findings are reproducible,
survive a model change, and need no confidence value.

| | Stage | Kind |
|---|---|---|
| **A1** | Package intake and registration | |
| **A2** | Exhibit registry | |
| **A3** | Segmentation and classification | generative |
| **A4** | Passage location | generative |
| **A5** | Search record | |
| **A6** | Comparison and exception checks | deterministic |
| **A7** | Assertion and finding register | |
| **A8** | Review workbench — paralegal and attorney views | human |
| **A9** | Report composition and handoff | generative |
| **S1** | Access control | shared |
| **S2** | Examination record | shared |
| **S3** | Boundary guard | shared |
| **S4** | Configuration and change control | shared |

The handling attorney sits outside the pipeline. No element holds authority and
no interface accepts a legal conclusion.

## Status

Built in the order the Solution Design Report specifies, which puts what
*measures* before what is *measured*, and deterministic work before generative
work.

| Step | What | State |
|---|---|---|
| 1 | Seeded corpus and answer key | corpus complete; key being authored |
| 2 | Register (A7) and examination record (S2) | not started |
| 3 | Access control (S1) | not started |
| 4 | Intake and registry (A1, A2) | not started |
| 5 | Comparison and exception checks (A6) | not started |
| 6 | Classification (A3) and its accuracy harness | not started |
| 7 | Passage location and search record (A4, A5) | not started |
| 8 | Boundary guard (S3) and refusal suite | not started |
| 9 | Workbench (A8), paralegal view | not started |
| 10 | Attorney view and the candidate gate | not started |
| 11 | Report composition (A9) | not started |
| 12 | Configuration pinning and regression gate (S4) | not started |

**Nothing runs yet.** Setup, run, and test instructions appear here as the
steps land. This section is the honest state of the work, not a plan.

## What is in the repository now

```
corpus/           three synthetic demand packages, 65 statements, 25 exhibit files
  P1-clean/       a package with nothing wrong
  P2-demo/        the demonstration package, carrying nine planted defect types
  P3-hard/        cases that are hard rather than defective
  PLANTING-LOG.md what was deliberately introduced, by type and location
keys/             the answer key, authored by hand
docs/             record of AI assistance
```

## Data

**Everything in this repository is synthetic.** The people, firms, hospitals,
insurers, claim numbers, bills, and medical records are fictional and were
written for this project. No real client material, no protected health
information, and no genuine insurer correspondence is present anywhere — not in
the corpus, not in the tests, and not in any prompt used to build this. The
declaration in `corpus/README.md` is why this can be a public repository.

No credentials, API keys, or tokens are committed. When the optional model
adapter arrives it will read its key from the environment, and the repository
will stay runnable without one.

## Known limitations

As of now, and kept current as the build proceeds.

- **No practitioner has reviewed the scenario.** The workflow is reasoned from a
  course-supplied scenario, not observed. A working paralegal would likely
  correct several details.
- **The corpus is written one sentence per line** so segmentation is
  deterministic and the key can be authored against stable identifiers. Real
  sentence segmentation is a problem this prototype does not solve. This is a
  simplification of the prototype, not of the design.
- **Volumes and rates in the report are estimates**, adopted for analysis and
  not measured.
- **The central assumption is untested**: that checkable factual assertions can
  be reliably distinguished from attorney characterization. If that fails, the
  capability retreats to the treatment chronology and the specials table, where
  what is checkable is determined by position rather than judgment.

## License

**All rights reserved.** Copyright © 2026 Mark Cunningham.

This repository is public so that it can be read and reviewed. That is not the
same as being open source: no license is granted, and the code, documentation,
and corpus may not be copied, reused, or incorporated into other work. See
[LICENSE](LICENSE) for the full notice, including what *is* permitted —
reading, linking, and short quotation with attribution.

If you are a student looking at this for a similar assignment: submitting any
part of it as your own work is plagiarism, and this repository is public,
timestamped, and indexed.
