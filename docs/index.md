---
layout: default
title: GitLab CI for Websites
permalink: /
---

## What is this for?

This repository contains boilerplate code for automatic build and deployment of
websites on GitLab CI. For now it targets websites built with Jekyll and
deployed to Google App Engine.

For a quick introduction, see below. Some steps contain links to more detailed
instructions if you need them. You can also check out the project
[readme][README].

## Quickstart

### Assumptions

* you have an existing Jekyll based website
* the website source is held in a Git repository
* the repository is set up with a GitLab remote repo

### Setup

1. Create projects on App Engine for the staging and production versions of
   your website.
2. Copy `.gitlab-ci.yml` into the root of your project.
3. Configure `.gitlab-ci.yml`
    1. Set the `APP_NAME` and `APP_NAME_STAGING` variables to the names of the
       projects created above.
    2. Set the `VERSION` variable as desired.
4. Copy the `app` directory into the root of your project.
5. Configure the `app/app_*.yaml` files accordingly. (A guide covering this
   will be written when I have time.)
6. [Create an App Engine service account][Guide_ServiceAccount] for each project
   and store the private keys in GitLab secret variables called `STAGING_KEY`
   and `PRODUCTION_KEY`.

### Workflow

1. Make desired changes to website source.
2. Commit and push changes to GitLab.
3. Wait for automated build and deployment to staging to finish.
4. Check changes on staging site.
5. If more changes are necessary, return to step 1.
6. Deploy to production by manually running the `deploy_app` job in the GitLab
   CI interface.

## Guides

* [General Introduction][Guide_Intro]
* [Authorization: Google App Engine Service Accounts][Guide_ServiceAccount]

[README]:   https://github.com/thornecc/gitlab-ci-website/blob/master/README.md
[Guide_Intro]: {{site.github.url}}/help/intro
[Guide_ServiceAccount]: {{site.github.url}}/help/service-accounts
