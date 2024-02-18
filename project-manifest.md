
1. beancli
2. bean continuous gatsbyjs/maven:lib unpack -> compile -> package -> publish -> deploy -> promote -> destroy (or clean?)
3. bean update/version
4. gitops:
    1. git push
    2. GitHubApp push to GitHubAppHook
    3. GHAHook create ArgoCDWorkflow
    5. bean continuous unpack app-name --framework gatsbyjs
        1. also includes resolve-dependencies and code generation
        2. `semver` string needs to be validated and reconciled
    6. bean continuous compile app-name --framework gatsbyjs
    6. bean continuous package app-name --framework gatsbyjs
        1. If `+semver:pre` string is supplied 
            1. from from SNAPSHOT to UAT.1 for maven:lib
            4. from UAT.1 to UAT.2 for maven:lib 
        1.  +semver:major -> SNAPSHOT/UAT to RELEASE and bump major
        2.  +semver:minor -> SNAPSHOT/UAT to RELEASE and bump minor
        2.  +semver:patch -> SNAPSHOT/UAT to RELEASE and bump patch
        3.  If no semver supplied
            1. must be SNAPSHOT pre-release
    6. bean continuous publish app-name --framework gatsbyjs
    6. bean continuous deploy app-name --framework gatsbyjs to PREVIEW/DEV env
    6. bean continuous promote app-name --framework gatsbyjs
        1. from DEV to PRE-POD/STG env 
        2. from PRE-PROD/STG to PROD env

6. environments
    1. preview
    3. dev
    4. preprod
    5. stg
    6. prod w/wo canary

7. Concepts
    1. Cloud, Project, Team, BoundedContext, App
        1. Infra
            1. K8s cluster > k8s namespace
            2. AWS Account
            3. VPC
        2. Project, Team, BC, App
            1. Project: cluster config, team members, context map, apps
    3. a Project must belong to one and only one Cloud
    4. a Cloud may or may not belong to another Cloud
    5. a Project has BoundedContexts each of which has Apps and is owned by a Team
    6. a Team is managed by a Project
    7. the UserAccount for each Team Member is managed by the Cloud
    8. one cluster for each project one of which is BeanContinuous
    9. each k8s namespace is a BoundedContext

### Difference Between Staging and Pre-Production Environments
Staging environments and pre-production environments are often used interchangeably, but they have subtle differences. While staging environments closely resemble the production environment, they are primarily used for final user acceptance testing (UAT) before the software is deployed. On the other hand, pre-production environments focus on comprehensive testing and fine-tuning of the software, including performance testing, load testing, and stress testing.



