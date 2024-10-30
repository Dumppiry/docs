---
layout: project
title: Docs
description: Documentation site for projects of the Dumppi Ry
date: 2024-10-30
repo: https://github.com/Dumppiry/docs
technologies:
  - Markdown
  - Jekyll
  - HTML
---

Site for documenting all of the projects of Dumppi Ry. Site is automatically deployed on pushes to `main` branch. This project is pretty much the basic example from Github Pages docs. Some modifications has been made to page templates and the modified templates are found under `docs/_layouts/`.

## Development

Feel free to discuss about improvements to this documentation site at our Discord. You can either develop the site it self or just add/edit documentation pages of projects.

### Add/Edit/Delete project pages

If you only want to add/edit/delete project page, you can do so by modifying the Markdown files under `docs/_projects/`. Every file under this directory will be made in to a project page shown under /projects.

If you need to delete a project, just delete the corresponding Markdown file. To modify the page, edit the corresponding Markdown file as needed.

#### Add a project page

Copy the `docs/_projects/_project_template.md` and rename the created file correctly. Name of the file should match the name of the project. Remove the `_` from the start of the file name as it tells Jekyll to ignore the file. Files starting with underscore, will not be included in the build site.

After you have created the file, you can start writing the documentation using Markdown language. Documentation written here, should be general information about the project and how it works etc. More technical documentation about how to get started with local development etc. should be written in to the projects own `README.md`.

## NO SENSITIVE INFORMATION

This site is public and available to anyone to see. Do not include any sensitive information in these documentation pages. For documenting sensitive information, please contact the current webmaster of Dumppi Ry.
