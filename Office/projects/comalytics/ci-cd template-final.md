# GitLab CI/CD Configuration for Multi-Environment Deployment

This guide explains the GitLab CI/CD configurations in `.yml` files provided for deploying to multiple environments (`test`, `stage`, and `production`) using separate Git branches and specific runners for each environment.

Each file includes essential stages (`checkout`, `build`, `publish`, `deploy`, `stop_website`, and `start_website`), which are executed sequentially. We’ll cover the purpose of each block, focusing on customizing branches, tags, and dead code removal as per the requirements.


## `gitlab-ci-template.yml`

This file serves as a template for the GitLab CI/CD pipeline, orchestrating the workflow and including environment-specific configuration files. It controls the flow by defining global rules and includes settings for each deployment branch.

### File Structure

```yaml
workflow:
  name: "Pipeline started at $CI_COMMIT_BRANCH branch"
  rules:
    - if: $CI_COMMIT_BRANCH == "clients/groceryexpress/develop" || $CI_COMMIT_BRANCH == "clients/groceryexpress/production" || $CI_COMMIT_BRANCH == "clients/groceryexpress/test"
      when: always
```

- **workflow**:
  - **name**: Sets the name of the pipeline dynamically based on the branch name, providing clarity on which branch the pipeline is associated with.
  - **rules**: Controls when the pipeline should run based on the branch. This rule specifies that the pipeline should execute for any of the defined branches (`develop`, `production`, or `test`), allowing environment-specific workflows.

### Include Section

```yaml
include:
  - local: gitlab-ci-live-deploy.yml
    rules:
      - if: $CI_COMMIT_REF_NAME == "clients/groceryexpress/develop"
  - local: gitlab-ci-test-deploy.yml
    rules:
      - if: $CI_COMMIT_REF_NAME == "clients/groceryexpress/test"
```

- **include**: References other configuration files based on branch-specific rules.
  - **local**: Specifies the path to the environment-specific `.yml` file (either `gitlab-ci-live-deploy.yml` for production/stage or `gitlab-ci-test-deploy.yml` for test).
  - **rules**: Determines which `.yml` file to include based on the branch name. If the branch is `develop`, it uses `gitlab-ci-live-deploy.yml`, and if the branch is `test`, it uses `gitlab-ci-test-deploy.yml`.

### Variables Section

```yaml
variables:
  AUTHOR: $CI_COMMIT_AUTHOR
```

- **variables**: Defines a global variable for this pipeline template.
  - **AUTHOR**: Stores the name of the commit author, using the environment variable `$CI_COMMIT_AUTHOR`. This variable is used to personalize deployment logs and can provide traceability.

### Default Job Definition

```yaml
default_job:
  stage: .pre
  script:
    - echo "Deployment started by '$AUTHOR'"
  rules:
    - if: $CI_COMMIT_BRANCH == "clients/groceryexpress/develop" || $CI_COMMIT_BRANCH == "clients/groceryexpress/production" || $CI_COMMIT_BRANCH == "clients/groceryexpress/test"
      when: always
  tags:
    - b2b-test-server
```

- **default_job**: A preliminary step to execute before other stages. It includes:
  - **stage**: `.pre` is a special stage that initializes the pipeline with setup tasks.
  - **script**: Outputs a message indicating who initiated the deployment, adding clarity to the pipeline logs.
  - **rules**: Limits this job to run only on the defined branches (`develop`, `production`, and `test`) to ensure it only initiates in valid contexts.
  - **tags**: Assigns the `b2b-test-server` tag to this job. This allows it to be run on a designated runner compatible with the `b2b-test-server` tag, ensuring appropriate environment usage.

---

### why this file is important?

The `gitlab-ci-template.yml` file provides centralized control over the pipeline flow, defining the branch-specific deployment files to include. By setting global rules and initializing variables, this template simplifies and organizes multi-environment deployment, enabling tailored workflows for `develop`, `production`, and `test` branches. The `default_job` provides an initial log entry that enhances pipeline traceability and debugging.


---

## 1. `gitlab-ci-live-deploy.yml`

This file handles the deployment to the **production** environment from the `production` branch. The `production_runner_tag` is used to execute jobs on the appropriate runner.

```yaml
# List of stages for jobs, and their order of execution
stages:
  - checkout
  - stop_website
  - build
  - publish
  - deploy
  - start_website
```

