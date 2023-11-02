# Conda and Jupyter

Currently this page only contains documentatoion about `conda`.

## Conda

### What is Conda?

[Conda](https://docs.conda.io) is an open source package and environment management system for any programming languages, but especially popular among the Python community. It runs on Windows, macOS, and Linux. From the [conda website](https://docs.conda.io): *"Conda quickly installs, runs, and updates packages and their dependencies. Conda easily creates, saves, loads, and switches between environments on your local computer."* For Python, the key strengths of `conda` are that it:
- Manages package dependencies
- Manages and compiles non-Python, binary dependencies (eg, C libraries), easing this common source of library installation problems.
- Enables creation and management of custom, isolated virtual environments
- Does not require administrative privileges
- Can be installed side by side with other Python installations without interfering with them

To learn more about conda, including installation, configuration, and the creation and management of conda environments, we recommend these two resources:

- [Carpentries — Introduction to Conda for (Data) Scientists](https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/)
- [Project Pythia — Installing and Managing Python with Conda — Pythia Foundations](https://foundations.projectpythia.org/foundations/conda.html)


### Installation

Conda can be installed through different distributions, with different pros and cons. These include, among others, `Anaconda`, `miniconda`, `mamba` and `mambaforge`. We strongly recommend the use of [miniconda](https://docs.conda.io/en/latest/miniconda.html) because, compared to `Anaconda`, it is more lightweight, can be installed quickly, and promotes the creation of environment to meet specific needs. Until recently, the distributions based on "mamba" performed much more quickly during the creation of environments ("package resolution"); however, `miniconda` can now leverage this mamba capabilities via the conda "libmamba solver" (see [here](https://conda.github.io/conda-libmamba-solver/) for more details). The installation instructions below include the steps to set the conda libmamba solver as the default.

#### Windows

Download the `Miniconda3 Windows 64bit` installation file from [this link](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe) on the [Miniconda web site](https://docs.conda.io/en/latest/miniconda.html). It's found under "Latest Miniconda Installer Links". Then follow these steps, taken from a Windows 10 computer (the steps are *probably* very similar in Windows 11):

1. Run (double click) the miniconda installation (`.exe`)` file
2. Select the option to install for the local user only
3. Accept the default installation path, which will likely be `C:\Users\<USERNAME>\miniconda3`, where `<USERNAME>` is your user name
4. On the "Advanced Installation Options" window, uncheck both boxes ("Add Miniconda3 ..." and "Register Miniconda3 ...")
5. On the "Completing Miniconda3" window, uncheck both boxes

If the installer asks you if you'd like to initialize Miniconda3 ("Do you wish the installer to initialize Miniconda3 by running `conda init`?"), select "yes". If it ends without asking that question, 

When the installation is finished, from the `Start` menu open the "Anaconda Powershell Prompt", a terminal where `conda` will already be available. Test it by running the command `conda list`. If the installer ended earlier without asking if you'd like to initialize Miniconda3, enter the following command: `C:\Users\<USERNAME>\miniconda3\bin\conda init`. 

Finally, complete two additional steps on the Powershell:

```bash
# Update the "base" conda environment
conda update -n base conda --yes
# Install or update the "conda-libmamba-solver", then configure it as the default
# This will make conda much faster
conda install -n base conda-libmamba-solver
conda config --set solver libmamba
```

`miniconda` can also be installed on Windows from a terminal. See [here](https://docs.conda.io/projects/miniconda/en/latest/#quick-command-line-install) for instructions.

#### macOS or Linux

We'll install conda via commands. On the terminal (which should be a `bash`-type shell), execute the following sequence of commands:

```bash
# On macOS
url=https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
# On Linux
url=https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# The rest of the commands are identical on macOS and Linux
mkdir -p ~/miniconda3
wget $url -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
```

Finally, we'll configure the conda installation:

```bash
# "Initialize" conda
~/miniconda3/bin/conda init
# Note this run time message:
# ==> For changes to take effect, close and re-open your current shell. <==
# Update the "base" conda environment
conda update -n base conda --yes
# Install or update the "conda-libmamba-solver", then configure it as the default
# This will make conda much faster
conda install -n base conda-libmamba-solver
conda config --set solver libmamba
```

### Temporarily reverting to the classic conda package solver

We don't recommend this, but you can revert to the "classic" conda solver instead of libmamba-solver as needed, for example, for backwards compatibility when using conda environments created with the classic solver. To install a package using the classic solver, use the `--solver=classic` flag. Using the `numpy` package as an example:

```bash
conda install numpy --solver=classic
```

### Best practices

- The `base` conda environment is a special environment used by conda. Avoid installing additional packages to it, as that may lead to 
- All your work should be based on custom environments created specifically for a project or a set of closely related projects
- Conda packages are hosted in package repositories called "channels"
- The most widely used conda package repository in the scientific -- and many other -- communities is [conda-forge](https://conda-forge.org). We recommend its use exclusively unless there is a specific reason to use a different channel, such as the "default" channel


### Conda virtual environments

Having the right computational environment is crucial for running your programs and accessing the necessary data sets. conda allows you to create and manage virtual environments that contain exactly the libraries required for a particular project or set of projects, down to the specific package versions if necessary. A conda environment definition can also be shared with others or in other computers, to recreate an environment.

Conda environments can be created either via individual conda commands on the terminal, or via an environment or requirements file that specifies the packages.

#### Create an environment through conda commands

Open a terminal (or Anaconda Powershell Prompt on Windows). The environment must specify Python itself, plus any packages you need. Most packages have dependencies that will be installed by default. If needed, specify the version for each package.

To create a new conda environment called `MYENV` with Python 3.10, `numpy` and `matplotlib` obtained from the `conda-forge` conda package channel:

```bash
conda create -c conda-forge -n MYENV python=3.10 numpy matplotlib
```

Alternatively, a simple environment can be created first, then packages installed on it via individual `conda install` commands:

```bash
conda create -c conda-forge -n MYENV python=3.10
# "Activate" the new environment in order to use it
conda activate MYENV
# Install additional packages
conda install -c conda-forge numpy
conda install -c conda-forge matplotlib
# Use pip install if the package is not available
# as a conda package. For "specialpackage":
pip install specialpackage
```

"deactivate" an environment when done using it, or to switch to a different environment:

```bash
conda deactivate
```

#### Create an environment from a file

The specifications for a conda environment can be stored in an ["environment" file (in `yaml` format)](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file) that can then be used to create a matching environment. 

An environment file with the following content reproduces the conda environment described in the previous section:

```yaml
name: MYENV
channels:
  - conda-forge
dependencies:
  - python=3.10
  - pip # install pip in the environment
  - numpy
  - matplotlib
  - pip:
    - specialpackage
```

If this file is named `environnment.yaml`, the `MYENV` environment can be created as follows, assuming the file is in the same directory you are currently at in the terminal:

```bash
conda env create -f environment.yaml
```

Alternatively, a conda environment can also be created using a `requirements.txt` file that follows the format used with `pip` (for example, see [here](https://linuxhint.com/conda-install-requirements-txt/)). In that case, you will need to specify the conda channel and the name of the environment:

```bash
conda create -c conda-forge -f requirements.txt -n MYENV
```

For additional information on conda environments, consult these resources:
- https://conda.io/docs/user-guide/tasks/manage-environments.html
- https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/02-working-with-environments/index.html
- https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/04-sharing-environments/index.html
- [OceanHackWeek 2022: Managing conda environments tutorial](https://oceanhackweek.org/ohw22/tutorials/optional/managing-conda-envs/README.html). Text-based screencasts demonstrating conda environments


### Other helpful materials

- [OceanHackWeek 2023: Software installation survival guide (conda and friends) tutorial / presentation](https://github.com/oceanhackweek/ohw-tutorials/blob/OHW23/00-Mon/README.md)
- This document drew in part from materials in the OceanHackWeek website, such as [this page](https://oceanhackweek.org/resources/prep/conda.html)
- If new to Python and programming, [this introduction may be useful](https://emiliom.github.io/dinosip-python/). But there are many introductions to Python online!
