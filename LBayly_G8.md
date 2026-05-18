About: 3-5 sentences of describing the use, audience and access of your information
This project is a tool to compile and present data about the NYPD, specifically as it relates to complaints and allegations made against NYPD officers due to misconduct. it provides
easer use and access to the information for end users who want to learn more about the NYPD officers in their area. The data is pulled from the NYC Open Data Portal as csv files, 
and then compiled into a single csv file that can be uploaded into AirTable for easier viewing. AirTable also provides additional metadata and explanation of domain specific
terminology. 

Methodology: 5-10 sentences or bullets describing how you generated the information structure and maintain it
- Python code hosted in Google Colab pulls three separate csv files from the NYC Open Data Portal. 
- Further code merges the csv files, and does some cleaning of the data to remove duplicate and unnecessary information. 
- A single csv file is generated, which can be uploaded to AirTable.
- AirTable provides metadata linked to each column heading to provide context for the data. The metadata is pulled from different sources, and is also available as a separate file. 
- The output can be updated every month when new data is uploaded to the city portal. 

Access: 5-10 sentences or bullets describing the steps a user takes to access the information
- Open Google Colab or another environment that can run Python
- Make a copy of or copy and paste the provided code to pull the csv files and merge them 
- Make any adjustments to the code in the specified places to generate the requested data 
- Run the code to generate csv file 
- Upload csv file to AirTable template. If not using AirTable with pre-filled metadata, download the supplied metadata term explanations 

Structure: Description of the main fields, types, properties of information schema
- The final structure is a csv file that can be displayed as a table in AirTable. 

Example: Show example request and response for at least one intended use of information that demonstrates access and structure

