# Connections Explorer
Qlik Sense Connections Explorer

## Summary

## Configuration

Log into QMC and Import apps
Connections Explorer.qvf
Connections Explorer Generator.qvf
Publish.qvf
Table Fields.qvf
Table Preview.qvf



Enable ODAG and Dynamic Views and hit apply


Optional Step Install and run butler-spyglass-1.0.0. Thanks to Göran Sander and PTARMIGAN LABS. 

If you don’t do this step Lineage information won’t be available.


Open a Qlik Sense app Connection Explorer Generator and create a new connection to your local PostgreSQL DB.




Configure the following variables and run the script

Let vQSRConnection = 'Local_PostgreSQL'; //The connection just created.

Let vExplorerFiles = 'LIB://QlikResource/CONFIG/CONNECTIONS_EXPLORER/QVD'; //Folder to store generated QVD files

Let vExplorerFilesLINEAGE = 'LIB://QlikResource/CONFIG/butler-spyglass-master/out/lineage'; //Folder where to find Lineage information generated with butler-spyglass-1.0.0

Let vConnectionsExcluded = '"AttachedFiles","Local_PostgreSQL","QLogs"'; //Any connections you’d like to exclude from Connection Explorer.

Open Connections Explorer and configure the following variable to the same value as the previous step.

Let vExplorerFiles = 'LIB://QlikResource/CONFIG/CONNECTIONS_EXPLORER/QVD';

In Connections Explorer create the following dynamic views
Table Preview
Table Fields
Add the Table Preview Dynamic View to the Table Preview Sheet
Add the Table Fields Dynamic View to the Table Fields Sheet

Create an on demand app navigation link and add it to the Table Preview sheet

Create an on demand app navigation link and add it to the Publish sheet


Enjoy!

## Help
daniel.rozental@itmaker.com.ar
