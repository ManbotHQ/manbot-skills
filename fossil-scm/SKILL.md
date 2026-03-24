> Description: Fossil SCM skill for distributed version control, integrated task tracking, and streamlined project management in a single unified repository system.

# Fossil SCM Skill

## Fossil requirements

If fossil is not installed, install it using Homebrew `brew install fossil` or ask human for help:

## Description
This skill enables you to work with Fossil SCM as a unified system for:

- Version control (commits, branches, merges)
- Task tracking (tickets)
- History exploration (timeline, diff)
- Lightweight project management

Fossil is a distributed version control system that integrates:
- Git-like versioning
- Built-in ticketing
- Built-in wiki
- Web UI and timeline

Use this skill whenever you need to:
- Track code changes
- Manage tasks
- Understand project history
- Coordinate development work

---

## When to use this skill

Use Fossil when:

- You need to persist changes in a repository
- You are modifying code or project files
- You want to track progress via tickets
- You need to inspect history or diffs
- You are working on a project with versioning

---

## ⚠️ Mandatory Pre-Work Step

**Before performing any work in a repository, you MUST always run:**

`fossil update`


This ensures:

- Your working copy is up to date
- You are not working on stale or conflicting state
- All latest changes are applied before modifications

**Rule:**
- No operation (edit, add, commit, branch, etc.) should happen before `fossil update`
- This applies to all workflows without exception

---

## Core Concepts

### Repository
A Fossil repository is a single `.fossil` file containing:
- source code history
- tickets
- wiki
- metadata

### Timeline
The timeline shows:
- commits
- merges
- ticket changes

### Tickets
Tickets are built-in tasks:
- title
- description
- status
- priority

---

## Actions

### 1. Repository Management

- Initialize repository (if doesn't exist): `fossil init <repo.fossil>`
- Open repository: `fossil open <repo.fossil>`
- Clone repository: `fossil clone <url> <repo.fossil>`

---

### 2. Working with Files

- Add file: `fossil add <file>`
- Remove file: `fossil rm <file>`


---

### 3. Version Control

- Check Changes: `fossil changes`
- Commit changes: `fossil commit -m "<message>"`
- View history: `fossil timeline`
- View differences: `fossil diff`
- Update working copy: `fossil update`


---

### 4. Branching

- Create branch: `fossil branch new <branch-name>`
- Switch branch: `fossil update <branch-name>`

---

### 5. Tickets (Task Management)

- Create ticket: `fossil ticket add title "<title>" description "<desc>"`
- List tickets: `fossil ticket list`
- Update ticket: `fossil ticket change <id> status <status>`
- Close ticket: `fossil ticket close <id>`

---

### 6. Exploration

- View timeline: `fossil timeline-n 20`
- View artifact: `fossil artifact <hash>`

---

## Agent Behavior Guidelines

- Always run `fossil update` before any work in a repository
- Always create commits for meaningful changes
- Use tickets to track tasks before implementation
- Prefer small, atomic commits
- Use branches for experimental or risky work
- Keep commit messages clear and descriptive

---

## Workflow Patterns

### Feature Development

1. Run `fossil update`
2. Create ticket
3. Create branch
4. Implement changes
5. Commit frequently
6. Merge into main

---

### Bug Fix

1. Run `fossil update`
2. Identify issue
3. Create ticket
4. Fix issue
5. Commit with reference to ticket
6. Close ticket

---

### Exploration

1. Run `fossil update`
2. Use timeline
3. Use diff
4. Inspect artifacts

---

## Safety Rules

- NEVER delete repositories without confirmation
- NEVER overwrite history unless explicitly required
- AVOID force operations unless necessary

---

## Notes

- Fossil is a single-file repository system
- ALWAYS open repository before any work: `fossil open <repo.fossil>`
- It supports distributed workflows without central servers


