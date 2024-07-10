# Git Workflow

## Environments:

- Test Site
- Stage Site
- Live Site

## Required Branches:

- `master`/`main`/`production`
- `develop`

## Branch Categories:

- `feature`: Manage your feature branches.
- `bugfix`: Manage your bugfix branches.
- `release`: Manage your release branches.
- `hotfix`: Manage your hotfix branches.

## Attention ⚠️

#### Until the deployment of the first phase, the following git process will be used:

## Process:

- **Feature Development:**
    - Developers create their branches following naming convension of specific branch category for example- `feature_xxx` branch from the `develop` branch.
    - After completing the work, create a pull request to the `develop` branch.
    - `A reviewer approves the pull request after resolving any issues and merges it applying the squash merging strategy.`
    - No sepate **test_deploy** will be maintained.


2. **Testing:**
    - Dev site deployment will be done from  the `develop` branch.
    - Each push to develop branch will trigger a CD pipeline
    to deploy code of the develop branch to dev site.
    - If there's any bugfix or feedback from QA, after resolving them,the pull request to `develop` branch needs to be reviewed again and the process will repeat.

3. **Deployment to Live Site:**
    - When the client requests deployment to the Live Site, create a new `release_xxx` branch from the `main` branch.
    - Merge the `feature_xxx` into the `release_xxx` branch, squashing commits.
    - Deploy the `release_xxx` branch to the Stage Site for UAT.
    - If needed, fix issues on the `feature_xxx` or `release_xxx` branches.
    - Once UAT is approved, merge `release_xxx` into `develop` and `master`, and deploy to the Live Site.

4. **Hotfix:**
    - For hotfixes, create a new branch from `master` and merge into both `master` and `develop`.

5. **Release Planning:**
    - Avoid including too many features in one release.
    - Plan for sprint-wise or batch-wise releases.


## Versioning Convention
<img src="media/versioning.png" alt="Workflow Image" width="300" height="200">



## Branch Naming Conventions:

- **Feature Branches** :  Use the prefix `feature/`. For instance, `feature/login-system`.
- **Bugfix Branches** : Use the `prefix bugfix/`. For example, `bugfix/header-styling`.
- **Hotfix Branches** : Use the prefix `hotfix/`. For instance, `hotfix/critical-security-issue`.
- **test Branches** :  Use the prefix `test/`. For example, `test/test-product-export`.
- **Release Branches** : prefix `release/`. For example, `release/v1.0.1`.



**Note:**
-
- Squash commits while merging into `develop`, `master`, and `release_xxx`.
- Delete the feature branch right after releasing. 

**Don't -**
-
-  create branch without following proper naming convention.


