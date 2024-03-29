# Changelog

All notable changes to this project will be documented in this file.

## [1.0.16] - 2024-03-25

### 🐛 Bug Fixes

- *(commit)* Add ci, security, revert, perf commit types

### ⚒  CI

- Add tag rules notes to tag-release

## [1.0.15] - 2024-03-23

### 🐛 Bug Fixes

- *(fixup)* Fix rebase target bug

### ⚒  CI

- Autobump next tag (minor.patch) based on unreleased commits
- Autobump major number when releasing breaking changes
- Fix bug in changelog generation after global set -e was enabled

### Release

- 1.0.15 - auto-increment versions based on commit messages

## [1.0.14] - 2024-03-23

### 🚀 Features

- *(fixup)* Add rebase autosquash mode

### 🐛 Bug Fixes

- *(git-helpers-lib)* Add new line at the end of the output of git_config_check_*_remote()
- *(git-helpers-lib)* Add bash shebang to help helix detect the file type
- *(git-fetchcr-helper)* Select remote first, then the remote type
- *(git-fetchcr-helper)* Set remote branch tracking, first try fork, then cr remote
- *(git-helpers-lib)* Split up exit_if_no_staged_changes() and has_staged_changes()
- *(fixup)* Improve ux around canceling prompts

### Release

- 1.0.14 - general improvements and new fixup feature

## [1.0.13] - 2024-03-15

### 🐛 Bug Fixes

- *(git-new-branch-helper)* Fix branch tracking when not using worktrees
- *(git-helpers-lib)* Default_branch fixes after refactoring
- *(git-helpers-lib)* Dangling variable fixes after refactoring
- *(delete-helpers)* Pull default branch after switching to it

### Release

- 1.0.13 - minor fixes and improvements

## [1.0.12] - 2024-03-09

### 🐛 Bug Fixes

- *(git-new-branch-helper)* Fix next steps doc

### ⚒  CI

- Add CODEOWNERS file

### Release

- 1.0.12 - cosmetic fix for git-new-branch-helper

## [1.0.11] - 2024-03-08

### 🐛 Bug Fixes

- *(git-helpers-lib)* Add git_guess_fork_remote() and git_guess_upstream_remote()
- *(git-helpers-lib)* More refactoring, fixes

### Release

- 1.0.11 - improvements and fixes

## [1.0.10] - 2024-03-06

### ⚒  CI

- *(tag-release)* Abort when no unreleased commits are found
- *(tag-release)* Reduce duplicate code by adding git_lg()

### Release

- 1.0.10 - tag-release improvements

## [1.0.9] - 2024-03-05

### 🐛 Bug Fixes

- *(install-git-aliases)* Add verbosity to script
- *(git-helpers-lib)* Move default branch guess to else branch in git_guess_default_branch()

### 📚 Documentation

- Reset terminal before running tag-release in release-create step
- Move Releases section before Helpers section

### ⚙️ Miscellaneous Tasks

- Add a checkout refresh script

### Release

- 1.0.9 - fix git_guess_default_branch()

## [1.0.8] - 2024-03-03

### 🐛 Bug Fixes

- *(git-new-branch-helper)* Make git worktrees optional

### Release

- 1.0.8 - make worktrees optional when creating a new branch

## [1.0.7] - 2024-03-03

### Ocs

- Don't include release-* playbook steps in runall

### Release

- 1.0.7 - fix release-create

## [1.0.6] - 2024-03-03

### 📚 Documentation

- Spell check readme
- Add runme playbook tasks for listing and creating releases
- Add runme playbook step to show unreleased commits

### ⚙️ Miscellaneous Tasks

- Rename CHANGE_LOG.md to CHANGELOG.md

### Release

- 1.0.6 - add releases-unreleased-commits runme task

## [1.0.5] - 2024-03-03

### ⚒  CI

- *(tag-release)* Fix gh release command recommendation
- *(tag-release)* Add gitlab release creation
- *(tag-release)* Strip header from change log in release notes

### Release

- 1.0.5 - add github and gitlab release creation

## [1.0.4] - 2024-03-03

### ⚒  CI

