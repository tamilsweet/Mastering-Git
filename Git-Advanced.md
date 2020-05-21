## Git Workflow Model

Ref: https://nvie.com/posts/a-successful-git-branching-model/

### Distribution Model

- Peer to Peer
- Centralized Model
- Pull Request Model - Maintainers and contributors
- Dictator and Lieutenants Model - Sub projects and integration in higher level

### Branching Model

- Stable branch - tip is working version
- Unstable branch - no guarantee of working tip

#### Branch names

- Integration branch (mainline / master)
- Release branch
- Feature branch (Topic branch)
- Hotfix branch

### Constriants

- Rebase don't merge (rebase feature branch on top of integration branch)
- Merge don't rebase (merge feature branch into the integration branch)
- Lock branches
- Don't push to a red build
- Hook that check the build status and shows warning if the build status is red to cancel push
- Squash the local commits before merging

## Git Configurations

- Repository (local)
- User Account (global)
- Git installation (system)

### Config file location

```
# Mac & Windows

# Local (repository)
repository/.git/config
D:/Mastering-Git/.git/config

# Global (user directory)
/Users/david/.gitconfig
C:/Users/tamilsweet/.gitconfig

# System (git installation)
/usr/local/etc/gitconfig
D:/Program Files/Git/etc/gitconfig
```

### Setting Config value

```
# Local (repository)
git config --local user.name "Tamilmozhi Gunasekar"

# Global (user directory)
git config --global user.name "Tamilmozhi Gunasekar"

# System (git installation)
git config --system user.name "Tamilmozhi Gunasekar"
```

## Git Settings

- Identity Settings
- File editor
- Merge tool
- Terminal color output
- Command aliases
