# Project Git Flow

## Introduction

This document outlines the Git flow we follow for collaborating on this project. It provides guidelines on branching, merging, and other best practices to ensure smooth collaboration within the team.

## Branches

### Main Branches

1. **`main`:** This branch contains production-ready code. It should always reflect the latest stable release.

2. **`develop`:** This branch is the main integration branch where all feature branches are merged. It contains code under development and is relatively stable compared to feature branches.

### Supporting Branches

3. **`feature branches`:** Each new feature should have its own branch branched off from `develop`. Once the feature is complete, it will be merged back into `develop`.

4. **`release branches`:** When preparing for a new release, a release branch is created from `develop`. It's used for final testing and bug fixes before merging into `main` and `develop`.

5. **`hotfix branches`:** If critical bugs are found in production, a hotfix branch is created from `main`. Once the hotfix is complete, it's merged into both `main` and `develop`.

## Workflow

1. Start a new feature:

   ```
   git checkout develop
   git pull origin develop
   git checkout -b feature/my-new-feature
   ```

2. Develop the feature on the feature branch. Make commits as necessary.

3. Once the feature is complete, ensure it's up to date with `develop`:

   ```
   git checkout develop
   git pull origin develop
   git merge --no-ff feature/my-new-feature
   ```

4. Resolve any merge conflicts if there are any.

5. Test the merged code thoroughly.

6. Push the changes:

   ```
   git push origin develop
   ```

7. Delete the feature branch if it's no longer needed:

8. When it's time to release:

   ```
   git checkout -b release/vX.X.X
   ```

9. Test the release thoroughly. Make any necessary bug fixes directly on the release branch.

10. Once ready, merge the release branch into `main` and `develop`:

    ```
    git checkout main
    git merge --no-ff release/vX.X.X
    git checkout develop
    git merge --no-ff release/vX.X.X
    ```

11. Tag the release:

    ```
    git tag -a vX.X.X -m "Version X.X.X"
    ```

12. Push the changes including tags:

    ```
    git push origin main
    git push origin develop
    git push --tags
    ```

13. Delete the release branch:

    ```
    git branch -d release/vX.X.X
    ```

14. For hotfixes, follow a similar process starting from step 8, but branch from `main` instead of `develop`.

## Conclusion

Following this Git flow will help us maintain a clean and organized codebase, enabling smooth collaboration and efficient release management.
