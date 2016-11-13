# HF_Calibration_Unit_Test
This repository stores the scripts to test the calibration mezzanines cards. 
In the following, the steps necessary are described.

# Step 1: Take the runs
First, one needs to set up the Run Control system to take runs.
Verify if any runs for the crate you intend to use are being taken. 
If it is available:
Choose the "key name": HF pulser study, sets up the number of events and mask the necessary crate.
Start to take runs.
-> The runs taken are stored at the 904 cluster. 

# Step 2: Update the runs
Once the runs were taken, one needs to upload them to the work area in the lxplus to analyze. For this, it is necessary to set up in the work area. There, inside the 




a CMSSW version (verify the current):

cmsrel CMSSW version
cd CMSSW version/src
cmsenv


-> Copy the ngHCAL folder from this repository to the src folder. (Add more info here)




# In the folder "bin" (path: ../ngHCAL/bin/), there is a file called "update_runs"
This file upload runs taken from the servidor at 904 for the lxplus area.
To run this code, you need to do: ./update_runs
The files copied to Lxplus are stored in the folder called "dat" (path: ../ngHCAL/QIE10_Testing/dat/)

# Step 3: Analyze the runs
After the runs have been uploaded to the lxplus area, the next step is analyze them. That is done using the python code "QIE10_testing.py". The command should be run is:

cmsRun QIE10_testing.py #number of the run and number of suite (from the  QIE10_testing.info) # 

-> As an example, one has a data root file called: QIE10testing_1000022166_7.root. You can analyze it doing:

cmsRun QIE10_testing.py 1000022166 7

# In the folder "dat" (path: ../ngHCAL/QIE10_Testing/dat/), there is a file called "plot_maker_newversion.cpp"
This file is used to make plots from the data files (root files) stored in the same folder.
In the file, you can locate three big blocks of the code in the following order with the comments: " RMS(IC)/Mean(IC) vs Bias Voltage",  " LED A + LED B / LED(AB) " and "INTEGRATED CHARGED VS BIAS VOLTAGE". Each name refers to one kind of test performed with the pulser mezzanine cards.
You should start changing the run number in the file. Then, if you the plots be saved in other format you can add as was added for the PDF format.

To run this code, you should do: 

root -l -x -q plot_maker_newversion.cpp++
