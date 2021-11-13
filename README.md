# Digital-Body-Farm

FILTER DRIVER INSTALLATION

(1) Turn off driver signing or turn on test signing to allow the filter driver to load.

(2) Unzip the Project folder.

(3) Fire up command propmt in administrative mode and navigate to the Project folder.

(4) Type bodyfarm.exe -install to install the program.

	(a) You may have to create an exception in your Antivirus program. 
  
	(b) If you get an error, its probably because your Antivirus is preventing the installation.
  
	(c) To check if it installed successfully, type sc query sectorinfo (sectorinfo is the name of the service the program runs).
  
(5) To uninstall type bodyfarm.exe -uninstall

RUNNING THE FILTER DRIVER PROGRAM/SECTORINFO SERVICE

(1) To start : Type bodyfarm.exe -start

(2) To stop: Type bodyfarm.exe -stop

(3) To check program/service state (RUNNING/STOPPED): Type sc query sectoinfo

NOTE

(1) Once the program starts up, a log file (delete.log) and folder (logs) will be created in the containing folder to hold information about every file 
    deleted from the system.
    
(2) An SQLite database file (sector.db) is also created to hold files of interest - specified in the config.ini file.

(3) To add more files to the list, just add the file extension to the config.ini file. You will have to restart the 
    program for the change to take effect.
    
(4) The program is currently set to insert files into the database if they are 10 MB and below. This setting can be adjusted in the config.ini file.

(5) To avoid data corruption, stop the driver/service before running the checker.

DELETING FILES

(1) Files should be deleted using ctrl+alt+del

(2) Sending files to the recycle bin does not constitute deletion - such files will not be monitored

(3) Files deleted from the recycle bin (emptying the recycle bin) will be monitored


RUNNING THE CHECKER PROGRAM

(1) The checker (Body_Farm_Checker.exe) is a python script compiled as an executable program. 

(2) The executable does not require python to be installed. However, it must be run with admin privileges.

(3) You may have to create an exception in your Antivirus program.

(4) You may try running the checker on a schedule using a task scheduling program that can run programs in administrative mode. Windows Task Schedular 
    did not do very well in this regard. Z-Cron did a better job, but requires some tweaking.
    
(5) Once run, the checker updates the database if it is found that any sectors/files have been overwritten on disk. 

(6) The checker creates a log in the logs folder, the log is updated each time the program runs. 

(7) The checker produces a pop-up notification, informing the user of the status of the program ie checking in progress, error occured, or checking complete.The 
    notification will not show up when the program is run on a schedule like if you use Z-Cron, it only shows up if you run it manually.
