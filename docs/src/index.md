# template-python

## Description

**Welcome!** This is a template repository for Python projects using the same
tools that are used to manage
[Spyglass](https://github.com/LorenFrankLab/spyglass). Click
"[Use this template](https://github.com/new?template_name=template-python&template_owner=CBroz1)"
to create your own repository from this template, then follow the
[quickstart](#quickstart) below.

## Project structure

```
template-python/
├── .github/                 # issue templates, PR template, CONTRIBUTING.md
├── .gitignore               # ignored files and directories
├── .pre-commit-config.yaml  # linting and formatting hooks
├── CHANGELOG.md             # version history
├── LICENSE                  # MIT license
├── README.md                # this file (symlink to docs/src/index.md)
├── docs/                    # documentation
│   ├── mkdocs.yml           # mkdocs configuration
│   └── src/                 # mkdocs source files
├── environment.yml          # conda environment
├── notebooks/               # example Jupyter notebooks
├── pyproject.toml           # package metadata and tool config
├── src/template_python/     # library source code
└── tests/                   # pytest test suite
```

## Quickstart

### 1. Rename the template

Replace the placeholder names throughout the repo with your own:

```sh
# set your names
repo_name="your-repo-name"
your_name="Your Name"
your_user="YourGitHubUsername"

# rename the source package directory
git mv "src/template_python" "src/${repo_name//-/_}"

# replace placeholder strings across all files
git grep -l "CBroz1"       | xargs sed -i "s|CBroz1|$your_user|g"
git grep -l "Chris Broz"   | xargs sed -i "s|Chris Broz|$your_name|g"
git grep -l "template_python" | xargs sed -i "s|template_python|${repo_name//-/_}|g"
git grep -l "template-python" | xargs sed -i "s|template-python|$repo_name|g"
```

### 2. Create the conda environment

This makes an isolated environment with all the dependencies needed to run the
code and tests.

```sh
conda env create -f environment.yml
conda activate $repo_name
```

Alternatively, you can update an existing environment with:

```sh
conda activate myenv
conda env update --file environment.yml --prune
```

### 3. Install pre-commit hooks

This is a one-time setup step to install tools that will run automatic checks on
your edits before you commit them. You can customize the hooks in
`.pre-commit-config.yaml`.

```sh
pre-commit install
```

Hooks run automatically before each commit. To run them manually:

```sh
pre-commit run --all-files
```

### 4. Run tests

Tests help ensure your code is working as expected when you make changes.
Example tests in `tests/` use the [pytest](https://docs.pytest.org/) framework.
You can run the test suite with:

```sh
pytest
```

If you see failed tests, you may want to rerun the test with debugging enabled:

```sh
pytest --pdb -v tests/test_your_module.py -k test_your_function
```

### 5. Build and serve docs locally

[`mkdocs`](https://www.mkdocs.org/getting-started/) is a static website
generator for documentation that can be automatically deployed as a
[GitHub Page](https://www.mkdocs.org/user-guide/deploying-your-docs/).

```sh
# serve with live reload
mkdocs serve -f docs/mkdocs.yml

# build static site
mkdocs build -f docs/mkdocs.yml
```

You can customize the documentation by editing the markdown files in `docs/src/`
and the configuration in `docs/mkdocs.yml`. Various extensions can even
automatically generate API reference documentation from your source code (e.g.,
[`mkdocs-gen-files`](https://github.com/oprypin/mkdocs-gen-files)) or auto-run
your notebooks to show as web pages (e.g.,
[`mkdocs-jupyter`](https://github.com/danielfrg/mkdocs-jupyter)).

## Resources

- [conda](https://docs.conda.io/) — environment and package management
- [pre-commit](https://pre-commit.com/) — Git hook framework for code quality
- [pytest](https://docs.pytest.org/) — Python testing framework
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) —
  documentation site generator
- GitHub docs:
  [forking a repo](https://docs.github.com/en/get-started/quickstart/fork-a-repo),
  [branching](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches),
  [opening a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
