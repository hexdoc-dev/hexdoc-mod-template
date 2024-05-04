# hexdoc-mod-template

<a href="https://github.com/hexdoc-dev/hexdoc"><img src="https://img.shields.io/endpoint?url=https://hexxy.media/api/v0/badge/hexdoc" alt="hexdoc" style="max-width:100%;"></a>

Copier template for adding a [hexdoc](https://pypi.org/project/hexdoc) plugin to a standalone mod. 

## Setting up a new plugin for an existing mod

### Copying the template

* Install Python 3.11.
* Follow [these instructions](https://pypa.github.io/pipx/#install-pipx) to install pipx (like npx for Python).
* Install Copier: `pipx install copier`
* In the root of your mod's repo, copy the template: `copier copy gh:hexdoc-dev/hexdoc-mod-template . --overwrite`
* Use your editor's Git diff tool to review any files overwritten by the template (eg. `.gitignore`).
  * All of the files in the template are there for good reasons, but you might want to merge some of your existing content into them.
  * If you want to use the recommended VSCode settings, make sure `.vscode` is not in your `.gitignore`.
* Commit the plugin.
* Follow the setup steps in `doc/README.md` (or whatever folder you entered for `plugin_root`), then try running the commands. Fix any errors you find.
  * Make sure to double-check the file paths and pattern regex in `doc/hexdoc.toml`.

### Setting up GitHub Pages

Follow these steps to set up GitHub Pages: https://hexdoc.hexxy.media/docs/guides/deployment/github-pages

### Setting up a PyPI account (optional, but highly recommended)

PyPI is the main Python package repository (like Node's NPM). hexdoc plugins are set up by default to (mostly) automatically publish versions to PyPI when you release a new version of your mod.

* [Create a PyPI account](https://pypi.org/account/register/).
* Follow [these steps](https://docs.pypi.org/trusted-publishers/creating-a-project-through-oidc/) to configure a pending publisher for your plugin.
  * PyPI Project Name: The `name` value from your pyproject.toml (eg. `hexdoc-yourmodid`).
  * Workflow name: `build_docs.yml`
  * Environment name: `pypi`
* Go to your GitHub repo settings > Environments, and create an environment called `pypi`.
* Try releasing the plugin to PyPI (push a tag, push a commit starting with `[Release]`, or manually run the hexdoc workflow from the Actions tab).

The default version number for your plugin is `1.0.dev0`. You can bump this by editing `doc/src/hexdoc_yourmodid/__version__.py`, or by manually running the hexdoc workflow and typing `major`, `minor`, `patch`, `dev`, and/or `release` in the "increment version" field.

### Next steps

* Read through the files added by the template - make sure you know what you just added to your repo!
* If you use VSCode, consider installing the recommended extensions for auto-formatting, linting, and type checking.
* When you're confident that your book is set up properly and publishing is working, remove `.dev0` from your plugin version (`doc/src/hexdoc_yourmodid/__version__.py`).
* For more hexdoc examples, take a look at these projects:
  * [hexdoc](https://github.com/hexdoc-dev/hexdoc)
  * [hexdoc-hexcasting](https://github.com/object-Object/HexMod)
  * [hexdoc-hexgloop](https://github.com/SamsTheNerd/HexGloop)

## FAQ

### Why should I publish my plugin to PyPI?

The main reason is to allow other hexdoc plugins to use content from your mod. [hexdoc-minecraft](https://pypi.org/project/hexdoc-minecraft/) is a hexdoc plugin that your web book already depends on.
