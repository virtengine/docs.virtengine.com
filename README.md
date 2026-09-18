# docs.virtengine.com

Legacy Jekyll source for VirtEngine documentation.

> **Status: legacy — this repository does not serve https://docs.virtengine.com.**
> The live site is built from
> [`virtengine/pages` → `sites/docs.virtengine.com`](https://github.com/virtengine/pages/tree/main/sites/docs.virtengine.com)
> (Astro 5 + Starlight) and deployed by Cloudflare Pages. Verified 2026-09-18: the live
> homepage reports `<meta name="generator" content="Astro v5.18.2">` and
> `<meta name="generator" content="Starlight v0.36.3">`.
>
> Changes merged here do **not** appear on the website.

VirtEngine - Private opensource + Private enterprise documentation.

Current network launch documentation is published in
[`_overview/network-launch-schedule.md`](_overview/network-launch-schedule.md):
TestNet is planned for January 2027 and MainNet for March 2027 after a separate
validation and production approval gate.

## Reporting a documentation defect

Issues are disabled on this repository, so there is no tracker here. File documentation
defects against the repository that owns the page:

- Content on the live site (<https://docs.virtengine.com>) → open an issue on
  [`virtengine/pages`](https://github.com/virtengine/pages/issues) (issues enabled).
- Defects specific to this legacy Jekyll source → open an issue on
  [`virtengine/virtengine`](https://github.com/virtengine/virtengine/issues) (issues enabled).

## Ruby

The Ruby version is pinned in [`.ruby-version`](.ruby-version) (currently `3.2.2`). Read that
file rather than trusting a version quoted in prose. The gem set is pinned in
[`Gemfile`](Gemfile): `jekyll ~> 4.0` plus `rexml`.

### Fork and clone the docs

```
git clone https://github.com/<your_github_id>/docs.virtengine.com

cd docs.virtengine.com

bundle install
```

<!-- UNVERIFIED: the `bundle install`, `jekyll clean`, `jekyll build` and `jekyll serve`
     commands in this README were not executed during the 2026-09-18 audit — Ruby, Bundler
     and Jekyll are not installed in the auditing environment. -->

### Edit & Test

Register a new collection in [`_config.yml`](_config.yml) for it to appear in the left
navbar: the navbar is generated from `site.collections` sorted by `order` in
[`_includes/primary-nav.html`](_includes/primary-nav.html).

```
jekyll clean

jekyll build

jekyll serve
```

### Push docs

```
git push
```

This repository has no CI and no deployment automation — it contains no `.github/`
directory. Merging a pull request here does not publish anything to the website.
