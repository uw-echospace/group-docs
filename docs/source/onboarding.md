# Echospace Group Onboarding

You are welcome to contribute to this guide. What will be useful to your future colleages?

### Computing Infrastructure:

* **Personal computers**: this works for building prototypes and when not working with big data
	* Advantages: you have good control over the programs you can install 
	* Disadvantages: limits the resources on your computer, code may eventually not work on another computer
* **[Google Colab](https://colab.research.google.com/)**: provides notebook environment with 16GB RAM and GPU support
	* Advantages: free, lots of preinstalled packages
	* Disadvantages: fixed python version, pip install only, some features don’t work as on standard Jupyter notebooks
	
	Please store your notebooks in the joint drive relevant to your project
	
* **Cloud Resources**: depending on your project needs, we may be able to provide some cloud computing resources
	* Advantages: you can outsource long-running jobs or big data jobs from your computer
	* Disadvantages: it takes some time to set up 
	
* **[Binder](https://mybinder.org/)** provides an option to run a notebook from a github repo and execute it in temporary environment. You may need provide a `requirements.txt` file. If you need environment for distributed computing, you can also try [Pangeo Binder](https://binder.pangeo.io/)
	* Advantages: it works well for demos
	* Disadvantage: the resources are limited

* [**Pangeo Clusters**](https://pangeo.io/): depending on your project, you may get access to use a community notebook environment with a cluster support
	* Sign up for using Pangeo [here](https://docs.google.com/forms/d/e/1FAIpQLSeqKncKG-s365pC_Lfe4_UetJ-wcFfjOSyHhYYQjXbKRHzswQ/viewform)
	* Link to log on: [http://aws-uswest2.pangeo.io/](http://aws-uswest2.pangeo.io/)

* **APL Remote Desktop** (8 cores): some more expensive processing can be done there if needed, ask Wu-Jung to get set up.


### Programming Setup: Anaconda Python, Jupyter, Git/GitHub
* [Setup Guide](https://github.com/uw-echospace/group_docs/blob/main/conda_jupyterlab.md)
* [Software Carpentry Setup](https://carpentries.github.io/workshop-template/#setup)


### Version Control: 
To ensure access and reuse of the developed software, code should be developed under version control. We use git & Github. The group’s Github organization is: [https://github.com/uw-echospace](https://github.com/uw-echospace) 

Some packages are also developed under:
[https://github.com/OSOceanAcoustics](https://github.com/OSOceanAcoustics)


If you do not have experience with version control: consider signing up for a Software Carpentry workshop which are usually taught during each quarter at the eScience Institute (sign up [here](https://escience.washington.edu/get-involved/) for announcements), or go through some tutorials on your own. The [Atlassian Tutorials](https://www.atlassian.com/git/tutorials/what-is-version-control) have great visuals!

Provide us with your Github username (sign up for an account [here](https://github.com/login)).

Your repo should have a `README.md` which explains what the project is about.

Make sure you are never uploading any private/big datasets to Github (keep in mind sometimes jupyter notebooks/plots store your data: clean cell output to avoid problems). You can use `.gitignore` in your repo to prevent from adding certain types of files. Also, avoid using `git add -A`.

If you work on a project with other people, decide on a collaboration policy. Here are some examples: [Collaboration Workflows] (https://www.atlassian.com/git/tutorials/comparing-workflows).

Your code should also have a license (code published online without a license cannot be used by others).  Here is some advice about picking a license:

[https://choosealicense.com/licenses/](https://choosealicense.com/licenses/)

Here are some licenses that we have used before:
Apache 2, MIT, BSD.



### Virtual Environments:

Having one’s code is not sufficient to rerun their experiments: everybody knows that. Having the right computational environment is crucial for running the programs and accessing the necessary data sets.

If you are using Python there are very helpful tools to help you manage the packages you are installing. We recommend using an Anaconda Python Distribution which already comes with a package manager. You can install packages with the `conda install` command. Keep a separate conda environment for every subproject. Ideally you should list on the README of your repo what packages are required. You can create a requirements.txt file and store it, so that others can easily install all the packages. For a thorough guide on virtual environments:

[https://conda.io/docs/user-guide/tasks/manage-environments.html](https://conda.io/docs/user-guide/tasks/manage-environments.html)

There are more language independent tools to abstract environments: such as Docker. Docker can be useful when you need non-Python dependencies. Note that sometimes even Python packages require for example separate independent libraries to be preinstalled (like gdal, ffmpeg, etc). Here is a tutorial on Docker: 

[https://carpentries-incubator.github.io/docker-introduction/](https://carpentries-incubator.github.io/docker-introduction/)

### Data Sharing: 

We like sharing data when possible. This requires understanding the conditions under which the data are acquired and the implications of sharing the data under certain licenses. Ask us regarding the conditions of sharing the data if not sure.

While you are working on your project you can identify also intermediate versions of the data which can be useful when shared with the community: discuss your ideas with us (you do not have to always wait for the final result). Keep your data as organized as possible so you do not have to fix it when on a vacation in Hawaii.

Data sharing resources:

* [Zenodo](https://help.zenodo.org/)
* [Dryad](https://datadryad.org/)
* [IEEE Data Port](https://ieee-dataport.org/)
* [https://www.nature.com/sdata/policies/repositories](https://www.nature.com/sdata/policies/repositories)


### Code Documentation:

Follow simple rules to document your code:

* Each function should have a docstring.
* Each file should have a docstring.
* Each class should have a docstring.
* Each function and script should have example calls.

For more conventions on Python documentation read below:
[PEP 8 Style Guide](https://www.python.org/dev/peps/pep-0008/)

You can use linters to check if your code follows the right style:
[https://pylint.readthedocs.io/en/latest/intro.html](https://pylint.readthedocs.io/en/latest/intro.html).

Some editors have built-in linting functionality (such as [Visual Studio Code](https://code.visualstudio.com/), [Atom](https://atom.io/), [PyCharm](https://www.jetbrains.com/pycharm/)).


### Code Publication:

Sometimes your code can be useful beyond the application you had in mind. It can be helpful to publish description of it in domain-agnostic journals. Some examples:
* [Journal of Statistical Software](https://www.jstatsoft.org/index)
* [Journal of Open Source Software](https://joss.theoj.org/)


### Progress Documentation: 

Decide on a strategy to record your progress (you will be thankful to yourself in the future):

* Nuclino
* Github’s repo Wiki
* Github’s repo Issues & Task Lists
* gh-pages website/blog
* Jupyter Notebooks
* Google Doc
* ...

Provide your mentor's with a link to your updates.


### Useful Classes/Lecture Materials:

* Software Engineering for Data Scientists: [http://uwseds.github.io/](http://uwseds.github.io/)
* [CSE 160&163] Introductory and Intermediade Data Programming
* [CSE/STAT 416 Introduction to Machine Learning](http://courses.cs.washington.edu/courses/cse416/)
* 2019 Oceanhackweek Lectures: [https://oceanhackweek.github.io/curriculum_2019.html](https://oceanhackweek.github.io/curriculum_2019.html)
* [Software Carpentry Lessons](https://software-carpentry.org/lessons/)


### Mailing Lists:
* [eScience Mailing list signup](https://escience.washington.edu/get-involved/)
* School of Aquatic and Fisheries Sciences [Quantitative Seminar](https://fish.uw.edu/news-events/seminar-series/quantitative-seminar/) 
* [Oceanography seminars](https://www.ocean.washington.edu/events)

### Events to attend:
* [Ocean Sciences Meeting](https://www.aslo.org/osm2022/)
* [Acoustical Society of America (ASA) Meetings]()
* [American Geophysical Union (AGU) Fall Meeting](https://www.agu.org/Fall-Meeting)
* [Federation of Earth Science Information Partners (ESIP) meetings](https://www.esipfed.org/meetings)
* [SciPy](https://www.scipy2021.scipy.org/)
* [PyCon](https://us.pycon.org/2021/)
* [PyData](https://global.pydata.org/)
