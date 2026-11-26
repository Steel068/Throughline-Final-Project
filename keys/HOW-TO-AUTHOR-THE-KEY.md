# How to author the answer key

The key is ground truth. Everything the prototype claims about its own accuracy
is measured against this file, so it has to be yours.

§8.5 of the Solution Design Report states that GenAI may not author the key: if
the same class of model both plants the defects and finds them, the test
measures agreement rather than correctness, and it will agree most confidently
exactly where both are wrong in the same way. The corpus documents were
model-drafted. This file must not be.

## What to fill in

Open `key-statements.csv`. It has one row per statement, 65 in total, with the
statement text already filled in. Five columns are blank and are yours:

**`classification`** — one of:

- `checkable` — a factual assertion that could be confirmed or contradicted by a
  document. Dates, amounts, providers, what a record says.
- `non-checkable` — attorney characterization, argument, or legal conclusion.
  "The collision was entirely avoidable" is not a fact to look up.
- `uncertain` — you genuinely cannot decide. Use it honestly; it is a real
  category and the prototype has to handle it.

**`support`** — for `checkable` statements only:

- `supported` — a passage in an attached exhibit bears it out.
- `unsupported` — nothing in the attached exhibit set does.
- `mismatched` — a passage addresses it but the values disagree.

Leave blank for `non-checkable`. For `uncertain`, leave blank.

**`exhibit`** — the exhibit file the support is in, e.g. `E09_pt_bill.txt`.

**`page`** — these are short text files, so use `1` unless a file is long enough
to need otherwise.

**`passage`** — the words in the exhibit that bear the statement out. A short
quote is enough; it is what a reviewer would click through to.

**`notes`** — anything you want recorded. Use it when a call was close.

## Then `key-defects.csv`

One row per package-level or exhibit-level defect: the superseded exhibit, the
duplicate, the uncited attachments, the indexed-but-absent exhibit, the
arithmetic error, the unreadable file. `PLANTING-LOG.md` says what was planted;
confirm each one against the documents before you record it, and add anything
you find that the log does not mention. Finding something unplanted would be a
useful result.

## How long this takes

65 statements. Most are obvious in a few seconds. Perhaps a dozen need you to
open an exhibit and read. Budget an hour, and do it in one sitting so your
judgment stays consistent.

## What not to do

Do not key a statement by what you expect the prototype to say about it. Key it
by what the documents support. The point of the exercise is that the two can
differ.
