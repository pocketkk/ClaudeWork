# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Workspace Purpose

This is a **documentation and analysis workspace** for Claude Code sessions, not a traditional software development project. It's used for storing analysis outputs, configuration documentation, and system administration tasks.

## Directory Structure

- `.claude/settings.local.json` - Claude Code permissions configuration
- `*.md files` - Documentation and analysis outputs from previous sessions

## Permissions Configuration

The `.claude/settings.local.json` file defines specific bash command permissions focused on system administration:
- System service management (`systemctl`)
- File operations (`cat`, `ls`, `find`, `grep`)
- Network diagnostics (`ss`)
- Package management (`dpkg`, `apt`)
- Process monitoring (`ps`, `top`, `htop`)

## Common Tasks

Since this is a documentation workspace, typical operations include:
- Analyzing system configurations (like Wave Terminal widgets)
- Creating documentation files
- System information gathering
- Configuration file analysis

## Architecture

This workspace follows a simple documentation-centric structure:
- Analysis outputs are stored as markdown files
- System configuration files may be documented here
- Claude Code session configurations are maintained in `.claude/`

## Working with This Workspace

When working here, expect to:
- Read and analyze existing documentation
- Create new analysis documents
- Use system administration commands for information gathering
- Document findings in markdown format