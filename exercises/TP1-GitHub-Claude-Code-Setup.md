# TP1: Setting Up GitHub with Claude Code

**Duration**: 30 minutes
**Level**: Beginner
**Prerequisites**: GitHub account, basic knowledge of Git

## Learning Objectives

By the end of this practical exercise, you will be able to:
- Set up Claude Code GitHub integration in your repository
- Trigger Claude Code using GitHub issues
- Understand the basic workflow of working with Claude Code

## Introduction

Claude Code is an AI assistant that can help you with coding tasks directly through GitHub. Once configured, you can mention `@claude` in issues or pull requests, and Claude will automatically respond and help with your request.

## Part 1: Repository Setup (10 minutes)

### Step 1: Fork or Create a Repository

1. Go to GitHub and either:
   - Fork an existing repository, OR
   - Create a new repository for this exercise

2. Make sure your repository is:
   - Either public OR private (if you have access to GitHub Apps for private repos)
   - Contains at least one file (like a README.md)

### Step 2: Install the Claude Code GitHub App

Open Claude Code in terminal, and run ```/install-github-app```, follow instructions
[Reference](https://code.claude.com/docs/en/github-actions)

## Part 2: Basic Configuration (5 minutes)

### Step 3: Create a CLAUDE.md File (Optional but Recommended)

Create a file named `CLAUDE.md` in the root of your repository. This file gives Claude context about your project.

Example content:
```markdown
# CLAUDE.md

## Project Overview

This is a practice repository for learning how to use Claude Code with GitHub.

## Development Guidelines

- Keep code simple and well-commented
- Follow Python PEP 8 style guide
- Write clear commit messages
```

**Why this matters**: The CLAUDE.md file helps Claude understand your project's context, coding standards, and preferences.

## Part 3: Testing the Integration (10 minutes)

### Step 4: Create Your First Issue

1. Go to the **Issues** tab in your repository
2. Click **"New Issue"**
3. Enter a title: `Test Claude Code Integration`
4. In the description, type:
   ```
   @claude Hello! Can you help me create a simple Python function that adds two numbers?
   ```
5. Click **"Submit new issue"**

### Step 5: Observe Claude's Response

1. Wait a few moments (typically 10-30 seconds)
2. Claude will automatically post a comment on your issue
3. Claude will show a checklist of tasks it's working on
4. Watch as Claude:
   - Creates the requested code
   - Commits the changes to a new branch
   - Provides a link to create a pull request

### Step 6: Review Claude's Work

1. Click on the branch link provided by Claude
2. Review the code that Claude created
3. If Claude created a PR link, click it to create a pull request
4. Review the pull request and merge it if everything looks good

## Part 4: Practice Scenarios (5 minutes)

Now that you understand the basics, try these additional exercises:

### Exercise A: Code Review
Create a new issue and ask:
```
@claude Can you review this code and suggest improvements?
[paste some simple code]
```

### Exercise B: Bug Fix
Create an issue with:
```
@claude I have a bug in my code at line X. Can you help me fix it?
```

### Exercise C: Documentation
Ask Claude to:
```
@claude Can you add documentation to my main Python file?
```

## Expected Outcomes

After completing this TP, you should have:
- ✅ A working Claude Code integration in your repository
- ✅ At least one successfully resolved issue with Claude's help
- ✅ Understanding of the basic workflow: Issue → Claude Response → Branch → PR → Merge
- ✅ A CLAUDE.md file with project context

## Troubleshooting

### Problem: Claude doesn't respond to my issue
**Solutions**:
- Make sure you typed `@claude` (not @Claude or @CLAUDE)
- Verify the GitHub App is installed correctly
- Check that the issue is in a repository where Claude is installed
- Wait a bit longer (sometimes it takes up to a minute)

### Problem: Claude creates code but I can't see it
**Solution**:
- Claude creates a new branch automatically
- Look for the branch name in Claude's comment
- Click on the branch link to view the code

### Problem: I want to give Claude more specific instructions
**Solution**:
- Use the CLAUDE.md file to set project-wide preferences
- Be specific in your issue description
- Include code snippets, file paths, and clear requirements

## Best Practices

1. **Be Specific**: The more details you provide, the better Claude can help
2. **Use CLAUDE.md**: Set up project guidelines to get consistent results
3. **Review Everything**: Always review Claude's code before merging
4. **Iterate**: If Claude's first attempt isn't perfect, ask for refinements in a follow-up comment
5. **Start Small**: Begin with simple tasks to understand the workflow

## Additional Resources

- [Claude Code Documentation](https://github.com/anthropics/claude-code)
- [Claude Code GitHub Action](https://github.com/anthropics/claude-code-action)
- [Example CLAUDE.md files](https://github.com/search?q=filename%3ACLAUDE.md)

## Submission

To complete this TP, submit:
1. Link to your repository with Claude Code installed
2. Link to at least one issue where Claude successfully helped you
3. Screenshot of your merged pull request
4. Brief reflection (2-3 sentences): What task do you think Claude Code would be most useful for in your projects?

---

**Congratulations!** You've successfully set up and tested Claude Code with GitHub. You can now use this powerful tool to assist with coding tasks, code reviews, documentation, and more.
