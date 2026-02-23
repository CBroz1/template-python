# Guidelines for contributing

## Summary

**PRs welcome!**

- **Consider starting a discussion to see if there's interest in what you want
    to do.**
- **Fork the repo and submit PRs from the fork.**
- **Ensure PRs pass all CI checks.**
- **Maintain test coverage at 70% or above.**

## Git

- _[Why use Git?](https://www.git-scm.com/about)_ Git enables creation of
    multiple versions of a code repository called branches, with the ability to
    track and undo changes in detail.
- Install Git by [downloading](https://www.git-scm.com/downloads) from the
    website, or with a package manager like [Homebrew](https://brew.sh/).
- [Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this
    repo.
- Create a
    [branch](https://www.git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
    in your fork.
- Commit your changes with a
    [properly-formatted Git commit message](https://chris.beams.io/posts/git-commit/).
- Create a
    [pull request (PR)](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
    to incorporate your changes into the upstream project you forked.

## Python

### Environment setup with conda

This project uses [conda](https://docs.conda.io/) for environment and dependency
management.

#### Installation

[Install conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/)
or [Miniconda](https://docs.conda.io/en/latest/miniconda.html), then create and
activate the project environment:

```sh
conda env create -f environment.yml
conda activate template-python
```

To update the environment after changes to _environment.yml_:

```sh
conda env update -f environment.yml --prune
```

### Testing with pytest

- Tests are in the _tests/_ directory.
- [pytest](https://docs.pytest.org/en/latest/) features used include:
  - [fixtures](https://docs.pytest.org/en/latest/how-to/fixtures.html)
  - [parametrize](https://docs.pytest.org/en/latest/how-to/parametrize.html)
- [pytest configuration](https://docs.pytest.org/en/latest/reference/customize.html)
    is in _pyproject.toml_.
- Run tests with pytest and [coverage.py](https://github.com/nedbat/coveragepy):

```sh
pytest                  # run tests
coverage run            # run tests with coverage tracking
coverage report         # print coverage summary
coverage html           # open interactive HTML coverage report
```

## Code quality

### pre-commit hooks

This project uses [pre-commit](https://pre-commit.com/) to run code quality
checks automatically before each commit.

Install the hooks after setting up your environment:

```sh
pre-commit install
```

Run all hooks manually at any time:

```sh
pre-commit run --all-files
```

### Code style

Python code is formatted with [Ruff](https://docs.astral.sh/ruff/). Ruff
configuration is stored in _pyproject.toml_.

- Markdown is formatted with [mdformat](https://mdformat.readthedocs.io/).

To format code manually:

```sh
ruff check --fix    # lint and auto-fix
ruff format         # format Python
```

### Spell check

Spell check is performed with [CSpell](https://cspell.org/). Configuration is
in _cspell.json_. CSpell runs automatically via the pre-commit hook.

## GitHub Actions workflows

[GitHub Actions](https://github.com/features/actions) is a continuous
integration/continuous deployment (CI/CD) service that runs on GitHub repos.
Actions are grouped into workflows and stored in _.github/workflows_.

## Maintainers

- **PRs should be merged into the default branch.** Head branches are deleted
    automatically after PRs are merged.
- **To create a release:**
  - Bump the version number in `src/template_python/__init__.py` and commit
        the changes.
  - Follow [SemVer](https://semver.org/) and
    [PEP 440](https://peps.python.org/pep-0440/) guidelines when choosing a
    version number.
  - Create an
    [annotated and signed Git tag](https://www.git-scm.com/book/en/v2/Git-Basics-Tagging).
    - Omit the leading `v` (use `1.0.0` instead of `v1.0.0`)
    - Example: `git tag -a -s 1.0.0`
  - Push the tag. GitHub Actions will test and build the Python package.
