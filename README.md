# GitLab CI for Websites

This repository contains boilerplate code for automatic build and deployment of
websites on GitLab CI. For now it targets websites built with Jekyll and
deployed to Google AppEngine.

## Usage

For usage with GitLab CI, simply copy `.gitlab-ci.yml` into your project. To
configure the script for your website you need only change the variables
declared at the top of the file and then configure your source and repository
accordingly. Read on for a quick summary, or see the [website][GitHubPages] for
full setup instructions.

For manual usage on your development machine, copy the `Makefile` and again,
configure it as with `.gitlab-ci.yml`. Note, however, that the makefile assumes
that you are already authenticated with a suitable Google account or service
account.

### Variables

Assuming you have not changed the default Jekyll config, you need to change only
the following variables:

* `APP_NAME`: the name of the Google AppEngine project for your website
* `APP_NAME_STAGING`: the name of the Google AppEngine staging project
* `VERSION`: is the version string for your app (choose as you see fit)

### Directory Structure

The default required directory structure is:

```
project
|   .gitlab-ci.yml
|   Makefile
|   ...
├── _site             (Jekyll output directory)
├── app               (AppEngine directory)
|     app.yaml        (config for production app)
|     app_staging.yml (config for staging app)
|     www             (copy of _site created by Makefile/GitLab CI script)
```

### Repository Config

In GitLab settings it will be necessary to define secret variables containing
the secret keys of the AppEngine service accounts authorized to deploy to the
appropriate AppEngine apps. These variables are

* `STAGING_KEY`
* `PRODUCTION_KEY`

## Design Goals

Later a more modular approach will be used, supporting multiple build systems,
deployment targets and CI platforms..

### Build Systems

* [X] [Jekyll][Jekyll]
* [ ] [Hakyll][Hakyll]
* [ ] [Hyde][Hyde]
* [ ] raw HTML/CSS

### Deployment Targets

* [X] Google AppEngine
* [ ] AWS
* [ ] SFTP

### CI Platforms

* [X] [GitLab CI][CI_GitLab]
* [ ] [Travis CI][CI_Travis]

[Jekyll]:       https://jekyllrb.com/
[Hakyll]:       https://jaspervdj.be/hakyll/
[Hyde]:         https://hyde.github.io/
[CI_GitLab]:    https://about.gitlab.com/features/gitlab-ci-cd/
[CI_Travis]:    https://travis-ci.org/
[GitHubPages]:  https://thornecc.github.io/gitlab-ci-website/
