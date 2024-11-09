---
layout: project
title: Dumppi-Website
description: Website of the Dumppi Ry
date: 2020-08-31
repo: https://github.com/Dumppiry/dumppi-website
technologies:
  - JavaScript
  - React
  - Gatsby
---

The official website of Dumppi Ry. This site is the main place to find information about Dumppi Ry and it also has important information for members like events and benefits.

## How it works?

Site is build with React and we use Gatsby for static site generation. Site is build using Github actions and deployed to Netlify from the action after successful build. During the build Gatsby fetches the content from our Sanity Studio.

### Sanity

We use Sanity CMS for managing content. You can find our Sanity Studio documentation [here](https://docs.dumppi.fi/projects/studio.html) and repository from [Github](https://github.com/dumppiry/studio). You only need to develop the studio if you wish to do changes to datastructures of our content and other stuff like that. For front end changes there is usually no need for changes to Studio.

#### Data structures

There is too many different Schemas to list here. If you need to see what kind of data is retrieved from Sanity, you can see the [Schemas](https://github.com/Dumppiry/studio/tree/main/schemas) directory under the Studio project. Also check out the Sanitys [documentation](https://www.sanity.io/docs/schema-types).

### Publish pipeline

When changes are wanted to the content, the content needs to be updated in the Sanity Studio. After the content is ready, it needs to be published by clicking the _Publish_ button in the bottom right corner of the Studio. Note that this will not make changes visible to the website alone. This only makes the data available. Next we need to rebuild the site and the build can be triggered with the _Deploy_ button in the Dashboard. After clicking the _Deploy_ button, the build-and-deploy action will run in Github. This will take anywhere from 2 to 7 minutes to finish and after it has successfully finished, the changes will be visible in the website.

> The build-and-deploy action will be triggered for every push against `main` branch in our Github or via the _Deploy_ button in our Sanity Studio.

## Development

For instructions how to get started with development, see the README of the [repository](https://github.com/dumppiry/dumppi-website).

## Deployment

The website is hosted in Netlify and there is automatic deployment pipeline set up. If something is broken or manual deployment is needed, please contact the current webmaster.
