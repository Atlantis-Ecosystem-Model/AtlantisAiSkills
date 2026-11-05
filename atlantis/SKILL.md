---
name: atlantis
description: Working with the Atlantis end-to-end marine ecosystem model (C code base, Atlantis-Ecosystem-Model/AtlantisTrunk on GitHub). Use whenever the user mentions Atlantis or their own Atlantis model and wants to report a bug, request a feature, open a pull request, write a commit message or CHANGELOG entry, test a code change against the SETas example, or check a diff against the project's rules, even if they never say "contribute". Currently covers contributing; model setup, parameter files and outputs will be added.
---

# Atlantis

Atlantis is a spatially explicit, end-to-end marine ecosystem model
(oceanography, biology, fisheries and management) written in C. Users run their
own regional models built on it, and some also change the Atlantis code, for
example adding output files or fixing bugs found in their own runs.

This skill currently covers **contributing to AtlantisTrunk**. Model structure,
parameter (`.prm`) files, initial conditions, forcing and output files are not
covered yet. For those, rely on what the user tells you, their files, the wiki
and the manual, and say when you are unsure rather than filling gaps from
general recollection: parameter names and output formats differ between
Atlantis versions.

## Key facts

| | |
|---|---|
| Repository | https://github.com/Atlantis-Ecosystem-Model/AtlantisTrunk |
| Branch to branch from and target with PRs | `dev` |
| Reference test model | SETas, in `example/` of the repository |
| Wiki | https://atlantis-ecosystem-model.github.io/atlantis-wiki/ |
| Manual | https://atlantis-ecosystem-model.github.io/AtlantisManual/ (repo: Atlantis-Ecosystem-Model/AtlantisManual) |
| Issue and PR templates | In AtlantisTrunk; GitHub shows them under New issue / New pull request. Their fields are described below. |

## What matters most

Apply these even for a quick draft; the sections below give the detail.

1. **Use the repository's templates.** Bug: title `[Bug Report]: ...`.
   Feature request: title `[Feature]: ...`. Fill every required field.
2. **Start every issue and pull request with :earth_asia: (`:earth_asia:`).**
   The contributing guide asks for it as the sign the guide was read; the
   templates don't include it, so add it yourself.
3. **Branch from `dev` and target `dev`**, not `main`.
4. **One bug fix or one feature per pull request.** No bundling, no
   reformatting or refactoring of unrelated code. If the user's branch mixes
   changes, propose how to split it.
5. **Open an issue first for anything non-trivial**, and link the PR to it.
6. **The PR description explains *why*.** Tick the change type, open an
   AtlantisManual issue for any bug fix, feature or breaking change, assign at
   least two reviewers (one a maintainer), and give reviewers exact test steps.
7. **Update the CHANGELOG** for every enhancement or fix, with the issue
   number and the contributor's GitHub username.
8. **Match the existing style of the file being edited.** Spaces, not tabs.
   Comments in full sentences.
9. **Commit messages** follow the format in "Commit messages" below. No
   `Signed-off-by` line is needed.
10. **Crash reports need valgrind output**, plus version, model name, system,
    exact error and the model files.

## Questions vs issues

GitHub issues are only for bug reports and feature requests. Problems with the
user's own model setup (parameterization, a run that won't balance, a crash
caused by inputs) don't belong there; help with those directly and point to
the wiki and manual. File an issue only once the problem looks like Atlantis
itself. The project's `CODE_OF_CONDUCT.md` applies throughout.

## Bug reports

Before filing: check the bug still exists in the **latest version**, review the
documentation, and **search open bug issues**. If it is already reported,
comment there with new information; to simply +1, use a reaction.

Title `[Bug Report]: <short description>`, label `bug`. Start the body with
:earth_asia:. Template fields (required unless noted):

| Field | What to put |
|---|---|
| Atlantis version and Model name | Release/tag or commit hash, branch, and the model's name. |
| Describe the bug | What happens, when, and what was expected instead. |
| Error Message | Exact compiler or runtime error in a fenced code block, or a screenshot. |
| Valgrind output | Needed if the model crashes. Command from the template: `valgrind -s --tool=memcheck --log-file=valgrind%p.log --track-origins=yes --leak-check=full --track-fds=yes --show-reachable=yes -i` followed by the usual run command from the model's `.sh` file. Paste the relevant part and attach the log. With no crash, write "Not applicable: no crash, wrong output only" rather than leaving it blank. |
| Is this a duplicate issue? | Tick only after actually searching. |
| Code and files used to run the model | Link to the model's repository if possible; otherwise attach files and the run command. If it reproduces on SETas, say so: that is the easiest example for maintainers. |
| Your set up | OS and version, RAM, compiler and key library versions (e.g. netCDF). |
| Additional content (optional) | Workarounds, related issues, what was already ruled out. |