- *(tag-release)* Fix tag/release message
- *(tag-release)* Gh release fixes

### Release

- 1.0.4 - gh release fixes

## [1.0.3] - 2024-03-03

### ⚒  CI

- *(tag-release)* Add changelog to annotated tags

### Release

- 1.0.3 - add changelog to annotated tags\n\n# Changelog

## [1.0.2] - 2024-03-03

### ⚒  CI

- *(tag-release)* Add prompt to automatically push commits and tag
- *(tag-release)* Add code to create github release

### Release

- 1.0.2 - tag-release creates tags and github releases

## [1.0.1] - 2024-03-03

### 🐛 Bug Fixes

- *(tag-release)* Add current branch to git push examples
- *(tag-release)* Show log difference with remote

### ⚒  CI

- Add tag-release script
- Split chore/ci categories

### Release

- 1.0.1 - add tag-release script

## [1.0.0] - 2024-03-03

### 🚀 Features

- Add initial overly complicated git commit helper script
- Add commit fixup helper
- *(git-commit-helper)* Show commit summary when necessary
- *(git-commit-helper)* Add staged change review prompts
- Add new branch helper
- Add delete branch helper
- *(git-delete-branch-helper)* Remove worktree before deleting branch
- *(git-delete-branch-helper)* Randomly celebrate after deleting branches
- *(git-clean-up-branches-helper)* Add helper that deletes the merged branches
- *(git-clean-up-branches-helper)* Add headless mode
- Add git alias installer
- *(git-fetch-cr-helper)* Add github pr fetcher
- *(git-fetch-cr-helper)* Add gitlab mr fetcher
- *(git-master-to-main-migration-helper)* Add master to main migration helper
- Add ctrl-c trap handler

### 🐛 Bug Fixes

- *(git-commit-helper)* Add instructions for when gitlint fails
- *(git-commit-helper)* Add --name-only to git show summary
- *(git-delete-branch-helper)* Remember previously selected branches
- *(git-commit-helper)* Set width of input boxes
- Clean up prose in readme
- *(git-clean-up-branches-helper)* Use a more reliable way of running confetty
- Remove "--list main" from git branch commands
- Println doesn't support format strings
- Make sure git alias installer is run from inside the git repo
- Add git-fetch-cr-helper helper alias to install script
- Remove "--list main" from git branch commands
- Move repo checkout to ~/.git-helpers
- Make install-git-aliases.sh verbose
- *(git-clean-up-branches-helper)* Use shared library
- *(git-clean-up-branches-helper)* Add exit conditions
- *(git-helpers-lib)* Use tabs for indents
- *(git-fetch-cr-helper)* Improve wording on remote selection prompts
- *(git-helpers-lib)* Change filetype to sh
- *(git-delete-branch-helper)* Use shared library
- *(git-delete-branch-helper)* Add exit conditions
- *(git-clean-up-branches-helper)* Move exit branch if no selected branches
- *(git-helpers-lib)* Move more code to shared library
- *(git-commit-helper)* Use shared library
- *(git-fetch-cr-helper)* Use shared library
- *(git-delete-branch-helper)* Use shared library
- *(git-master-to-main-migration-helper)* Use shared library
- *(git-fetch-cr-helper)* Move additional code to the shared library
- *(git-new-branch-helper)* Use shared library

### 🚜 Refactor

- *(git-commit-helper)* Add improvements from other helpers

### 📚 Documentation

- Add MIT license file
- Add top-level readme file
- Rename project
- Add initial notes on project goals
- Add helper documentation section
- Add fixup helper documentation section
- Prose clean up
- Add dependency section and installation script
- Update to support runme
- Create a setup section
- Add runme entry for refreshing git aliases
- Update runme config sections
- Add github and gitlab cli dependencies

### ⚒  CI

- Add git-cliff configuration

### ⚙️ Miscellaneous Tasks

- *(config)* Add default gitlint configuration
- Add initial .gitignore
- Spell check with aspell
- Add .vscode to .gitignore
- Add glow dependency
- Spellcheck readme
- Clean up variables

### Release

- 1.0.0 - first release with 7 git helpers written in bash

<!-- generated by git-cliff -->
