# Git Basics

> A distributed version control system for tracking changes in source code

## Date Learned
2026-01-21

## Key Concepts

- Version control
- Commits and branches
- Remote repositories
- Collaboration

## Notes

### Overview
Git is a distributed version control system that helps developers track changes in their codebase, collaborate with others, and manage different versions of their projects.

### Important Points
- Git stores snapshots of your project at different points in time
- Each commit has a unique SHA-1 hash
- Branches allow parallel development
- Remote repositories enable collaboration

### Code Examples

```bash
# Initialize a new git repository
git init

# Check status of files
git status

# Add files to staging area
git add .

# Commit changes
git commit -m "Your commit message"

# Push to remote repository
git push origin main

# Pull latest changes
git pull origin main

# Create a new branch
git checkout -b feature-branch

# Merge branches
git merge feature-branch
```

## Use Cases

- Managing project versions
- Collaborating with team members
- Tracking code history
- Experimenting with new features safely

## Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Pro Git Book](https://git-scm.com/book/en/v2)
- [GitHub Git Handbook](https://guides.github.com/introduction/git-handbook/)

## Related Topics

- GitHub/GitLab/Bitbucket
- Version control strategies
- Git workflows (GitFlow, GitHub Flow)

---
*Tags: git, version-control, devops, basics*
