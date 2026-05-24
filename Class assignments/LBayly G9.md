# NYPD Officer 360 Test Plan 

## Purpose
This document outlines the testing strategy for the NYPD Officer 360 project to ensure the quality, accuracy, and performance of the system. 

consideration for tests, alarms and actions. Consider both functional as well as performance tests. 



The quality of the output is highly dependent on the input. It relies on New York City continuing to publish this data through an openly accessible platform. If the format of the uploads is changed, this workflow will no longer work. To maintain this workflow, the Python code should be regularly checked to make sure that the pulls from the portal are still working as expected. It is also important to regularly check that column names have not be renamed, so that the column filtering contonues to work as expected. Similarly, the metadata provided for the columns should be regularly checked to make sure that the definitions or possible values that the city uses have not changed.

It is important that any users of this workflow duplicate the AirTable so that the original stays preserved with all the relevant columns and metadata. Ideally, the access use restrictions will make sure that this is the case.

## Test Objectives

- Ensure all key features function as expected
- Verify that the NYC Open Data Portal is providing data in the expected format
- Confirm that metadata is accurate to the data being provided

# Functional test 

| Test Case | Description | Method | Expected Result |
|-----------|-------------|--------|-----------------|
| CSV pull from portal| Make sure csvs can be accessed as expected | Manually run the code to pull each required csv | Code runs without errors |
| Adapt code to different boroughs | Change borough in code | Test each of the boroughs, Manhattan, Queens, Bronx, Brooklyn, Staten Island | Code will run without warning message |
| Single Valid Term | Text: `"liquidity"` | Manual or automated test | Returns correct definition |
| Mixed Valid & Invalid Terms | Text with `"liquidity"`, `"xzyterm"` | Text UI + GET `/definitions` | Valid terms returned, others skipped |
| Definition Fallback | Use a term with no `mntl-sc-block_2-0` but with `short-definition__text_1-0` | Unit test | Definition found via fallback |
| Frontend Error Handling | Kill backend + submit from frontend | Observe behavior | "Failed to fetch definitions" shown |
| CORS Access | Use live GitHub Pages frontend | DevTools Network tab | 200 from Azure API, no CORS errors |

