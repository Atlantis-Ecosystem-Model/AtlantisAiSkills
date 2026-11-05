---
name: atlantis
description: Working with the Atlantis end-to-end marine ecosystem model (C code base, Atlantis-Ecosystem-Model/AtlantisTrunk on GitHub). Use whenever the user mentions Atlantis or their own Atlantis model and wants to report a bug, request a feature, open a pull request, write a commit message or CHANGELOG entry, test a code change against the SETas example, or check a diff against the project's rules, even if they never say "contribute". Currently covers contributing; model setup, parameter files and outputs will be added.
---

# Atlantis

Atlantis is a spatially explicit, end-to-end marine ecosystem model
(oceanography, biology, fisheries and management) written in C. Users run their
own regional models built on it, and some also change the Atlantis code, for
example adding output files or fixing bugs they found in their own runs.

## Key facts

| | |
|---|---|
| Repository | https://github.com/Atlantis-Ecosystem-Model/AtlantisTrunk |
| Branch to branch from and target with PRs | `dev` |
| Reference test model | SETas, in `example/` of the repository |
| Wiki | https://atlantis-ecosystem-model.github.io/atlantis-wiki/ |
| Manual | https://atlantis-ecosystem-model.github.io/AtlantisManual/ (repo: Atlantis-Ecosystem-Model/AtlantisManual) |

## What this skill covers so far

| Topic | Where |
|---|---|
| Contribution rules, how to fill each template, commit messages, coding style, checklist | `references/contributing.md` |
| The repository's own templates, verbatim | `references/templates/bug_report.yml`, `feature_request.yml`, `pull_request_template.md` |

Model structure, parameter (`.prm`) files, initial conditions, forcing and
output files are not covered yet. For those, rely on what the user tells you,
the files in front of them, the wiki and the manual, and say when you are
unsure rather than filling gaps from general recollection of Atlantis:
parameter names and output formats differ between Atlantis versions.

## Contributing: what matters most

Read `references/contributing.md` before drafting any issue, pull request,
commit message or CHANGELOG entry, or before reviewing a diff headed for
AtlantisTrunk. The points below are the ones most often missed, so apply them
even for a quick draft:

1. **Use the repository's templates.** Bugs: title `[Bug Report]: ...`.
   Feature requests: title `[Feature]: ...`. Fill every required field; the
   field-by-field guidance is in `references/contributing.md`.
2. **Start every issue and pull request with :earth_asia: (`:earth_asia:`).**
   The contributing guide asks for it as the sign the guide was read; the
   templates don't include it, so add it yourself.
3. **Branch from `dev` and target `dev`**, not `main`.
4. **One bug fix or one feature per pull request.** Don't bundle, and don't
   reformat or refactor unrelated code. If the user's branch mixes changes (a
   new output plus a bug fix found along the way), propose splitting it and
   say how.
5. **Open an issue first for anything non-trivial**, and link the PR to it.
6. **The PR description explains *why*.** Commits and code already show what
   and how. Tick the change type, open an issue in the AtlantisManual repo for
   any bug fix, feature or breaking change, assign at least two reviewers (one
   a maintainer), and give reviewers exact steps to build and test.
7. **Update the CHANGELOG** for every enhancement or fix, with the issue
   number and the contributor's GitHub username.
8. **Match the existing style of the file being edited** (naming, prefixes,
   comment style). Spaces, not tabs. Comments in full sentences.
9. **Commit messages:** subject of 50 characters or fewer, capitalized,
   imperative ("Fix", not "Fixed"), no trailing period, optional component
   prefix (`[Harvest] Fix ...`); blank line; body wrapped at about 72
   characters explaining *why*; `Fixes #NNN` where it applies. No
   `Signed-off-by` line is needed.
10. **Bug reports for crashes need valgrind output**, plus the Atlantis version,
    the model name, the system (OS, RAM), the exact error message, and the
    model files (ideally a link to the model's repository). Check the latest
    version and search existing issues first. Issues are for Atlantis bugs and
    feature requests, not for debugging one's own model parameterization.

## Testing a code change with SETas

SETas in `example/` is the shared reference model, so reviewers can rerun
anything tested on it. For a code change:

- Run SETas with the unchanged `dev` build and with the changed build, using
  the run script in `example/` (read it rather than guessing the command line).
- Bug fix: show the bug on the unchanged build and its absence on the changed
  one, and say which other outputs changed and by how much (ideally none).
- New output: check it against existing outputs that cover the same quantity,
  e.g. a new catch breakdown summed over its extra dimensions should match the
  existing catch output. Report the size of any differences.
- If the change was first found or tested on the user's own model, still show
  it on SETas; the user's model is supporting evidence only.
- Put these steps in the PR's reviewer instructions so reviewers can repeat them.

## Turning a modeller's local changes into a contribution

- Separate what is general (useful to every Atlantis user) from what is
  specific to their regional model; only the general part goes in the PR.
- Describe discrepancies the user has found but not explained as open
  observations, not as diagnosed causes, and consider a separate bug report.
- Check whether a similar issue or PR already exists before drafting.
