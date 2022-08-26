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

## Build conda env 
From source root run 
```
bash exp_scripts/reinit_conda.sh ~/Desktop/CL_conda $(pwd)
```

## Run experiments: 
you could use use ```exp_scripts/run_exp.sh``` script to run multiple experiments. Please edit it for your needs before you run. 

Or could use ```exp_scripts/train_pool.py``` python script to run a single experiment. Please have a look at the command line arguments before you run. 
