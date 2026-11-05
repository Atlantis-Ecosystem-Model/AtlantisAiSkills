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
└── SKILL.md    # the whole skill: when it applies, rules, template guidance, checklist
```

The skill is a single file on purpose, so it can be uploaded anywhere that
accepts only a SKILL.md.

## Installing

- **Claude apps (web, desktop):** upload `atlantis/SKILL.md` as a custom skill
  in Claude's settings.
- **Claude Code:** copy the folder to `~/.claude/skills/atlantis/` (all your
  projects) or `.claude/skills/atlantis/` inside one project.
- **Other AI tools that read SKILL.md files:** put the folder in that tool's
  skills directory. Tools without skill support can take the file as custom
  instructions.

Then ask Claude something like *"Write a bug report for Atlantis: my model
crashes in the harvest step after year 20"* or *"Check this diff before I open
a PR to AtlantisTrunk"*.

## Keeping it in step with AtlantisTrunk

`SKILL.md` describes AtlantisTrunk's `CONTRIBUTING.md` and its bug report,
feature request and pull request templates field by field. When those change
upstream, update the matching sections of `SKILL.md`.

## Contributing

Issues and pull requests are welcome, especially additions on model setup,
parameter files and outputs. Keep everything in `SKILL.md` (under about 500
lines) so it still works where only that one file can be uploaded.

The first version was drafted with Claude and reviewed by a human.
