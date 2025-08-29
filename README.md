# registry-ref-data

Reference datasets used for integration test of the registry.

This repository aims at maintaining the reference datasets on github before them being published as a release of this repository and used by the integration tests (in docker compose) in the NASA-PDS/registry repository.

## Tester manual:

1. Clone the repository

2. Update the reference test datasets as needed for the feature/bug fix that need to be tested.

3. reduce the size of the data files as much as possible:

	a. Binary files, use `truncate`

    b. CSV or TAB files, use sed, e.g. `sed '10,$ d' input.csv`

3. Commit your changes and push them

4. The new reference dataset will be published in the Latest release of the repository and automatically used by the docker compose deployment in the `NASA-PDS/registry` repository.



### Documentation

This project uses [Sphinx](https://www.sphinx-doc.org/en/master/) to build its documentation. You can generate the HTML version of the documentation with:

    python3.13 -m venv .venv  # Or use a later version of Python
    .venv/bin/pip install 'sphinx~=8.2.3' 'sphinx_rtd_theme~=3.0.2'
    .venv/bin/sphinx-build -b html docs/source docs/build/

You can access the built files in the following directory relative to the project root:

    docs/build/index.html


## CI/CD

The template repository comes with a "standard" CI/CD workflow, `unstable-cicd`. The unstable build runs on any push to `main` (± ignoring changes to specific files) and publishes a `custom-datasets.tar.gz` to this project's [release page](https://github.com/NASA-PDS/registry-ref-data/releases).
