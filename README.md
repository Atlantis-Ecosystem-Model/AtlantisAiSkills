# AtlantisAiSkills

[Claude](https://claude.ai) skills for people working with the
[Atlantis](https://github.com/Atlantis-Ecosystem-Model/AtlantisTrunk) end-to-end
marine ecosystem model. There is one skill so far, `atlantis`.

When you ask Claude about Atlantis, it loads this skill and follows the
project's own conventions instead of guessing. It currently covers
**contributing to AtlantisTrunk**:

- bug reports and feature requests that fill in the repository's issue
  templates field by field (including the valgrind output for crashes);
- pull requests that branch from and target `dev`, explain *why*, link an
  AtlantisManual issue, name reviewers and give reviewers test steps;
- testing code changes on the SETas example model in `example/`;
- commit messages and CHANGELOG entries in the project's format;
- checking a diff against the contributing guide.

Model setup, parameter (`.prm`) files, forcing and outputs are planned next.

## Contents

```
atlantis/
├── SKILL.md                      # when the skill applies and the key rules
└── references/
    ├── contributing.md           # full rules, field-by-field guidance, checklist
    └── templates/                # AtlantisTrunk's templates, unchanged
        ├── bug_report.yml
        ├── feature_request.yml
        └── pull_request_template.md
```

## Installing

The skill is the `atlantis/` folder.

- **Claude Code:** copy the folder to `~/.claude/skills/atlantis/` (all your
  projects) or `.claude/skills/atlantis/` inside one project.
- **Claude apps (web, desktop):** zip the `atlantis/` folder and upload it as a
  custom skill in Claude's settings. The Claude help center describes where.

Then ask Claude something like *"Write a bug report for Atlantis: my model
crashes in the harvest step after year 20"* or *"Check this diff before I open
a PR to AtlantisTrunk"*.

## Keeping it in step with AtlantisTrunk

The files in `atlantis/references/templates/` are copies of
`.github/ISSUE_TEMPLATE/*.yml` and the pull request template in AtlantisTrunk.
When those or `CONTRIBUTING.md` change, update the copies and the matching
sections of `references/contributing.md`.

## Contributing

Issues and pull requests are welcome, especially additions on model setup,
parameter files and outputs. Keep `SKILL.md` short and put detail in
`references/`, which Claude reads only when it needs it.

The first version was drafted with Claude and reviewed by a human.
