# Seeded corpus

Three synthetic demand packages used to measure every accuracy requirement in
the Throughline prototype. Nothing here is real.

## Synthetic provenance declaration

Every document in this directory is fictional and was authored for this project.
No real client, matter, provider, insurer, correspondence, bill, or medical
record informed any of it. No protected health information is present. The
people, firms, hospitals, insurers and claim numbers do not exist. This
declaration satisfies NFR-07 and is the reason the corpus can live in a public
repository.

## The three packages

| Package | Purpose | Statements | Exhibit files |
|---|---|---|---|
| `P1-clean` | A package with nothing wrong. Establishes that the system reports an absence of findings without ever claiming the package is clean. | 11 | 4 |
| `P2-demo` | The demonstration package described in §8.1 of the Solution Design Report. Carries all nine planted defect types. | 38 | 15 |
| `P3-hard` | Cases that are hard rather than defective: client-sourced assertions, support split across a combined bill, a statement referring outside the exhibit set, and an unreadable file. | 16 | 6 |

## Segmentation rule

The prototype's A3 must reproduce the segmentation shipped in each package's
`statements.tsv` exactly. That file is the authoritative segmentation and makes
FR-02 (identifier stability) testable rather than assumed.

A statement is a non-blank line of the letter that is:

- after the `RE:` line, so the address and claim block is excluded;
- not a section heading (`LIABILITY`, `SPECIAL DAMAGES`, and the rest);
- not inside the `EXHIBIT INDEX` block;
- not part of the signature block.

The letters are written one sentence per line so this rule is deterministic and
checkable by eye. A production system would need real sentence segmentation;
this is a recorded simplification of the prototype, not of the design.

## Exhibit numbering

Files are named `E<nn>_<slug>.txt`. For `P2-demo` the mapping between the
letter's exhibit index and the files on disk is deliberately imperfect — that
is where several of the planted defects live. See `PLANTING-LOG.md`.

## Answer key

The key is **not** in this directory. It lives in `../keys/` and is authored by
hand. See `../keys/HOW-TO-AUTHOR-THE-KEY.md` and §8.5 of the Solution Design
Report for why.
