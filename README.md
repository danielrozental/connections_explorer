# Connections Explorer
Qlik Sense Connections Explorer

## Summary

## Configuration

1. Log into QMC and Import apps
  - Connections Explorer.qvf
  - Connections Explorer Generator.qvf
  - Publish.qvf
  - Table Fields.qvf
  - Table Preview.qvf

2. Enable ODAG and Dynamic Views and hit apply

3. Optional Step Install and run [butler-spyglass](https://ptarmiganlabs.com/blog/2019/03/10/butler-spyglass-data-lineage-and-metadata-tool-for-qlik-sense/). Thanks to Göran Sander and PTARMIGAN LABS. 

If you don’t do this step Lineage information won’t be available.

4. Open a Qlik Sense app Connection Explorer Generator and create a new connection to your local PostgreSQL DB.

  - Host name: localhost
  - Port: 4432
  - Database: QSR

5. Configure the following variables and run the script

```
Let vQSRConnection = 'Local_PostgreSQL'; //The connection just created.
Let vExplorerFiles = 'LIB://QlikResource/CONFIG/CONNECTIONS_EXPLORER/QVD'; //Folder to store generated QVD files
Let vExplorerFilesLINEAGE = 'LIB://QlikResource/CONFIG/butler-spyglass-master/out/lineage'; //Folder where to find Lineage information generated with butler-spyglass-1.0.0
Let vConnectionsExcluded = '"AttachedFiles","Local_PostgreSQL","QLogs"'; //Any connections you’d like to exclude from Connection Explorer.
```

6. Open Connections Explorer and configure the following variable to the same value as the previous step.

```
Let vExplorerFiles = 'LIB://QlikResource/CONFIG/CONNECTIONS_EXPLORER/QVD';
```

7. In Connections Explorer create the following dynamic views
- Table Preview and add the Table Preview Dynamic View to the Table Preview Sheet
- Table Fields and add the Table Fields Dynamic View to the Table Fields Sheet

8. Create an on demand app navigation link and add it to the Table Preview sheet

9. Create an on demand app navigation link and add it to the Publish sheet

10. Enjoy!

## Help
daniel.rozental@itmaker.com.ar
