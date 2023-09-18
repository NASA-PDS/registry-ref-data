# registry-ref-data

## Description

Reference datasets used for integration test of the registry.

This repository aims at maintaining the reference datasets on github before them being published on https://pds.nasa.gov/data/pds4/test-data/custom-datasets/

## Tester manual:

1. Clone the repository

2. Update the reference test datasets as needed for the feature/bug fix that need to be tested.

3. Commit your changes and push them

4. Create the test dataset package:

    % tar cvzf custom-datasets.tar.gz  custom-datasets

5. Publish it:

    % scp custom-datasets.tar.gz {/tmp in the cloud machine}
    % ssh cloud-machine
    % ssh pds4@localhost
    % cp /tmp/custom-datasets.tar.gz {to the folder where the data is published}



