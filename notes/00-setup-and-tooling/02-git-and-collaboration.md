# Phase 0 - Git and Collaboration

Date: 2026-10-16
Source: `ai-engineering-from-scratch/phases/00-setup-and-tooling/02-git-and-collaboration/docs/en.md`

Git tracks a project through four places a file can live in: the working directory where I actually edit things, the staging area where `git add` marks what's ready to save, the local repo where `git commit` takes a permanent snapshot, and the remote (GitHub) where `git push` backs everything up. I'd already been doing this whole flow throughout today's setup work without naming it explicitly.

A commit is a snapshot of the entire project at one point in time, not just a diff. A branch is a movable pointer to a commit, used to try something without touching main until it's ready. A remote is just a copy of the repo hosted somewhere else.

For the branching exercise, instead of forking the actual course repo (which I'm deliberately not tracking in git), I practiced it directly in my own `day-learn-ai-engineering` repo: created a branch called `experiment/git-lesson-notes`, wrote this notes file on that branch, committed it, then merged the branch back into `main`.

For the `.gitignore` exercise, I added patterns for model checkpoint files (`*.pt`, `*.pth`, `*.safetensors`) and for `.venv/` directories. Testing it caught something real: an experiment folder I'd made earlier (`exercises/new-project/my-ai-project`) had two full virtual environments sitting inside it with hundreds of binary files. Without the `.gitignore` rule those would have been committed. Only the actual project source files (`pyproject.toml`, `README.md`, `src/`, `uv.lock`) got staged once the ignore rule was in place.

For the commit history exercise, I ran `git log --oneline` and `git log --oneline -- phases/00-setup-and-tooling` inside the course clone, which still has its own real git history from when it was cloned. Picking one commit with `git show --stat` showed it was the exact commit that added the `--route` logic to `verify.py`, the script I'd already run yesterday to check my environment.

Result of exercises: all three completed, using the repo's own history in place of forking, and my own tracking repo in place of the course repo for the branch/merge practice.
