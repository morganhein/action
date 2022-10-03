**DEPRECATED** Fork here!

This fork supports pulling pre-commit repositories from private repos using a github token.

___


pre-commit/action
=================

a GitHub action to run [pre-commit](https://pre-commit.com)

### using this action

To use this action, make a file `.github/workflows/pre-commit.yml`.  Here's a
template to get started:

```yaml
name: pre-commit

on:
  pull_request:
  push:
    branches: [main]

jobs:
  pre-commit:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - uses: actions/setup-python@v3
    - uses: morganhein/action@v0.1.0
```

This does a few things:

- clones the code
- installs python
- sets up the `pre-commit` cache

### using this action with custom invocations

By default, this action runs all the hooks against all the files.  `extra_args`
lets users specify a single hook id and/or options to pass to `pre-commit run`.

Here's a sample step configuration that only runs the `flake8` hook against all
the files (use the template above except for the `pre-commit` action):

```yaml
    - uses: morganhein/action@v0.1.0
      with:
        extra_args: flake8 --all-files
```

### using this action in private repositories

Provide the `access_token` for this action, which should be the ${GITHUB_TOKEN}.