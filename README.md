# docs.virtengine.com

VirtEngine - Private opensource + Private enterprise documentation.

Current network launch documentation is published in
[`_overview/network-launch-schedule.md`](_overview/network-launch-schedule.md):
TestNet is planned for January 2027 and MainNet for March 2027 after a separate
validation and production approval gate.

## Ruby  
You need ruby 2.3.x

### Fork and clone the docs

```

git clone https://github.com/<your_github_id>/docs.virtengine.com

cd docs.virtengine.com

bundle install

```

### Edit & Test

Add sections to appear in the left navbar by editing `_config.yaml`

```

jekyll clean

jekyll build

jekyll serve

```

### Push docs

```

git push 

```

The documentation should get updated automatically upon merging your pull request.
