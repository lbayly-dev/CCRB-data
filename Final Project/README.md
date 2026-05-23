# CCRB-data
An insight into NYPD Civilian Complaint Review Board data

# Project use:
This workflow allows the user to more easily see and understand data related to complaints made against New York City Police Department officers. This information is useful when evaluting the presence of officers in a particular community, and can allow for members of that community to advocate for better policing practices. The raw data is drawn from the NYC Open Data Portal, and configured uisng Python code. The resulting csv file can be uploaded into an AirTable, which includes descriptions for each column to provide additional context to the user, and make the data more understandable and usable. This final product provides a comprehensive overview of police officer information, allegations, and complaints, all in one place, rather than spread out across multiple files. This also allows for searches to be done across multiple different officer identifiers, such as Tax ID, shield number, last name, rank, or precinct. The raw data files do not each include the entirety of this information, meaning that users would have to cross-reference multiple large tables. 

# Project background: 
This project came out of my experience working as a paralegal at the Manhattan District Attorney's Office. There were frequently acronyms and data that I did not understand, and had to find explanations for across different sources. Beyond merging three different csv files into one table, this project provides definitions for terms. These definitions are pulled together from what the NYC Open Data portal provides, NYPD documentation, and some of my own knowledge. 

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
