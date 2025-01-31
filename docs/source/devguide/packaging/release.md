# Release Checklist

## Pre-Release

- Update [translation] `po` files from [Launchpad] account.
- Changelog is updated with relevant commits and release date is added.
- Tag release in git and push upstream e.g.

      git tag -a deluge-2.0.0 -m "Deluge 2.0.0 Release"

## Release

- Create source and wheel distributions:

      python setup.py sdist bdist_wheel

- Upload to PyPi (currently only accepts `tar.gz`):

      twine upload dist/deluge-2.0.0.tar.gz dist/deluge-2.0.0-py3-none-any.whl

- Create packages (Ubuntu, Windows, OSX).
- Calculate `sha256sum` for each file e.g.

      cd dist; sha256sum deluge-2.0.0.tar.xz > deluge-2.0.0.tar.xz.sha256

- Upload source tarballs and packages to `download.deluge-torrent.org`.
  - Ensure file permissions are global readable: `0644`
  - Sub-directories correspond to _major.minor_ version e.g. all `2.0.x` patch
    releases are stored in `source/2.0`.
- Update latest release version in `version` files at `download.deluge-torrent.org`.

## Post-Release

- Update with version, hashes and release notes:
  - Publish docs on [ReadTheDocs].
  - ReleaseNotes (Create new version page and add link to this page)
  - Forum announcement
  - IRC welcome message
  - Website homepage version `/var/www/deluge-torrent.org/htdocs/index.php`
  - [Wikipedia]
- Close Trac milestone and add new milestone version for future tickets.
- Ensure all stable branch commits are also applied to development branch.

[readthedocs]: https://deluge.readthedocs.io
[wikipedia]: http://en.wikipedia.org/wiki/Deluge_%28software%29
[launchpad]: https://translations.launchpad.net/deluge
[translation]: ../contributing/translations.md
