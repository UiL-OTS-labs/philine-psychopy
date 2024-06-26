# Installing psychopy on lab-images

This is a small tutorial that documents how to make a PsychoPy-2023.2.3
experiment run on the pc's from the lab. This tutorial is written down
in order for Philine Link to run her experiments.

## System python-3.8.10

The lab pc's run python-3.8.10 at the moment, which is getting outdated. This,
writes down the dependencies that do not install as what you would expect when
installing with pip (The recommended way according psychopy documentation).

### working in a python virtual environment

The packages have to be installed in a way that is not disruptive for other
users of the lab pc's. So we recommend installing psychopy in a virtual
environment.

In the fragments below <name> has to be substituted with a appropriate
name for your experiment. Omit the <> characters. You might save your self
trouble by choosing a name without capital letters and special reading symbols
such as spaces.

```console
# go to the experiments folder
cd ~/Desktop/Experiments
# create an directory folder for your experiment
mkdir <name>
# Go to to your folder
cd name
# create the virtual python enviroment
python -m venv venv
# activate the environment
source venv/bin/activate
```

### Installing dependencies

It's important to install the dependencies before installing psychopy as
psycho doesn't mind older versions of e.g. PyQt. Note Qt is a C++ library
this is a bit harder to wrap than pure python libs.

In order to install anything on a lab pc you'll have to use a python virtual
environment. Open a terminal:

```console
# Newer version of pyqt refuse to install (likely a python-3.8 issue)
pip install pyqt5==5.15.7  # newer version cannot be build..
# It's handy to get a wheel for wxPython
pip install -U -f https://extras.wxpython.org/wxPython4/extras/linux/gtk3/ubuntu-20.04 wxPython
# install psychopy itself
pip install psychopy==2023.2.3
```

### Installing the experiment

Open firefox browser download the experiment/fetch it from a usb drive etc and
put the experiment inside of the Experiments/<name> 

## Running the experiment

These steps are added on how to run the experiment on a daily basis.
Assuming the steps above have succeeded. You have to activate the virtual
environment before running the experiment else psychopy won't be found, if 
you have just installed psychopy, the virtual environment will probably still
be active.

```console
# Go to your terminal
cd ~/Desktop/Experiments/<name>
source venv/bin/activate

# Use the psyhopy GUI
psychopy /path/to/fanfan_replication_new.psyexp
# Just run the script
python /path/to/generated_script.py
```
