# Critical Thinking Project: Source Code Management for a Distributed Development Team

## Student Information

*Name:* Adepomola Ayomide

---

# Task 1: Evaluate Different SCM Tools

## Introduction

Source Code Management (SCM) is the process of tracking, managing, and controlling changes made to source code during software development. SCM enables multiple developers to collaborate efficiently, maintain version history, recover previous versions, and manage software releases.

Version Control Systems are generally divided into two categories:

- Centralized Version Control Systems (CVCS)
- Distributed Version Control Systems (DVCS)

Popular examples include Subversion (SVN) for centralized version control and Git for distributed version control.

## Comparison Between Centralized and Distributed Version Control Systems

| Feature | Centralized VCS (SVN) | Distributed VCS (Git) |
|----------|-----------------------|-----------------------|
| Repository | Single central server | Every developer has a complete repository |
| Internet Requirement | Usually required | Can work offline |
| Speed | Slower | Faster |
| Backup | Single point of failure | Multiple backups available |
| Collaboration | Depends on central server | Developers work independently |
| Branching | Limited and slower | Fast and lightweight |

## Advantages of Git

- Faster performance
- Offline development
- Efficient branching and merging
- Complete project history on every developer's computer
- Better collaboration for distributed teams
- Easy integration with GitHub and CI/CD tools

## Challenges of Git

- Steeper learning curve for beginners
- Merge conflicts when multiple developers modify the same files
- Requires proper branch management
- Incorrect Git commands can affect project history

## Why the Team Should Move to Git

Git provides better collaboration, faster development, reliable version history, and strong support for distributed software development. Every developer can work independently without relying on a central server, making Git highly suitable for geographically distributed teams.

# Task 2: Implement Git Workflows for a Team Project

## Git Workflow Strategy

The project uses a feature branching workflow to allow multiple developers to work on different features simultaneously while keeping the main branch stable.

### Branching Strategy

- *main* – Contains the stable production-ready code.
- *development* – Used to integrate completed features before merging into the main branch.
- *feature-login* – Used to develop the login feature independently.

## Git Commands Used

### Clone the Repository

```bash
git clone https://github.com/adepomola/CRITICAL-SCM-FIXED-2.git
```


### Create the Development Branch

```bash
git checkout -b development
```


### Create the Feature Branch

```bash
git checkout -b feature-login
```


### Stage Changes

```bash
git add .
```

### Commit Changes

```bash
git commit -m "Add project documentation and planning files"
git commit -m "Add login feature documentation"
```


### Push Changes

```bash
git push -u origin development
git push -u origin feature-login
```


### Merge the Feature Branch

```bash
git checkout development
git merge feature-login
git push
```

### Merge into the Main Branch

```bash
git checkout main
git merge development
git push
```


## Pull Request Workflow

The team follows a pull request workflow where developers create feature branches, commit their work, push the branch to GitHub, and open a pull request. Team members review the code before it is merged into the development branch. After testing, the development branch is merged into main.

## Benefits of This Workflow

- Isolates feature development.
- Enables code reviews through pull requests.
- Reduces the risk of unstable code reaching production.
- Makes collaboration easier for distributed teams.

# Task 3: Automate Code Quality and Deployment

## CI/CD Pipeline Implementation

A GitHub Actions workflow was created in:

```text
.github/workflows/ci.yml
```


The workflow automatically runs whenever code is pushed to the main, development, or feature-login branches, and whenever a pull request is opened for the main or development branch.

### Pipeline Functions

- Checks out the repository.
- Verifies that the workflow runs successfully.
- Lists the project files.
- Provides a foundation for adding automated tests and deployments in the future.

### Benefits

- Automatically validates repository changes.
- Supports continuous integration.
- Reduces manual verification.
- Improves collaboration for distributed development teams.
# Task 4: Enforce Security Best Practices

## Repository Security

To improve repository security and maintain code integrity, the following best practices were implemented.

### User Access Control

GitHub repository permissions ensure that only authorized team members can push changes or approve pull requests.

### SSH Authentication

SSH keys provide secure authentication between developers' computers and GitHub without repeatedly entering passwords.

### Branch Protection

The main branch should be protected by requiring pull requests before merging changes. Direct pushes to the production branch should be restricted.

### Signed Commits

Developers should use GPG or SSH commit signing to verify the authenticity of commits and ensure that code changes originate from trusted contributors.

### Audit Trail

Git maintains a complete history of commits, branches, merges, and contributors. This audit trail allows teams to track every code change and quickly identify when and why changes were made.

## Benefits

- Improved repository security
- Better accountability
- Protected production code
- Secure collaboration
- Complete change history

# Task 5: Handle a Real-World Git Challenge

## Merge Conflict Scenario

During development, two developers modified the same file on different branches, resulting in a merge conflict when attempting to merge the branches.

## Conflict Resolution Process

The following Git commands were used during the conflict resolution process:

```bash
git pull origin main
git status
git merge feature-login
```


After identifying the conflicting sections, the file was edited manually to keep the correct changes. The conflict markers were removed, and the resolved file was saved.

The changes were then committed using:

```bash
git add .
git commit -m "Resolve merge conflict"
git push
```


## Preventing Future Merge Conflicts

To reduce merge conflicts in future projects, the team will:

- Communicate regularly before modifying shared files.
- Create smaller and more frequent pull requests.
- Pull the latest changes before starting new work.
- Perform code reviews before merging.
- Use feature branches for independent development.

## Conclusion

This project demonstrated how Git supports distributed software development through feature branching, pull requests, merge conflict resolution, GitHub Actions, and security best practices. These practices improve collaboration, code quality, and project reliability.