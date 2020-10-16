## Detecting Signal Corruptions in Voice Recordings for Speech Therapy

### Installation

1. Clone this repository.
2. Optional but recommended: install [CUDA](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html).
3. Acquire TIMIT, place the root directory (containing `DOC`, `TEST`, `TRAIN` and `README.DOC`) in the folder `timit` (or replace the folder with a link, see `man ln`).
4. Acquire [gm_hmm](https://github.com/FirstHandScientist/genhmm) and place its root directory in the folder `classifier/gm_hmm` (or do the link trick again).
5. Follow the installation instructions for gm_hmm. The dataset preparation steps etc. are not needed but can be good to verify the installation.
    - This includes installing [Kaldi](https://kaldi-asr.org). Install it into a folder at `features/kaldi` or make a link as above.
6. Install llvm via `sudo apt-get install llvm`.
7. Create a virtualenvironment with a Python 3.6 interpreter.
8. Activate the environment via e.g. `source pyenv/bin/activate`.
9. Install Matlab.
10. Go to `[your Matlab root]/extern/engines/python/` and run `python setup.py install`.
11. Return to this project's root folder and install the dependencies listed in [`requirements.txt`](requirements.txt), via e.g. `pip install -r requirements.txt`.
12. Run `degradation/create_dataset.py prepare` to convert noise files (recordings for air-conditioning noise and electric hum are included) to the right formats, convert the TIMIT files from NIST sphere to standard wavefile etc.
13. Given that the above steps completed successfully, you should now be all set to run `./experiments.py`.

### Tests
The default settings will generate the `Realistic` set and train/test an LSTM with similar settings to the report. To change the definition of the corruptions, or the classification algorithm or features used to detect a corruption, edit the [`noise_classes/noise_classes.json`](noise_classes/noise_classes.json) file. Here you may also change the parameters of the algorithm. If you want to change a default property for all instances of a classifier this can be done via [`classifier/defaults.json`](classifier/defaults.json) for less copy-pasting.
