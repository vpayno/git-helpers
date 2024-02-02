# git-helpers

Starting out with a demo for a git-commit-helper using bash and Gum and seeing where this eventually ends up.

## Iterations

Just finished the book [Effortless](https://gregmckeown.com/books/effortless/) and I'm trying it out for this project.

- v1 - it's ugly but it's at least written down/created

    - Go through my ~/.gitconfig files and manual command clumps and create v1 versions of them first.
    - Only working on one script at a time.
    - Mostly only using [Bash](https://www.gnu.org/software/bash/manual/bash.html), [Gum](https://github.com/charmbracelet/gum) and [Glow](https://github.com/charmbracelet/glow)

- v2 - improve them without burning out, over effort, or maximizing diminishing returns

    - Use theese as practice for learing Go+Cue+BubbleTea.
    - Slow is smooth, smooth is fast.

## Helpers

### git-commit-helper

Not a dumb tool, it helps:

- remind you of the proper format for commit subjects,
- spell check your subject and body and
- lint unpushed commit(s) or the task branch.

### git-fixup-helper

This one makes using fixup commits easier.

As I add scripts, they are succesfully better than the last.

- Checks to see if the user has staged changes.
- Has different behavior if on the default branch or a task branch.
- Has a roundabout way of browsing commit fixup candidates.
- Guides user on next steps.

### git-new-branch-helper

This script creates a new worktree and branch and then shows you how to clean up after you're done with your change review.

Note: Using `cr` for `change-review` instead of `pr` for `pull-request` or `mr` for `merge-request`.

- worktree path layout "repo root path"-cr-"branch name"
- only allows alpha-numeric characters, dash and underscore in branch names
    - spaces, /, etc can create a lot of headaches
- show users how to start using their new branch and worktree
- show users how to remove their new worktree and branch (that will get replaced by the next helper)