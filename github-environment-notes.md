# GitHub Environment Configuration Notes

This document outlines the GitHub workflow setup and lessons learned while working in this environment.

## Environment Setup

### GitHub CLI Installation
- **Status**: GitHub CLI (`gh`) is installed at `/usr/bin/gh`
- **Version**: 2.45.0 (Ubuntu package)
- **Issue**: The `gh` command is aliased to `history | grep` in the shell
- **Solution**: Use full path `/usr/bin/gh` to access the actual GitHub CLI

### Authentication
- **Method**: GitHub Personal Access Token (GITHUB_TOKEN)
- **Account**: pocketkk
- **Protocol**: HTTPS
- **Scopes**: gist, project, read:org, repo, workflow, write:discussion
- **Status**: ✅ Successfully authenticated

### Git Configuration Issues Encountered

#### Problem 1: HTTPS Authentication Failure
- **Error**: `fatal: could not read Username for 'https://github.com': No such device or address`
- **Cause**: Git credential helper not configured to work with GitHub CLI
- **Solution**: Run `/usr/bin/gh auth setup-git` to configure git authentication

#### Problem 2: Shell Alias Conflict
- **Issue**: `gh` command aliased to `history | grep`
- **Impact**: Cannot use standard `gh` commands directly
- **Workaround**: Use full path `/usr/bin/gh` for all GitHub CLI operations

## Successful Workflow

### Repository Creation
```bash
/usr/bin/gh repo create ClaudeWork --public --description "Description here"
```

### Git Setup and Push
```bash
# Initialize and commit
git init
git add .
git commit -m "Initial commit"

# Create branch
git checkout -b branch-name

# Add remote and configure authentication
git remote add origin https://github.com/pocketkk/ClaudeWork.git
/usr/bin/gh auth setup-git

# Push branch
git push -u origin branch-name
```

## Key Learnings

### 1. Shell Configuration Impact
- Custom shell aliases can interfere with CLI tools
- Always check for aliases when tools behave unexpectedly
- Use full paths as workaround when needed

### 2. GitHub CLI Authentication
- GitHub CLI provides seamless authentication for git operations
- Must run `gh auth setup-git` to configure git credential helper
- Personal access tokens work well for automated workflows

### 3. Permission Management
- Claude Code permissions needed updating to include GitHub CLI operations
- Added `"Bash(gh:*)"` to allowed commands in `.claude/settings.local.json`

### 4. Repository Creation Best Practices
- Use descriptive repository names and descriptions
- Public repositories are default for documentation projects
- GitHub CLI can create and configure repositories in one command

## Environment Specifics

### File Paths
- **GitHub CLI**: `/usr/bin/gh`
- **Git config**: Uses global configuration
- **Claude permissions**: `/home/sylvia/ClaudeWork/.claude/settings.local.json`

### Account Details
- **GitHub username**: pocketkk
- **Repository created**: https://github.com/pocketkk/ClaudeWork
- **Authentication method**: Personal Access Token via GitHub CLI

## Recommendations for Future Sessions

1. **Always use full path** for GitHub CLI: `/usr/bin/gh`
2. **Check authentication status** before starting: `/usr/bin/gh auth status`
3. **Run setup command** if git push fails: `/usr/bin/gh auth setup-git`
4. **Update Claude permissions** as needed for new tools
5. **Test git operations** in small steps to identify issues early

## Troubleshooting Quick Reference

| Issue | Command to Fix |
|-------|----------------|
| `gh` command not working | Use `/usr/bin/gh` instead |
| Git push authentication fails | `/usr/bin/gh auth setup-git` |
| Repository creation fails | Check `/usr/bin/gh auth status` |
| Permissions denied | Update `.claude/settings.local.json` |

This environment is now fully configured for GitHub operations using the GitHub CLI with proper authentication.