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

** Environment Variables can also be used to set git configurations **

### View Config Values

```
# Show all config values and the file where they are defined
git config --list --show-origin

# Show the current user.name config value (sub any key)
git config user.name
```

### Removing Git Config Values

```
# Remove a specific setting for a specific level of config
git config --global --unset user.name

# Edit a specific level of config directly
git config --global --edit

# Remove a section of config for specific level
git config --global --remove-section user
```

### Editor setting

```
git config --global core.editor "code --new-window --wait"

# Use following config for using vscode as diff tool

[diff]
  tool = vscode-diff
[difftool]
  prompt = false
[difftool "vscode-diff"]
  cmd = code --wait --diff $LOCAL $REMOTE

# Use following config for using vscode as merge tool
[merge]
  tool = vscode-merge
[mergetool]
  keepBackup = false
[mergetool "vscode-merge"]
  cmd = code --wait $MERGED
```

### Git Attributes

Configuration settings that dictate how files are handled.

- Configuring line ending in files
- Specifying binary files
- Enabling large binary files to be handled by Git LFS
- Excluding files from exported version of a repository
- Specify clean and smudge filters

### Exclude files from export

```
# .gitattributes
.*      export-ignore
tests   export-ignore
```

### Clean and Smudge Filter

```
git config --local filter.updateAPIKey.smudge 'sed "s/{SECRET_API_KEY}/asdfdsfsdfasdfasdf/"'
git config --local filter.updateAPIKey.clean 'sed "s/asdfdsfsdfasdfasdf/{SECRET_API_KEY}/"'

echo ".js   filter=updateAPIKey" >> .gitattibutes
```

## Git Hooks

Scripts that executes on specific Git events

- Client-side hooks
- Server-side hooks

### Client-sde Git Hooks

- pre-commit
- prepare-commit-msg
- commit-msg
- post-commit

_Use Cases_

- Linting files
- Running tests
- Verifying no TODO's in commited code
- Preparing a commit message
- Cleaning up files after specific actions

### Server-side Git Hooks

- pre-receive
- update
- post-receive

_Use Cases_

- Enforcing commit message format
- Enforcing user identity information
- Enforcing signing of tags and/or commits
- Block access for specific IP addresses
- Blocking specific file extensions

### Client-side hook config

Config for local git repo `.git/hooks/pre-commit.sample`
To store config inside repo use `.githooks/pre-commit`
Make sure that the file is executable using `chmod +x .githooks/pre-commit`

`set -e` to run scripts and use non-zero return values as errors

## Custom Git Commands

Any script can be added as custom git command involed using `git <customcommand>`
Make sure the script starts with `git-` eg. `git-customcommand`
Make sure script is executable `chmod +x git-customcommand`
Add the script to PATH `export PATH="script_path:$PATH"`
Run the custom command using `git customcommand`
