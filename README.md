# HF_Calibration_Unit_Test
This repository stores the scripts to test the calibration mezzanines cards

# In the folder "bin" (path: HF_Calibration_Unit_Test/ngHCAL/bin/), there is a file called "update_runs"
This file upload runs taken from the servidor at 904 for the lxplus area.

To run this code, you need to do: ./update_runs

The files copied to Lxplus are stored in the folder called "dat" (path: HF_Calibration_Unit_Test/ngHCAL/QIE10_Testing/dat/)

# In the folder "dat" (path: HF_Calibration_Unit_Test/ngHCAL/QIE10_Testing/dat/), there is a file called "plot_maker_newversion.cpp"
This file is used to make plots from the data files (root files) stored in the same folder.
In the file, you can locate three big blocks of the code in the following order with the comments: " RMS(IC)/Mean(IC) vs Bias Voltage",  " LED A + LED B / LED(AB) " and "INTEGRATED CHARGED VS BIAS VOLTAGE". Each name refers to one kind of test performed with the pulser mezzanine cards.
You should start changing the run number in the file. Then, if you the plots be saved in other format you can add as was added for the PDF format.

To run this code, you should do: 

root -l -x -q plot_maker_newversion.cpp++
