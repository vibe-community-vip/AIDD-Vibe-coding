# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AIDD-Vibe-coding is a specialized AI prompt repository for automating software development workflows using AI agents (Gemini and Claude). The project focuses on standardizing and automating processes like semantic commit generation, code analysis, and documentation creation.

## Project Structure and Architecture

The project follows a **Prompt-Based Configuration Pattern** that separates AI-specific configurations from general task prompts:

```
/.claude/          # Claude CLI specific configurations and commands
/.gemini/          # Gemini CLI specific configurations and commands
/prompts/          # AI-agnostic prompts that define agent tasks
```

### Key Directories:
- **`.claude/commands/`** - Contains Claude-specific command definitions (commit.md)
- **`.gemini/commands/`** - Contains Gemini-specific command definitions
- **`prompts/`** - Core prompt templates for various AI tasks:
  - `commit.md` - Semantic commit generation logic
  - `contex.md` - Project analysis and documentation templates
  - `crear_requerimientos.md` - Requirements creation prompts
  - `lluvia_de_ideas.md` - Brainstorming session prompts
  - `readme.md` - README generation templates

## AI Agent Configuration

### Claude Commands
The project includes a custom `/commit` slash command configured in `.claude/commands/commit.md` that:
- Analyzes staged git changes automatically
- Generates semantic commit messages in Spanish following Conventional Commits specification
- Includes emoji prefixes and automatic type detection
- Supports advanced git options like `--amend`, `--no-verify`, `--dry-run`

### Prompt Templates
The `prompts/` directory contains reusable prompt templates that can be invoked by either AI CLI:
- All prompts are written in Spanish
- Follow structured formats with clear role definitions
- Include detailed step-by-step processes
- Specify expected output formats

## Development Workflow

### No Traditional Build Process
This is a prompt/configuration repository with no package dependencies or build steps. The workflow involves:

1. **Prompt Development**: Create/modify prompts in `/prompts/`
2. **Agent Configuration**: Configure AI-specific commands in `/.claude/` or `/.gemini/`
3. **Testing**: Execute prompts via respective AI CLIs

### AI CLI Execution
Agents are executed by invoking prompts through their respective CLIs:
```bash
# Example for Gemini
gemini -p prompts/commit.md

# Example for Claude (using custom commands)
/commit
```

## Environment Requirements

### Prerequisites
- Git
- Google AI CLI (Gemini)
- Anthropic CLI (Claude)
- Proper API key configuration for each AI service

### No Package Management
The project does not use npm, pip, or other package managers. All functionality is delivered through prompt engineering and AI CLI integration.

## Important Conventions

- **Language**: All prompts, documentation, and outputs are in Spanish
- **Commit Style**: Uses Conventional Commits with emoji prefixes
- **File Organization**: Maintain separation between AI-specific configs and general prompts
- **Prompt Structure**: Follow established patterns with role definition, process steps, and output specifications

## Testing and Validation

No automated testing framework is used. Validation occurs through:
- Manual execution of prompts via AI CLIs
- Verification that generated outputs meet specification requirements
- Testing prompt effectiveness with actual development workflows