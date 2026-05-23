# CCRB-data
An insight into NYPD Civilian Complaint Review Board (CCRB) data

# Project background: 
This project came out of my experience working as a paralegal at the Manhattan District Attorney's Office. There were frequently acronyms and data that I did not understand, and had to find explanations for across different sources. Beyond merging three different csv files into one table, this project provides definitions for terms. These definitions are pulled together from what the NYC Open Data portal provides, NYPD documentation, and some of my own knowledge. 

# Project use & information story:
When a police officer engages in misconduct against a civilian in New York City, the civilian can lodge a complaint with the Civilian Complaint Review Board (CCRB), who will investigate the claim. The data about these complaints is made public by New York City, and published throught the NYC Open Data Portal. 
This workflow allows the user to more easily see and understand data related to complaints made against New York City Police Department officers. Having easy access to this information is valuable for members of the community to be informed about the history of conduct of law enforcement in their area. Because of the current state of policing in the United States, having transparency around police conduct has become more important. It is useful when evaluating the presence of officers in a particular community, and can allow for members of that community to advocate for better policing practices. Being able to access this information easily can also empower people who have been victims of police misconduct to file a complaint with the CCRB, rather than remaining silent. At the moment, the data that provides informaiton about NYPD officer conduct and the resulting allegations and complaints is spread out across three different datasets that are available through the NYC Open Data Portal. These datasets are downloadable as csv files, and the portal itself provides some quering capabilities. However, there is no option to combine the various datafiles into one place, which can make it harder to find information. For example, only the "Police Officers" file contains the names of the officers involved. The "Complaints" file does not include any information by which to identify the officer invovled in a complaint beyond a complaint ID, which has to be cross-referenced to the "Allegations" file. In files of this size, and using terminology that is not understandable to a lot of people, it can be an overwhelming task to find the relevant information. Therefore, creating an easier to understand information structure that has all the relevant information in one place is a valuable project. 

The raw data is drawn from the NYC Open Data Portal (https://data.cityofnewyork.us/browse?q=Data-Collection_Data-Collection%3DCCRB+Complaints+Database&sortBy=relevance&pageSize=20&page=1), and configured uisng Python code. The resulting csv file can be uploaded into an AirTable, which includes descriptions for each column to provide additional context to the user, and make the data more understandable and usable. This final product provides a comprehensive overview of police officer information, allegations, and complaints, all in one place, rather than spread out across multiple files. This also allows for searches to be done across multiple different officer identifiers, such as Tax ID, shield number, last name, rank, or precinct. The AirTable presentation of the data also includes notes in the column headings to explain what the data in that column means, so that the user does not have to go and look for that information elsewhere. If the user chooses not to use the AirTable component of this project, they can also reference the data as csv files attached to this GitHub. 
Therefore, this project amends the existing information structure in the following ways: 
* Information itself: data is filtered to only show what is relevant to the user. Comments throughout the code explain the modifications being made to the code, such as filtering only for officers that are active. The code can be adapted to the needs of the user, or run as is. 
* Access methodology: the data is no longer stuck in an overwhelming csv file, but can be viewed in a more easily understandable table through AirTable. 

# What can be done:
This workflow allows for the data to be pulled from the NYC Open Data portal and viewed in AirTable. AirTable functionalities allow for searching and filtering within the data. 

# How to install the required libraries:
The data configuration for this project occurs in Python, and is shared as a Google Colab notebook. The required libraries are listed here and at the beginning of the code: 

import requests  

import pandas as pd  

import io  

import matplotlib.pyplot as plt  

import seaborn as sns

# How to use code: 
The code can be opened directly in Colab using the button link. Alternatively, it can be copied and pasted into Colab or another Python notebook and used. It is reliant on New York City continuing to publish it's data as an easily accessible source in csv format. 
