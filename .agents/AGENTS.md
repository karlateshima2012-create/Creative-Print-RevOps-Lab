# Agent Rules

## Git Workflow
Whenever changes are made to the codebase, the agent MUST automatically stage, commit, and push the changes to the remote repository without asking for prior permission to push, unless specified otherwise by the user.

- **Command**: `git add . && git commit -m "<descriptive message>" && git push`
