# hexdoc-hexcasting-template
Copier template for adding a hexdoc plugin to a Hex Casting addon.

## Migrating from Cookiecutter

* Install Copier: `pip install copier`
* In your repo, copy the initial version of the template: `copier copy gh:object-Object/hexdoc-hexcasting-template . --vcs-ref v0.0.1 --overwrite`
* Use your editor's Git diff tool to reapply any changes you've made since baking the Cookiecutter template, then commit your changes.
* Update to the latest template: `copier update --skip-answered`
* Again, use the diff to fix any issues and/or merge conflicts caused by the update, then commit.
  * NOTE: Since the Cookiecutter template was last updated, the default props file was renamed from `properties.toml` to `hexdoc.toml`. Copier doesn't seem to pick up on this, so make sure to carefully compare these files.
* Follow the setup instructions in the README, then run `hexdoc serve` and fix any issues that show up.
