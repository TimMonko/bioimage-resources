# Python Setup

## General Information

While there are many ways to get Python working on your machine, this method is intended to get python set up using an environment manager. Due to the nature of our work, many packages are updated frequently and become incompatible with each other. You *will* break your Python install multiple times, and environments will prevent this from being a chore to resolve. I fully endorse using [Mambaforge](https://github.com/conda-forge/miniforge#mambaforge)*, which installs a minimal conda and mamba environment manager. This is much better than using Miniconda, which is certainly always preferred over Anaconda's bloat. 

For more information on Mamba vs Conda see this [Focal Plane post](https://focalplane.biologists.com/2022/12/08/managing-scientific-python-environments-using-conda-mamba-and-friends/). A helpful installation guide (intended for a different environment manager) can be found from [the BioIAN site](https://haesleinhuepf.github.io/BioImageAnalysisNotebooks/01_introduction/readme.html).

\*Perhaps on Mac, Mambaforge is not the easiest, so you can instead set up Miniconda.

## Set-up

### 1. Install Mambaforge

[Click the install link](https://github.com/conda-forge/miniforge#mambaforge) appropriate to your operating system. If prompted by Windows with `Windows protected your PC` click `more info` and then `run anyway`. When prompted, install for `Just Me`.

#### Advanced installation options:

- **check** `Add Mambaforge to my PATH environment variable` (despite this being not recommended, it will make using Python much easier)
- Leave all else the same

### 2. Environment Creation

1. start conda: open command prompt/terminal equivalent. 
2. create a new environment: `mamba create --name __env_name__ python=3.10` This will install python through mamba, but no other packages.
3. Then: `mamba activate __env_name__` to activate the envrionment. *If you do not activate the environment you may modify and thus break your base environment*

### 3. Package installation

Pip installing is currently the better way to manage packages. Conda installs much more slowly (to try to ensure package compatability) and also install out of date packages, despite being up to date in conda-forge. As such, pip installing brute forces the packages we want, and if needed frozen environments can be used if package updates break the environment. There are a few different ways to set up your environment.

- If using a plugin requiring `hdbscan` such as `napari-clusters-plotter` then `mamba install hdbscan` prior to any pip installation methods below. 
- At any point, using [`napari-aicsimageio`](https://github.com/AllenCellModeling/napari-aicsimageio) is likely best for opening proprietary image formats (at minimum it offers consistent metadata reading). If you need to use bioformats accessible images, such as .oib, then follow the instruction to conda install bioformats_jar. 

#### A. Requirement.txt files

Place a `requirements.txt` file from the `Environments` folder in the same directory shown in the command prompt (i.e. `C:\Users\TimMonko\`) 
Then, once your environment is activated (i.e. `mamba activate __env_name__`): 

`pip install -r __requirements_file_name__.txt`. (replace filename appropriately). This will install a curated list of packages. Environments will be described below as they are added:

1. napari-analysis-general-requirements.txt: General napari image analysis, including napari-ndev, followed by compatability with jupyter notebooks and statistical analysis. Will cover most beginning use cases. Once torch/cuda/other deep learning things are needd this will be insufficient and incompatible.

#### B. Custom new environment

1. `mamba isntall __package_name__` or
2. `pip install __package_name__`
Both can be space separated to install multiple at once such as `pip install napari seaborn jupyterlab`. Some packages will have many dependencies, and so install many other packages. 

### 4. Using the Environment

1. Open command line: `conda activate bastian-lab` Then:
2. `napari` for interactive image processing or
3. `naparia` for napari with the clesperanto-assistant displayed or
4. `code` or `jupyter-lab` for coding

### Environment maintenance

If packages appear to not be properly installed check with `pip list`. At any time you may export the list of versions of packages installed with `pip freeze`; this will create a `requirements.txt` file in your current directory.

If you are having particular difficulties with package compatabilities, check `pip list` and `pip -V` to see if there is versions of these packages which exist in the equivalent `C:\Users\TimMonko\AppData\Roaming\Python\Python39\`. If so, you'll want to delete this entire folder, this exists from installing things in the Anaconda directory, so should not normally be an issue with a new miniconda installation.  
