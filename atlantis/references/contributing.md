# Contributing to Atlantis

Distilled from AtlantisTrunk's `CONTRIBUTING.md` and its issue and pull request
templates (bundled verbatim in `templates/`). Rules first, then how to fill each
template, then a checklist.

## Contents

1. Code of conduct
2. Questions vs issues
3. Bug reports (rules + template fields)
4. Feature requests (rules + template fields)
5. Pull requests (rules + template sections)
6. Commit messages
7. Coding style
8. Certificate of origin
9. Pre-submission checklist

## 1. Code of conduct

The project's `CODE_OF_CONDUCT.md` applies at all times, to everyone.

## 2. Questions vs issues

GitHub issues are only for bug reports and feature requests. Problems with the
user's own model setup (parameterization, a run that won't balance, a
model-specific crash caused by inputs) don't belong there. Help with those
directly, and point to the wiki and manual. File an issue only once the problem
looks like Atlantis itself.

## 3. Bug reports

Before filing:

- Check the bug still exists in the **latest version**; updating may fix it.
- **Review the documentation** (wiki, manual).
- **Search open bug issues.** If it is already reported, comment there with any
  new information. To simply +1, use a reaction, not a comment.

Template `templates/bug_report.yml`, title `[Bug Report]: <short description>`,
label `bug`. Start the body with :earth_asia:. Fields (required unless noted):

| Field | What to put |
|---|---|
| Atlantis version and Model name | Release/tag or commit hash, branch, and the model's name. |
| Describe the bug | What happens, when, and what was expected instead. |
| Error Message | Exact compiler or runtime error, pasted in a fenced code block, or a screenshot. |
| Valgrind output | Needed if the model crashes. The template gives the command: `valgrind -s --tool=memcheck --log-file=valgrind%p.log --track-origins=yes --leak-check=full --track-fds=yes --show-reachable=yes -i` followed by the usual run command from the model's `.sh` file. Paste the relevant part and attach the log. If there's no crash, say so ("Not applicable: no crash, wrong output only") rather than leaving it blank. |
| Is this a duplicate issue? | Tick only after actually searching. |
| Code and files used to run the model | Link to the model's repository if possible; otherwise attach the files and run command. If the bug reproduces on SETas (`example/`), say so: that is the easiest reproducible example for maintainers. |
| Your set up | OS and version, RAM, compiler and key library versions (e.g. netCDF). |
| Additional content (optional) | Workarounds, related issues, what was already ruled out. |

Write the ticket you would want to receive.

## 4. Feature requests

- Search open feature issues first; if a similar request exists, comment there.
- Be precise about the outcome and how it relates to existing features.
- No guarantee of acceptance or timeline.

Template `templates/feature_request.yml`, title `[Feature]: <short
description>`, label `feature`. Start the body with :earth_asia:. Fields:

| Field | What to put |
|---|---|
| Description (required) | The idea and what it should do. Add pseudo code for how it could be implemented if possible. |
| References (optional) | Publications, or the equations the feature uses. |
| Connection to code (required) | Where it fits in the current code, how it relates to existing features, implementation details: a new flag, a new option on an existing flag, new parameters, new output files and their format. |
| Trade offs (required) | Whether it adds to or replaces existing behaviour; if it replaces, what must not be lost. Default behaviour and backward compatibility for existing models. |

## 5. Pull requests

Rules:

- **Discuss first** for non-trivial changes: open an issue, or comment on the
  existing one with the intended approach, before writing the code. Large
  changes need maintainer agreement or the work may be wasted.
- **Branch from `dev` and open the PR against `dev`.**
- **One PR per bug fix or feature.** No refactoring or reformatting of
  unrelated code. Many small PRs beat one big one; very large PRs may be
  rejected.
- **Clarity over cleverness**; comment where the purpose isn't obvious.
- **Follow the existing architecture and patterns.**
- **Tests:** add tests where possible, following existing patterns; at a
  minimum, demonstrate the change on SETas (`example/`).
