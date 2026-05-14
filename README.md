# charset-fix 🔤

**Fix Chinese/Unicode text encoding when running AI agents on Windows through POSIX shells.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skill: Windows](https://img.shields.io/badge/Skill-Windows-0078D4)](SKILL.md)

## The Problem

When you run AI coding agents (Claude Code, Codex CLI, Cline, Cursor, etc.) on Windows through Git Bash, BusyBox, or any POSIX-compatible shell, Chinese/Unicode text output gets garbled:

```
$ python3 -c "print('中文测试')"
���Ĳ���
```

This happens because Windows-native tools (Python, PowerShell, cmd.exe) output text in **GBK/CP936** encoding, but the POSIX shell expects **UTF-8**.

## What This Skill Does

Provides AI agents with the knowledge and patterns to:
- Fix Python Chinese output → `PYTHONIOENCODING=utf-8`
- Fix PowerShell Chinese output → `[Console]::OutputEncoding = UTF8`
- Fix cmd.exe/native tool output → Python `subprocess` bridge with `encoding='gbk'`

## Quick Start

This is an **AI agent skill** — install it for your agent:

### Claude Code / Codex CLI

```bash
# Clone the repo
git clone https://github.com/gkd2323c/charset-fix.git

# Claude Code
claude add-skill ./charset-fix

# Codex CLI
codex add-skill ./charset-fix
```

### Cline / Cursor

Place the `charset-fix` folder in your project's `.cline/skills/` or `.cursor/skills/` directory.

### OpenClaw / ClawHub

```bash
clawhub install charset-fix
```

## Manual Fix

If you just need the one-liner right now:

```bash
PYTHONIOENCODING=utf-8 python3 -c "print('中文测试 ✅')"
```

## Repository Structure

```
charset-fix/
├── SKILL.md       # Agent skill definition (main entry)
├── README.md      # This file
├── LICENSE        # MIT License
└── scripts/
    └── fix.py     # Helper script
```

## Compatibility

| OS | Status |
|----|--------|
| Windows + Git Bash | ✅ Tested |
| Windows + BusyBox | ✅ Tested |
| Windows + MSYS2 | ✅ Tested |
| Windows + WSL | ✅ Works |
| macOS / Linux | ❌ Not applicable |

## License

MIT
