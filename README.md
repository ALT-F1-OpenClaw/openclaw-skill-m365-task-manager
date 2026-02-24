# openclaw-skill-m365-task-manager

OpenClaw skill for Microsoft 365 task management with real Microsoft Graph CRUD for Microsoft To Do.

## Author
Abdelkrim BOUJRAF

## Company
ALT-F1 SRL
https://www.alt-f1.be

## License
MIT

## Features

- Real Graph API CRUD for Microsoft To Do tasks
- Delegated Device Code authentication with token cache reuse
- Task naming formatter helper script
- Lightweight operational playbook

## Requirements

- Node.js 18+
- Entra app registration (public client)
- Graph delegated permissions:
  - `Tasks.ReadWrite`
  - `User.Read`
  - `offline_access`

## Environment

```bash
M365_TENANT_ID=your-tenant-id-or-common
M365_CLIENT_ID=your-public-client-app-id
# optional
M365_TOKEN_CACHE_PATH=/home/user/.cache/openclaw/m365-task-manager-token.json
```

## Install

```bash
npm install
```

## Usage

```bash
# verify auth and user
npm run todo -- info

# list lists
npm run todo -- lists

# list tasks
npm run todo -- tasks:list --list-name "Tasks"

# create
npm run todo -- tasks:create --list-name "Tasks" --title "Burn 2 DVDs" --due 2026-02-28

# update
npm run todo -- tasks:update --list-name "Tasks" --task-id <TASK_ID> --status inProgress

# delete
npm run todo -- tasks:delete --list-name "Tasks" --task-id <TASK_ID>
```

## Included files

```text
skills/m365-task-manager/
├── SKILL.md
├── references/playbook.md
└── scripts/
    ├── m365-todo.mjs
    └── format-task-name.sh
```
