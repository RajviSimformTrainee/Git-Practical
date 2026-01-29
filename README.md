1. Branching Workflow:
   - Create feature/sub-branches from `develop` or `project-setup` to isolate work.
   - Small, focused PRs are preferred; multiple commits can be combined when related.

2. Commit Message Hooks:
   - Enforce consistent commit messages to maintain history clarity and standards.

3. Squash Commits:
   - Use `git rebase -i HEAD~n` or `git merge --squash` to combine multiple small commits into a single commit for cleaner PRs.

4. Rebase:
   - Keep feature branches up-to-date with `develop` without creating unnecessary merge commits.
   - Resolve conflicts with `git add <file>` and `git rebase --continue`.
   - Use `git pull --rebase` and `--force-with-lease` for safer pushes after rebasing.
   - `git rebase -i`
     pick (p):keep commit as is, reword (r):edit commit message only,  edit (e):amend commit content,  squash (s):combine this commit into previous one, drop (d):remove commit entirely


5. Cherry-Pick:
   - Apply specific commits from one branch to another using `git cherry-pick <commit>`.
   - Useful for hotfixes or selective changes.
   - Conflicts during cherry-pick are resolved with `git cherry-pick --continue`.

6. Reset:
   - Undo commits with `git reset --soft` (preserve staged changes) or `git reset --hard` (discard changes completely).

7. Stash:
   - Temporarily save work-in-progress changes without committing using `git stash`.
   - Use `git stash -u` to include untracked files.
   - Apply stashes safely with `git stash apply`; `git stash pop` removes stash after applying.

8. Interactive Staging:
   - `git add -p` stages changes hunk-by-hunk for better commit granularity.
   - Helps in splitting changes logically for cleaner commit history.

9. Merge Conflicts:
   - Same-line conflicts require manual resolution (`<<<<<<<`, `=======`, `>>>>>>>`).
   - Multi-file conflicts can be complex; combine contributions manually before committing.

10. Tags & Versioning:
    - Tag important commits for releases: `git tag -a v1.0.0 -m "Release v1.0.0"`.

11. Collaboration Best Practices:
    - Always sync branches with `develop` before creating a PR or rebasing.
    - Avoid overwriting others’ work using `--force-with-lease` after rebasing.

12. Practical Learnings from Exercises:
    - Cherry-pick conflicts require `--continue`, not normal commit.
    - Rebasing requires updated develop branch to avoid unnecessary conflicts.
    - Squash merges keep PR history concise and readable.
    - Stashing tracked vs untracked files behaves differently; use `-u` for untracked files.
    - Merge, rebase, and cherry-pick workflows differ in conflict resolution mechanics.

13. Undo/Recover Work:
    - Reset, revert, and restore help safely undo mistakes in commits, staged or unstaged files.
    - Helps keep unfinished work isolated or remove unwanted commits.

14. Real-Life Scenario Applications:
    - Hotfixes can be applied quickly using cherry-pick without merging entire branches.
    - Multiple developers editing the same config or status file can create 2-way or 3-way conflicts; manual resolution is essential.
    - Stashing allows switching branches without losing unfinished work.
    - Rebasing and squash workflows help maintain clean, linear commit history in collaborative projects.

15. merge VS rebase
    git merge
    - Doesn't modify history, only adds to it
    - Non-destructive operation
    - Leaves more commits in history
    - Leaves commit hashes and timestamps alone
    - Can safely be used on pushed commits

    git rebase
    - Modifies history
    - Destructive operation
    - More linear history
    - Modifies commit hashes and timestamps
    - Never rebase pushed commits
