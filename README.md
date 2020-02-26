# Samples-RecordMapper
This repository contains a sample production that reads data from delimited text files and writes the data to a fixed-width text file using record maps. Additionally, the repository contains sample data. 

You can load the production into your InterSystems IRIS instance and use it to explore the concepts described in [Using the Record Mapper](https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=EGDV_recmap).

---

## SET UP
To load the production, you must have an InterSystems IRIS instance. To obtain an instance, go to [Get InterSystems IRIS](https://learning.intersystems.com/course/view.php?name=Get%20InterSystems%20IRIS).

---

## COMPONENTS OF THE PRODUCTION

The production includes two business hosts:
- **`Delimited.RecordMap.FileService`:** Business service that consumes delimited text files in the `<repo home>/data/In` directory, maps each record in a file to a message, and passes the message to the `FixedWidth.RecordMap.FileOperation` business operation. 

	The names of the files must begin with `RecordMap_Delimited_`.
	
- **`FixedWidth.RecordMap.FileOperation`:** Business operation that consumes messages from the `Delimited.RecordMap.File.Service` business service, maps the fields in the messages to fields in a fixed-width text file, and writes the file to the `<repo home>/data/Out` directory. 

	The name of the output file is `RecordMap_FixedWidth_Output.txt`.

Additionally, the production includes two record maps for transforming data:
- `Demo.RecordMap.Map.Delimited`
- `Demo.RecordMap.Map.FixedWidth`

---

## LOAD AND START THE PRODUCTION 
1) Clone this repository: 

	`git clone https://github.com/intersystems/Samples-RecordMapper`
	
2) Create a production-enabled namespace, or enable the `USER` namespace for productions using the InterSystems Terminal as follows:

	`do ##class(%Library.EnsembleMgr).EnableNamespace("USER")`
	
3) In a production-enabled namespace in the InterSystems Management Portal, navigate to **System Explorer** > **Classes**, and import `<repo home>/data/Demo_RecordMap_Production.xml`.

	For instructions, see [Importing Classes](https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=ACLS_import).
	
4) Navigate to **Interoperability** > **List** > **Productions**, and open `Demo.RecordMap.Production`.
5) For `Delimited.RecordMap.FileService`, change the **File Path** value to `<repo home>/data/In` and the **Archive Path** value to `<repo home>/data/SampleFiles/`. 
	
	Ensure that you click **Apply** to save your changes.
	
6) For `Delimited.RecordMap.BatchOperation`, change the **File Path** value to `<repo home>/data/Out`. 
7) For `FixedWidth.RecordMap.FileOperation`, change the **File Path** value to `<repo home>/data/Out`.
6) Click **Start** to start the production.
 
---

## REVIEW THE INPUT AND OUTPUT DATA
 
1) Navigate to **Interoperability** > **View** > **Messages** to review the message that you passed in when you started the production.

	For more information, see [Viewing, Searching, and Managing Messages](https://docs.intersystems.com/irislatest/csp/docbook/Doc.View.cls?KEY=EMONITOR_message).
	
2) Optionally, pass another message in by copying `RecordMap_Delimited_FL` from the `<repo home>/data/SampleFiles` folder to the `<repo home>/data/In` folder.

---

## REVIEW THE RECORD MAPS
1) Navigate to **Interoperability** > **List** > **Record Maps**.
2) Open `Demo.RecordMap.Map.Delimited` or `Demo.RecordMap.Map.FixedWidth`.