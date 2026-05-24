# NYPD Officer 360 Test Plan 

## Purpose
This document outlines the testing strategy for the NYPD Officer 360 project to ensure the quality, accuracy, and performance of the system. 

The quality of the output is highly dependent on the input. It relies on New York City continuing to publish this data through an openly accessible platform. If the format of the uploads is changed, this workflow will no longer work. To maintain this workflow, the Python code should be regularly checked to make sure that the pulls from the portal are still working as expected. It is also important to regularly check that column names have not be renamed, so that the column filtering contonues to work as expected. Similarly, the metadata provided for the columns should be regularly checked to make sure that the definitions or possible values that the city uses have not changed.

It is important that any users of this workflow duplicate the AirTable so that the original stays preserved with all the relevant columns and metadata. Ideally, the access use restrictions will make sure that this is the case.

## Test Objectives

- Ensure all key features function as expected
- Verify that the NYC Open Data Portal is providing data in the expected format
- Confirm that metadata is accurate to the data being provided

## 2. System Overview & Components Under Test

| Component | Description | 
|---|---|
| NYC Open Data API Pull | Python library pulls live CSVs from the Open Data Portal |
| Data Merge (pandas) | Three CSVs joined on Complaint ID and Tax ID; columns filtered and renamed | 
| Output CSV | Final merged file saved locally or exported for upload | 
| AirTable Upload | CSV imported into AirTable base; column metadata (hover text) maintained | 
| AirTable Access Controls | Invite-link sharing; duplication requirement to protect source base | 
| Column Metadata / Definitions | Hover-text descriptions on each AirTable column | 

---

## 3. Quality & Performance Objectives

| Objective | Target | Rationale |
|---|---|---|
| Data completeness | 0% missing values in required fields (Tax ID, Complaint ID, Officer Last Name) | Identity fields must be present to be useful |
| Record count accuracy | Merged row count matches the Allegations file row count ±0% | Allegations is the base join table; no records should be silently dropped |
| Column name stability | All expected column names present after every run | Downstream AirTable metadata breaks if columns are renamed or removed |
| Data availability | Data pull succeeds within 60 seconds per dataset | Colab sessions time out; long pulls indicate portal issues |
| AirTable record limit | Final filtered dataset ≤50,000 records per borough filter | AirTable free-tier limit |
| End-to-end runtime | Full pipeline completes in under 5 minutes | Practical usability in Colab |
| Schema change detection | Any added/removed columns flagged within 1 week of portal change | Portal can rename fields without notice |

---

## 4. Functional Tests

| Test Name | Steps | Expected Result | 
|---|---|---|
| Column presence check | After loading each CSV, assert all expected column names are present | No KeyError; all join keys (Tax ID, Complaint ID) exist |
| CSV pull from portal| Make sure csvs can be accessed as expected | Manually run the code to pull each required csv | Code runs without errors |
| Adapt code to different boroughs | Change borough in code | Test each of the boroughs, Manhattan, Queens, Bronx, Brooklyn, Staten Island | Code will run without warning message |
| CSV file created | Run full pipeline; check that output CSV exists at expected path | File exists and is non-empty |
| CSV imports into AirTable | Upload CSV via AirTable import flow | All rows imported; column headers mapped correctly and row count in AirTable matches CSV |
| Column metadata intact | After upload, hover over each column header; verify description text is present | All columns have their hover descriptions visible and no columns missing metadata |

---

## 5. Performance Tests

Performance tests verify the system behaves within acceptable time and scale limits under realistic conditions.

| Test Name | Method | Threshold | Action if Fails |
|---|---|---|---|
| Retrieval time per dataset | Check how long it takes to retrieve each csv file | Aim for < 60 seconds per dataset | Log warning |
| Full workflow runtime | Time full notebook execution from first cell to CSV creation| < 5 minutes total | Optimize or document exception |
| CSV file size | Check output file size after generation | < 100 MB (AirTable practical upload limit) | Apply additional column or row filtering before upload |
| AirTable upload time | Time the CSV import from start to confirmation | < 5 minutes for filtered dataset | Pre-filter to smaller dataset; contact AirTable support if persistent |
| AirTable search response | Run 5 searches by Last Name, Shield Number, and Tax ID; record response time | < 3 seconds per search | Review AirTable plan tier |

---

## 6. Data Quality Tests

These tests go beyond functional correctness to verify that the data content itself is meaningful, consistent, and trustworthy.

| Test Name | Method | Expected Result |
|---|---|---|
| Date field validity | Assert all complaint dates are within a plausible range (e.g., 1985–present) | No dates in the future; no dates before CCRB was established |
| Allegation type vocabulary | Check unique values in Allegation Type column against known CCRB taxonomy | No unexpected free-text values; all values match known categories |
| Precinct code validity | Assert all precinct numbers are integers within 1–123 (valid NYPD precincts) | No out-of-range or non-numeric precinct values |
| Cross-file consistency | Sample 20 Complaint IDs; verify officer Tax ID matches across all three source files | 100% consistency on sampled records |
| Definition currency | Manually review column metadata against current NYC Open Data data dictionary and other relevant sources | All definitions match current portal documentation |

---

## 7. Alarms & Ongoing Monitoring

Because the system depends on an external data source (NYC Open Data) and a third-party platform (AirTable), conditions can change without notice. The following monitoring strategy ensures issues are caught early.

Within code:
- Statement that alerts if the borough entered is not one of the five in New York City
  
Manually: 
- Regularly run full workflow to ensure that it works as expected
- Review NYC Open Portal data dictionary to see whether there are any chnages or updates to column names and definitions
- Confirm that link to AirTable still works for other users

| Action | Action if failed | 
|---|---|
| Regularly run full workflow to ensure that it works as expected | Check where issues arise, document, remedy | 
| Review NYC Open Portal data dictionary to see whether there are any chnages or updates to column names and definitions| Document, update metadata descriptions in AirTable and Column Definitions csv |
| Confirm that link to AirTable still works for other users | Creat new share link and make a note in GitHub | 

---
