---
name: m365-task-manager
description: Manage simple Microsoft 365 tasks using Microsoft To Do and Planner patterns. Use when creating, assigning, tracking, or reminding operational tasks in M365, including daily follow-ups, owner assignment, due dates, and status updates.
---

# M365 Task Manager

Use this skill to run simple task management workflows in Microsoft 365 with low friction.

## Default workflow

1. Normalize the task title using this pattern: `YYYY-MM-DD short-action-owner`.
2. Capture owner, due date, and status.
3. Store task in Microsoft Planner for team tasks, Microsoft To Do for personal tasks.
4. Add daily reminder if the task is operationally critical.
5. Keep updates short and executive-friendly.

## Task fields

- Title
- Owner
- Due date
- Status (`Open`, `In Progress`, `Blocked`, `Done`)
- Evidence link (optional)

## Naming convention

- `2026-02-24-burn-2-dvd-send-robert`
- `2026-02-24-review-m365-license-assignment`

## References

- Read `references/playbook.md` for implementation playbook.

## Scripts

- Use scripts in `scripts/` for deterministic formatting and payload generation.


## Author

Abdelkrim BOUJRAF - ALT-F1 SRL - https://www.alt-f1.be

## License

MIT
