# registry-ref-data

Reference datasets used for integration test of the registry.

This repository aims at maintaining the reference datasets on github before them being published on https://pds.nasa.gov/data/pds4/test-data/custom-datasets/

## Tester manual:

1. Clone the repository

2. Update the reference test datasets as needed for the feature/bug fix that need to be tested.

3. reduce the size of the data files as much as possible:

	a. Binary files, use `truncate`
        b. CSV or TAB files, use sed, e.g. `sed '10,$ d' input.csv` 

3. Commit your changes and push them

4. The new reference dataset will be published in the Latest release of the repository

 

### Documentation

Your project should use [Sphinx](https://www.sphinx-doc.org/en/master/) to build its documentation. PDS' documentation template is already configured as part of the default build. You can build your projects docs with:

    sphinx-build -b html docs/source docs/builds/

You can access the build files in the following directory relative to the project root:

    build/

## CI/CD

The template repository comes with our two "standard" CI/CD workflows, `stable-cicd` and `unstable-cicd`. The unstable build runs on any push to `main` (± ignoring changes to specific files) and the stable build runs on push of a release branch of the form `release/<release version>`. Both of these make use of our GitHub actions build step, [Roundup](https://github.com/NASA-PDS/roundup-action). The `unstable-cicd` will generate (and constantly update) a SNAPSHOT release. If you haven't done a formal software release you will end up with a `v0.0.0-SNAPSHOT` release (see NASA-PDS/roundup-action#56 for specifics).
