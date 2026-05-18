# About
This project is a tool to compile and present data about the NYPD, specifically as it relates to complaints and allegations made against NYPD officers due to misconduct. it provides easer use and access to the information for end users who want to learn more about the NYPD officers in their area. The data is pulled from the NYC Open Data Portal as csv files, and then compiled into a single csv file that can be uploaded into AirTable for easier viewing. AirTable also provides additional metadata and explanation of domain specific terminology. 

# Methodology
- Python code hosted in Google Colab pulls three separate csv files from the NYC Open Data Portal. 
- Further code merges the csv files, and does some cleaning of the data to remove duplicate and unnecessary information. 
- A single csv file is generated, which can be uploaded to AirTable.
- AirTable provides metadata linked to each column heading to provide context for the data. The metadata is pulled from different sources, and is also available as a separate file. 
- The output can be updated every month when new data is uploaded to the city portal. 

# Access
- Open Google Colab or another environment that can run Python
- Make a copy of or copy and paste the provided code to pull the csv files and merge them 
- Make any adjustments to the code in the specified places to generate the requested data 
- Run the code to generate csv file 
- Upload csv file to AirTable template. If not using AirTable with pre-filled metadata, download the supplied metadata term explanations 

# Structure
- The final structure is a csv file that can be displayed as a table in AirTable.
- Most of the fields are strings. Some of them are dates.

# Example
```
import requests
import pandas as pd
import io

# Downloading police officer csv 
csv_url = 'https://data.cityofnewyork.us/api/views/2fir-qns4/rows.csv?accessType=DOWNLOAD'

try:
    # Send a GET request to the URL
    response = requests.get(csv_url)
    response.raise_for_status() # Raise an exception for HTTP errors (4xx or 5xx)

    # Read the content into a pandas DataFrame
    df = pd.read_csv(io.StringIO(response.text))

# Downloading allegations csv 
allegations_url = 'https://data.cityofnewyork.us/api/views/6xgr-kwjq/rows.csv?accessType=DOWNLOAD'

try:
    response_allegations = requests.get(allegations_url)
    response_allegations.raise_for_status()
    df_allegations = pd.read_csv(io.StringIO(response_allegations.text))

# Downloading complaints csv 
complaints_url = 'https://data.cityofnewyork.us/api/views/2mby-ccnw/rows.csv?accessType=DOWNLOAD'

try:
    response_complaints = requests.get(complaints_url)
    response_complaints.raise_for_status()
    df_complaints = pd.read_csv(io.StringIO(response_complaints.text))

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Filter file for active officers
filtered_df = (df['Active Per Last Reported Status'] == 'Yes')

# Convert filtered_df Series to a DataFrame containing only active officers
active_officers_df = df[filtered_df].copy()

# Perform an inner join between active_officers_df and df_allegations on 'Tax ID'
merged_active_officers_allegations = pd.merge(active_officers_df, df_allegations, on='Tax ID', how='inner', suffixes=('_officer', '_allegation'))

print(merged_active_officers_allegations.columns.tolist())

# Perform an inner join between merged_active_officers_allegations and df_complaints on 'Complaint Id'
merged_active_officers_allegations_complaints = pd.merge(merged_active_officers_allegations, df_complaints, on='Complaint Id', how='inner', suffixes=('_allegation_complaint', '_incident_detail'))

print(merged_active_officers_allegations_complaints.columns.tolist())

# Filter file for incidents in Manhattan
filtered_merged_df = merged_active_officers_allegations_complaints[merged_active_officers_allegations_complaints['Borough Of Incident Occurrence'] == 'Manhattan'].copy()

columns_to_drop = [col for col in filtered_merged_df.columns if 'Tax ID' in col and col != 'Tax ID_combined']

# Drop the identified columns
filtered_merged_df = filtered_merged_df.drop(columns=columns_to_drop)

date_columns = [
    'As Of Date_officer',
    'As Of Date_allegation',
    'As Of Date',
    'Incident Date',
    'CCRB Received Date',
    'Close Date'
]

for col in date_columns:
    if col in filtered_merged_df.columns:
        # Convert to datetime, coercing errors will turn unparseable dates into NaT (Not a Time)
        filtered_merged_df[col] = pd.to_datetime(filtered_merged_df[col], errors='coerce')
        # Format as 'YYYY-MM-DD' string, NaT values will become NaN
        filtered_merged_df[col] = filtered_merged_df[col].dt.strftime('%Y-%m-%d')

# Select the first 100 rows
first_100_rows_df = filtered_merged_df.head(100)

# Export the filtered DataFrame to a CSV file
output_filename_100_rows = 'manhattan_police_complaints_100_rows.csv'
first_100_rows_df.to_csv(output_filename_100_rows, index=False)

from google.colab import files
files.download('manhattan_police_complaints_100_rows.csv')
```

