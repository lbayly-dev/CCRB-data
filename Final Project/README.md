# CCRB-data
An insight into NYPD Civilian Complaint Review Board (CCRB) data

## Project background: 
This project came out of my experience working as a paralegal at the Manhattan District Attorney's Office. There were frequently acronyms and data that I did not understand, and had to find explanations for across different sources. Beyond merging three different csv files into one table, this project provides definitions for terms. These definitions are pulled together from what the NYC Open Data portal provides, NYPD documentation, and some of my own knowledge. 

## Project use & information story:
When a police officer engages in misconduct against a civilian in New York City, the civilian can lodge a complaint with the Civilian Complaint Review Board (CCRB), who will investigate the claim. The data about these complaints is made public by New York City, and published throught the NYC Open Data Portal. 
This workflow allows the user to more easily see and understand data related to complaints made against New York City Police Department officers. Having easy access to this information is valuable for members of the community to be informed about the history of conduct of law enforcement in their area. Because of the current state of policing in the United States, having transparency around police conduct has become more important. It is useful when evaluating the presence of officers in a particular community, and can allow for members of that community to advocate for better policing practices. Being able to access this information easily can also empower people who have been victims of police misconduct to file a complaint with the CCRB, rather than remaining silent. At the moment, the data that provides informaiton about NYPD officer conduct and the resulting allegations and complaints is spread out across three different datasets that are available through the NYC Open Data Portal. These datasets are downloadable as csv files, and the portal itself provides some quering capabilities. However, there is no option to combine the various datafiles into one place, which can make it harder to find information. For example, only the "Police Officers" file contains the names of the officers involved. The "Complaints" file does not include any information by which to identify the officer invovled in a complaint beyond a complaint ID, which has to be cross-referenced to the "Allegations" file. In files of this size, and using terminology that is not understandable to a lot of people, it can be an overwhelming task to find the relevant information. Therefore, creating an easier to understand information structure that has all the relevant information in one place is a valuable project. 

The raw data is drawn from the NYC Open Data Portal (https://data.cityofnewyork.us/browse?q=Data-Collection_Data-Collection%3DCCRB+Complaints+Database&sortBy=relevance&pageSize=20&page=1), and configured uisng Python code. The resulting csv file can be uploaded into an AirTable, which includes descriptions for each column to provide additional context to the user, and make the data more understandable and usable. This final product provides a comprehensive overview of police officer information, allegations, and complaints, all in one place, rather than spread out across multiple files. This also allows for searches to be done across multiple different officer identifiers, such as Tax ID, shield number, last name, rank, or precinct. The AirTable presentation of the data also includes notes in the column headings to explain what the data in that column means, so that the user does not have to go and look for that information elsewhere. If the user chooses not to use the AirTable component of this project, they can also reference the data as csv files attached to this GitHub. Since the code automatically pulls the most recent data from the Open Data Portal, the user knows that they are working with the most up to date information, without having to manually download csv files. 
Therefore, this project amends the existing information structure in the following ways: 
* Information itself: data is filtered to only show what is relevant to the user. Comments throughout the code explain the modifications being made to the code, such as filtering only for officers that are active. The code can be adapted to the needs of the user, or run as is. 
* Access methodology: the data is no longer stuck in an overwhelming csv file, but can be viewed in a more easily understandable table through AirTable.

## How to use the workflow: 
The code to execute the workflow can be opened directly in Colab using the button link. Alternatively, it can be copied and pasted into Colab or another Python notebook and used. 
To use the AirTable format, 

## How to install the required libraries:
**Python instructions**
The data configuration for this project occurs in Python, and is shared as a Google Colab notebook. The required libraries are listed here and at the beginning of the code: 

import requests  

import pandas as pd  

import io  

import matplotlib.pyplot as plt  

import seaborn as sns

* The code will generate a csv file. This can be saved and used as is, or opened in a spreadsheet viewer like Excel.
* Using the AirTable component is optional, but provides integrated metadata in the column headings. 

**AirTable instructions**
If none of the columns is further edited from the code, the resulting csv can be uploaded into AirTable through the following link: https://airtable.com/invite/l?inviteId=invCxT6hEEdCLxNTH&inviteToken=a58d9ed4b56b18bab9b55d67f6a8b6585b8ae85d935595e6c3edc1720dc493da&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts 

* A **duplicate** of the table should be made by clicking on the carrot next to Interactive Data Explorer
* Click on the three dots on the right hand side of the menu
* Click duplicate base
  
* The data can be uploaded by clicking on the carrot next to Manhattan Police Complaints
* Import data -> csv file
* Note that AirTable has a limit of 50,000 records in one base. Filtering the data by borough should reduce the number of records to this amount
* Hovering over the i icon in each column header will reveal information about the data in that column
* If any further filtering or manipulation is done to the data in AirTable, the resulting information can be exported as a new csv file

## FAIR assessment 
This project integrates different datasets about the New York City Police Department that are available through the New York City Open Data portal. Each of the base data sets comes with a set of metadata (F, I, R) that clearly lays out how the data was created and have data dictionaries to go along with them to explain terms used (I). This metadata has been enhanced with further information from other sources, and will be provided as a set of metadata and explanation of terms to provide context for the information (A, I, R). The final dataset will be searchable to allow for easy information retrieval and will also be exportable as a csv file (F, I). The data and metadata can be reused by others following the steps outlined above (R). 

## Sources
The data used in this project comes from the NYC Open Data Portal, published by the City of New York https://opendata.cityofnewyork.us/
Information for the metadata provided in this project comes from the Data Dictionary published alongside the data in the Open Data Portal. It has been enhanced with information from the following sources: 
https://nypdonline.org/link/1026
https://www.nyc.gov/assets/nypd/downloads/pdf/public_information/post-final/body-worn-cameras-nypd-Impact-and-use-policy_2.4.26_final.pdf
https://www.nyclu.org/data/nypd-misconduct-database
https://www.nyc.gov/site/ccrb/complaints/file-a-complaint/file-complaint.page

