# AdaL CLI / Sylph AI Setup

How to use planning-with-files with AdaL CLI (Sylph AI).

---

## About AdaL

[AdaL](https://docs.sylph.ai/) is a CLI tool from SylphAI that brings AI-powered coding assistance to your terminal. AdaL skills are **compatible with Claude Code skills**, so you can use the same skill format.

---

## Installation

### Option 1: Copy to personal skills directory

```bash
git clone https://github.com/OthmanAdi/planning-with-files.git
cp -r planning-with-files/.adal/skills/planning-with-files ~/.adal/skills/
```

### Option 2: Copy to project skills directory

```bash
git clone https://github.com/OthmanAdi/planning-with-files.git
cp -r planning-with-files/.adal/skills/planning-with-files .adal/skills/
```

### Option 3: Windows (PowerShell)

```powershell
git clone https://github.com/OthmanAdi/planning-with-files.git
Copy-Item -Recurse -Path "planning-with-files\.adal\skills\planning-with-files" -Destination "$env:USERPROFILE\.adal\skills\"
```

---

## Skill Locations

AdaL supports three skill sources:

| Source | Location | Use Case |
|--------|----------|----------|
| Personal | `~/.adal/skills/` | Your custom skills |
| Project | `.adal/skills/` | Team skills shared via git |
| Plugin | `~/.adal/plugin-cache/` | External skills from GitHub |

---

## Important: Hook Compatibility

> **Note:** Hooks (PreToolUse, PostToolUse, Stop, SessionStart) may have limited support in AdaL depending on your version.

### What works in AdaL:

- Core 3-file planning pattern
- Templates (task_plan.md, findings.md, progress.md)
- All planning rules and guidelines
- The 2-Action Rule
- The 3-Strike Error Protocol
- Read vs Write Decision Matrix
- Scripts for manual execution

### What may vary:

- Hook execution (check AdaL documentation for hook support)

---

## Manual Workflow for AdaL

If hooks are not supported, follow the pattern manually:

### 1. Create planning files first

Before any complex task:
```
Create task_plan.md, findings.md, and progress.md using the planning-with-files templates.
```

### 2. Re-read plan before decisions

Periodically ask:
```
Please read task_plan.md to refresh the goals before continuing.
```

### 3. Update files after phases

After completing work:
```
Update task_plan.md to mark this phase complete.
Update progress.md with what was done.
```

### 4. Verify completion manually

Before finishing:
```
Check task_plan.md - are all phases marked complete?
```

---

## Using /skills Command

In AdaL, you can view all active skills with:

```
/skills
```

This shows skills from all sources (personal, project, plugins).

---

## File Structure

```
your-project/
├── .adal/
│   └── skills/
│       └── planning-with-files/
│           ├── SKILL.md
│           ├── templates/
│           │   ├── task_plan.md
│           │   ├── findings.md
│           │   └── progress.md
│           ├── scripts/
│           │   ├── init-session.sh
│           │   ├── init-session.ps1
│           │   ├── check-complete.sh
│           │   ├── check-complete.ps1
│           │   └── session-catchup.py
│           └── references/
│               ├── examples.md
│               └── reference.md
├── task_plan.md        ← Your planning files go here
├── findings.md
├── progress.md
└── ...
```

---

## Templates

The templates in `.adal/skills/planning-with-files/templates/` work in AdaL:

- `task_plan.md` - Phase tracking template
- `findings.md` - Research storage template
- `progress.md` - Session logging template

Copy them to your project root when starting a new task.

---

## Scripts

Helper scripts for manual execution:

```bash
# Initialize planning files
./~/.adal/skills/planning-with-files/scripts/init-session.sh

# Check task completion
./~/.adal/skills/planning-with-files/scripts/check-complete.sh

# Session recovery
python ~/.adal/skills/planning-with-files/scripts/session-catchup.py $(pwd)
```

---

## Tips for AdaL Users

1. **Pin planning files:** Keep task_plan.md open in a split view for easy reference.

2. **Use /skills command:** View all installed skills and verify planning-with-files is active.

3. **Use explicit prompts:** Be explicit when starting complex tasks:
   ```
   This is a complex task. Let's use the planning-with-files pattern.
   Start by creating task_plan.md with the goal and phases.
   ```

4. **Check status regularly:** Manually verify completion before finishing.

---

## Need Help?

- AdaL Documentation: [docs.sylph.ai](https://docs.sylph.ai/)
- Open an issue at [github.com/OthmanAdi/planning-with-files/issues](https://github.com/OthmanAdi/planning-with-files/issues)
