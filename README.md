# Connections Explorer
Connections Explorer for Qlik Sense

## Summary

Qlik Sense Connections Explorer's main goal is to allow the user to explore and live query Qlik Sense QVDs files and ODBC Connections.

It also includes field, metadata and lineage information and allows you to publish QVDs to a blank QVF application.

## Connections Explorer Sheets
### Table Preview
Allows you to navigate to the QVD File/Table, get a limited rows/fields or full preview, make from to or particular selections on a field (e.g. category_id = 8). You can also create a new app out of a selected table using the Table Export ODAG button.

### Lineage
Lineage allows you to select a particular QVD and see what App is generating and what Apps are reading that file.

### Field Preview
Shows metadata information about QVD fields (max min avg count nulls).

### Publish
Allows the user to select multiple QVDs and publish them to a QVF through ODAG. It also shows what fields are present in multiple files and allows the user to select which of the will be qualified with the table name in order to avoid unwanted associations.

### QVDs
Shows all the QVDs in the Connections Folders and the last time each file has been read (Last time an App that reads that file has run) and written (File time).

### Metadata
Shows available metadata from QVD Files and Databases

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
