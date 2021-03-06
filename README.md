# KoL-Log-Parser
Python based log parser for kol

Original work all done by CaptainScotch and posted here https://github.com/docrostov/KOL-Log-Parser forked with his permission.

# Getting this to work
This is not meant to be a definitive guide to getting this to work, there are many ways, but if you know of others you probably don't need this guide.

First I am going to assume you are on Windows 10 and at least on version 1903 (May 2019 release) that is key because it enables certain features of WSL that you will need.

## Step 1 install WSL
First step is easy, open powershell as admin and type this command 

```dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart```

Once thats complete go to the Microsoft Appstore, download and install Ubuntu, then launch it. You should now be seeing a linux terminal. Setup a username and password and we are ready to start for real.

## Step 2 Install Python and Pip

in the terminal type the following commands
```
sudo apt update
sudo apt install python3-pip python3-dev

```

## Step 3 Setup a Environment for Jupyter

We need to start by installing a few things to make our environment work

```
sudo -H pip3 install --upgrade pip
sudo -H pip3 install virtualenv
```

Now that virtualenv is installed we can setup our environment. Run the following command to open explorer in you ubuntu home directory:
```
explorer.exe .
```
From here, make a new folder, I called mine parser, and download the contents of this repo and extract it into that folder. Go back to the terminal and type (again substituting parser for whatever you decide to name your folder)
```
cd parser
virtualenv parser
source parser/bin/activate
```
this should change your terminal prompt to look more user@somputer:~/parser$

## Step 4 Install Jupyter and this repos dependancies
```
pip install jupyter
pip install pandas
pip install requests
```
All right, now you are ready to install and use Jupyter Notebooks and this parser!

```jupyter notebook```

From there copy and paste the URL it provides into your browser. it will look something like this:
http://localhost:8888/?token=biglongstringornumbersandletter123456789

When you are ready to stop the notebook navigate back to your Ubuntu terminal and just hit CTRL+C

# What about the gosh darned parsing?
If you want to know more about how Jupyter works, go here:

https://jupyter.readthedocs.io/en/latest/architecture/how_jupyter_ipython_work.html


Otherwise lets just get to the good stuff.
If you click on KOLMafia RunLog Generator (v1.0).ipynb from within your jupyter notebook it will take you to a screen with a bunch of boxes (hereafter cells), each of these boxes can be run individually by clicking the run button, labled so, at the top of your screen. 

First you need to actually get your logs to a location that we can access them. Copy your logs somewhere onto your machine using the explorer.exe method mentioned above. If you are following along exactly with me I created a KoL folder in the same directory as my environment was set up in. Which would be:```/home/tbh/parser/parser/KoL/sessions```

Next in the cell starting with ``` class newLogParser():``` make sure to fill out the appripriate variables for:
```
            kolmafDir = '/home/tbh/parser/parser/KoL/',
            outputDir = '/home/tbh/parser/parser/KoL/',
            kolName   = 'threebullethamburgler',
```

Finally you need to run at least these cells, order matters.:
 ```
 import requests
 def zoneInformation(mafEnc,mafCom):
 # To minimize server hits, grab a few files from the Mafia SVN data
 class newLogParser():
 def resourcesByZone(log)
 ```

 After that just use the following formula:
 
 ```
runlog = newLogParser(runDates=['20200510','20200511','20200512','20200513'],zInfo=zoneInfo).prepareNewLog()
resourcesByZone(runlog).to_csv('runlogLocationSummary.csv')
 ```
 Filling in appropriate run dates for the session logs provided. It should create 2 files, one for the turn by turn summary and a second location summary that breaks down resources by zone. 
 
 ## Other misc stuff
 
 There are also currently some other goodies in the KOL Log Wrapper v2.1 (DG) notebook including some initial Pizza support. 
 
 
 # TODO
 Fix Output directory handling
 
 Finish supporting current IoTM
