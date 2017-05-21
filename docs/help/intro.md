---
layout: help
title: "Help: General Introduction"
permalink: /help/intro
---

# General Introduction

[Jekyll][Jekyll] is a _static site generator_. It takes templates,
content files and themes and outputs the finished site. The "static" part of the
name means that there is no database or serverside code involved.
A classic CMS like [WordPress][WordPress] has a content database and a server that
generates pages from templates in real time (albeit with some caching for
performance). Jekyll, on the other hand, generates all the pages in advance, in
a process called compilation,
before they are placed on the web server.

[Google App Engine][AppEngine] is a _platform as a service_ [PaaS][PaaS] where
developers can host their apps. While the main focus of App Engine is apps with
serverside logic, it also supports static files, meaning it is possible to host
a Jekyll generated site there.

The purpose of this repository is to provide boilerplate code to automate the
process of building a site with Jekyll and deploying it to Google App Engine.
This repository _is not_ a finished product you can use out of the box. It
simply provides a few sample files you can start from to implement automatic
build and deployment of your static site on [GitLab CI][GitLabCI].

[Jekyll]: https://jekyllrb.com/
[AppEngine]: https://cloud.google.com/appengine/
[WordPress]: https://wordpress.org/
[PaaS]: https://en.wikipedia.org/wiki/PaaS/
[GitLabCI]: https://about.gitlab.com/features/gitlab-ci-cd/
