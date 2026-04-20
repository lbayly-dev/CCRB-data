# CCRB-data
An insight into NYPD Civilian Complaint Review Board data

# Project use:
This visualization allows the user to see the top 25 precints in which active NYPD officers have one or more complaints against them. This information is useful when evaluting the presence of officers in a particular community, and can allow for members of that community to advocate for better policing practices. It is also an interesting entry point to analyze other aspects of policing in New York, such as why certain specialized units have high numbers of complaints. 

# What can be done:
This code allows for some simple graphing of the data from the NYC Open Data portal. To have the most up to date data, the relevant csv file needds to be re-downloaded when the user wants to run the analysis. 

# How to install the required libraries:
import pandas as pd  

import matplotlib.pyplot as plt  

import seaborn as sns

# How to use: 
The code can be copied into Collab and run. The relevant dataset can be downloaded as a csv at this link: https://data.cityofnewyork.us/Public-Safety/Civilian-Complaint-Review-Board-Police-Officers/2fir-qns4/about_data. It will then need to be uploaded into the Collab space to be able to run the code. It is reliant on New York City continuing to publish it's data as an easily accessible source in csv format. 
