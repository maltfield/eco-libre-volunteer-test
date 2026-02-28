![docs_pages_workflow](https://github.com/maltfield/eco-libre-volunteer-test/actions/workflows/docs_pages_workflow.yml/badge.svg?branch=main)

# Michael Alfield’s Eco-Libre Volunteer Test

This repo hold the GitHub Pages documentation site, which is the deliverable for Michael Altfield's Volunteer Test of the Eco-Libre project

The GitHub Pages site is built with Sphinx using the Read The Docs theme. For more info on how this works, see:

<p align="center">
  <a href="https://tech.michaelaltfield.net/2020/07/18/sphinx-rtd-github-pages-1/"><img src="docs/_static/sphinx-rtd-github-pages-1_featuredImage1.jpg?raw=true" alt="Continuous Documentation with Read the Docs on GitHub Pages using GitHub Actions"/></a>
</p>

 * https://tech.michaelaltfield.net/2020/07/18/sphinx-rtd-github-pages-1/

# How to use this repo

New Eco-Libre volunteers are encourage to do their Volunteer Test by forking this repo. To do so:

1. Fork this repo (click the "Fork" button at the top of this page)
1. On your forked repo, go to "Settings" tab. Then click Actions -> General -> Workflow permissions
1. Change "Read repository contents and packages permissions" to "Read and write permissions"
2. On your forked repo, in the "Settings" tab. Under "Pages". Under "Branch". Choose 'gh-pages' then '/(root)' then click 'Save'
1. Make a small change to [docs/index.rst](/docs/index.rst)
1. `git commit` and `git push` something to trigger your site to be built

Every time you push to github.com on your 'main' branch, GitHub will automatically spin up a container in their cloud to update your documentation.

After you begin to edit the contents of the site, you'll probably also want to customize  the following files:

1. [docs/conf.py](/docs/conf.py)
1. Other `.rst` files in [docs/](/docs) as needed

For more details on how this works, see [Continuous Documentation: Hosting Read the Docs on GitHub Pages](https://tech.michaelaltfield.net/2020/07/18/sphinx-rtd-github-pages-1/)

# Local Iteration

As shown above, you can simply push your changes to GitHub to update your sphinx documentation website.

However, you can also build the site locally on your computer for faster iteration.

## Linux

To build the site on Debian Linux, first download some dependencies

```
sudo apt-get update
sudo apt-get -y install git firefox-esr python3-git python3-sphinx python3-sphinx-rtd-theme
```

Change into the `docs` directory of this repo and build the sphinx site with `make`

```
cd eco-libre-volunteer-test/docs/
make clean
make html
```

You can view the site (built into the `_build/html/` directory) using firefox

```
firefox-esr _build/html/index.html
```

# License

The contents of this repo are dual-licensed. All code is GPLv3 and all other content is CC BY-SA.
