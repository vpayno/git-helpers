# git-helpers

Starting out with a demo for a git-commit-helper using bash and Gum and seeing where this eventually ends up.

## Iterations

Just finished [Effortless](https://gregmckeown.com/books/effortless/) and I'm trying it out for this project.

- v1 - it's ugly but it's at least written down/created

    - Go through my ~/.gitconfig files and manual command clumps and create v1 versions of them first.
    - Only working on one script at a time.
    - Mostly only using [Bash](https://www.gnu.org/software/bash/manual/bash.html), [Gum](https://github.com/charmbracelet/gum) and [Glow](https://github.com/charmbracelet/glow)
    - Adding headless modes to some of the scripts.

- v2 - improve them without burning out, over effort, or maximizing diminishing returns

    - Use these as practice for learning Go+Cue+BubbleTea.
    - Slow is smooth, smooth is fast.

## Setup

To install the git helpers and project dependencies run the following commands:

```bash { background=false category=setup closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=setup-git-helpers promptEnv=true terminalRows=10 }
git clone https://github.com/vpayno/git-helpers.git ~/.git-helpers
cd ~/.git-helpers
./install-git-aliases.sh
./install-deps.sh
```

### Dependencies

Note: you can use [RunMe](https://github.com/stateful/runme) to use this readme as a playbook.

To install all the dependencies at once you can use the included installation script:

```bash { background=false category=setup closeTerminalOnSuccess=false excludeFromRunAll=false interactive=true interpreter=bash name=install-dep-all promptEnv=true terminalRows=10 }
./install-deps.sh
```

<details>
    <summary><hr4>Individual Dependencies</hr4></summary>

- [Gum](https://github.com/charmbracelet/gum)

```bash { background=false category=dependency closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=install-dep-gum promptEnv=true terminalRows=10 }
go install github.com/charmbracelet/gum@latest
```

- [Glow](https://github.com/charmbracelet/glow)

```bash { background=false category=dependency closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=install-dep-glow promptEnv=true terminalRows=10 }
go install github.com/charmbracelet/glow@latest
```

- [Confetty](https://github.com/maaslalani/confetty)

```bash { background=false category=dependency closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=install-dep-confetty promptEnv=true terminalRows=10 }
go install github.com/maaslalani/confetty@latest
```

- [GitHub Cli](https://github.com/cli/cli)

```bash { background=false category=dependency closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=install-dep-github-cli promptEnv=true terminalRows=10 }
go install github.com/cli/cli/v2/cmd/gh@latest
```

- [GitLab Cli](https://gitlab.com/gitlab-org/cli)

```bash { background=false category=dependency closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=install-dep-gitlab-cli promptEnv=true terminalRows=10 }
go install gitlab.com/gitlab-org/cli/cmd/glab@latest
```

</details>

## Releases

The `./tag-release` script is used to

- update the [CHANGELOG](./CHANGELOG.md)
- create an annotated tag
- create a GitHub and/or GitLab release

Use this Runme playbook to list the latest 10 releases:

```bash { background=false category=release closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=releases-list promptEnv=true terminalRows=10 }
printf "\n"
printf "Latest releases:\n"
printf "\n"
git tag --list -n1 | tail
printf "\n"
```

Use this Runme playbook to list the unreleased commits:

```bash { background=false category=release closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=releases-unreleased-commits promptEnv=true terminalRows=10 }
printf "\n"
printf "Unreleased commits since %s:\n" "$(git tag --list -n0 | tail -n1)"
printf "\n"
git log --pretty=format:'%h -%d %s (%cr) <%an>' --abbrev-commit --decorate "$(git tag --list -n0 | tail -n1)"..
printf "\n"
```

Use this Runme playbook to tag a new release.

```bash { background=false category=release closeTerminalOnSuccess=false excludeFromRunAll=true interactive=true interpreter=bash name=release-create promptEnv=true terminalRows=20 }
export TAG_TITLE="short description"

reset
./tag-release "${TAG_TITLE}"
```

## Helpers

Install or refresh git aliases for the helpers.

```bash { background=false category=refresh,git closeTerminalOnSuccess=false excludeFromRunAll=false interactive=true interpreter=bash name=install-git-helpers promptEnv=true terminalRows=10 }
./install-git-aliases.sh
```

<details>
    <summary><hr3>git-commit-helper</hr3></summary>

Not a dumb tool, it helps:

- remind you of the proper format for commit subjects,
- spell check your subject and body and
- lint unpushed commit(s) or the task branch.

</details>

<details>
    <summary><hr3>git-fixup-helper</hr3></summary>

This one makes using fixup commits easier.

As I add scripts, they are successfully better than the last.

- Checks to see if the user has staged changes.
- Has different behavior if on the default branch or a task branch.
- Has a roundabout way of browsing commit fixup candidates.
- Guides user on next steps.

</details>

<details>
    <summary><hr3>git-new-branch-helper</hr3></summary>

This script creates a new worktree and branch and then shows you how to clean up after you're done with your change review.

Note: Using `cr` for `change-review` instead of `pr` for `pull-request` or `mr` for `merge-request`.

- worktree path layout "repo root path"-cr-"branch name"
- only allows alpha-numeric characters, dash and underscore in branch names
    - spaces, /, etc can create a lot of headaches
- show users how to start using their new branch and worktree
- show users how to remove their new worktree and branch (that will get replaced by the next helper)

</details>

<details>
    <summary><hr3>git-delete-branch-helper</hr3></summary>

This scripts automates the deletion of branches, and associated worktrees, from a local and remotes.

Instead of over complicating the script, assume it will wipe the branch from existence (except for the reflog).

If you need to perform a surgical deletion of the branch, do it by hand.

- prompt for "enter name" or "search for branch"
- confirm the branch name by showing the last 10 commits in the branch
- check if a worktree is associated with the branch
- delete both the worktree and branch from local
- delete the branch from all remotes
- declare victory over the evil Branchians, maybe use that terminal fireworks CLI

</details>

<details>
    <summary><hr3>git-clean-up-branches-helper</hr3></summary>

Almost the same as `git-delete-branch-helper`.
The difference is that the user starts with all the merged branches selected and all the not-merged branches are omitted from the selection screen.

- Supports headless mode so it can be run from git.

</details>

<details>
    <summary><hr3>git-fetch-cr-helper</hr3></summary>

Used to simplify the process of checking out a change review (CR) branch from GitHub/GitLab.

- Uses git worktrees.
- Checks out change review to immutable branch `prs-number` (GitHub) or `mrs-number` (GitLab).
- If both GitHub and GitLab push URLs are found for the `origin` remote, check GitHub first, then Gitlab.
- Uses [gh](https://github.com/cli/cli) and [glab](https://gitlab.com/gitlab-org/cli) clis.
- Creates worktree with the same branch name as the one used in the change review.
- Adds remote (when the change review author used a fork) that can be tracked and pushed to.
- Reminds users to use `git-fixup-helper` when modifying existing commits to make it easier to show/review changes by the change review author..

</details>

<details>
    <summary><hr3>git-master-to-main-migration-helper</hr3></summary>

I hate it when someone renames the `master` branch to `main` without taking care that other developers don't just re-push the `master` branch and keep working with it.

This helper helps with that problem. It's a lot of steps to run by hand over and over again so this is a perfect task for automation.

- clone `master` to `main`
- update the default branch on github and/or gitlab
- make sure force pushes are blocked on `main`
- reset commit history on `master` to 1 commit
    - add new readme with info on the rename and instructions they should run on their local clone
    - amend and reword the only commit
    - goal is to make it very obvious they need to stop using `master` and to start using `main`
    - force push `master`
    - block force pushes on `master` upstream(s)

</details>
