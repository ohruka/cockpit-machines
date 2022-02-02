# cockpit-machines

This is the [Cockpit](https://cockpit-project.org/) user interface for virtual machines.

## Technologies

- [libvirt-dbus](https://libvirt.org/dbus.html) for enumerating machines, getting status
  update notifications, and operations such as start/stop/delete
- [virt-install](https://manpages.org/virt-install) and [virt-xml](https://manpages.org/virt-xml)
  for creating and modifying machine definitions; both part of the
  [virt-manager](https://virt-manager.org/) project

# Automated release

Releases are automated using [Cockpituous release](https://github.com/cockpit-project/cockpituous/tree/main/release)
which aims to fully automate project releases to GitHub, Fedora, Ubuntu, COPR, Docker
Hub, and other places. The intention is that the only manual step for releasing
a project is to create a signed tag for the version number.

The release steps are controlled by the
[cockpituous-release](./cockpituous-release) script.

Pushing the release tag triggers the [release.yml](.github/workflows/release.yml)
[GitHub action](https://github.com/features/actions) workflow. This uses the
secrets in the [release GitHub action environment](https://github.com/cockpit-project/cockpit-machines/settings/environments).

# Automated maintenance

It is important to keep your [NPM modules](./package.json) up to date, to keep
up with security updates and bug fixes. This is done with the
[npm-update bot script](https://github.com/cockpit-project/bots/blob/main/npm-update)
which is run weekly or upon [manual request](https://github.com/cockpit-project/cockpit-machines/actions) through the
[npm-update.yml](.github/workflows/npm-update.yml) [GitHub action](https://github.com/features/actions).

Similarly, translations are refreshed every Tuesday evening (or manually) through the
[weblate-sync-po.yml](.github/workflows/weblate-sync-po.yml) action.
Conversely, the PO template is uploaded to weblate every day through the
[weblate-sync-pot.yml](.github/workflows/weblate-sync-pot.yml) action.
