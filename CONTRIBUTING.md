# Contributing

This is coursework for CEN 4010 at Florida Atlantic University, developed as an
individual project and submitted for academic credit. Issues and discussion are
welcome; pull requests changing the prototype's behavior are not, because the
submitted work has to be mine.

The repository is public for review, not for reuse. No license is granted — see
[LICENSE](LICENSE). If you want to build on any of this, ask first.

## If you are reviewing this project

The quickest route in is `README.md`, then `corpus/README.md`, then the
Solution Design Report linked from the README. The report explains why the
architecture is shaped the way it is; the code shows whether the shape held.

## Ground rules that apply to any change here

These come from the Solution Design Report and are not negotiable within this
project:

1. **No real data.** Everything in `corpus/` is synthetic and declared as such.
   No real client material, protected health information, or genuine insurer
   correspondence enters this repository, any test, or any prompt.
2. **No credentials.** No API keys, tokens, or secrets are committed. The
   optional model adapter reads its key from the environment and the repository
   must stay runnable without one.
3. **Only a named human writes a disposition.** Nothing in the pipeline may set
   a disposition or a review status. Any change that touches that boundary gets
   read line by line, because a plausible-looking shortcut through it would be
   invisible in a review of behavior alone.
4. **The answer key is authored by hand.** Generated content may not define
   ground truth. See `keys/HOW-TO-AUTHOR-THE-KEY.md`.

## Commit messages

One slice per commit where possible, named for the build step in §8.2 of the
report: `step 4: intake and registry (A1, A2)`.
