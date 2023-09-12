# Conda and Jupyter

Some topics to consider:
- What is conda?
- What are in the Jupyter ecosystem? Jupyter Notebook, Jupyter Lab, Jupyter Hub, ???
- Installation
    - consider different platforms
- How we use conda environments when working on projects
    - separate environments for different projects
    - library versions can matter quite a bit!
- ...

## Conda (to run customized Python environments)

### What is Conda?
(from https://oceanhackweek.org/resources/prep/conda.html)

[Conda](https://docs.conda.io) is an open source `package` and `environment` management system for any programming languages, but very popular among the Python community.

Conda runs on Windows, macOS, and Linux: *"Conda quickly installs, runs, and updates packages and their dependencies. Conda easily creates, saves, loads, and switches between environments on your local computer. It was created for Python programs but it can package and distribute software for any language."* (from [conda website](https://docs.conda.io))

For Python, the advantage of conda compared to `pip` is that it has a built in environment management system as well as the management of binaries, and non-Python dependencies.

**TODO:** Describe all the advantages, not just that one.
- package and dependency management
- management of binary dependencies (eg, C libraries)
- custom environments
- conda-forge!

### Virtual environments
(from https://github.com/uw-echospace/group-docs/blob/main/Onboarding.md#virtual-environments)

Having one’s code is not sufficient to rerun their experiments: everybody knows that. Having the right computational environment is crucial for running the programs and accessing the necessary data sets.

If you are using Python there are very helpful tools to help you manage the packages you are installing. We recommend using an Anaconda Python Distribution which already comes with a package manager. You can install packages with the conda install command. Keep a separate conda environment for every subproject. Ideally you should list on the README of your repo what packages are required. You can create a requirements.txt file and store it, so that others can easily install all the packages. For a thorough guide on virtual environments:

https://conda.io/docs/user-guide/tasks/manage-environments.html
### Installation (installing Python on Windows through conda)
(from https://github.com/uw-echospace/group-docs/blob/main/conda_jupyterlab.md)

We'll install Python (3.8) via the [conda](https://conda.io) "open source package management system and environment management system". The advantages of conda include:

- Doesn't require administrative privileges
- Can be installed side by side with other Python installations w/o interfering with them
- Allows you to easily create "virtual environments" with custom Python installations

conda can be installed in one of two ways, either with "Anaconda" or "Miniconda". We'll use Miniconda, which is much lighter weight than Anaconda, for your own personal use, you may find Anaconda more user friendly. Go to https://docs.conda.io/en/latest/miniconda.html
Download the Windows Python 3.8 installer; I don't know whether you'd use the 32bit or 64 bit one. I did my Windows testing on the 64bit version. If your computer is not too old, I suspect it'll be 64bit; but pick the one that's right for your computer.

Installation instructions for Windows are [here](https://conda.io/projects/conda/en/latest/user-guide/install/index.html). You can find MacOS instructions [here](https://conda.io/projects/conda/en/latest/user-guide/install/index.html), but the process should be pretty similar as on Windows (except that you can do it via the command line, I think).

Assuming you're on Windows 10:

- After downloading the miniconda .exe file, double-click on it
- Select the option to install for the local user only
- Accept the default installation path. I assume it'll be something like C:\Users\<USERNAME>\miniconda3
- On the Advanced Installation Options window, uncheck both boxes ("Add Miniconda3 ..." and "Register Miniconda3 ...")
- On the "Completing Miniconda3" window, you can do whatever you want (check or uncheck the boxes). If you have no preference, uncheck both boxes.

When installation is finished, from the Start menu, open the Anaconda Prompt or Anaconda Powershell Prompt; the latter will probably be nicer. Test it by running the command "conda list"


### Instalación de JupyterLab y Conda
(From https://github.com/Intercoonecta/Aula-invertida/blob/main/Intro-a-Jupyter/instalacion-jlab-conda.md)

[Conda](https://docs.conda.io) es un administrador de paquetes y entornos para cualquier lenguaje de programación, pero especialmente popular en la comunidad de usuarios de Python. Permite la instalación de diferentes combinaciones y versiones de paquetes de software o librerías y de sus dependencias en diferentes entornos, con la capacidad de cambiar fácilmente de un entorno a otro, donde cada entorno puede estar relacionado a un proyecto específico. Conda da acceso a miles de paquetes, y puede ser instalado en tu computadora sin necesidad de tener privilegios administrativos.

Conda funciona tanto en Windows como en macOS y Linux. Conda y los paquetes disponibles a través de conda son generalmente gratuitos y accesibles bajo licencias de código abierto. Hay diferentes maneras de instalar conda. Aquí utilizaremos [Miniconda](https://conda.io/miniconda.html), una distribución ligera de conda. Otra manera popular de instalar conda es a travez de la distribución [Anaconda](https://www.anaconda.com/products/distribution), que pre-instala una gran cantidad de paquetes comunes de Python. Recomendamos Miniconda porque se instala más rápidamente, requiere menos espacio en el disco, y promueve la inclusión selectiva de los paquetes necesarios para proyectos específicos en entornos bien definidos.

En estos tutoriales iniciales no profundizaremos sobre conda más allá de lo necesario. Entraremos en más detalles durante el hackatón. Si quieres aprender más, visita los enlaces al final de esta página.

### Instalar Miniconda

Incluimos instrucciones breves para instalar Miniconda.

#### Windows

En la página https://docs.conda.io/en/latest/miniconda.html, bajo "Latest Miniconda Installer Links", baja el instalador `Miniconda3 Windows 64bit`. Si tu computadora es vieja, tal vez la versión 32bit es la indicada. En Windows 10:

- Haz doble clic en el archivo instalador después de bajarlo.
- Selecciona la opción para instalar como usuario local solamente (local user only).
- Acepta la ruta (*path*) de archivos de instalación de defecto, que probablemente será: `C:\Users\MIPERFIL\miniconda3`
- En la ventana "Advanced Installation Options", remueve la selección de ambas cajas ("Add Miniconda3 ..." y "Register Miniconda3 ...")
- En la ventana "Completing Miniconda3", remueve la selección de ambas cajas.

Cuando la instalación ha concluído, abre el "Anaconda Powershell Prompt" desde el menú de Start. Puedes comprobar que funciona bien corriendo el comando `conda list`.

### macOS o Linux

En la **terminal** (*shell*, generalmente la terminal tipo "bash"):

```bash
# En macOS
url=https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
# En Linux
url=https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

wget $url -O miniconda.sh
bash miniconda.sh -b -p $HOME/miniconda3
```

Si el instalador te pregunta si quieres que inicialize Miniconda3 corriendo `conda init` ("Do you wish the installer to initialize Miniconda3 by running conda init?"), selecciona "yes". Si concluye sin hacer esa pregunta, ejecuta el siguiente comando: `./miniconda3/bin/conda init`. Por último, ejecuta el comando `conda update conda --yes`

### New details on adding libmamba to conda
(From Don's Slack message, July)

Please do the following for your conda to use the latest `conda` version and also install the `libmamba` solver for `conda`, so that you don't need to use `mamba` directly. Note that you only need to do this ONCE:

```bash
# updates conda to latest version
conda update -n base conda

# installs the libmamba solver
conda install -n base conda-libmamba-solver

# set the solver as default
conda config --set solver libmamba
```

If you need to use the classic conda solver for some reason such as backwards compatibility (not recommended, only for long living conda environment), simply use the --solver flag when installing packages like so:

```bash
# use classic solver
conda install numpy --solver=classic 
```

For detailed explanations about this and the technical details, you can go to: https://conda.github.io/conda-libmamba-solver/

### Filipe's OHW23 tutorial / presentation
(from https://github.com/oceanhackweek/ohw-tutorials/blob/OHW23/00-Mon/README.md)

Software installation survival guide (conda and friends)