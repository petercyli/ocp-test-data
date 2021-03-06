# Omnibus Test Data

This application loads test data into Omnibus Care Plan (OCP) application. 

## Build

### Prerequisites

+ You need to build ocp-fis using a profile: mvn clean install -Pdata-load

### Commands

+ To build a JAR: run mvn clean install from the folder that contains pom.xml

## Run

### Prerequisities

+ Get the Excel file(available in resources folder) that contains the test data and place it in a folder.

+ Get the files for valuesets (available in resource folder) and place it in a folder. Replace the server url to point to your uaa server.

+ Get all the scripts from ocp-uaa/external-scripts in Github and place them in a folder. 

+ Create a file data.properties in the same folder as your jar file. Place the following contents;

`xlsxfile=/home/utish/Downloads/OCP.xlsx
valuesetsdir=/home/utish/Downloads/valuesets
scriptsdir=/home/utish/Downloads/external-scripts
fhirserverurl=http://localhost:8444/`

+ Replace the values for xlsxfile (path to Excel file above), valuesetdir (path to valueset files above), scriptsdir (path to scripts directory above), fhirsererurl (path to fhir server where you want to load the data) with your values.

+ Drop the old databases (both hapi and uaa) being used by the fhir server

+ Create two new databses (hapi and uaa)

### Commands

+ This should be run in a linux environment because the program invokes a linux shell to run the scripts.

+ Run the command: `java -jar ocp-test-data-<VERSION-NUMBER>.jar`. This will pull the data from excel file and valueset files and populate the data in the fhir server.

### Verify

+ Check the logs for errors.

+ Check the fhir database by access fhir URL (Eg: http://localhost:8080/fhir)