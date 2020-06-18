eztrack-testing-data
====================
Data for eztrack testing. This layout was borrowed from `mne-python` testing data at 
[mne-testing-data](https://github.com/mne-tools/mne-testing-data).

Acquire this data in EZTRACK
------------------------
Use `eztrack.datasets.testing.data_path(verbose=True)`.

Update to the latest version in EZTRACK
-----------------------------------
Use `eztrack.datasets.testing.data_path(force_update=True, verbose=True)`.

Add or change files in the repo for use with EZTRACK
------------------------------------------------
1. Ensure your only option is to add files here. Alternatives would be e.g.:

   - See if you can make use of existing files
   - Synthesize the necessary testing files using e.g. RawArray and NumPy directly

2. If new files are needed, make a PR to this repo to add your files.

   .. warning:: Make files as small as possible while ensuring proper testing!
                This often means e.g. cropping to a very short segment of data
                or using a small subset of channels.

3. Update the `version.txt` of the repo in your PR to the next increment.

4. Once your PR is merged, ask a maintainer to cut a new release of the testing data, e.g. 0.53.

5. In EZTRACK, update `eztrack/datasets/utils.py` to:

   1. Change the `'testing'` value in the `releases` dict in `eztrack/datasets/utils.py` to the new version.

   2. Set the new hash. This can be easily done by either:
   
      1. Downloading and running `md5sum` on this (with the proper version number):

          https://codeload.github.com/eztrack-tools/eztrack-testing-data/tar.gz/0.53

         or

      2. Force-updating the repo and looking at the error message (as it gives the new true hash), e.g.:

             $ python -c "import eztrack; eztrack.datasets.testing.data_path(force_update=True)"