### Explanation
- **stages**: Defines the sequential execution order of pipeline jobs. Each environment configuration will follow this set order, ensuring the site is stopped, updated, and restarted in a controlled manner.

### Variables

```yaml
variables:
  PLUGINS_DIR_LIVE : "C:\\Users\\nopsupport\\Desktop\\gitlab-ci-cd\\artifacts\\Plugins"
  DEPLOY_DIR_SITE1_LIVE: "C:\\HostingSpaces\\JSG001\\groceryexpress.co.za\\wwwroot\\Plugins"
  DEPLOY_DIR_SITE2_LIVE: "C:\\HostingSpaces\\JSG002\\foodgistics.co.za\\wwwroot\\Plugins"
  ...
  BRANCH_LIVE: "clients/groceryexpress/production"
```

- **variables**: Define paths and settings unique to the production environment. The `BRANCH_LIVE` variable identifies the branch used for production deployment.

### Job: `checkout_live`

```yaml
checkout_live:
  stage: checkout
  tags:
    - production_runner_tag
  script:
    - git config --system core.longpaths true
    - git config --global advice.nameTooLong false
    - git config --global safe.directory '*'
    - git checkout $BRANCH_LIVE
    - git pull
  only:
    - clients/groceryexpress/production
```

- **checkout_live**: Checks out the latest code from the `production` branch. Ensures `production_runner_tag` is specified to use the correct runner, and Git configurations avoid errors in directory paths and permissions.

### Job: `build_live`

```yaml
build_live:
  stage: build
  tags:
    - production_runner_tag
  script:
    - cd $SCRIPT_DIR_LIVE
    - powershell -File build_project.ps1
  only:
    - clients/groceryexpress/production
  cache:
    key: build-cache
    paths:
      - $CACHE_DIR_LIVE
```

- **build_live**: Runs the build script, `build_project.ps1`, which compiles and prepares the code. It includes caching for build artifacts to optimize performance.

### Job: `publish_live`

```yaml
publish_live:
  stage: publish
  tags:
    - production_runner_tag
  environment: production
  script:
    - cd $SCRIPT_DIR_LIVE
    - powershell -File publish_project.ps1
  only:
    - clients/groceryexpress/production
  cache:
    key: build-cache
    paths:
      - $CACHE_DIR_LIVE
```

- **publish_live**: Publishes artifacts to the environment. Ensures production files are staged, cached, and prepared for deployment.

### Job: `stop-website_live`

```yaml
stop-website_live:
  stage: stop_website
  tags:
    - production_runner_tag
  script:
    - Stop-Website $LIVE_SITE1_NAME
    - Stop-WebAppPool -Name $LIVE_SITE1_NAME 
  only:
    - clients/groceryexpress/production
```

- **stop-website_live**: Stops the production website before deployment, ensuring no active connections interfere with deployment.

### Job: `deploy_live`

```yaml
deploy_live:
  stage: deploy
  tags:
    - production_runner_tag
  script:
    - xcopy $PLUGINS_DIR_LIVE $DEPLOY_DIR_SITE1_LIVE /y /c /h /e /r /s
  only:
    - clients/groceryexpress/production
  retry: 2
```

- **deploy_live**: Copies files from the local build directory to the deployment directory, retrying up to twice if necessary.

### Job: `start-website_live`

```yaml
start-website_live:
  stage: start_website
  tags:
    - production_runner_tag
  script:
    - Start-Website $LIVE_SITE1_NAME
  only:
    - clients/groceryexpress/production
  when: always
```

- **start-website_live**: Restarts the website to complete the deployment process.

---

## 2. `gitlab-ci-stage-deploy.yml`

This file uses the `develop` branch and the `stage_runner_tag` for **stage deployment**. The structure mirrors the `gitlab-ci-live-deploy.yml` file but customizes paths, branch, and runner tag.

---

## 3. `gitlab-ci-test-deploy.yml`

Configured similarly to `gitlab-ci-live-deploy.yml`, but it:
- Uses the `test` branch and `test_runner_tag`.
- Deploys to **test** environment sites specified in the variables section.

The files are structured similarly, with appropriate runner tags, paths, and branches tailored for **test** deployment.

---
## All Scripts of CI-CD 

