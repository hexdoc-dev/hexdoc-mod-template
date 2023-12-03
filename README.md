# hexdoc-hexcasting-template
Copier template for adding a hexdoc plugin to a Hex Casting addon.

## Setting up a new plugin for an existing mod

### Copying the template

* Install Copier: `pip install pipx && pipx install copier`
* In your repo, copy the template: `copier copy gh:hexdoc-dev/hexdoc-hexcasting-template . --overwrite`
* Use your editor's Git diff tool to review any files overwritten by the template (eg. `.gitignore`).
  * All of the files in the template are there for good reasons, but you might want to merge some of your existing content into them.
  * Make sure `.vscode` is not in your `.gitignore`.
* Commit the plugin.
* Follow the setup steps in `doc/README.md`, then try running the commands. Fix any errors you find.
  * Make sure to double-check the file paths and pattern regex in `doc/hexdoc.toml`.

### Setting up Pages

* Run these commands to create an empty branch for GitHub Pages:
  ```sh
  git switch --orphan gh-pages
  git commit --allow-empty -m "Initial commit"
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

PyPI is the main Python package repository (like Node's NPM). hexdoc plugins are set up by default to (mostly) automatically publish versions to PyPI when you release a new version of your mod.

* [Create a PyPI account](https://pypi.org/account/register/).
* Follow [these steps](https://docs.pypi.org/trusted-publishers/creating-a-project-through-oidc/) to configure a pending publisher for your plugin.
  * PyPI Project Name: The `name` value from your pyproject.toml (ie. `hexdoc-yourmodid`).
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

* It allows other hexdoc plugins to use content from your mod ([hexdoc-hexcasting](https://pypi.org/project/hexdoc-hexcasting/) and [hexdoc-minecraft](https://pypi.org/project/hexdoc-minecraft/) are two examples of hexdoc plugins that your web book already depends on).
* Publishing to PyPI is **mandatory** if you want your mod to be supported by [HexBug](https://github.com/object-Object/HexBug), [hexdoc-lsp](https://github.com/hexdoc-dev/hexdoc-lsp), and/or [vscode-hex-casting](https://github.com/object-Object/vscode-hex-casting).
