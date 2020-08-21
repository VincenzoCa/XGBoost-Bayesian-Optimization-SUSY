# SUSY with XGBoost and Bayesian Optimization

The goal of this project is to optimize [**XGBoost**](https://xgboost.readthedocs.io/en/latest/index.html#) hyperparameters in the [supersymmetry (SUSY) dataset](https://archive.ics.uci.edu/ml/datasets/SUSY#), first introduced by [1402.4735](https://arxiv.org/pdf/1402.4735.pdf), using [**Ax**](https://ax.dev/), the new open-source AI framework launched by Facebook in 2019. 

In this project, `Ax` is used for Bayesian hyperparameter optimization.
[Bayesian optimization](https://en.wikipedia.org/wiki/Bayesian_optimization) in `Ax` is powered by `BoTorch`, a modern library for Bayesian optimization research built on `PyTorch`.

This is a **binary classification** task where we will try to distinguish between a process where new supersymmetric particles are produced (**signal process**), leading to a final state in which some particles  are  detectable  and  others  are  invisible  to  the experimental apparatus, and a **background process** with the  same  detectable  particles  but  fewer  invisible  particles  and  distinct  kinematic  features.

![Decision Tree](https://github.com/VincenzoCa/XGBoost-Bayesian-Optimization-SUSY/blob/master/trees/tree_10.gv-1.png)
<p align="center">
The 10th Decision Tree of our Trained XGBoost Model used to classify the Supersymmetry dataset
</p>   

## How to create a Conda environment for Machine Learning

1. Set up [miniconda](https://docs.conda.io/en/latest/miniconda.html).

   Download the Linux installer:

   - `wget -nv http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh`

   Install [Conda](https://docs.conda.io/en/latest/index.html) (same for macOS and Linux):

   - `bash miniconda3.sh -b -p $HOME/miniconda`

   - `source $HOME/miniconda/etc/profile.d/conda.sh`
   
3. Create a project folder called project on the desktop using `mkdir project` then enter it using `cd project`.   

4. Use 

   - `conda create --prefix ./env pandas numpy matplotlib scikit-learn jupyter` 
  
   to create an environment folder called env containing pandas, NumPy, Matplotlib, scikit-learn and Jupyter inside your project folder.
   
5. Activate your environment using `conda activate /path-to-your-folder/project/env`

6. Start a Jupyter Notebook using `jupyter notebook` and perform a final check by importing pandas, NumPy, Matplotlib and sklearn to the Jupyter Notebook.

7. Install xgboost and python-graphviz (in your current environment):

   - `conda install -c conda-forge xgboost `
   
   - `conda install -c conda-forge python-graphviz`
   
8. Install Ax

   - `conda install pytorch torchvision -c pytorch`
   
   - `pip3 install ax-platform`
   

You may want to take a look at [this article](https://www.mrdbourke.com/get-your-computer-ready-for-machine-learning-using-anaconda-miniconda-and-conda/) to discover more on Conda and miniconda.

### How to Run Jupyter Notebooks on Remote Servers - SSH

1. Start the Jupyter Notebook on your remote computer:

   - ```jupyter notebook --no-browser --port 1234```
   
   This will start the Jupyter Notebook on port 1234. You will also get a URL with authentication token.
   
2. To start SSH tunneling on unix, open the terminal on your local computer and enter the following command:

   - ```ssh -NL 1234:localhost:1234 username@lx03.hep.ph.ic.ac.uk```
   
3. Open up your favorite browser and go to URL you got before and you will see the Jupyter Notebook running in your browser.

Click [here](https://medium.com/@apbetahouse45/how-to-run-jupyter-notebooks-on-remote-server-part-1-ssh-a2be0232c533) to read more about how to run Jupyter Notebooks on remote server.
