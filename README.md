# runupTool-Toolbox
A repository containing code and documentation to use the runupTool to digitize wave runup time stacks.

Background:

Runup is the time-dependent location of the land-sea boundary, i.e. the landward excursion of breaking waves on a beach. It is an important signal for a variety of reasons ranging from its diagnostic capabilities in studies of nearshore fluid dynamics to its role in dune erosion and overtopping. Digitization of runup is accomplished in a semi-automated way using the CIL tool runupTool. Input to runupTool is in the form of cross-shore time stacks, created as described in the document makingStacks.html. 

The basic assumption in automated runup digitization is that the runup edge will be of a lighter intensity than the underlying beach and that this contrast difference can be exploited to find runup edges automatically. Thus, the conceptual signal of interest is the intensity difference between any transect (time) and the intensity of the underlying, darker beach sand. The runup location is defined as the landward-most location where this difference exceeds a threshold. 

Operation:

When you type 'help {toolboxName}' where you insert your own toolbox name, will give the Contents of the toolbox.

This toolbox has been extracted from the full CIL version and SHOULD work on a standalone basis. In doing this, a number of checks have been removed since these depend on CIL databases and standards.

Demo files are provided as well as example data. 'demo_runupTool.m' sets the initial directory and paths in Matlab, and runs 'extractRunup_Timeseries.m'. 'extractRunup_Timeseries.m' sets the input and output paths, and runs  'runupTool.m'. This is currently set to analyze a test data set, '1578258000.Sun.Jan.05_21_00_00.GMT.2020.madbeach.cx.runup90.mat'. There are also two other example data sets that can be run ((b) 1510070340.Tue.Nov.07_15_59_00.GMT.2017.argus02b.cx.runup945.mat; (c) 1573920000.Sat.Nov.16_16_00_00.GMT.2019.madbeach.cx.runup90.mat).

runupTool.m needs the wave runup time stack; this is provided by specifying a data path, a date/time and the runup location (all this is handled by 'extractRunup_Timeseries.m'). Once the runupTool is executed a figure is produced which contains multiple image frames. The camera collects a ~17 minute video at 2 Hertz, which equals >2000 pixel lines that are stacked, which is then split into ~9 image frames. The automated line in the image frames can be edited by adjusting various parameters and manual clicks to digitize the wave runup line. See 'runupTool_userGuide.pdf' for a more thorough explanation of how to operate the tool. The output of the tool is a Matlab structure of the digitized runup line and includes parameters of the runup line file, camera name,  date/time, and position of the digitized runup line.

In addition to the main edit mode, there is an additional edit option at the end of 'extractRunup_Timeseries.m' in case an already digitzied line needs to be edited. Running the main body of 'extractRunup_Timeseries.m' loads the raw time stack, it does not open an existing, pre-edited digitized runup file. This edit mode must be activated manually.
