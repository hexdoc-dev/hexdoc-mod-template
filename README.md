# hexdoc-hexcasting-template
Copier template for adding a hexdoc plugin to a Hex Casting addon.

## Setting up a new plugin for an existing mod

### Copying the template

* Install Copier: `pip install pipx && pipx install copier`
* In your repo, copy the template: `copier copy gh:hexdoc-dev/hexdoc-hexcasting-template . --overwrite`
* Use your editor's Git diff tool to review any files overwritten by the template (eg. `.gitignore`).
  * All of the files in the template are there for good reasons, but you might want to merge some of your existing content into them.
* Commit the plugin.
* Follow the setup steps in `doc/README.md`, then try running the commands. Fix any errors you find.

### Setting up Pages

* Run these commands to create an empty branch for GitHub Pages:
  ```sh
  git switch --orphan gh-pages
  git commit --allow-empty "Initial commit"
  git push -u origin gh-pages
  ```
* Go to your GitHub repo settings > Pages > Build and deployment.
* Set these values:
  * Source: `Deploy from a branch`
  * Branch: `gh-pages`
  * Folder: `/docs`
* Save your changes.
* Push the commits that added your plugin, monitor the Actions tab, and cross your fingers!

### Setting up a PyPI account (optional, but highly recommended)

PyPI is the main Python package repository (like Node's NPM). hexdoc plugins are set up by default to (mostly) automatically publish versions to PyPI when you release a new version of your mod, so that other hexdoc plugins can use content from them. [hexdoc-hexcasting](https://pypi.org/project/hexdoc-hexcasting/) and [hexdoc-minecraft](https://pypi.org/project/hexdoc-minecraft/) are two examples of hexdoc plugins that your web book already depends on.

* [Create a PyPI account](https://pypi.org/account/register/).
* Follow [these steps](https://docs.pypi.org/trusted-publishers/creating-a-project-through-oidc/) to configure a pending publisher for your plugin.
  * PyPI Project Name: The `name` value from your pyproject.toml (ie. `hexdoc-yourmodid`).
  * Workflow name: `build_docs.yml`
  * Environment name: `pypi`
* Go to your GitHub repo settings > Environments, and create an environment called `pypi`.
* Try releasing the plugin to PyPI (push a tag, push a commit starting with `[Release]`, or manually run the hexdoc workflow from the Actions tab).

The default version number for your plugin is `1.0.dev0`. You can bump this by editing `doc/src/hexdoc_yourmodid/__version__.py`, or by manually running the hexdoc workflow and typing `major`, `minor`, `patch`, `dev`, and/or `release` in the "increment version" field.

## Migrating from Cookiecutter

* Install Copier: `pip install pipx && pipx install copier`
* In your repo, copy the initial version of the template: `copier copy gh:hexdoc-dev/hexdoc-hexcasting-template . --vcs-ref v0.0.1 --overwrite`
* Use your editor's Git diff tool to reapply any changes you've made since baking the Cookiecutter template, then commit your changes.
* Update to the latest template: `copier update --skip-answered`
* Again, use the diff to fix any issues and/or merge conflicts caused by the update, then commit.
  * NOTE: Since the Cookiecutter template was last updated, the default props file was renamed from `properties.toml` to `hexdoc.toml`. Copier doesn't seem to pick up on this, so make sure to carefully compare these files.
* Follow the setup instructions in the README, then run `hexdoc serve` and fix any issues that show up.
