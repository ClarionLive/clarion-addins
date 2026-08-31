# ClarionLive Addins

Publisher list for **ClarionLive** in the [Clarion Addin Registry](https://github.com/msarson/clarion-addin-registry).

[`addins.json`](./addins.json) is the file the registry reads. AddinFinder resolves it from the
`publishers` entry in the registry's `registry.json`, so releasing a new version is a change here
(or, for setup addins, nothing at all) rather than a pull request against the registry.

## What we publish

| Addin | Install id | Repository | Distribution |
|-------|-----------|------------|--------------|
| CA Debugger | `ClarionDebugger` | [ClarionLive/CA-Debugger](https://github.com/ClarionLive/CA-Debugger) | Windows setup installer |

It ships as a setup installer, so it is listed under `setupAddins` rather than `addins`. Those
entries carry no `version` and no download URLs: AddinFinder resolves the latest GitHub release of
`githubRepo` directly, and **the release tag is the version**.

> Clarion Assistant will be added here once its own version reconciliation ships. Adding an addin to
> this file needs no change to the registry and nobody's approval — that is what being a listed
> publisher means.

## Releasing

For a setup addin the release *is* the publication:

1. Bump the project version **and** `<Identity version>` in the `.addin` manifest - they must agree.
2. Update the repo's `CHANGELOG.md`.
3. Tag and publish the GitHub release with the installer attached.

There is no step 4. Nothing in this file needs editing.

> `<Identity version>` must equal the release tag with any leading `v` removed. Tag `v1.2.1`, ship
> `<Identity version="1.2.1"/>`. A manifest that says anything else leaves the addin reading
> *Update available* permanently, because re-running the installer cannot change what the manifest
> says. `1.2` and `1.2.0` count as equal; nothing else does.

> `id` must be exactly the folder name the installer creates under `accessory\addins`. For
> CA Debugger that is `ClarionDebugger`, which is **not** the repository name.

## Terms

Listed publishers agree to the registry's [PUBLISHERS.md](https://github.com/msarson/clarion-addin-registry/blob/master/PUBLISHERS.md).
Issues with our addins belong on their own repositories, not on the registry.
