-`main` - stable production branch
-`dev` - integration branch for features
-`feature1`, `feature2`, `feature3` - experimental branches
-`hotfix` - fix ready for `main`
- To visualize locally:
- feature1: Merged `dev` into `feature1`, resolved a conflict in `Main.java`, tested, then fast-forward merged `feature1` into `dev` and deleted the branch.
- feature2: Rebased `feature2` onto `dev` to keep a linear history. Resolved conflicts in `GameEngine.java` and kept the public API (`hasUserQuit`) consistent so `GameUI`/tests still compiled. Synced again from `dev` and merged back into `dev`.
- feature3: Squashed 4 commits into **one** using interactive rebase (clean history). Rebased onto `dev` and resolved conflicts (hint code vs existing API). Merged the squashed result into `dev`.
- hotfix: Cherry-picked the `hotfix` commit onto `main` (fix for `Utils.randomInt` upper bound), verified tests, then merged `main` back into `dev` to keep `dev` up-to-date.
- Merge: Combines histories, preserves branch topology.  
  Used for: bringing `feature1` back into `dev`, and merging `main` into `dev` after hotfix.
- Rebase: Rewrites feature history onto a new base (linearizes).  
  Used for: updating `feature2` (and `feature3` after squashing) to sit cleanly on top of `dev`.
- Squash: Compresses multiple commits into one for a tidy story.  
  Used for: cleaning up `feature3`’s many WIP commits before integrating.
- Cherry-pick: Copies a single commit onto another branch.  
  Used for: applying the urgent `hotfix` onto `main` without touching `dev`, then merging back.
- feature1 shows a simple merge-based flow (one conflict in `Main.java`, then fast-forward into `dev`).
- feature2 shows a rebase flow with conflict resolution and API compatibility work.
- feature3 shows squash + rebase to avoid bringing noisy WIP commits into `dev`.
- The hotfix commit appears on both `main` and `dev` (cherry-pick → merge), keeping production and integration consistent.
- Merge: when preserving full context of parallel work matters, or when many collaborators are touching the feature.
- Rebase: for private feature branches to keep history linear and reviewable before integration.
- Squash: to present a clean, atomic change for a feature (one “what/why” commit) before merging.
- Cherry-pick: to apply a focused fix across branches (e.g., urgent production hotfix) without merging all intermediate work.
- `dev` history is linear and readable (squashed feature3 helps).
- Feature branches can be messy internally, but rebasing/squashing before merge keeps `dev` clean.
- Hotfix applied to `main` also exists in `dev`.
