[![Esri Canada](images/ER_EN.png "Esri Canada")](https://hed.esri.ca)
# Python for ArcGIS - Working with ArcGIS Notebooks
#### Tutorial for ArcGIS

---

## Quick Reference:

* Tutorial Overview (this document): [Word](ArcGIS_Notebooks_Tutorial.docx) | [PDF](ArcGIS_Notebooks_Tutorial.pdf)
* ArcGIS Notebook Basics:
    * [`starter_notebook.ipynb`](notebook_basics/starter_notebook.ipynb)
    * [`arcgispro_notebook.ipynb`](notebook_basics/arcgispro_notebook.ipynb)
    * [`hosted_notebook.ipynb`](notebook_basics/hosted_notebook.ipynb)
* Data Science with ArcGIS Notebooks:
    * [`part1_prepare_hurricane_data.ipynb`](hurricane_analysis/part1_prepare_hurricane_data.ipynb)
    * [`part2_explore_hurricane_tracks.ipynb`](hurricane_analysis/part2_explore_hurricane_tracks.ipynb)
    * [`part3_analyze_hurricane_tracks.ipynb`](hurricane_analysis/part3_analyze_hurricane_tracks.ipynb)

## Tutorial Overview

This tutorial introduces you to using Python code in a Jupyter Notebook, an open source web application that enables you to create and share documents that contain rich text, equations and multimedia, alongside executable code and visualization of analysis outputs.  The tutorial begins by stepping through the basics of setting up and being productive with Python notebooks.  You will be introduced to ArcGIS Notebooks, which are Python Notebooks that are well-integrated within the ArcGIS platform.  Finally, you will be guided through a series of ArcGIS Notebooks that illustrate how to create compelling notebooks for data science that integrate your own Python scripts using the ArcGIS API for Python and ArcPy in combination with thousands of open source Python libraries to enhance your analysis and visualization.

### Learning Outcomes
By completing this tutorial, you will become comfortable with the following skills:
* Setting up Jupyter Notebook server and different variations of ArcGIS Notebooks,
* Basic interaction with a notebook, and techniques for using them effectively, and
* Composing effective notebooks for data science.

### Time Required
The following time is required to complete this tutorial:
* Two hours

### Materials Required

#### Technology:
* *Required*: This tutorial was last tested on August 27th, 2024, using `ArcGIS Pro 3.3`. If you're using a different version of ArcGIS Pro, you may encounter different functionality and results.
* *Recommended*: ArcGIS Online subscription account with permissions to use Notebooks and GeoEnrichment
* *Optional*: Notebook Server for ArcGIS Enterprise 11.3+ ([installation guide for administrators](https://enterprise.arcgis.com/en/notebook/latest/install/windows/welcome-to-the-arcgis-notebook-server-install-guide.htm))

#### Data:
* Sample data for this tutorial are included as part of the download.

#### Data Sources
* Toronto Police Service: Major Crime Indicators: https://data.torontopolice.on.ca/pages/major-crime-indicators
* NOAA National Centers for Environmental Information: NCDC International Best Track Archive for Climate Stewardship (IBTrACS) Project, Version 3:  https://data.nodc.noaa.gov/cgi-bin/iso?id=gov.noaa.ncdc:C00834

### Production Date
The Education and Research Group at Esri Canada makes every effort to present accurate and reliable information. The Web sites and URLs used in this tutorial are from sources that were current at the time of production, but are subject to change without notice to Esri Canada.
* Production Date: January 2022
* Last Update Date: August 2024

## Background Information
The Python programming language was first introduced to the ArcGIS community in 2004, with the release of ArcGIS version 9.0, as one of the scripting languages that provides access to the ArcGIS geoprocessing framework.  Since then, Python has become the language of choice for scripting and automation among ArcGIS users, and indeed many other applications.  At the same time, the ecosystem of Python libraries has continued to grow (e.g., NumPy or SciPy for advanced mathematical and scientific processing, or more specialized modules for integrating deep learning and machine learning tools such as Tensorflow).  With the introduction of the notebook interface, initially using IPython, and more recently with the Jupyter Notebook server, the Python language and specifically Python Notebooks have become highly valuable tools for data science.

While using Python notebooks with ArcGIS has been possible for many years, it has become a much more integrated experience with the release of the ArcGIS API for Python in 2016, and more recently Notebook Server for ArcGIS Enterprise (10.7.1 released in 2019), in ArcGIS Notebooks in ArcGIS Pro (starting in 2020 with version 2.5) and in ArcGIS Online (released in 2020).

By completing this tutorial, you will learn how to set up and interact with ArcGIS Notebooks, and how to load, analyze, and visualize GIS datasets in a Python Notebook to create a compelling document that communicates your GIS data processes or data science workflows for other developers.


#### References and Reading
* Introducing ArcGIS Notebooks
https://www.esri.com/arcgis-blog/products/arcgis-enterprise/analytics/introducing-arcgis-notebooks/
* What's new in ArcGIS Pro (check with each release for updates to capabilities with ArcPy and ArcGIS Notebooks in ArcGIS Pro): https://pro.arcgis.com/en/pro-app/latest/get-started/whats-new-in-arcgis-pro.htm#ESRI_SECTION1_546A5C8048144FC595A58DAA6F9EBF47
* ArcGIS Blog (check regularly for posts about new capabilities of ArcGIS Notebooks across the ArcGIS System): https://www.esri.com/arcgis-blog/?s=#arcgis%20notebooks


## Tutorial Folder Contents

The following table summarises the required folders and files provided with this tutorial – copy these files to your hard drive. The location should have a simple and easy to find path that does not include spaces or special characters. With these files copied to your hard drive, and with ArcGIS Pro optionally licensed for offline use, you will be able to complete the entire tutorial without a connection to the Internet (portions that require ArcGIS Online services can be skipped).  All references to files later in this document will be relative to the top arcgis_notebooks folder:

| Folder Name / File Name | Description |
| - | - |
| `arcgis_notebooks/` | Top folder |
| `+- documents/` | Related tutorial documents |
| `+- hurricane_analysis/`	| Sample Python notebooks - hurricane track analysis |
| `\|  +- data/` | Pre-packaged sample data and required files |
| `\|  +- part1_prepare_hurricane_data.ipynb` | Part 1: Data wrangling
| `\|  +- part2_explore_hurricane_data.ipynb` | Part 2: Data exploration and analysis
| `\|  +- part3_analyze_hurricane_data.ipynb` | Part 3: Statistical correlation analysis
| `+- notebook_basics/` | Sample Python notebooks |
| `\|  +- data/` | Pre-packaged sample data and required files |
| `\|  +- starter_notebook.ipynb` | Basic overview of working with Jupyter Notebook |
| `\|  +- notebook_basics.aprx` | ArcGIS Pro project configured for working with the `arcgispro_notebook.ipynb` notebook |
| `\|  +- arcgispro_notebook.ipynb` | Overview of notebooks integrated into ArcGIS Pro |
| `\|  +- hosted_notebook.ipynb` | Overview of notebooks in ArcGIS Online/Enterprise |


## Part A: Getting Started
First, ensure that you have the following software installed:
* ArcGIS Pro 3.3
  * If necessary: obtain a trial copy of ArcGIS Pro (https://www.esri.com/en-us/arcgis/trial)
  * Optional: authorize ArcGIS Pro for offline use (https://pro.arcgis.com/en/pro-app/get-started/start-arcgis-pro-with-a-named-user-license.htm#ESRI_SECTION1_15AD453E27C446CE9B51D45C021E8067)

With ArcGIS Pro installed and licensed, prepare a clone of the default Python environment installed with ArcGIS Pro. To do this use the following steps:
1. Open the ArcGIS Pro settings (or when working on a project in Pro, click the Project tab)
2. Select Package Manager in the left-hand menu to access the Python Package Manger interface
3. On the right-hand, Click the Environment Manager button ![Gear_button.png](images%2FGear_button.png), the Environment Manager dialog box appears.
4. Click the clone button next to the default environment named arcgispro-py3, and enter a name for your new environment and click Clone in the following prompt.
5. Wait for the clone operation to complete, ensure that your new cloned environment is set as active, and close ArcGIS Pro.
6. Now that you have a cloned copy of the default ArcGIS Pro Python environment, you are free to modify it as you see fit.  This tutorial will make use of several packages that are not installed by default. Double-click a row representing the environment you want to activate. 
7. To install these, open the Python Command Prompt installed with ArcGIS Pro (Windows Start Menu > ArcGIS > Python Command Prompt).  When the command prompt opens, you should see the name of the Python environment you just cloned in ArcGIS Pro to the left of the cursor and current path.  Ensure your PC is connected to the Internet, execute the following command, answer 'y' when prompted to confirm the installation:

```py
conda install dask python-graphviz seaborn
```

Executing this command will install additional open source packages that are used in some of the sample notebooks included in this tutorial.

***Note:*** *if you are working with ArcGIS Pro version 2.5 or 2.6, you can optionally execute the following commands to install additional packages that enable additional configuration options in the Python Notebook environment:*

```py
conda install jupyter_contrib_nbextensions
conda install jupyter_nbextensions_configurator
```

This installation process will take some time to complete, depending on your Internet connection and PC's hardware capacity.  If you see any warning messages, you can safely ignore them. ***Do not close the command prompt until the process is completed***, and the command prompt has returned (with the blinking cursor visible).  When the process is completed, you can proceed to the next section to open the Jupyter Notebook server.

8. Once you have completed the installation of the above packages, you will want to lunch the Jupyter Notebook in the current drive and directory to the folder on your hard drive that contains the files for this tutorial copied earlier. You can do this with the following commands (adjust the drive letter and path to the `arcgis_notebooks` folder in the first two commands as appropriate):

```sh
D:\
cd D:\arcgis_notebooks
jupyter notebook
```

The last command above will launch the Jupyter web interface in your default Web browser, and you will see a view of the contents of the `arcgis_notebooks` directory.

8. Consider enabling the table of contents extension in Jupyter by navigating to the 'Nbextensions' tab in the Jupyter web interface, and clicking the checkbox next to the 'Table of Contents (2)' item (if this checkbox is greyed-out, you may need to uncheck the option near the top labelled 'disable configuration for nbextensions without explicit compatibility').

With the 'Table of Contents (2)' extension enabled, you can easily navigate within your notebooks using an interactive table of contents that displays and synchronizes with headers in Markdown cells of your notebook.

## Part B: Python Notebook Basics
For this portion of the tutorial, you will start by reviewing basic aspects of the Python Notebook environment, how to compose rich text and multimedia, and how to interact with code to execute Python commands and visualize outputs.

### Using the Jupyter Notebook Web interface:
1. Within the web interface launched at the end of the steps in Part 1 (above), navigate into the `notebook_basics` folder, and open the
`starter_notebook.ipynb` file.
***Note:*** You can always show or hide it by clicking on the table of content icon located in the menu bar on the top of the webpage.
    * At this point, you may choose to open the `documents/Jupyter_Cheatsheet.pdf` document, and keep it open for reference as you work with your notebooks in the Jupyter environment.
    * For a tour of the notebook interface, you can select 'User Interface Tour' in the Help menu.
2. To start the notebook from scratch, you can choose "Restart & Clear Output" from the Kernel menu.
3. You can follow the notebook by running code inside each code block in one of the following ways:
    * Select a cell with Python code in it and do one of the following:
        1. Click the 'Run' button in the main toolbar.
        2. Press CTRL+Enter
        3. Press SHIFT+Enter (this automatically selects the next cell; repeat the SHIFT+Enter keystroke to execute multiple cells in sequential order)
        4. In the main Cell menu at the top, select one of the 'Run ...' options.

***Note:*** *one of the code cells in the `starter_notebook.ipynb` notebook will deliberately generate an error, so this notebook will not successfully run if you choose the 'Restart & Run All' option from the 'Kernel' menu.*

### Using ArcGIS Pro:
4. Open the `notebook_basics.aprx` project file located in the `notebook_basics` folder in ArcGIS Pro.  In the Catalog pane, expand the Folders item, then the `notebook_basics`, then right-click on the `arcgispro_notebook.ipynb` file and choose 'Add To Project'.  Expand the 'Notebooks' item in the Catalog pane, then double-click on the notebook file to open it.
5. Once the notebook is opened in ArcGIS Pro, you can follow its workflow by executing the code cells as described in step 3 above, or optionally choose 'Restart & Run All' option from the 'Kernel' menu. Before selecting 'Restart & Run All,' ensure that the Major Crime Indicator has been added to your content, as described in "Accessing layers in an active Map" Section of the notebook. [Add Crime Indicator Data](notebook_basics/arcgispro_notebook.ipynb)

***Note1:*** *If you can't view the Map and the Notebook side by side, you can dock the Notebook next to ArcGIS Pro by dragging and aligning the windows manually.*

***Note2:*** *Some of the code in this notebook includes processes that consume credits with ArcGIS Online services, and some may take a long time to execute.  If you prefer to skip any of these steps, do not choose the ‘Restart & Run All’ option from the ‘Kernel’ menu, and refer to the corresponding instructions included in the notebook.*

### Using ArcGIS Enterprise or ArcGIS Online:
6. Open a web browser and login to your ArcGIS Online organization with an account has access to advanced notebooks (currently in beta for ArcGIS Online), or login to your ArcGIS Enterprise portal that has a Notebook Server enabled with it (this must be installed and configured by your ArcGIS Enterprise administrator).
7. Navigate to the Content section and click 'New Item' (or 'Add Item' -> 'From my computer' for older versions of ArcGIS Enterprise).  In the dialog that appears drag and drop the the `hosted_notebook.ipynb` file from the `notebook_basics` folder and enter one or more tags.
8. At the bottom of the dialog, there will be a drop-down box that allows you to select which ArcGIS Notebooks runtime you want to use to run the notebook.  By default, this will be set to 'ArcGIS Notebook Python 3 Standard - [version number]'.  Change this to 'ArcGIS Notebook Python 3 **Advanced** - [version number]'.  The Advanced runtime gives you access to the ArcPy library, which is needed for this notebook.
    * If you are running an older version of ArcGIS Enterprise and do not see this drop-down box at the bottom of the dialog, you can change the notebook runtime in the next step below.
    * If you do not see an option for the Advanced runtime in this drop-down box, please contact your ArcGIS Online or ArcGIS Enterprise administrator.
9. At the bottom of the dialog, click 'Save' or 'Add Item'.  When your notebook has been uploaded as a new item in your content, you will be taken to its details page.
    * If you were not able to set the notebook runtime in the previous step, click the 'Settings' tab near the top of the details page, scroll down, and there will be a drop-down box that will allow you to change the runtime.  Choose the latest version of the 'Advanced' runtime.  When finished, click the  'Overview' tab near the top of the page.
10. Click the 'Open Notebook' button near the top of the details page to launch the hosted notebook in your web browser.
11. Follow this notebook by reading the Markdown text cells, and executing code cells as described in step 3 above, or optionally by choosing the 'Restart & Run All' option from the 'Kernel' menu.

***Note:*** *Some of the code in this notebook includes processes that consume credits with ArcGIS Online services, and some may take a long time to execute.  If you prefer to skip any of these steps, do not choose the ‘Restart & Run All’ option from the ‘Kernel’ menu, and refer to the corresponding instructions included in the notebook.*

## Part C: Data Science with ArcGIS and Python Notebooks
In this section of the tutorial, you step through a series of thee notebooks that demonstrate how different stages of an end-to-end data science workflow can be created using ArcGIS Notebooks. These notebooks have been adapted from a set of [sample notebooks](https://www.arcgis.com/home/search.html?q=Hurricane%20analysis%20owner%3A%22ArcGISPyAPIBot%22&focus=notebooks) prepared by Esri that prepare and analyze hurricane track data using GeoAnalytics in ArcGIS Enterprise.  For this tutorial, they have been adapted to use the GeoAnalytics toolbox in ArcGIS Pro, enabling the analysis to be completed on a desktop PC with ArcGIS Pro installed.

The stages of the data science workflow demonstrated in this series of notebooks begin with data preparation (or 'data wrangling') in the first notebook.  This is followed by data exploration in the second notebook, and finally correlation analysis in the third notebook.

Complete the following steps to work through the three notebooks for this section of the tutorial:
1. Launch the Jupyter Notebook web interface (by opening the Python Command Prompt, changing to the arcgis_notebooks folder, and executing the jupyter notebook command – as described in Part A of this tutorial), navigate into the `hurricane_analysis` folder, and open the `part1_prepare_hurricane_data.ipynb` file.
2. Optionally, restart the kernel and clear all output in the notebook (if you do not, previous outputs remain visible).
3. Follow the instructions within the notebook as you did in the previous Python Notebook Basics section of the tutorial.
4. Repeat steps 1-3 above for the `part2_explore_hurricane_tracks.ipynb` and `part3_analyze_hurricane_tracks.ipynb` notebooks.

***Note:*** *Some of the code in these notebooks includes processes that consume credits with ArcGIS Online services, and some may take a long time to execute. If you prefer to skip any of these steps, do not choose the ‘Restart & Run All’ option from the ‘Kernel’ menu, and refer to the corresponding instructions included in the notebooks.*

## Summary
After completing this tutorial, you have learned how to work effectively with Jupyter Notebook to create documents that enable you to write and execute Python code interactively, visualize analysis outputs, and provide detailed narration using rich text and multimedia written in Markdown syntax.  In Part B of the tutorial, you gained basic skills for using Jupyter Notebook server as a standalone application in Python, or as an embedded interface within ArcGIS Pro and ArcGIS Online / ArcGIS Enterprise.  You also learned how to integrate the capabilities of the ArcPy and ArcGIS API for Python libraries, alongside the capabilities of ArcGIS Pro and ArcGIS Online to create interactive and engaging ArcGIS Notebooks.

In Part C, you worked through a series of notebooks that demonstrate a complete end-to-end data science workflow for analyzing historical data for hurricanes.  In these notebooks, you used ArcPy, the ArcGIS API for Python, open source Python libraries, and ArcGIS Online within a cohesive 3-part series of notebooks that demonstrate and articulate the data processing and analysis outputs throughout the exercise.

## Future Considerations
You now have a good understanding of how to create ArcGIS Notebooks, and how they can be an effective medium for presenting detailed data processing and analysis workflows for data science. The next step is to consider how you can apply these skills to your current or future work.  If you are processing or analyzing data for a project and need to document your workflows to share the results to others, consider adapting your work into the Jupyter Notebook environment.  This will allow you easily to create and share notebook documents that show the exact methods you used so that it is easily repeatable for your own purposes as well as by others (i.e., the python code), with presentation of the results, alongside your explanation/interpretation with rich text and multimedia.

There are many additional examples and documentation sources available for you to learn more.  The resources listed at the end of this document are a good starting point for reference as you continue developing your skills to work effectively with ArcGIS Notebooks.

## Resources
* [ArcGIS API for Python](https://developers.arcgis.com/python/) (API reference, guides, sample notebooks)
* [Hosted ArcGIS Notebooks Samples](https://www.arcgis.com/home/search.html?q=owner%3A%22ArcGISPyAPIBot%22) by Esri:
* [ArcGIS Pro Python reference](https://pro.arcgis.com/en/pro-app/arcpy/main/arcgis-pro-arcpy-reference.htm) (ArcPy)
* [Jupyter Notebook project](https://jupyter.org/) (community, documentation, resources):
* [Coding Standards for Jupyter Notebook](https://www.esri.com/about/newsroom/arcuser/coding-standards-for-jupyter-notebook/)


© 2022 Esri Canada. All rights reserved. Trademarks provided under license from Environmental Systems Research Institute Inc. Other product and company names mentioned herein may be trademarks or registered trademarks of their respective owners. Errors and omissions excepted.
This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. The Education and Research Group at Esri Canada makes every effort to present accurate and reliable information. The Web sites and URLs used in this tutorial are from sources that were current at the time of production but are subject to change without notice to Esri Canada.

![CC-BY-NC-SA-4.0](images/CC-BY-NC-SA-4.0.png "CC-BY-NC-SA-4.0")
