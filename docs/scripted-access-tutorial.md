# Scripted Flywheel Access

## Preliminaries

### Login

1. In Google Chrome, go to [flywheel.naccdata.org](https://flywheel.naccdata.org).
2. Click the button "University Credentials via CILogon"
3. Under "Select an Identity Provider" choose "University of Washington" and click the "Log On" button.
4. You should be taken to the UW login page and be asked to login using 2FA.

### Install a Python Environment

As a first step for using Jupyter notebooks, you'll need a Python environment installed on your computer.

If you are new to Python programming, we suggest following the steps from Software Carpentry to
[Install Python](https://swcarpentry.github.io/python-novice-inflammation/#install-python)
by downloading Anaconda.
This is an application that manages the Python environment for you.
Once Anaconda is downloaded, you will use the Anaconda Navigator.

### Creating your API Key

An API key allows you to access Flywheel programmatically.
It should be treated like a password, though you'll need to have a copy on your computer.

1. Find the "avatar" in the upper right corner.
   This is a circle with your initials.
2. Click the avatar dropdown, and select "Profile"
3. Under "Flywheel Access" at the bottom of the page, click "Generate API Key".
4. Set key name to "tutorial-access" and leave the expiration date set to a month away.
5. Make a copy of your API key and save it on your machine.

## First Notebook

We are going to start with an existing notebook.

1. Open [first-notebook source](https://github.com/naccdata/flywheel-tutorial/blob/main/notebooks/first-notebook.ipynb) in your browser.
2. Click the download icon ("Download raw file") to download the file.
   You'll need to note where your browser saves the file.
3. Open the Anaconda Navigator, and launch the Jupyter Notebook.
   (This is [illustrated on the Carpentries page](https://swcarpentry.github.io/python-novice-inflammation/#option-a-jupyter-notebook).)
   This will open a browser window with the Jupyter Notebook interface.
4. In the browser with the Jupyter Notebook interface, click `Files`, navigate to the downloaded `first-notebook.ipynb` file you just saved, and select the file.

### Anatomy of a notebook

A Jupyter notebook has "cells", each of which, for our purposes, can hold either text formatted using [Markdown](https://daringfireball.net/projects/markdown/), or code.
(See [Structure of a notebook document](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html#structure-of-a-notebook-document) for more detail.)

### Running the code

We are going to run the code cells one at a time.

Starting with the first cell that says `%pip install flywheel-sdk`

1. Click in the cell to select it
2. Click `Run` at the top of the notebook window.

If a cell has output, it will appear in an output cell in the notebook.

Keep selecting and running each successive cell.
You will need your Flywheel API Key for the cell under the `Connect to Flywheel` header -- you will be prompted for the API Key.
(Remember to treat the API Key like a password.)

## Learning more

1. [Jupyter Notebooks](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html)

2. [Software Carpentry](https://software-carpentry.org) Python Lessons
    - [Programming](https://swcarpentry.github.io/python-novice-inflammation/)
    - [Programming and Plotting](https://swcarpentry.github.io/python-novice-gapminder/)

3. [Flywheel Python SDK](https://flywheel-io.gitlab.io/product/backend/sdk/branches/master/python/getting_started.html)

4. [Software Carpentry Workshops at UW eScience](https://escience.washington.edu/data-science-learning/software-carpentry/)
