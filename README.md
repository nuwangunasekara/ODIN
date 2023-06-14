# ODIN
Code for paper:

"Adaptive Neural Networks for Online Domain Incremental Continual Learning"
Online Domain Incremental Networks (ODIN)
Discovery Science 2022
Nuwan Gunasekara, Heitor Gomes, Albert Bifet, and Bernhard Pfahringer
AI Institute, University of Waikato, Hamilton, New Zealand.


## How to get the code 
```
git clone --recurse-submodules --branch ODIN git@github.com:nuwangunasekara/avalanche.git
```
verify you are using the correct git tag (ODIN)
```
% cd avalanche
% git reflog                          
a6b017ef (HEAD, tag: ODIN, origin/master, origin/HEAD) HEAD@{0}: clone: from github.com:nuwangunasekara/avalanche.git
```

## Take the following steps to create an environment and have the code run after cloning the code.

1. Download `spec-file.txt`

2. `conda create --prefix Users/pouya/PhD/CL_conda --file spec-file.txt`
    * `Users/pouya/PhD/CL_conda` is the direction where one wants to create an environment
    *  `spec-file.txt` is the list of the used library and should be replaced in the directory your terminal shows as active.
3. `conda env list`: Check whether the environment has been created.
4. `conda activate /Users/pouya/PhD/CL_conda`
    * `/Users/pouya/PhD/CL_conda` shows the created environment's directory.
5. Clone skmultiflow on your system: `git clone https://github.com/scikit-multilearn/scikit-multilearn.git`
    * It is important to clone `skmultiflow` on your system and install it manually, do not install it from the website directly to avoid upgrading `Numpy` and other libraries.
6. `pip install -e /Users/pouya/PhD/sckit-multiflow` 
    * `/Users/pouya/PhD/sckit-multiflow` is the directory where you have cloned `skmultiflow`
7. `cd /Users/pouya/PhD/avalanche`: Change the directory to the cloned place of the avalanche
8. `pip install -e .`: Install the avalanche library on the created environment
9. `pip install gdown`
10. `pip install scikit-image==0.19.0`
    * `0.19.0: `: version should be stated to avoid upgrading Numpy
11. Run an experiment: `bash exp-script/run-exp.sh exp-scripts/train-pool.py ~/PhD/CL/results ~/PhD/CL_conda`
    * `~/PhD/CL/results` is the path where the results will be saved
    * `~/PhD/CL_conda` is the created environment directory


## Consider the following points:
1. If one's system does not support `quantize` approach, in the line 618 from Multi-MLP, put the `quantize` variable as `False`.

2. If, in the middle of the process, you decide to start from scratch, make sure to remove the created file before:
    * Make sure you delete existing conda env (if there is any) and results directory
         ```
         rm -rf  ~/PhD/CL/results/ ~/PhD/CL_conda 
         ```

## Run experiments: 
You could use use ```exp_scripts/run_exp.sh``` script to run multiple experiments. Please edit it for your needs before you run (running step 11).
1. One could tail the logfile output to continually monitor the status of the experiment.
2. One could also use ```exp_scripts/train_pool.py``` python script to run a single experiment. Please have a look at the command line arguments before you run. 

## Please let us know if you come across any issue with the build or running experiments
