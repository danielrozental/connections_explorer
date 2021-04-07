# Connections Explorer
A new solution to your everyday problems

## Summary

- Why doesn't this record show up on the dashboard? 
- Is it not present at the source or was it lost in some intermediate process?
- Have all the necessary files been updated?
- What processes read or write this QVD?

If any of these questions sound familiar and you're tired of having to put together a new dashboard or access multiple files or query tools every time a question or problem arises, Connections Explorer may make your life a little easier.

In a dashboard made entirely in Qlik Sense (without extensions other than those provided in the installation package bundle) it allows you to directly browse and query the tables of the connections defined in Qlik Sense and the QVDs files. The user can choose the connection, table, file, fields to see, filter by a value or get all the records.

In addition, it adds metadata information, lineage and in case it is necessary to publish one or more QVDs to a new board without the need to write script or queries.

The dashboard and necessary scripts are provided as is free of charge. Download Link and more information. 

If you need help setting it up or want to include additional information, please contact us.

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
