---
layout: project
title: Dumppi TV
description: Info tv photo slider for our office
date: 2024-10-07
repo: https://github.com/Dumppiry/dumppi-tv
technologies:
  - TypeScript
  - React
  - Tailwind
  - Sanity
---

This project is a minimalist photo slider web site that can be accessed with
the raspberry pi at our office. Content is managed via Sanity. Project is written with TypeScript, React and Vite. For styling it uses Tailwind.

## How it works?

Dumppi TV is a website build with React. It fetches all available images from
the sanity on page load and after the initial load, in 5 minute intervals.
There is no need for any tokens as the dataset `dumppi-sides` does not
contain any private data and is available with `public` visibility. This allows the content to be updated without any build steps or reloads of the browser.

### Sanity

Content is managed in Sanity. Document is found under `dumppi-sides` workspace in the pinned document named "Photo Slider" and the data is saved to `dumppi-sides` dataset.

#### Document (photoSlider)

Project uses one type of document in sanity and it is `photoSlider`. The photoSlider has the following fields in addition to Sanitys default fields:

|     Name      |      Data type      |                                       Description                                       |
| :-----------: | :-----------------: | :-------------------------------------------------------------------------------------: |
| autoPlaySpeed |       Integer       |               Time in seconds for how long single slide should be shown.                |
|    photos     | Array[Sanity Image] | An array of Sanitys [Image](https://www.sanity.io/docs/image-type) objects to be shown. |

## Development

For development details, checkout the README of the [project](https://github.com/dumppiry/dumppi-tv).
