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

# Step 2: Build into the work space area a CMSSW version (verify which one)
cmsrel CMSSW version

cd CMSSW version/src

cmsenv

-> Copy the ngHCAL folder from this repository at github to the src folder. 

# Step 3: Update the runs
Once work area is set up, go to the folder "../src/ngHCAL/QIE10_Testing/bin", open the file "update_runs" and change your work space path before run it.
After this change, save the code and run the command: ./update_runs 

The runs will be uploaded in the public folder inside the work space area.


# Step 4: Analyze the runs
After the runs have been uploaded to the lxplus area, the next step is analyze them. That is done using the python code "QIE10_testing.py". The command used is:

cmsRun QIE10_testing.py # run number and number of suite (from the  QIE10_testing.info) # 

-> As an example, one has a data root file called: B904_Integration_'+runNumber+'.root'. 

You can analyze it doing:

cmsRun QIE10_testing.py 1000022166 7

As a result, the analized file will be stored inside the dat folder under the path: "../ngHCAL/QIE10_Testing/dat" with the name "QIE10testing_1000022166_7.root" .

Observation: The suite number has to do with which study will be performed. In our case, pulser studies, then the suite number is 7. Look at into the QIE10testing.info file.

# Step 5: Run the plot maker code over the analyzed root files
In the folder "dat" (path: ../ngHCAL/QIE10_Testing/dat/), there is a file called "plot_maker_newversion.cpp" .

This file is used to make plots from the data files (root files) stored in the same folder.
In the file, you can locate three big blocks of the code in the following order with the comments: " RMS(IC)/Mean(IC) vs Bias Voltage",  " LED A + LED B / LED(AB) " and "INTEGRATED CHARGED VS BIAS VOLTAGE". Each name refers to one kind of test performed with the pulser mezzanine cards.
In principle, you should start changing the "run number" in the beginning of the file. More precisely, this line:

----> int runs = {22798};

The "run number" can be identified in the root file name that one intends to run over like this: QIE10testing_1000022798_7.root

Then, if you want the plots be saved in other formats just add it as was added for the PDF format.

To run this code, you should do: 

root -l -x -q plot_maker_newversion.cpp++
