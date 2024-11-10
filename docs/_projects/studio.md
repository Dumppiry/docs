---
layout: project
title: Studio
description: Sanity Studio content management system for us.
date: 2024-10-30
repo: https://github.com/Dumppiry/studio
technologies:
  - JavaScript
  - Sanity
---

Sanity Studio is our content management system. It is originally build for our websites content but later expanded to manage all contents of our projects. Sanity CMS is very customizable software which allows us to create a content management system for our specific needs.

## Studio

Studio is the web UI for managing the content. It is build with JavaScript(or TypeScript). For extensive documentation, check out Sanitys own [documentation](https://www.sanity.io/docs). Usually the Studio needs development only when building new stuff or deprecating old things.

We have build a custom widget for the dashboard that is found in the [plugins/sanity-github-action-widget](https://github.com/Dumppiry/studio/tree/main/plugins/sanity-github-actions-widget). It is used to trigger github actions and to manage access tokens.

## Development

Instructions on how to get local development environment up can be found in the repositorys README.

It is important to keep in mind that even though you spin up local web ui for the Studio, the data is still same data that is used for production. This should be change soon so that we don't use production data for development.

## Deployment

Studio is deployed automatically to Netlify via Github action which triggers on pushes against `main` branch.
