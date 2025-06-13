# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a personal development tools repository containing the `dev-start` script, which is a Bash utility that initializes development environments for various project types (Python, Node.js, Django, Docker).

## Architecture

The main component is the `dev-start` script which:
1. Validates Git repository status and prompts for uncommitted changes
2. Checks for updates from remote branches
3. Automatically detects and activates Python virtual environments
4. Analyzes project type (Django, Node.js, Docker) and provides relevant commands
5. Checks for port conflicts and environment files

## Commands

The primary command is:
```bash
./dev-start
```

This script performs comprehensive environment setup including Git status checks, Python virtual environment activation, project type detection, and port availability checks.

Additional options:
```bash
./dev-start --reset  # Reconfigure project settings
```

## Project Settings

The script uses a `.dev-start.conf` file in each project to remember your preferences:
- First run: Interactive setup, saves preferences
- Subsequent runs: Uses saved settings, no prompts
- Settings include directory preferences, project type, and venv check options
- File is automatically added to .gitignore (project-specific, not shared)

## Script Structure

The `dev-start` script follows a modular design with separate functions for each check:
- `check_git_repo()` - Validates Git repository
- `check_git_status()` - Handles uncommitted changes and sync status
- `activate_python_venv()` - Finds and activates virtual environments
- `analyze_project_type()` - Detects Django, Node.js, and Docker projects
- `check_project_structure()` - Interactively creates recommended directories (src, tests, docs, examples, scripts, data, config, .github)
- `check_ports()` - Identifies port conflicts on common development ports
- `check_env_files()` - Validates environment configuration files

## Recommended Directory Structure

The script enforces this Python project structure:
- `src/` - Source code
- `tests/` - Test files (pytest standard)
- `docs/` - Documentation
- `examples/` - Usage examples and demos
- `scripts/` - Build/deployment scripts
- `data/` - Sample data files
- `config/` - Configuration files
- `.github/` - GitHub workflows and templates