- **Example project:** update SETas if the new functionality needs it to be
  exercised.
- **Documentation:** code comments, plus an issue in the AtlantisManual repo
  (see the template below).
- **CHANGELOG:** update it for every enhancement and bug fix, with the issue
  number and the contributor's GitHub username.
- **Resolve merge conflicts** before asking for review.
- Comments in full sentences with punctuation. Spaces, not tabs.
- All contributions are licensed under the project's license.

Template `templates/pull_request_template.md`. Start the description with
:earth_asia:, then fill its sections:

- **Justification.** The *why*: the problem, its importance or impact, and how
  the change solves it. Don't restate what the commits and code already show.
  Link the issue (`Fixes #NNN` / `Closes #NNN`).
- **Types of changes.** Tick one: Bugfix (non-breaking), New feature
  (non-breaking), Breaking change (existing behaviour or existing models stop
  working as before), or Other. Anything that changes the results of existing
  models without a flag deserves a sentence here even if not ticked as breaking.
- **Further comments.** A bug fix, new feature or breaking change needs an
  issue in https://github.com/Atlantis-Ecosystem-Model/AtlantisManual
  documenting it; tick "I've created an issue" and link it, or "This is NA".
- **Reviewer instructions.** At least two reviewers: one a maintainer, the
  others familiar with the code area. Give exact steps: how to build, the
  SETas run command, which output files and variables to compare, and the
  expected result (e.g. "outputs identical to `dev` except the new file", or
  "differences in X of at most Y").

## 6. Commit messages

1. Separate subject from body with a blank line.
2. Subject line 50 characters or fewer.
3. Capitalize the subject line.
4. No period at the end of the subject line.
5. Imperative mood in the subject ("Fix food web issue").
6. Wrap the body at about 72 characters.
7. Body explains **why**, not what or how.
8. Optionally prefix the subject with the component: `[Docs] Fix typo`.
9. Link the issue it fixes: `Fixes #1234`.

No `Signed-off-by:` line is required. Count the subject's characters,
including any `[Component]` prefix, before presenting a commit message.

Example:

```
[Harvest] Add per-fishery catch output by box

Users comparing spatial management options need catch by species,
fishery and box per year, which existing outputs only give
aggregated. Writing it during the harvest step avoids having to
reconstruct it after the run.

Fixes #1234
```

## 7. Coding style

Consistency with the file being modified, and with the project, comes first.
Match existing naming and formatting: if private names are prefixed with `_`,
new ones are too; if functions are camelCase, new ones are camelCase. When in
doubt, find similar code in the code base and copy its conventions. Style
deviations lengthen review because reviewers deal with them before looking at
function.

## 8. Certificate of origin

By contributing, contributors certify the Developer's Certificate of Origin 1.1:
they wrote the contribution or have the right to submit it under the project's
open source license, and the contribution and its record are public and kept
indefinitely. No sign-off line is needed in commits.

## 9. Pre-submission checklist

Issues:
- [ ] :earth_asia: at the top
- [ ] Right template and title prefix (`[Bug Report]: ` / `[Feature]: `)
- [ ] Latest version checked; duplicates searched
- [ ] Every required field filled (bugs: version and model name, exact error,
      valgrind output or why not applicable, model files, system)
- [ ] Code and output in fenced code blocks

Pull requests:
- [ ] :earth_asia: at the top; issue linked
- [ ] Branched from and targets `dev`; conflicts resolved
- [ ] Single, isolated change; no unrelated reformatting
- [ ] Justification explains why; change type ticked
- [ ] AtlantisManual issue created and linked, or marked NA
- [ ] Two or more reviewers, one a maintainer
- [ ] Reviewer instructions with exact build and SETas test steps
- [ ] CHANGELOG entry with issue number and username
- [ ] Commit subjects ≤ 50 characters, imperative, capitalized, no period
