# Buildkite erb pipeline

Presuming you have ruby and erb installed on your agent machine, create a
Buildkite pipeline with "Read steps from the repository" at the beginning, but change
the command to:

```sh
erb .buildkite/pipeline.yml.erb | buildkite-agent pipeline upload
```

like this:

![New Pipeline page with erb pre-processed pipeline upload step](https://cloud.githubusercontent.com/assets/14028/15920018/150cd1ec-2e5a-11e6-84f6-9f5133e12620.png)

with a file like:

```erb
# .buildkite/pipeline.yml.erb
steps:
  - command: echo <%= "Hello from Ruby #{RUBY_VERSION}".inspect %>
```

and you should get a result like:

![Build page with Ruby-constructed Pipeline steps](https://cloud.githubusercontent.com/assets/14028/15920090/a41545e0-2e5a-11e6-877a-a782c0a3d2e8.png)
