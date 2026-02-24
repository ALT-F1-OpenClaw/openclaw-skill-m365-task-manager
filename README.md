# Openclaw Skill M365 Task Manager

Production-ready OpenClaw skill for **Microsoft 365 task operations** using **Microsoft Graph API** (Microsoft To Do).

[![ClawHub](https://img.shields.io/badge/ClawHub-openclaw--skill--m365--task--manager--by--altf1be-orange)](https://clawhub.ai/skills/openclaw-skill-m365-task-manager-by-altf1be)
[![Security](https://img.shields.io/badge/Security_Scan-Benign-green)](https://clawhub.ai/skills/openclaw-skill-m365-task-manager-by-altf1be)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Install via ClawHub:**
```bash
clawhub install openclaw-skill-m365-task-manager-by-altf1be
```

## What this project is

This repository provides a practical skill package to create, read, update, and delete Microsoft To Do tasks from OpenClaw workflows.

If this is your first time reading this repo, start with:
1. **Prerequisites**
2. **Quick Start**
3. **Command Reference**

---

## Core capabilities

- Microsoft Graph CRUD for Microsoft To Do tasks
- Device Code delegated authentication (first login interactive, then cached)
- Deterministic task naming helper
- Lightweight operational playbook for consistent usage

---

## Prerequisites

- Node.js 18+
- Microsoft Entra app registration configured as **public client**
- Microsoft Graph delegated permissions:
  - `Tasks.ReadWrite`
  - `User.Read`
  - `offline_access`

---

## Configuration

Create environment variables:

```bash
M365_TENANT_ID=your-tenant-id-or-common
M365_CLIENT_ID=your-public-client-app-id
# optional override
M365_TOKEN_CACHE_PATH=/home/user/.cache/openclaw/m365-task-manager-token.json
```

> First execution opens Device Code flow. Sign in once, token is cached for reuse.

---

## Install

```bash
npm install
```

---

## Quick Start

```bash
# 1) Validate auth + user profile
npm run todo -- info

# 2) List available Microsoft To Do lists
npm run todo -- lists

# 3) Create a task in default Tasks list
npm run todo -- tasks:create --list-name "Tasks" --title "2026-03-01-submit-weekly-status-report" --due 2026-03-01
```

---

## Command Reference

```bash
# Connection + profile
npm run todo -- info

# Lists
npm run todo -- lists

# Read tasks
npm run todo -- tasks:list --list-name "Tasks"
npm run todo -- tasks:list --list-id <LIST_ID>

# Create task
npm run todo -- tasks:create --list-name "Tasks" --title "Task title" [--body "Notes"] [--due YYYY-MM-DD]

# Update task
npm run todo -- tasks:update --list-name "Tasks" --task-id <TASK_ID> [--title "..."] [--body "..."] [--status notStarted|inProgress|completed|waitingOnOthers|deferred] [--due YYYY-MM-DD]

# Delete task
npm run todo -- tasks:delete --list-name "Tasks" --task-id <TASK_ID>
```

---

## Project structure

```text
skills/m365-task-manager/
├── SKILL.md
├── references/playbook.md
└── scripts/
    ├── m365-todo.mjs
    └── format-task-name.sh
```

---

## Operational convention

Recommended task title pattern:

`YYYY-MM-DD-short-action-owner`

Examples:
- `2026-03-01-review-monthly-budget`
- `2026-03-05-prepare-quarterly-planning-notes`

---

## Troubleshooting

### `invalid_grant`
Usually app or tenant mismatch. Verify `M365_TENANT_ID` and `M365_CLIENT_ID` point to the correct app.

### Device login shows wrong app name
Your service env is using another client ID. Update env, restart service, and retry.

### No lists returned / request fails
Confirm delegated permissions are granted and admin consent applied.

---

## License

MIT (see `LICENSE`).

---

## Credits

Created by **Abdelkrim BOUJRAF**

Company: **ALT-F1 SRL**  
Website: https://www.alt-f1.be
