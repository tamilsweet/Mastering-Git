# Git Submodules

Options to utilize code from other repositories

- Package Manager, eg. NPM
- Git Subtrees
- Git Submodules

Configuration stored in `.gitmodules` file

## Commands

```
git submodules foreach 'cat .gitmodules'


# Steps to get latest changes when using submodules
git pull
git submodules sync --recursive
git submodules update --init --recursive
```

Make sure the child modules doesn't have any pending commits referenced by parent

```
# Push child modules changes also when pushing parent module
git config --global push.recurseSubmodules on-demand
```