### .gitlab-ci.yml file 
``` yml
workflow:
  name: "Pipeline started at $CI_COMMIT_BRANCH branch"
  rules:
    - if: $CI_COMMIT_BRANCH == "develop" || $CI_COMMIT_BRANCH == "production" || $CI_COMMIT_BRANCH == "test"
      when: always

include:
  - local: gitlab-ci-live-deploy.yml
    rules:
      - if: $CI_COMMIT_REF_NAME == "develop"
  - local: gitlab-ci-test-deploy.yml
    rules:
      - if: $CI_COMMIT_REF_NAME == "test"

variables:
  AUTHOR: $CI_COMMIT_AUTHOR

default_job:
  stage: .pre
  script:
    - echo "Deployment started by '$AUTHOR'"
  rules:
    - if: $CI_COMMIT_BRANCH == "develop" || $CI_COMMIT_BRANCH == "production" || $CI_COMMIT_BRANCH == "test"
      when: always
  tags:
    - template_runner_tag

```

### gitlab-ci-test-deploy.yml
``` yml
# List of stages for jobs, and their order of execution
stages:
  - checkout
  - stop_website
  - build
  - publish
  - deploy
  - start_website

variables:
  PLUGINS_DIR_TEST : "/path/to/artifacts/Plugins"
  DEPLOY_DIR_SITE_TEST: "/path/to/site/wwwroot/Plugins"
  ROOT_DIR_TEST: "/path/to/root"
  SCRIPT_DIR_TEST: "/path/to/scripts"
  CACHE_DIR_TEST: "/path/to/build/cache"
  BACKUP_DIR_SITE_TEST: "/path/to/backup/site"
  TEST_SITE_NAME: "test.site.com"
  BRANCH_TEST: "test"

checkout_test:
  stage: checkout
  tags:
    - test_runner_tag
  script:
    - git config --system core.longpaths true
    - git config --global advice.nameTooLong false
    - git config --global safe.directory '*'
    - git checkout $BRANCH_TEST
    - git pull
  only:
    - test

build_test:
  stage: build
  tags:
    - test_runner_tag
  script:
    - dotnet clean --configuration Release
    - dotnet restore
    - dotnet build --no-restore -c Release
  only:
    - test
  cache:
    key: build-cache
    paths:
      - $CACHE_DIR_TEST

publish_test:
  stage: publish
  tags:
    - test_runner_tag
  environment: test
  script:
    - dotnet restore
    - dotnet publish "Nop.Web.csproj" -c Release -o $PUBLISH_DIR /p:CopyRefAssembliesToPublishDirectory=true
  only:
    - test
  cache:
    key: build-cache
    paths:
      - $CACHE_DIR_TEST

stop-website_test:
  stage: stop_website
  tags:
    - test_runner_tag
  script:
    - Stop-Website $TEST_SITE_NAME
    - Stop-WebAppPool -Name $TEST_SITE_NAME
  only:
    - test

deploy_test:
  stage: deploy
  tags:
    - test_runner_tag
  script:
    - xcopy $DEPLOY_DIR_SITE_TEST $BACKUP_DIR_SITE_TEST /y /c /h /e /r /s
    - xcopy $PLUGINS_DIR_TEST $DEPLOY_DIR_SITE_TEST /y /c /h /e /r /s
  only:
    - test
  retry: 2  

start-website_test:
  stage: start_website
  tags:
    - test_runner_tag
  script:
    - Start-WebAppPool -Name $TEST_SITE_NAME
    - Start-Website $TEST_SITE_NAME
  only:
    - test
  when: always


```

