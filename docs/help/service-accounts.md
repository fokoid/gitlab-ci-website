---
layout: help
title: "Guide: App Engine Service Accounts"
permalink: /help/service-accounts
---

For the GitLab CI process to deploy your website to the Google App Engine
application automatically, it needs to be properly authorized. When pushing to
App Engine manually, a Google account with the appropriate permissions for the
app can be used. For deployment by an automated process, a _service account_
should be used.

## Prerequesites

* projects on App Engine for [production and staging sites][Guide_GAEProjects]

## Creating a service account

The service account can be created in the [Google Cloud Console][CloudConsole]
with the following steps.

1. Select your staging app.
2. Enable the App Engine Admin API
    1. Go to the _API Manager_
    2. Click _Enable API_
    3. Select _App Engine Admin API_
3. Create the service account
    1. Go to _IAM & Admin_ > _Service Accounts_
    2. Click _Create Service Account_
    3. Choose a name for the service account, e.g. _gitlab-deploy_
    4. Select the following roles:
        * `App Engine Admin`
        * `Storage Object Admin`
    5. Enable `Furnish a new private key` and select `JSON`
4. Select the production app and repeat steps 2 and 3

This will result in a JSON file being downloaded containing a private key for
the newly created service account. This key will enable access to the
permissions selected previously so treat it with appropriate care.

## Providing credentials to GitLab CI

The service key created above must be provided to GitLab CI so the build script
can obtain appropriate authorization. We should not place this key in the
repository for security reasons. We will in fact store it as a GitLab _secret
variable_.

The content of the key file for the staging app file should be stored in the
secret variable `STAGING_KEY`, and for the production app it should be stored in
`PRODUCTION_KEY`.

Note that there are security implications of storing these keys in the GitLab CI
system, for example they will be stored in the build log if you dump
environment variables with `env`.

For details of configuring Gitlab secret variables, see the relevant
[documentation][GitLabCI_SecretVariables].

[CloudConsole]: https://console.cloud.google.com/
[GitLabCI_SecretVariables]: https://docs.gitlab.com/ee/ci/variables/#secret-variables
[Guide_GAEProjects]: {{site.github.url}}/help/appengine-projects
