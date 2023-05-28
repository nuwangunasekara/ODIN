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
## Please apply below patch to force the build to use numpy==1.19.5 pytorch==1.11.0 and  torchvision==0.12.0
```
diff --git a/environment-dev.yml b/environment-dev.yml
index 2565b613..cc05b637 100644
--- a/environment-dev.yml
+++ b/environment-dev.yml
@@ -13,12 +13,12 @@ channels:
 - conda-forge
 dependencies:
 - psutil
+- conda-forge::numpy=1.19.5
 - conda-forge::gputil
 - wandb
 - tensorboard
 - scikit-learn
 - matplotlib
-- numpy
 - conda-forge::quadprog
 - tqdm
 - pip
@@ -30,6 +30,7 @@ dependencies:
 - conda-forge::pycocotools
 - pandas
 - pip:
+    - numpy==1.19.5
     - pytorchcv
     - gdown
     - scikit-multiflow
diff --git a/install_environment_dev.sh b/install_environment_dev.sh
index f065b094..fe21b41c 100755
--- a/install_environment_dev.sh
+++ b/install_environment_dev.sh
@@ -87,15 +87,15 @@ conda create --prefix $conda_location python=$python -c conda-forge
 conda activate $conda_location
 if [[ "$cuda_version" = "none" ]]; then
     if [[ "$python_version" = 3.9 ]]; then
-        conda install pytorch torchvision cpuonly -c pytorch -c=conda-forge
+        conda install numpy==1.19.5 pytorch==1.11.0 torchvision==0.12.0 cpuonly -c pytorch -c=conda-forge
     else
-        conda install pytorch torchvision cpuonly -c pytorch
+        conda install numpy==1.19.5 pytorch==1.11.0 torchvision==0.12.0 cpuonly -c pytorch
     fi
 else
     if [[ "$python_version" = 3.9 || "$cuda_version" = 11.1 ]]; then
-        conda install pytorch torchvision cudatoolkit=$cuda_version -c pytorch -c=conda-forge
+        conda install numpy==1.19.5 pytorch==1.11.0 torchvision==0.12.0 cudatoolkit=$cuda_version -c pytorch -c=conda-forge
     else
-        conda install pytorch torchvision cudatoolkit=$cuda_version -c pytorch
+        conda install numpy==1.19.5 pytorch==1.11.0 torchvision==0.12.0 cudatoolkit=$cuda_version -c pytorch
     fi
 fi
 conda env update --file "$yml_file"
```

## Build conda env 
From source root run 
```
bash exp_scripts/reinit_conda.sh ~/Desktop/CL_conda $(pwd)
```

## Run experiments: 
you could use use ```exp_scripts/run_exp.sh``` script to run multiple experiments. Please edit it for your needs before you run. 
### if you are using exp_scripts/run_exp.sh
#### Create a results directory:
```
 mkdir -p ~/Desktop/CL/results/
```
#### Edit exp_scripts/run_exp.sh as required 
#### Run experiments from source root
```
bash exp_scripts/run_exp.sh  exp_scripts/train_pool.py ~/Desktop/CL/results/ ~/Desktop/CL_conda
```
It outputs the relevant ```exp_scripts/train_pool.py``` command and the log file.
One could tail the logfile output to continually monitor the status of the experiment.


### One could also use ```exp_scripts/train_pool.py``` python script to run a single experiment. Please have a look at the command line arguments before you run. 

## Please let me know if you come across any issue with the build or running experiments
