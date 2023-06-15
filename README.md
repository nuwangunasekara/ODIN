# ODIN
Code for paper:

"Adaptive Neural Networks for Online Domain Incremental Continual Learning"
Online Domain Incremental Networks (ODIN)
Discovery Science 2022
Nuwan Gunasekara, Heitor Gomes, Albert Bifet, and Bernhard Pfahringer
AI Institute, University of Waikato, Hamilton, New Zealand.


## How to get the code 
```
git clone --recurse-submodules --branch ODIN git@github.com:nuwangunasekara/avalanche.git ~/ODIN/avalanche
```
verify you are using the correct git tag (ODIN)
```
% cd ~/ODIN/avalanche
% git reflog                          
a6b017ef (HEAD, tag: ODIN, origin/master, origin/HEAD) HEAD@{0}: clone: from github.com:nuwangunasekara/avalanche.git
```

## Take the following steps to create an environment and have the code run after cloning the code.

1. Download `spec-file.txt`

2. `conda create --prefix ~/ODIN/CL_conda --file spec-file.txt`
    * `~/ODIN/CL_conda` is the direction where one wants to create an environment
    *  `spec-file.txt` is the list of the used library and should be replaced in the directory your terminal shows as active.
3. `conda env list`: Check whether the environment has been created.
4. `conda activate ~/ODIN/CL_conda`
    * `~/ODIN/CL_conda` shows the created environment's directory.
5. Clone scikit-multiflow on your system: `git clone https://github.com/scikit-multiflow/scikit-multiflow.git ~/ODIN/scikit-multiflow`
    * It is important to clone `scikit-multiflow` on your system and install it manually, do not install it from the website directly to avoid upgrading `Numpy` and other libraries.
6. `pip install -e ~/ODIN/scikit-multiflow` 
    * `~/ODIN/scikit-multiflow` is the directory where you have cloned `skmultiflow`
7. `cd ~/ODIN/avalanche`: Change the directory to the cloned place of the avalanche
8. `pip install -e .`: Install the avalanche library on the created environment
9. `pip install gdown`
10. `pip install scikit-image==0.19.0`
    * `0.19.0: `: version should be stated to avoid upgrading Numpy
11. Run an experiment: `bash exp-script/run-exp.sh exp-scripts/train-pool.py ~/ODIN/results ~/ODIN/CL_conda`
    * `~/ODIN/results` is the path where the results will be saved
    * `~/ODIN/CL_conda` is the created environment directory


## Consider the following points:
1. If one's system does not support `quantize` approach, in the line 618 from Multi-MLP, put the `quantize` variable as `False`.

2. If, in the middle of the process, you decide to start from scratch, make sure to remove the created file before:
    * Make sure you delete existing conda env (if there is any) and results directory
         ```
         rm -rf  ~/ODIN/results ~/ODIN/CL_conda
         ```

## Run experiments: 
You could use use ```exp_scripts/run_exp.sh``` script to run multiple experiments. Please edit it for your needs before you run (running step 11).
1. One could tail the logfile output to continually monitor the status of the experiment.
2. One could also use ```exp_scripts/train_pool.py``` python script to run a single experiment. Please have a look at the command line arguments before you run. 

## Notes

Please let us know if you come across any issue with the build or running experiments

Special thanks to [pouya1996](https://github.com/pouya1996) for improving this installation instructions.
