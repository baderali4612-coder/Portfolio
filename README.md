# Portfolio
Git Workflow & Project Notes

1. Branching Strategy & Workflow
   Branching Model: Feature-branch workflow branching off `main`.
   Naming Conventions: Descriptive prefix-based branch names (e.g., `feature/contact-form-validation`, `fix/ci-failure`).
   PR Process: All changes are submitted via Pull Requests to `main`. PRs require passing GitHub Actions CI checks before merging.

2. CI Pipeline & Branch Protection
   GitHub Actions: Automated workflow triggered on pushes and pull requests to validate HTML markup and lint codebase styles.
   Protection Rules: Enforced branch protection on `main` requiring passing status checks before PRs can be merged.

3. Conflict Resolution Case Study
   During the development process, a merge conflict occurred when pulling updates from `main` into a working feature branch (`origin/main` contained updated HTML structure while the feature branch had local form changes).

Resolution Steps:

1. Ran `git pull origin main` (and `--allow-unrelated-histories` where initial commit trees differed).
2. Inspected conflicting files and identified Git markers (`<<<<<<<`, `=======`, `>>>>>>>`).
3. Manually reconciled the differences by preserving semantic structure and keeping the updated form validation logic.
4. Staged the resolved files with `git add <file>`.
5. Completed the merge commit using `git commit -m "fix: resolve merge conflict between main and feature branch"`.
6. Verified local tests and pushed the clean resolution back to remote.

7. Release & Deployment
   Deployment: Live portfolio hosted via GitHub Pages from the `main` branch.
   Tagging & Releases: Semantic versioning applied. Initial stable release tagged as `v1.0.0`.
