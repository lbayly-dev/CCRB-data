# CCRB-data
An insight into NYPD Civilian Complaint Review Board (CCRB) data

## Project background and information story: 
This project came out of my experience working as a paralegal at the Manhattan District Attorney's Office. There were frequently acronyms and data that I did not understand, and had to find explanations for across different sources. Beyond merging three different csv files into one table, this project provides definitions for terms. These definitions are pulled together from what the NYC Open Data portal provides, NYPD documentation, and some of my own knowledge. 

When a police officer engages in misconduct against a civilian in New York City, the civilian can lodge a complaint with the Civilian Complaint Review Board (CCRB), who will investigate the claim. The data about these complaints is made public by New York City, and published throught the NYC Open Data Portal. 
This workflow allows the user to more easily see and understand data related to complaints made against New York City Police Department officers. Having easy access to this information is valuable for members of the community to be informed about the history of conduct of law enforcement in their area. Because of the current state of policing in the United States, having transparency around police conduct has become more important. It is useful when evaluating the presence of officers in a particular community, and can allow for members of that community to advocate for better policing practices. Being able to access this information easily can also empower people who have been victims of police misconduct to file a complaint with the CCRB, rather than remaining silent. 

## Project use:
**Current information structure:**

Currently, the data that provides information about NYPD officer conduct and the resulting allegations and complaints is spread out across three different datasets that are available through the NYC Open Data Portal. These datasets are downloadable as csv files, and the portal itself provides some quering capabilities. However, there is no option to combine the various datafiles into one place, which can make it harder to find information. For example, only the "Police Officers" file contains the names of the officers involved. The "Complaints" file does not include any information by which to identify the officer invovled in a complaint beyond a complaint ID, which has to be cross-referenced to the "Allegations" file. In files of this size, and using terminology that is not understandable to a lot of people, it can be an overwhelming task to find the relevant information. Therefore, creating an easier to understand information structure that has all the relevant information in one place is a valuable project. When information is hard to find and access, users are less likely to look at it. 

**Changes to information structure:**

The raw data is drawn from the NYC Open Data Portal (https://data.cityofnewyork.us/browse?q=Data-Collection_Data-Collection%3DCCRB+Complaints+Database&sortBy=relevance&pageSize=20&page=1), and configured uisng Python code. The resulting csv file can be uploaded into an AirTable, which includes descriptions for each column to provide additional context to the user, and make the data more understandable and usable. This final product provides a comprehensive overview of police officer information, allegations, and complaints, all in one place, rather than spread out across multiple files. This also allows for searches to be done across multiple different officer identifiers, such as Tax ID, shield number, last name, rank, or precinct. The AirTable presentation of the data also includes notes in the column headings to explain what the data in that column means, so that the user does not have to go and look for that information elsewhere. If the user chooses not to use the AirTable component of this project, they can also reference the data as csv files attached to this GitHub. Since the code automatically pulls the most recent data from the Open Data Portal, the user knows that they are working with the most up to date information, without having to manually download csv files. 
Therefore, this project amends the existing information structure in the following ways: 
* Information itself: data is filtered to only show what is relevant to the user. Comments throughout the code explain the modifications being made to the code, such as filtering only for officers that are active. The code can be adapted to the needs of the user, or run as is. 
* Access methodology: the data is no longer stuck in an overwhelming csv file, but can be viewed in a more easily understandable table through AirTable.

## How to use the workflow: 

**Python instructions:**

The code to execute the workflow runs in Python and is accessible as a python document in the repository (nypd_officer_360.py). The python document contains a link to a Google Colab notebook at the top, which can be used to view and copy the code in that application. The code can also be copy and pasted into a Python notebook in another application. 
Due to access restrictions, any changes made to the notebook in Colab will not save unless a copy is made. Making a copy immediately is recommended. 
The required libraries are listed here and at the beginning of the code: 
 
import requests  
import pandas as pd  
import io  
import matplotlib.pyplot as plt  
import seaborn as sns

* The code will generate a csv file. This can be saved and used as is, or opened in a spreadsheet viewer like Excel.
* Using the AirTable component is optional, but provides integrated metadata in the column headings. 

**AirTable instructions:**

The resulting csv can be uploaded into AirTable through the following link (recommend opening in a new tab): https://airtable.com/appwE4Y7weLf9rSru/shr6hBM2WKjwuM6Ve

* A **copy base** button should appear in the top left corner of the screen, next to the "Interactive Data Explorer" title. 
* The data can be uploaded by clicking on the carrot next to Manhattan Police Complaints
* Import data -> csv file (this will be the csv file you created using the python code above)
* The columns should automatically map to the pre-filled column headings, as long as no additional columns have been removed
* In "Other Settings" in the upload screen, toggle on "Exclude first row on import" to not duplicate column headings
* Note that AirTable has a limit of 50,000 records in one base. Filtering the data by borough should reduce the number of records to this amount
* If any further filtering or manipulation is done to the data in AirTable, the resulting information can be exported as a new csv file from AirTable

* The PowerPoint presentation in the folder provides some useful screenshots for using Airtable

**Note on Metadata**
* Hovering over the i icon in each column header will reveal information about the data in that column
* Column metadata and other useful data can be found in the adjoining tables 
  

## FAIR assessment 
This project integrates different datasets about the New York City Police Department that are available through the New York City Open Data portal. Each of the base data sets comes with a set of metadata (F, I, R) that clearly lays out how the data was created and have data dictionaries to go along with them to explain terms used (I). This metadata has been enhanced with further information from other sources, and will be provided as a set of metadata and explanation of terms to provide context for the information (A, I, R). The final dataset will be searchable to allow for easy information retrieval and will also be exportable as a csv file (F, I). The data and metadata can be reused by others following the steps outlined above (R). 

## Sources
The data used in this project comes from the NYC Open Data Portal, published by the City of New York https://opendata.cityofnewyork.us/
Information for the metadata provided in this project comes from the Data Dictionary published alongside the data in the Open Data Portal. It has been enhanced with information from the following sources: 
https://nypdonline.org/link/1026
https://www.nyc.gov/assets/nypd/downloads/pdf/public_information/post-final/body-worn-cameras-nypd-Impact-and-use-policy_2.4.26_final.pdf
https://www.nyclu.org/data/nypd-misconduct-database
https://www.nyc.gov/site/ccrb/complaints/file-a-complaint/file-complaint.page