### gitlab-ci-live-deploy.yml file 
``` yml
# List of stages for jobs, and their order of execution
stages:
  - checkout
  - stop_website
  - build
  - publish
  - deploy
  - start_website

variables:
  PLUGINS_DIR_LIVE : "/path/to/artifacts/Plugins"
  DEPLOY_DIR_SITE_LIVE: "/path/to/site/wwwroot/Plugins"
  ROOT_DIR_LIVE: "/path/to/root"
  SCRIPT_DIR_LIVE: "/path/to/scripts"
  CACHE_DIR_LIVE: "/path/to/build/cache"
  BACKUP_DIR_SITE_LIVE: "/path/to/backup/site"
  LIVE_SITE_NAME: "live.site.com"
  BRANCH_LIVE: "develop"

checkout_live:
  stage: checkout
  tags:
    - production_runner_tag
  script:
    - git config --system core.longpaths true
    - git config --global advice.nameTooLong false
    - git config --global safe.directory '*'
    - git checkout $BRANCH_LIVE
    - git pull
  only:
    - develop

build_live:
  stage: build
  tags:
    - production_runner_tag
  script:
    - dotnet clean --configuration Release
    - dotnet restore
    - dotnet build --no-restore -c Release
  only:
    - develop
  cache:
    key: build-cache
    paths:
      - $CACHE_DIR_LIVE

publish_live:
  stage: publish
  tags:
    - production_runner_tag
  environment: production
  script:
    - dotnet restore
    - dotnet publish "Nop.Web.csproj" -c Release -o $PUBLISH_DIR /p:CopyRefAssembliesToPublishDirectory=true
  only:
    - develop
  cache:
    key: build-cache
    paths:
      - $CACHE_DIR_LIVE

stop-website_live:
  stage: stop_website
  tags:
    - production_runner_tag
  script:
    - Stop-Website $LIVE_SITE_NAME
    - Stop-WebAppPool -Name $LIVE_SITE_NAME
  only:
    - develop

deploy_live:
  stage: deploy
  tags:
    - production_runner_tag
  script:
    - xcopy $DEPLOY_DIR_SITE_LIVE $BACKUP_DIR_SITE_LIVE /y /c /h /e /r /s
    - xcopy $PLUGINS_DIR_LIVE $DEPLOY_DIR_SITE_LIVE /y /c /h /e /r /s
  only:
    - develop
  retry: 2   

start-website_live:
  stage: start_website
  tags:
    - production_runner_tag
  script:
    - Start-WebAppPool -Name $LIVE_SITE_NAME
    - Start-Website $LIVE_SITE_NAME
  only:
    - develop
  when: always


```


### gitlab-ci-stage-deploy.yml file 
``` yml
# List of stages for jobs, and their order of execution
stages:
  - checkout
  - stop_website
  - build
  - publish
  - deploy
  - start_website

variables:
  PLUGINS_DIR_STAGE: "/path/to/artifacts/Plugins"
  DEPLOY_DIR_SITE_STAGE: "/path/to/site/wwwroot/Plugins"
  ROOT_DIR_STAGE: "/path/to/root"
  SCRIPT_DIR_STAGE: "/path/to/scripts"
  CACHE_DIR_STAGE: "/path/to/build/cache"
  BACKUP_DIR_SITE_STAGE: "/path/to/backup/site"
  STAGE_SITE_NAME: "stage.site.com"
  BRANCH_STAGE: "stage"

checkout_stage:
  stage: checkout
  tags:
    - stage_runner_tag
  script:
    - git config --system core.longpaths true
    - git config --global advice.nameTooLong false
    - git config --global safe.directory '*'
    - git checkout $BRANCH_STAGE
    - git pull
  only:
    - stage

build_stage:
  stage: build
  tags:
    - stage_runner_tag
  script:
    - dotnet clean --configuration Release
    - dotnet restore
    - dotnet build --no-restore -c Release
  only:
    - stage
  cache:
    key: build-cache
    paths:
      - $CACHE_DIR_STAGE

publish_stage:
  stage: publish
  tags:
    - stage_runner_tag
  environment: stage
  script:
    - dotnet restore
    - dotnet publish "Nop.Web.csproj" -c Release -o $PUBLISH_DIR /p:CopyRefAssembliesToPublishDirectory=true
  only:
    - stage
  cache:
    key: build-cache
    paths:
      - $CACHE_DIR_STAGE

stop-website_stage:
  stage: stop_website
  tags:
    - stage_runner_tag
  script:
    - Stop-Website $STAGE_SITE_NAME
    - Stop-WebAppPool -Name $STAGE_SITE_NAME
  only:
    - stage

deploy_stage:
  stage: deploy
  tags:
    - stage_runner_tag
  script:
    - xcopy $DEPLOY_DIR_SITE_STAGE $BACKUP_DIR_SITE_STAGE /y /c /h /e /r /s
    - xcopy $PLUGINS_DIR_STAGE $DEPLOY_DIR_SITE_STAGE /y /c /h /e /r /s
  only:
    - stage
  retry: 2   

start-website_stage:
  stage: start_website
  tags:
    - stage_runner_tag
  script:
    - Start-WebAppPool -Name $STAGE_SITE_NAME
    - Start-Website $STAGE_SITE_NAME
  only:
    - stage
  when: always


```
