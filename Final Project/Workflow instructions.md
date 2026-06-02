# Workflow Instructions

## Python instructions:

The code to execute the workflow runs in Python and is accessible as a python document in the repository (nypd_officer_360.py). The python document contains a link to a Google Colab notebook at the top, which can be used to view and copy the code in that application. The code can also be copy and pasted into a Python notebook in another application. 
Due to access restrictions, any changes made to the notebook in Colab will not save unless a copy is made. Making a copy immediately is recommended. 
The required libraries are listed here and at the beginning of the code: 
 
import requests  
import pandas as pd  
import io  
import matplotlib.pyplot as plt  
import seaborn as sns

* There are comments throughout the code to explain what is happening. The borough filter can be updated (Manhattan, Bronx, Queens, Staten Island, Brooklyn) to reflect different data. 
* The code can be adjust to include or exclude columns. 
* The code will generate a csv file. This can be saved and used as is, or opened in a spreadsheet viewer like Excel.
* Using the AirTable component is optional, but provides integrated metadata in the column headings. 
* Please note that for file size reasons, the code filters the original dataset to only display currently active officers. It is not recommended to use this workflow for research on officers who have retired from the NYPD. 

## AirTable instructions:

The resulting csv can be uploaded into AirTable through the following link (recommend opening in a new tab): https://airtable.com/appwE4Y7weLf9rSru/shr6hBM2WKjwuM6Ve

* A **copy base** button should appear in the top left corner of the screen, next to the "Interactive Data Explorer" title.
* The data can be uploaded by clicking on the carrot next to Manhattan Police Complaints
* Import data -> csv file (this will be the csv file you created using the python code above)
* The columns should automatically map to the pre-filled column headings, as long as no additional columns have been removed
* In "Other Settings" in the upload screen, toggle on "Exclude first row on import" to not duplicate column headings
* Note that AirTable has a limit of 50,000 records in one base. Filtering the data by borough should reduce the number of records to this amount
* If any further filtering or manipulation is done to the data in AirTable, the resulting information can be exported as a new csv file from AirTable

* Slide 10 of the PowerPoint presentation in the folder provides some useful screenshots for uploading the data into Airtable

## Note on Metadata
* Hovering over the i icon in each column header will reveal information about the data in that column
* Column metadata and other useful data can be found in the adjoining tables 
