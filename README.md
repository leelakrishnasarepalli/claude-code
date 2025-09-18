# Claude Code GitHub Actions

A repository configured with GitHub Actions to integrate Claude AI for automated code reviews and issue/PR assistance.

## Overview

This repository demonstrates how to set up Claude Code GitHub Actions for:
- Automated code reviews on pull requests
- Interactive AI assistance on issues and PRs via @claude mentions
- Integration with Claude's code analysis capabilities

## Features

### 🤖 Claude Code Integration
- **Interactive Assistant**: Tag `@claude` in issues or PR comments to get AI assistance
- **Automated Code Reviews**: Automatic code review on new pull requests
- **Context-Aware Responses**: Claude understands repository context and provides relevant help

### 📋 Supported Events
- Issue comments containing `@claude`
- Pull request review comments with `@claude`
- Pull request reviews mentioning `@claude`
- New issues opened with `@claude` in title or body

## Setup

### Prerequisites
1. Access to [Claude Code](https://claude.ai/code)
2. GitHub repository with Actions enabled
3. Claude Code OAuth token

### Installation

1. **Get Claude Code OAuth Token**
   - Visit [Claude Code](https://claude.ai/code) 
   - Generate an OAuth token for GitHub integration

2. **Add Repository Secret**
   - Go to Settings → Secrets and variables → Actions
   - Add new repository secret: `CLAUDE_CODE_OAUTH_TOKEN`
   - Paste your Claude Code OAuth token

3. **Workflows Already Configured**
   - `.github/workflows/claude.yml` - Interactive Claude assistant
   - `.github/workflows/claude-code-review.yml` - Automated PR reviews

## Usage

### Getting Claude's Help

#### In Issues
Create or comment on an issue with `@claude` followed by your request:
```
@claude can you help me implement feature X?
```

#### In Pull Requests
Comment on a PR with `@claude` to get assistance:
```
@claude please review this implementation
```

### Automatic Code Reviews
Every new pull request automatically triggers Claude to:
- Review code quality and best practices
- Identify potential bugs or issues
- Check performance considerations
- Highlight security concerns
- Assess test coverage

## Configuration

### MCP Servers
The repository includes `.mcp.json` configuration for Context7 integration, enabling enhanced documentation lookups.

### Customizing Workflows

#### Modify Review Prompt
Edit `.github/workflows/claude-code-review.yml` to customize the review criteria:
```yaml
prompt: |
  Your custom review instructions here
```

#### Adjust Permissions
Configure Claude's allowed tools in the workflow:
```yaml
claude_args: '--allowed-tools "Bash(command:*)"'
```

## Workflow Permissions

The workflows are configured with these permissions:
- `contents: read` - Read repository content
- `pull-requests: read` - Read PR information
- `issues: read` - Read issue information  
- `id-token: write` - Required for Claude authentication
- `actions: read` - Read CI results (optional)

## Best Practices

1. **Clear Instructions**: Be specific when asking Claude for help
2. **Context**: Provide relevant context in your requests
3. **Review Feedback**: Claude's suggestions are meant to assist, not replace human judgment
4. **Security**: Never share sensitive information in public comments

## Troubleshooting

### Claude Not Responding
- Verify `@claude` is correctly mentioned
- Check workflow runs in Actions tab
- Ensure `CLAUDE_CODE_OAUTH_TOKEN` secret is set

### Workflow Failures
- Check Actions tab for error logs
- Verify repository permissions
- Ensure OAuth token is valid

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Claude Code Action](https://github.com/anthropics/claude-code-action)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

## Contributing

Feel free to submit issues or pull requests to improve the Claude Code integration!

## License

This repository's Claude Code integration is configured for demonstration purposes. Please refer to your own license requirements for production use.