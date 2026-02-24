# openclaw-skill-m365-task-manager

OpenClaw skill for simple Microsoft 365 task management using Microsoft To Do and Planner patterns.

## Author
Abdelkrim BOUJRAF

## Company
ALT-F1 SRL
https://www.alt-f1.be

## License
MIT

## What this skill does

This skill standardizes lightweight task operations in M365:
- create task records with clear naming
- assign owner and due date
- track status using a simple lifecycle
- support daily operational follow-up reminders

## When to use

Use this skill when you need fast, consistent task capture for operations work in Microsoft 365:
- personal tasks in Microsoft To Do
- team tasks in Microsoft Planner
- recurring follow-up actions where ownership and due dates must be explicit

## Included files

```text
skills/m365-task-manager/
├── SKILL.md
├── references/
│   └── playbook.md
└── scripts/
    └── format-task-name.sh
```

## Naming convention

Pattern:
- `YYYY-MM-DD-short-action-owner`

Examples:
- `2026-02-24-burn-2-dvd-send-robert`
- `2026-02-24-review-m365-license-assignment`

## Task fields standard

- Title
- Owner
- Due date
- Status: Open | In Progress | Blocked | Done
- Evidence link (optional)

## Quick test

```bash
./skills/m365-task-manager/scripts/format-task-name.sh 2026-02-24 "Burn 2 DVD Send Robert"
```

Expected output:

```text
2026-02-24-burn-2-dvd-send-robert
```

## Publish workflow

1. Commit changes
2. Push to GitHub
3. Publish to ClawHub from repo root

Example:

```bash
git add .
git commit -m "docs: update"
git push
# then clawhub publish according to your local clawhub auth/setup
```