## Feature requests

Search open feature issues first; if a similar request exists, comment there.
No guarantee of acceptance or timeline.

Title `[Feature]: <short description>`, label `feature`. Start the body with
:earth_asia:. Template fields:

| Field | What to put |
|---|---|
| Description (required) | The idea and what it should do; pseudo code for an implementation if possible. |
| References (optional) | Publications, or the equations the feature uses. |
| Connection to code (required) | Where it fits in the current code, how it relates to existing features, implementation details: a new flag, a new option on an existing flag, new parameters, new output files and their format. |
| Trade offs (required) | Whether it adds to or replaces existing behaviour; if it replaces, what must not be lost. Default behaviour and backward compatibility for existing models. |

## Pull requests

Rules:

- **Discuss first** for non-trivial changes (an issue, or a comment on the
  existing one). Large changes need maintainer agreement or may be wasted.
- **Branch from `dev`, open the PR against `dev`**, resolve merge conflicts
  before asking for review.
- **One fix or feature per PR**; many small PRs beat one big one; very large
  PRs may be rejected.
- **Clarity over cleverness**; comment where the purpose isn't obvious.
  **Follow the existing architecture and patterns.**
- **Tests** where possible; at a minimum, demonstrate the change on SETas.
  Update SETas if new functionality needs it to be exercised.
- **Documentation:** code comments plus an AtlantisManual issue.
- **CHANGELOG** entry with issue number and GitHub username.
- Contributions are licensed under the project's license, and contributors
  certify the Developer's Certificate of Origin 1.1 (no sign-off line needed).

Description: start with :earth_asia:, then the template's sections:

- **Justification.** The *why*: the problem, its importance, and how the
  change solves it. Commits and code already show what and how; don't restate
  them. Link the issue (`Fixes #NNN`).
- **Types of changes.** Tick one: Bugfix (non-breaking), New feature
  (non-breaking), Breaking change (existing behaviour or models stop working as
  before), or Other. A change that alters existing models' results without a
  flag deserves a sentence even if not ticked as breaking.
- **Further comments.** For a bug fix, feature or breaking change, create an
  issue in https://github.com/Atlantis-Ecosystem-Model/AtlantisManual
  documenting it and tick "I've created an issue" (with link), else "This is NA".
- **Reviewer instructions.** At least two reviewers: one a maintainer, the
  others familiar with the code area. Exact steps: how to build, the SETas run
  command, which output files and variables to compare, and the expected result.

## Testing a code change with SETas

SETas in `example/` is the shared reference model, so reviewers can rerun
anything tested on it.

- Run SETas with the unchanged `dev` build and with the changed build, using
  the run script in `example/` (read it rather than guessing the command).
- Bug fix: show the bug on the unchanged build and its absence on the changed
  one; say which other outputs changed and by how much (ideally none).
- New output: check it against existing outputs covering the same quantity,
  e.g. a new catch breakdown summed over its extra dimensions should match the
  existing catch output. Report the size of any differences.
- If the change was found or tested on the user's own model, still show it on
  SETas; their model is supporting evidence.
- Put these steps in the PR's reviewer instructions.

## Turning a modeller's local changes into a contribution

- Separate what is general (useful to every Atlantis user) from what is
  specific to their regional model; only the general part goes in the PR.
- Describe discrepancies found but not explained as open observations, not
  diagnosed causes, and consider a separate bug report.
- Check whether a similar issue or PR already exists.

## Commit messages

1. Subject line 50 characters or fewer (count it, including any prefix).
2. Capitalized, imperative mood ("Fix food web issue"), no trailing period.
3. Optional component prefix: `[Harvest] Fix ...`, `[Docs] Fix typo`.
4. Blank line, then a body wrapped at about 72 characters.
5. Body explains **why**, not what or how.
6. `Fixes #1234` where it applies.

```
[Harvest] Add per-fishery catch output by box

Users comparing spatial management options need catch by species,
fishery and box per year, which existing outputs only give
aggregated. Writing it during the harvest step avoids having to
reconstruct it after the run.

Fixes #1234
```

## Coding style

Consistency with the file being modified, and with the project, comes first:
match naming, prefixes and formatting (if private names start with `_`, new
ones do too; if functions are camelCase, new ones are camelCase). When in
doubt, copy the conventions of similar code in the code base. Style deviations
lengthen review.

## Checklist before handing over a draft

Issues:
- [ ] :earth_asia: at the top; right title prefix
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
