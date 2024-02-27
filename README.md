# SoICT 2023.2 - Software Engineering Project

## Group member:

| Student ID | Fullname           |
| ---------- | ------------------ |
| 20215178   | Nguyen Thi Mai Anh |
| 20215205   | Pham Trung Hieu    |
| 20215220   | Vu Thuy Linh       |
| 20215238   | Ngo Minh Quy       |
| 20215243   | Nguyen Tien Than   |

## Introduction

_Updating..._

## For development team

This document outlines the workflow we follow for collaborating on this project. It provides guidelines on gitflow, project structure and other best practices to ensure smooth collaboration within the team.

### I. Project Structure

1. **Doc** folder contain document and material of project include description, instruction, diagrams, designs, etc...

2. **Source** folder contain source code of project. It has 2 sub directory are **`Server`** for containing backend source and **`Client`** containing UI/UX source (WEb frontend, mobile, desktop app, etc...)

### II. Git branches

1. **`main`:** This branch contains production-ready code. It should always reflect the latest stable release.

2. **`develop`:** This branch is the main integration branch where all feature branches are merged. It contains code under development and is relatively stable compared to feature branches.

3. **`feature branches`:** Each new feature should have its own branch branched off from `develop`. Once the feature is complete, it will be merged back into `develop`.

4. **`release branches`:** When preparing for a new release, a release branch is created from `develop`. It's used for final testing and bug fixes before merging into `main` and `develop`.

5. **`hotfix branches`:** If critical bugs are found in production, a hotfix branch is created from `main`. Once the hotfix is complete, it's merged into both `main` and `develop`.

### III. Workflow

1. Start a new feature:

   ```
   git checkout develop
   git pull origin develop
   git checkout -b feature/<my-new-feature>
   ```

2. Develop the feature on the feature branch. Make commits as necessary.

3. Once the feature is complete, ensure it's up to date with `develop`:

   ```
   git checkout develop
   git pull origin develop
   ```

4. Push the changes:

   ```
   git push origin develop
   ```

5. Create a pull request merge to develop branch and tech lead will review and decide whether to merge or not.

6. When it's time to release:

   ```
   git checkout -b release/vX.X.X
   ```

7. Test the release thoroughly. Make any necessary bug fixes directly on the release branch.

8. Once ready, merge the release branch into `main` and `develop`:

9. Tag the release:

   ```
   git tag -a vX.X.X -m "Version X.X.X"
   ```

10. Push the changes including tags:

    ```
    git push origin main
    git push origin develop
    git push --tags
    ```

11. For hotfixes, follow a similar process starting from step 7, but branch from `main` instead of `develop`.

**Note**: step 5 to 11 is for project manager/tech lead only so developer just have to devlope the features and create a pull request following wolkflow. Remember to **pull** code from `develop` before **push** new feature.

Following this flow will help us maintain a clean and organized codebase, enabling smooth collaboration and efficient release management.

### IV. Commit code convention:

```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

**Header**

- Type: Indicates the kind of change being made. Common types include feat (feature), fix (bug fix), docs (documentation), style (formatting, no code change), refactor (code change that neither fixes a bug nor adds a feature), test (adding missing tests), and others.

- Scope: (Optional) Describes the scope of the change, such as a module, component, or feature affected by the commit.

- Description: A brief summary of the changes made.

**Body**

- (Optional) Provides a more detailed description of the changes, including the motivation behind them and any relevant information.

**Footer**

- (Optional) Contains metadata or references related to the commit, such as issue tracker IDs or breaking changes.

_Example:_

```
feat(user): Add sign-up functionality

- Implemented sign-up form
- Added validation for email and password fields

Closes #123

```
