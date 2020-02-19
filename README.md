# Samples-RecordMapper
This repository contains a sample production that transforms delimited text files into fixed-width text files using a record map. Additionally, the repository contains sample data. You can load the production into your InterSystems IRIS instance and use the sample data to interact with the Record Mapper tool.
The repository illustrates the concepts described in "Using the Record Mapper:"
https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=EGDV_recmap

---

## SET UP
To load the production, you must have an InterSystems IRIS instance. To obtain an instance, go to [Get InterSystems IRIS](https://learning.intersystems.com/course/view.php?name=Get%20InterSystems%20IRIS).

---

## LOAD AND START THE PRODUCTION 
1) Clone this repository: `git clone https://github.com/intersystems/Samples-RecordMapper`
2) Create a production-enabled namespace or enable the USER namespace for productions using the InterSystems Terminal as follows: 
	`do ##class(%Library.EnsembleMgr).EnableNamespace("USER")`
3) Navigate to System Explorer > Classes and import data/Demo_RecordMap_Production.xml.
4) Navigate to Interoperability > List > Productions and open Demo.RecordMap.Production.
5) Change the File Path for Delimited.RecordMap.FileService to <repo home>/data/In, Archive Path to <repo home>/data/SampleFiles/. Ensure that you click Apply to save your change.
6) Change the File Path for Delimited.RecordMap.BatchOperation to <repo home>/data/Out. 
7) Change the File Path for FixedWidth.RecordMap.FileOperation to <repo home>/data/Out.
6) Click Start to start the production.

---

## REVIEW THE INPUT AND OUTPUT DATA
 
1) Load and start the production.
2) Navigate to Interoperability > View > Messages to review the message that you passed in when you started the production. For more information, see "Viewing, Searching, and Managing Messages:"
https://docs.intersystems.com/irislatest/csp/docbook/Doc.View.cls?KEY=EMONITOR_message
3) Optionally, pass another message in by copying RecordMap_Delimited_FL from the <repo home>/data/SampleFiles folder to the <repo home>/data/In folder.

---

## REVIEW THE RECORD MAPS
1) Load the production.
2) Navigate to Interoperability > List > Record Maps.
3) Open Demo.RecordMap.Map.Delimited or Demo.RecordMap.Map.FixedWidth.