# Releasing

A `pypdf` release contains the following artifacts:

* A new [release on PyPI](https://pypi.org/project/pypdf/)
* A [release commit](https://github.com/py-pdf/pypdf/commit/91391b18bb8ec9e6e561e2795d988e8634a01a50)
    * Containing a changelog update
    * A new [git tag](https://github.com/py-pdf/pypdf/tags)
        * A [Github release](https://github.com/py-pdf/pypdf/releases/tag/3.15.0)

## Who does it?

`pypdf` should typically only be released by one of the core maintainers / the
core maintainer. At the moment, this is Martin Thoma.

Any owner of the py-pdf organization also has the technical permissions to
release.

## How is it done?

The release contains the following steps:

1. Update the CHANGELOG.md and the _version.py via `python make_release.py`.
   This also prepares the release commit message.
2. Create a release commit: `git commit -eF RELEASE_COMMIT_MSG.md`.
3. Tag that commit: `git tag -s {{version}} -eF RELEASE_TAG_MSG.md`.
4. Push both: `git push && git push --tags`.
5. CI now builds a source and a wheels package which it pushes to PyPI. It also
   creates a GitHub release.

![](../_static/releasing.drawio.png)

### The Release Tag

* Use the release version as the tag name. No need for a leading "v".
* Use the changelog entry as the body.


## When are releases done?

There is no need to wait for anything. If the CI is green (all tests succeeded),
we can release.

I (Martin Thoma) typically only release once a week, because it costs a little
bit of time and I don't want to spam users with too many releases.
