# openclaw-skill-m365-task-manager

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-%3E%3D18-green.svg)](https://nodejs.org/)
[![Microsoft 365](https://img.shields.io/badge/Microsoft%20365-To%20Do-blue.svg?logo=microsofttodo)](https://todo.microsoft.com/)
[![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-orange.svg)](https://clawhub.ai)
[![ClawHub](https://img.shields.io/badge/ClawHub-openclaw--skill--m365--task--manager--by--altf1be-orange)](https://clawhub.ai/skills/openclaw-skill-m365-task-manager-by-altf1be)
[![Security](https://img.shields.io/badge/Security_Scan-Benign-green)](https://clawhub.ai/skills/openclaw-skill-m365-task-manager-by-altf1be)
[![GitHub last commit](https://img.shields.io/github/last-commit/ALT-F1-OpenClaw/openclaw-skill-m365-task-manager)](https://github.com/ALT-F1-OpenClaw/openclaw-skill-m365-task-manager/commits/master)
[![GitHub issues](https://img.shields.io/github/issues/ALT-F1-OpenClaw/openclaw-skill-m365-task-manager)](https://github.com/ALT-F1-OpenClaw/openclaw-skill-m365-task-manager/issues)
[![GitHub stars](https://img.shields.io/github/stars/ALT-F1-OpenClaw/openclaw-skill-m365-task-manager)](https://github.com/ALT-F1-OpenClaw/openclaw-skill-m365-task-manager/stargazers)

Production-ready OpenClaw skill for **Microsoft 365 task operations** using **Microsoft Graph API** (Microsoft To Do).

By [Abdelkrim BOUJRAF](https://www.alt-f1.be) / ALT-F1 SRL, Brussels 🇧🇪 🇲🇦

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [Setup](#setup)
- [Commands](#commands)
- [Project Structure](#project-structure)
- [Operational Convention](#operational-convention)
- [Security](#security)
- [Troubleshooting](#troubleshooting)
- [ClawHub](#clawhub)
- [License](#license)
- [Author](#author)
- [Contributing](#contributing)

## Features

- **CRUD tasks** — Create, read, update, and delete Microsoft To Do tasks
- **List management** — Browse available task lists
- **Device Code auth** — Delegated authentication (first login interactive, then cached)
- **Deterministic naming** — Task naming helper for consistent conventions
- **Operational playbook** — Lightweight guidelines for consistent usage

## Quick Start

```bash
# 1. Clone
git clone https://github.com/ALT-F1-OpenClaw/openclaw-skill-m365-task-manager.git
cd openclaw-skill-m365-task-manager

# 2. Install
npm install

# 3. Configure
# Set environment variables (see Setup section)

# 4. Use
npm run todo -- info
npm run todo -- lists
npm run todo -- tasks:create --list-name "Tasks" --title "My first task" --due 2026-03-15
```

## Setup

### Prerequisites

- Node.js 18+
- Microsoft Entra app registration configured as **public client**
- Microsoft Graph delegated permissions:
  - `Tasks.ReadWrite`
  - `User.Read`
  - `offline_access`

### Configuration

Set environment variables:

```bash
M365_TENANT_ID=your-tenant-id-or-common
M365_CLIENT_ID=your-public-client-app-id
# optional override
M365_TOKEN_CACHE_PATH=/home/user/.cache/openclaw/m365-task-manager-token.json
```

> First execution opens Device Code flow. Sign in once, token is cached for reuse.

## Commands

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

See [SKILL.md](./skills/m365-task-manager/SKILL.md) for full command reference.

## Project Structure

```text
skills/m365-task-manager/
├── SKILL.md
├── references/playbook.md
└── scripts/
    ├── m365-todo.mjs
    └── format-task-name.sh
```

## Operational Convention

Recommended task title pattern:

`<project>-<date>-<person>-<action>`

Examples:
- `finance-2026-03-01-abdelkrim-review-monthly-budget`
- `ops-2026-03-05-morad-prepare-quarterly-planning-notes`

## Security

- Device Code delegated auth (no client secrets stored)
- Token cached locally with configurable path
- Delegated permissions scoped to `Tasks.ReadWrite` only
- No secrets or tokens printed to stdout

## Troubleshooting

### `invalid_grant`
Usually app or tenant mismatch. Verify `M365_TENANT_ID` and `M365_CLIENT_ID` point to the correct app.

### Device login shows wrong app name
Your service env is using another client ID. Update env, restart service, and retry.

### No lists returned / request fails
Confirm delegated permissions are granted and admin consent applied.

## ClawHub

Published as: `openclaw-skill-m365-task-manager-by-altf1be`

```bash
clawhub install openclaw-skill-m365-task-manager-by-altf1be
```

## License

MIT — see [LICENSE](./LICENSE)

## Author

Abdelkrim BOUJRAF — [ALT-F1 SRL](https://www.alt-f1.be), Brussels 🇧🇪 🇲🇦
- GitHub: [@abdelkrim](https://github.com/abdelkrim)
- X: [@altf1be](https://x.com/altf1be)

## Contributing

Contributions welcome! Please open an issue or PR.
